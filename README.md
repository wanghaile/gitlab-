安装须知:
操作系统:Centos6.5
用户root
安装方式：一键式安装

首先:yum update

其次
1. 安装配置依赖项
sudo yum install curl openssh-server postfix cronie
sudo service postfix start
sudo chkconfig postfix on
sudo lokkit -s http -s ssh

2. 添加并安装GitLab软件包

curl http://packages.gitlab.cc/install/gitlab-ce/script.rpm.sh | sudo bash   
sudo yum install gitlab-ce

3. 配置和使用GitLab

sudo gitlab-ctl reconfigure

4. 在浏览器访问GitLab主机名

Username: root 
Password: 5iveL!fe

此安装已经验证，源码托管也测试成功。

问题1：
安装过程中会遇到访问502错误
执行gitlab-ctl tail 跟踪查看一下 是否为8080等端口被占用错误，
/etc/gitlab/gitlab.rb 找到8080/修改8080 端口
gitlab-ctl reconfigure //重新配置一下看看最后是否解决问题。
问题2:
改web端口号
https://gitlab.com/gitlab-org/omnibus-gitlab/blob/629def0a7a26e7c2326566f0758d4a27857b52a3/doc/settings/nginx.md

重点备注:
一键安装所有配置文件在/etc/gitlab/gitlab.rb中如果不会修改查看里面的帮助提示。


备注2：
学习git源码托管请参考廖雪峰老师博客，非常详细，学习成本预计俩小时。
http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000
