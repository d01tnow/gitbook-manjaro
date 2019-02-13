# Pacman

## 常用命令

```shell

## 交互方式(-i)按i排名（-m rank)设置中国(-c China)源
## 在弹出的列表框里勾选需要设置的源， 推荐 ustc
sudo pacman-mirrors -i -c China -m rank

## 同步源
pacman -Sy
## 刷新缓存
pacman -Syy
## 同步源，并更新系统
pacman -Syu

## 提高数据库访问速度
pacman-optimize && sync

## 安装软件
pacman -S package
## 同步源后安装软件
pacman -Sy package
## 搜索软件
pacman -Ss package
## 从数据库中搜索包package的信息
pacman -Si package

## 清理/var/cache/pacman/pkg目录下的旧包
pacman -Sc
## 清除所有下载的包和数据库
pacman -Scc

## 删除 package 包
pacman -R package
## 移除包所有不需要的依赖包并删除其配置文件
## Pacman不会删除软件包安装后才创建的配置文件。你可以从你的home文件夹中手动删除它们。
pacman -Rsn package
## 删包和对应的依赖包，而且软件名称可以只输入主名称
pacman -Rsncd package
## 删除孤立软件包（递归的,小心用)
pacman -Rs $(pacman -Qtdq)
## 升级时不升级包foo
pacman -Su --ignore foo
## 安装下载的abs包，或新编译的本地package包
pacman -U   package.pkg.tar.gz
## 查询package这个包组包含的软件包
pacman -Sg package

## 列出系统中所有的包
pacman -Q
## 在本地包数据库搜索(查询)指定软件包
pacman -Q package
## 在本地包数据库搜索(查询)指定软件包并列出相关信息
pacman -Qi package
## 找出孤立包
pacman -Qdt
```

### keys 错误时解决方案

```shell
rm -rf /etc/pacman.d/gnupg   # 移除旧的keys
pacman-key --init            # 确保密匙环已正确初始化
pacman-key --populate archlinux manjaro  # 从 (给定的) 密匙环中重新加载默认密匙
pacman-key --refresh-keys  # 从密匙服务器中更新指定的或所有的密匙
pacman -Sc # 清空并且下载新数据
pacman -Syu # 更新
pacman -Syy   # 更新源数据库
pacman -Syyu  # 安装更新
```
