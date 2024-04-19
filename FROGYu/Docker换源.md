## 1.阿里云个人镜像获取

访问：[阿里云官网--镜像服务](https://cr.console.aliyun.com/)

![img](https://img-blog.csdnimg.cn/cfcef6d06c3e40699888e55af5d92f1e.png)

绿色箭头处即为自己的个人加速器地址。

## 2.在Ubuntu添加镜像源

### 2.1.修改镜像地址

修改/etc/docker/daemon.json（如果没有则新建此文件）

```
cd /etc/docker  #进入文件夹查看是否存在这个文件daemon.json

ls

#如果没有,就新建一个
sudo touch daemon.json

#修改这个文件内容,添加镜像内容

sudo vim /etc/docker/daemon.json
#不熟悉vim的人:
输入sudo vim /etc/docker/daemon.json按i键进行编辑,然后粘贴过去自己的镜像内容,格式在下面,然后按esc键,然后输入:wq 回车,就能保存成功
```

内容如下：

```
{
  "registry-mirrors": ["你的源地址"]
}
```



### 2.重新加载并重启docker

```bash
sudo systemctl daemon-reload
sudo systemctl restart docker
```

### 3.验证

执行如下命令：

```undefined
docker info
```

![image-20240417195115016](C:\Users\35628\AppData\Roaming\Typora\typora-user-images\image-20240417195115016.png)

出现这个就是正确配置好了

然后回去再执行下载,就很快