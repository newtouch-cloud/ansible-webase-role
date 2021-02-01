基于 ansible 的 WeBASE 企业级自动化部署
=========

自动化部署 [WeBASE](https://github.com/WeBankFinTech/WeBASE) 区块链通用组件。

可部署以下组件：

* WeBASE-Sign
* WeBASE-Front

ansible 执行环境
--------------

Linux 系统，并安装以下依赖。

* ansible 2.10+
* sshpass
* git
* python
* python-pip
* python-netaddr

如果你需要使用 Docker 方式部署，请增加以下依赖。

* docker
* python-docker

WeBASE 运行环境
--------------

* 已部署了 FISCO BCOS 的节点。推荐使用[一键生成 FISCO-BCOS 企业级架构部署](https://github.com/newtouch-cloud/ansible-for-fisco-bcos)。
* 其它依赖关系请查看 [WeBASE 官方文档](https://webasedoc.readthedocs.io/zh_CN/latest/docs/WeBASE-Install/index.html)。例如 MySQL 服务需另行搭建。

Role 变量
--------

请查看 `defaults/main.yml` 文件内的注释说明。

Playbook 用例
------------

首先在你的项目下安装这个 role。编写 ansible-roles.yml 文件，内容如下：

```
- src: https://github.com/newtouch-cloud/ansible-webase-role.git
  version: develop
  name: newtouch.webase
```

然后执行

```
ansible-galaxy install -r ansible-roles.yml
```

inventory 实例

```
webase-1 ansible_host=172.17.8.101
webase-2 ansible_host=172.17.8.102
webase-3 ansible_host=172.17.8.103
webase-4 ansible_host=172.17.8.104
webase-5 ansible_host=172.17.8.105
webase-6 ansible_host=172.17.8.106

# WeBASE-Front 群组内节点必须是已经部署了 fisco bcos 节点服务。
[group_webase_front]
webase-[1:6]

[group_webase_sign]
webase-6
```

Playbook 示例

```
- hosts: group_webase_sign
  vars:
    project: webase_sign
  roles:
     - role: newtouch.webase
       tags: sign
```

License
-------

GPL-2

贡献者
-----

本项目由 [FISCO BCOS 自动化工具兴趣小组](https://github.com/FISCO-BCOS/Wiki/blob/master/FISCO%20BCOS%E8%87%AA%E5%8A%A8%E5%8C%96%E5%B7%A5%E5%85%B7%E7%A0%94%E5%8F%91%E5%85%B4%E8%B6%A3%E5%B0%8F%E7%BB%84README.md) 成员共同编写。
