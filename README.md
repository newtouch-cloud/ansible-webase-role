基于 ansible 的 WeBase 自动化部署
=========

自动化部署 [WeBase](https://github.com/WeBankFinTech/WeBASE) 区块链通用组件。

ansible 执行环境
--------------

* Linux 系统
* ansible 2.10+
* python3
* python-netaddr
* sshpass
* docker

WeBase 运行环境
--------------

* 已部署了 FISCO BCOS 的节点。推荐使用[一键生成 FISCO-BCOS 企业级架构部署](https://github.com/newtouch-cloud/ansible-for-fisco-bcos)。
* 其它依赖关系请查看 [WeBase 官方文档](https://webasedoc.readthedocs.io/zh_CN/latest/docs/WeBASE-Install/index.html)

Role 变量
--------

请查看 `defaults/main.yml` 内的说明。

Playbook 用例
------------

```
- hosts: fisco_bcos_nodes
  roles:
     - name: newtouch.webase
       tags: webase
```

License
-------

GPL-2

贡献者
-----

本项目由 [FISCO BCOS 自动化工具兴趣小组](https://github.com/FISCO-BCOS/Wiki/blob/master/FISCO%20BCOS%E8%87%AA%E5%8A%A8%E5%8C%96%E5%B7%A5%E5%85%B7%E7%A0%94%E5%8F%91%E5%85%B4%E8%B6%A3%E5%B0%8F%E7%BB%84README.md) 成员共同编写。
