[[!meta title="Cool Unix Features: df -T"]]

Just discovered (thanks to XTaran): *df -T* -- show file system type.

    $ df -Th
    Filesystem    Type    Size  Used Avail Use% Mounted on
    /dev/mapper/benz-root
                  ext3    6.6G  4.9G  1.4G  79% /
    tmpfs        tmpfs    1.6G     0  1.6G   0% /lib/init/rw
    udev         tmpfs    1.6G  228K  1.6G   1% /dev
    tmpfs        tmpfs    1.6G     0  1.6G   0% /dev/shm
    /dev/sda1     ext3    236M   21M  203M  10% /boot
    /dev/mapper/benz-home
                  ext3    135G   82G   53G  61% /home
    newton:/home   nfs    459G  145G  291G  34% /nfs

[[!tag debian unix]]
