---
title: "mounttree"
date: 2014-11-28T10:29:06+01:00
---

If you think this is confusing ...

<pre>
$ mount
</pre>
<font size="-2">
<pre>
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,relatime,size=10240k,nr_inodes=1008105,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,relatime,size=1616484k,mode=755)
/dev/mapper/benz-root on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=22,pgrp=1,timeout=300,minproto=5,maxproto=5,direct)
mqueue on /dev/mqueue type mqueue (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
/dev/sda1 on /boot type ext2 (rw,relatime)
/dev/mapper/benz-home on /home type ext4 (rw,relatime,data=ordered)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,relatime)
tmpfs on /run/user/124 type tmpfs (rw,nosuid,nodev,relatime,size=808244k,mode=700,uid=124,gid=131)
/dev/mapper/benz-home on /var/lib/schroot/mount/sid-amd64-ed5e5176-2c0f-4708-b259-663d20011b26 type ext4 (rw,relatime,data=ordered)
proc on /var/lib/schroot/mount/sid-amd64-ed5e5176-2c0f-4708-b259-663d20011b26/proc type proc (rw,nosuid,nodev,noexec,relatime)
sysfs on /var/lib/schroot/mount/sid-amd64-ed5e5176-2c0f-4708-b259-663d20011b26/sys type sysfs (rw,nosuid,nodev,noexec,relatime)
udev on /var/lib/schroot/mount/sid-amd64-ed5e5176-2c0f-4708-b259-663d20011b26/dev type devtmpfs (rw,relatime,size=10240k,nr_inodes=1008105,mode=755)
devpts on /var/lib/schroot/mount/sid-amd64-ed5e5176-2c0f-4708-b259-663d20011b26/dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
/dev/mapper/benz-home on /var/lib/schroot/mount/sid-amd64-ed5e5176-2c0f-4708-b259-663d20011b26/home type ext4 (rw,relatime,data=ordered)
/dev/mapper/benz-root on /var/lib/schroot/mount/sid-amd64-ed5e5176-2c0f-4708-b259-663d20011b26/tmp type ext4 (rw,relatime,errors=remount-ro,data=ordered)
/dev/mapper/benz-home on /var/lib/schroot/mount/sid-amd64-ed5e5176-2c0f-4708-b259-663d20011b26/srv type ext4 (rw,relatime,data=ordered)
/dev/mapper/benz-root on /var/lib/schroot/mount/sid-amd64-ed5e5176-2c0f-4708-b259-663d20011b26/media type ext4 (rw,relatime,errors=remount-ro,data=ordered)
//newton/credativ on /credativ/credativ type cifs (rw,nosuid,nodev,noexec,relatime,vers=1.0,cache=strict,username=cbe,domain=CREDATIV,uid=0,noforceuid,gid=0,noforcegid,addr=172.26.14.2,unix,posixpaths,serverino,acl,rsize=1048576,wsize=65536,actimeo=1,user)
//newton/cbe on /credativ/cbe type cifs (rw,nosuid,nodev,noexec,relatime,vers=1.0,cache=strict,username=cbe,domain=CREDATIV,uid=0,noforceuid,gid=0,noforcegid,addr=172.26.14.2,unix,posixpaths,serverino,acl,rsize=1048576,wsize=65536,actimeo=1,user)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
devpts on /var/lib/schroot/mount/sid-amd64-ed5e5176-2c0f-4708-b259-663d20011b26/dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run/user/2062 type tmpfs (rw,nosuid,nodev,relatime,size=808244k,mode=700,uid=2062,gid=2062)
gvfsd-fuse on /run/user/2062/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=2062,group_id=2062)
/dev/mapper/benz-home on /var/lib/schroot/mount/wheezy-i386-a6e9e772-1061-4587-8321-c1615f21ebb2 type ext4 (rw,relatime,data=ordered)
proc on /var/lib/schroot/mount/wheezy-i386-a6e9e772-1061-4587-8321-c1615f21ebb2/proc type proc (rw,nosuid,nodev,noexec,relatime)
sysfs on /var/lib/schroot/mount/wheezy-i386-a6e9e772-1061-4587-8321-c1615f21ebb2/sys type sysfs (rw,nosuid,nodev,noexec,relatime)
udev on /var/lib/schroot/mount/wheezy-i386-a6e9e772-1061-4587-8321-c1615f21ebb2/dev type devtmpfs (rw,relatime,size=10240k,nr_inodes=1008105,mode=755)
devpts on /var/lib/schroot/mount/wheezy-i386-a6e9e772-1061-4587-8321-c1615f21ebb2/dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
devpts on /var/lib/schroot/mount/sid-amd64-ed5e5176-2c0f-4708-b259-663d20011b26/dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
/dev/mapper/benz-home on /var/lib/schroot/mount/wheezy-i386-a6e9e772-1061-4587-8321-c1615f21ebb2/home type ext4 (rw,relatime,data=ordered)
/dev/mapper/benz-root on /var/lib/schroot/mount/wheezy-i386-a6e9e772-1061-4587-8321-c1615f21ebb2/tmp type ext4 (rw,relatime,errors=remount-ro,data=ordered)
/dev/mapper/benz-home on /var/lib/schroot/mount/wheezy-i386-a6e9e772-1061-4587-8321-c1615f21ebb2/srv type ext4 (rw,relatime,data=ordered)
/dev/mapper/benz-root on /var/lib/schroot/mount/wheezy-i386-a6e9e772-1061-4587-8321-c1615f21ebb2/media type ext4 (rw,relatime,errors=remount-ro,data=ordered)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
devpts on /var/lib/schroot/mount/sid-amd64-ed5e5176-2c0f-4708-b259-663d20011b26/dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
devpts on /var/lib/schroot/mount/wheezy-i386-a6e9e772-1061-4587-8321-c1615f21ebb2/dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
</pre>
</font>

... try <a href="http://svn.df7cb.de/dotfiles/cb/bin/mounttree">mounttree</a>:

<pre>
$ mounttree
</pre>
<font size="-3">
<pre>
/                               rootfs                          rw
/                               /dev/mapper/benz-root (ext4)    rw,relatime,errors=remount-ro,data=ordered
  boot                          /dev/sda1 (ext2)                rw,relatime
  credativ/cbe                  //newton/cbe (cifs)             rw,nosuid,nodev,noexec,relatime,vers=1.0,cache=strict,username=cbe,domain=CREDATIV,uid=0,noforceuid,gid=0,noforcegid,addr=172.26.14.2,unix,posixpaths,serverino,acl,rsize=1048576,wsize=65536,actimeo=1
  credativ/credativ             //newton/credativ (cifs)        rw,nosuid,nodev,noexec,relatime,vers=1.0,cache=strict,username=cbe,domain=CREDATIV,uid=0,noforceuid,gid=0,noforcegid,addr=172.26.14.2,unix,posixpaths,serverino,acl,rsize=1048576,wsize=65536,actimeo=1
  dev                           udev (devtmpfs)                 rw,relatime,size=10240k,nr_inodes=1008105,mode=755
    hugepages                   hugetlbfs                       rw,relatime
    mqueue                      mqueue                          rw,relatime
    pts                         devpts                          rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000
    pts                         devpts                          rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000
    pts                         devpts                          rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000
    pts                         devpts                          rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000
    pts                         devpts                          rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000
    shm                         tmpfs                           rw,nosuid,nodev
  home                          /dev/mapper/benz-home (ext4)    rw,relatime,data=ordered
  proc                          proc                            rw,nosuid,nodev,noexec,relatime
    sys/fs/binfmt_misc          systemd-1 (autofs)              rw,relatime,fd=22,pgrp=1,timeout=300,minproto=5,maxproto=5,direct
    sys/fs/binfmt_misc          binfmt_misc                     rw,relatime
  run                           tmpfs                           rw,nosuid,relatime,size=1616484k,mode=755
    lock                        tmpfs                           rw,nosuid,nodev,noexec,relatime,size=5120k
    user/124                    tmpfs                           rw,nosuid,nodev,relatime,size=808244k,mode=700,uid=124,gid=131
    user/2062                   tmpfs                           rw,nosuid,nodev,relatime,size=808244k,mode=700,uid=2062,gid=2062
      gvfs                      gvfsd-fuse (fuse.gvfsd-fuse)    rw,nosuid,nodev,relatime,user_id=2062,group_id=2062
  sys                           sysfs                           rw,nosuid,nodev,noexec,relatime
    fs/cgroup                   tmpfs                           ro,nosuid,nodev,noexec,mode=755
      blkio                     cgroup                          rw,nosuid,nodev,noexec,relatime,blkio
      cpu,cpuacct               cgroup                          rw,nosuid,nodev,noexec,relatime,cpu,cpuacct
      cpuset                    cgroup                          rw,nosuid,nodev,noexec,relatime,cpuset
      devices                   cgroup                          rw,nosuid,nodev,noexec,relatime,devices
      freezer                   cgroup                          rw,nosuid,nodev,noexec,relatime,freezer
      net_cls,net_prio          cgroup                          rw,nosuid,nodev,noexec,relatime,net_cls,net_prio
      perf_event                cgroup                          rw,nosuid,nodev,noexec,relatime,perf_event
      systemd                   cgroup                          rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd
    fs/fuse/connections         fusectl                         rw,relatime
    fs/pstore                   pstore                          rw,nosuid,nodev,noexec,relatime
    kernel/debug                debugfs                         rw,relatime
    kernel/security             securityfs                      rw,nosuid,nodev,noexec,relatime
  var/lib/schroot/mount/sid-amd64-ed5e5176-2c0f-4708-b259-663d20011b26  /dev/mapper/benz-home (ext4)    rw,relatime,data=ordered
    dev                         udev (devtmpfs)                 rw,relatime,size=10240k,nr_inodes=1008105,mode=755
      pts                       devpts                          rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000
      pts                       devpts                          rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000
      pts                       devpts                          rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000
      pts                       devpts                          rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000
    home                        /dev/mapper/benz-home (ext4)    rw,relatime,data=ordered
    media                       /dev/mapper/benz-root (ext4)    rw,relatime,errors=remount-ro,data=ordered
    proc                        proc                            rw,nosuid,nodev,noexec,relatime
    srv                         /dev/mapper/benz-home (ext4)    rw,relatime,data=ordered
    sys                         sysfs                           rw,nosuid,nodev,noexec,relatime
    tmp                         /dev/mapper/benz-root (ext4)    rw,relatime,errors=remount-ro,data=ordered
  var/lib/schroot/mount/wheezy-i386-a6e9e772-1061-4587-8321-c1615f21ebb2  /dev/mapper/benz-home (ext4)    rw,relatime,data=ordered
    dev                         udev (devtmpfs)                 rw,relatime,size=10240k,nr_inodes=1008105,mode=755
      pts                       devpts                          rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000
      pts                       devpts                          rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000
    home                        /dev/mapper/benz-home (ext4)    rw,relatime,data=ordered
    media                       /dev/mapper/benz-root (ext4)    rw,relatime,errors=remount-ro,data=ordered
    proc                        proc                            rw,nosuid,nodev,noexec,relatime
    srv                         /dev/mapper/benz-home (ext4)    rw,relatime,data=ordered
    sys                         sysfs                           rw,nosuid,nodev,noexec,relatime
    tmp                         /dev/mapper/benz-root (ext4)    rw,relatime,errors=remount-ro,data=ordered
</pre>
</font>
