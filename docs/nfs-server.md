# NFS Structure
这个咚咚真的是很简单，上面我们提到的 NFS 软件中，配置文件只有一个，执行档也不多， 记录文件也三三两两而已吶！赶紧先来看一看吧！ ^_^

## 主要配置文件：/etc/exports
这个档案就是 NFS 的主要配置文件了！不过，系统并没有默认值，所以这个档案『 不一定会存在』，你可能必须要使用 vim 主动的建立起这个档案喔！我们等一下要谈的设定也仅只是这个档案而已吶！

##  文件系统维护指令：/usr/sbin/exportfs
这个是维护 NFS 分享资源的指令，我们可以利用这个指令重新分享 /etc/exports 变更的目录资源、将 NFS Server 分享的目录卸除或重新分享等等，这个指令是 NFS 系统里面相当重要的一个喔！至于指令的用法我们在底下会介绍。

## 源的登录档：/var/lib/nfs/*tab
在 NFS 服务器的登录文件都放置到 /var/lib/nfs/ 目录里面，在该目录下有两个比较重要的登录档， 一个是 etab ，主要记录了 NFS 所分享出来的目录的完整权限设定值；另一个 xtab 则记录曾经链接到此 NFS 服务器的相关客户端数据。

## 查询服务器分享资源的指令：/usr/sbin/showmount
这是另一个重要的 NFS 指令。exportfs 是用在 NFS Server 端，而 showmount 则主要用在 Client 端。这个 showmount 可以用来察看 NFS 分享出来的目录资源喔！

# NFS start
```bash
[root@www ~]# /etc/init.d/rpcbind start
# 如果 rpcbind 本来就已经在执行了，那就不需要启动啊！

[root@www ~]# /etc/init.d/nfs start
# 有时候某些 distributions 可能会出现如下的警告讯息：
exportfs: /etc/exports [3]: No 'sync' or 'async' option specified 
for export "192.168.100.10:/home/test".
  Assuming default behaviour ('sync').
# 上面的警告讯息仅是在告知因为我们没有指定 sync 或 async 的参数，
# 则 NFS 将默认会使用 sync 的信息而已。你可以不理他，也可以加入 /etc/exports。

[root@www ~]# /etc/init.d/nfslock start
[root@www ~]# chkconfig rpcbind on
[root@www ~]# chkconfig nfs on
[root@www ~]# chkconfig nfslock on
```

# Problem Met
## readonly file system?
/etc/exports hold the control

# refs
http://cn.linux.vbird.org/linux_server/0330nfs.php
https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/5/html/deployment_guide/s1-nfs-server-config-exports

