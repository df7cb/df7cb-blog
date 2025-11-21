We have this PostgreSQL server with plenty of RAM that is still using some of
its swap over the day (up to 600MB). Then suddenly everything is swapped in
again.

<img src="http://www.df7cb.de/blog/2012/dbsrv_swap.png">

It turned out the reason is there are two clusters running, and the second one
isn't used as heavily as the first one. Disk I/O activity of the first cluster
slowly evicts pages from the second shared buffers cache to swap, and then the
daily pg_dump run reads them back every evening.

I was not aware of an easy way to get numbers for "amount of SysV shared memory
swapped to disk", but some googling led to shmctl(2):

<pre>
#define _GNU_SOURCE 1
#include &lt;sys/ipc.h&gt;
#include &lt;sys/shm.h&gt;
#include &lt;stdio.h&gt;
#include &lt;unistd.h&gt;

int main ()
{
        struct shm_info info;
        int max;
        long PAGE_SIZE = sysconf(_SC_PAGESIZE);

        max = shmctl(0, SHM_INFO, (struct shmid_ds *) &info);
        printf ("max: %d\nshm_tot: %ld\nshm_rss: %ld\nshm_swp: %ld\n",
                        max,
                        info.shm_tot * PAGE_SIZE,
                        info.shm_rss * PAGE_SIZE,
                        info.shm_swp * PAGE_SIZE);

        return 0;
}
</pre>

The output looks like this:

<pre>
max: 13
shm_tot: 13232308224
shm_rss: 12626661376
shm_swp: 601616384
</pre>

<b>Update:</b> Mark points out that *ipcs -mu* shows the same information. Thanks for the hint!

<pre>
# ipcs -mu

------ Shared Memory Status --------
segments allocated 2
pages allocated 3230544
pages resident  3177975
pages swapped   51585
Swap performance: 0 attempts     0 successes
</pre>

[[!tag debian postgresql]]
