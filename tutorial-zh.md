# 使用 Ansible 管理云资源

## 简介

[Ansible](https://www.ansible.com) 是一个开源的用于自动执行资源的配置管理和应用程序部署产品。云命令行已经为您安装、配置完成 Ansible v2.8.5，您可以直接使用。同时阿里云提供了 Ansible 的 [阿里云模块](https://github.com/alibaba/ansible-provider)。

利用该该模块您可以通过 Ansible 非常方便管理您的阿里云资源，同时，您还可以使用 Ansible 在环境中自动配置资源和部署应用。

本教程介绍了如何使用 Ansible 来管理阿里云资源以及部署应用。

<tutorial-nav></tutorial-nav>

## 配置 Ansible

在 Cloud Shell 中，您可以直接使用 Ansible 来管理您的云资源。Cloud Shell 为您内置了授权，并且默认配置好了阿里云模块，您无需进行额外配置。默认 Cloud Shell 会使用临时 AK 帮您配置好 AK 信息，同时默认 region 为 `cn-hangzhou`。

您也可以如下方式自行配置阿里云模块。

```
export ALICLOUD_ACCESS_KEY="your_accesskey"
export ALICLOUD_SECRET_KEY="your_accesskey_secret"
export ALICLOUD_REGION="your_region"
```

## 创建资源

在示例中，您会通过 Ansible 编排创建 VPC、VSwitch、安全组和 ECS。其中 `create.yml` playbook 声明了编排配置信息，<tutorial-editor-open-file filePath="tutorial-cli-ansible/ansible/create.yml">在 Cloud Shell 编辑器中查看 create.yml</tutorial-editor-open-file>。

首先定位到 Ansible playbook 的目录。

```bash
cd ~/tutorial-cli-ansible/ansible
```

最后，您就可以一键配置好您编排的资源。

```bash
ansible-playbook create.yml
```

如果出现错误，请检查您的所需服务是否开通，以及您的账户是否实名认证同时账户余额大于 100 元。

## 动态 Inventory

## 部署应用

## 销毁资源

## 总结

恭喜！

您已完成学习如何使用 Ansible 管理阿里云资源和部署应用！