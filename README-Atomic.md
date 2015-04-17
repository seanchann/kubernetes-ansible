1. 查看你的主机IP，配置inventory文件，对atomic而言，我们的master和etcd在一台主机上
2. 编辑group_vars/all.yml配置：ansible_ssh_user: root
3. 在命令行终端配置我们ansible的访问密码：echo "18048143" > ~/rootpassword
4. ansible-playbook -i inventory pre-setup/ping.yml
5. ansible-playbook -i inventory pre-setup/key.yml
6. ansible-playbook -i inventory preset-atomic.yml -vvv 主要是
针对atomic系统目前的bug做修正
7. ansible-playbook -i inventory flannel.yml 配置网络
8. ansible-playbook -i inventory setup.yml
9. test your k8.



curl -s -L http://127.0.0.1:4001/v2/keys/test/config -XPUT -d value='{"Network": "172.16.0.0/8", "SubnetLen": 24, "Backend": {"Type": "vxlan"}}'
