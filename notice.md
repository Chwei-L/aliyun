# 使用 Ansible 管理云资源


## 须知

创建的资源有：

- ECS
    - 实例规格：ecs.t5-lc2m1.nano
    - 实例数量：1
    - 系统盘：20G 高效云盘

## 配置 Ansible

在 Cloud Shell 中，直接使用 Ansible 来管理您的云资源。Cloud Shell 内置了授权，并且默认配置好了阿里云模块，无需进行额外配置。Cloud Shell 使用临时 AK 帮您配置好 AK 信息，使用默认 region 为 `cn-hangzhou`。

## 创建资源

通过 Ansible 编排创建 VPC、VSwitch、安全组和 ECS。其中 `create.yml` playbook 声明了编排配置信息，<tutorial-editor-open-file filePath="tutorial-cli-ansible/ansible/create.yml">在 Cloud Shell 编辑器中查看 create.yml</tutorial-editor-open-file>。其中，各资源的详细的配置分别在：

- 变量定义：<tutorial-editor-open-file filePath="tutorial-cli-ansible/ansible/group_vars/all">group_vars/all</tutorial-editor-open-file>
- VPC：<tutorial-editor-open-file filePath="tutorial-cli-ansible/ansible/roles/vpc/tasks/main.yml">roles/vpc/tasks/main.yml</tutorial-editor-open-file>
- VSwitch：<tutorial-editor-open-file filePath="tutorial-cli-ansible/ansible/roles/vswitch/tasks/main.yml">roles/vswitch/tasks/main.yml</tutorial-editor-open-file>
- 安全组：<tutorial-editor-open-file filePath="tutorial-cli-ansible/ansible/roles/security_group/tasks/main.yml">roles/security_group/tasks/main.yml</tutorial-editor-open-file>
- ECS：<tutorial-editor-open-file filePath="tutorial-cli-ansible/ansible/roles/ecs/tasks/main.yml">roles/ecs/tasks/main.yml</tutorial-editor-open-file>

定位到 Ansible playbook 的目录。

```bash
cd ~/aliyun/ansible
```

一键配置好您编排的资源。

```bash
ansible-playbook create.yml
```

执行完后，在对应产品的控制台看到创建的 ECS：


## 基于阿里云平台ansible部署应用 

```bash
pip install ansible_alicloud_module_utils
```

```bash
pip install footmark --upgrade
```

```bash
wget -P ~/tutorial-cli-ansible/ansible/ https://raw.githubusercontent.com/alibaba/ansible-provider/master/contrib/inventory/alicloud.py;\
chmod +x ~/tutorial-cli-ansible/ansible/alicloud.py
```

```bash
ansible-playbook -i ~/tutorial-cli-ansible/ansible/alicloud.py ~/tutorial-cli-ansible/ansible/deploy.yml -u root -k
```

## 销毁资源

```bash
ansible-playbook ~/tutorial-cli-ansible/ansible/destory.yml
```
