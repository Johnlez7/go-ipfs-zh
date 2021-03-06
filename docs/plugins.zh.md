
# 插件

从 0.4.11 开始,go-ipfs有一个实验性的插件系统,可以在不重新编译的情况下扩充守护进程功能. 

创建IPFS节点时,它将从`$IPFS_PATH/plugins`目录加载插件 (默认情况下`~/.ipfs/plugins`) . 

### 插件类型

#### IPLD

IPLD插件增加了对其他格式的支持 到`ipfs dag`和其他与IPLD相关的命令. 

### 支持的插件

| 名称  | 类型   |
| --- | ---- |
| git  | IPLD |

#### 安装

##### Linux

1.  构建包含的插件: 

```bash
go-ipfs$ make build_plugins
go-ipfs$ ls plugin/plugins/*.so
```

3.  将所需的插件复制到`$IPFS_PATH/plugins`

```bash
go-ipfs$ mkdir -p ~/.ipfs/plugins/
go-ipfs$ cp plugin/plugins/git.so ~/.ipfs/plugins/
go-ipfs$ chmod +x ~/.ipfs/plugins/git.so # ensure plugin is executable
```

4.  如果守护程序正在运行,请重新启动它

##### 其他

Go目前仅支持Linux上的插件,对于其他平台,您需要将它们编译为 IPFS二进制文件. 

1.  取消插件的相关注释在`plugin/loader/preload_list`
2.  构建ipfs

```bash
go-ipfs$ make build
```
