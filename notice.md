## 须知
- ECS
    - 操作系统：CentOS:7.7
    - 实例规格：ecs.s6-c1m1.small
    - 实例数量：1
    - 系统盘：20G 高效云盘


## 创建资源
通过 Ansible 编排创建 VPC、VSwitch、安全组和 ECS。其中 `create.yml` playbook 声明了编排配置信息，<tutorial-editor-open-file filePath="tutorial-cli-ansible/ansible/create.yml">在 Cloud Shell 编辑器中查看 create.yml</tutorial-editor-open-file>。其中，各资源的详细的配置分别在：

- 变量定义：<tutorial-editor-open-file filePath="tutorial-cli-ansible/ansible/group_vars/all">group_vars/all</tutorial-editor-open-file>
- VPC：<tutorial-editor-open-file filePath="tutorial-cli-ansible/ansible/roles/vpc/tasks/main.yml">roles/vpc/tasks/main.yml</tutorial-editor-open-file>
- VSwitch：<tutorial-editor-open-file filePath="tutorial-cli-ansible/ansible/roles/vswitch/tasks/main.yml">roles/vswitch/tasks/main.yml</tutorial-editor-open-file>
- 安全组：<tutorial-editor-open-file filePath="tutorial-cli-ansible/ansible/roles/security_group/tasks/main.yml">roles/security_group/tasks/main.yml</tutorial-editor-open-file>
- ECS：<tutorial-editor-open-file filePath="tutorial-cli-ansible/ansible/roles/ecs/tasks/main.yml">roles/ecs/tasks/main.yml</tutorial-editor-open-file>

编排资源：
```bash
cd ~/aliyun/ansible;ansible-playbook create.yml
```
执行完后，在对应产品的控制台看到创建的 ECS


## 主机始化化基线安全配置

获取 Invectory
```bash
wget -P ~/aliyun/ansible/ https://raw.githubusercontent.com/alibaba/ansible-provider/master/contrib/inventory/alicloud.py;\
chmod +x ~/aliyun/ansible/alicloud.py;\
wget -P ~/aliyun/ansible/ https://raw.githubusercontent.com/alibaba/ansible-provider/master/contrib/inventory/alicloud.ini
```
获取安全整改 playbook
```bash
cloudshell-git-open https://github.com/Chwei-L/Linux.git /home/shell/Linux
```
编排资源：
```bash
cd ~/Linux/BaseSecurity;ansible-playbook -i ~/aliyun/ansible/alicloud.py config.yml -u root -k
```


## Nginx应用部署 
```bash
ansible-playbook -i ~/aliyun/ansible/alicloud.py ~/aliyun/ansible/deploy.yml -u root -k
```


## 销毁资源
```bash
ansible-playbook ~/aliyun/ansible/destory.yml
```
