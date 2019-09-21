# df
用于显示硬盘的使用情况，包括文件系统所在硬盘分区的总容量、已使用的容量、剩余容量等。

- -a: 显示所有文件信息
- -h: 使用习惯单位显示容量

```
vagrant@ubuntu:/data/www/skill$ df -h
Filesystem                   Size  Used Avail Use% Mounted on
udev                         981M     0  981M   0% /dev
tmpfs                        201M  3.3M  197M   2% /run
/dev/mapper/ubuntu--vg-root   28G   15G   12G  55% /
tmpfs                       1001M  4.0K 1001M   1% /dev/shm
tmpfs                        5.0M     0  5.0M   0% /run/lock
tmpfs                       1001M     0 1001M   0% /sys/fs/cgroup
/dev/sda1                    472M   58M  390M  13% /boot
/home/vagrant/.Private        28G   15G   12G  55% /home/vagrant
vagrant                      466G   50G  417G  11% /vagrant
data_www                     466G   50G  417G  11% /data/www
tmpfs                        201M     0  201M   0% /run/user/1000
```

# du
统计目录或文件所占磁盘空间大小

- -a: 显示每个子文件的磁盘占用量
- -h: 使用习惯单位显示磁盘占用量
- -s: 统计磁盘总占用量，而不列出子文件和子目录的磁盘占用量
