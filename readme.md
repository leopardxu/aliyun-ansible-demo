### This demo for interview
```text
Thank you very much repo:  https://github.com/johniezz/ADT.git
some problems are encountered as Aliyun-Ansible is not maintained for a long time.
details as debug section.
```
#### Ready on ansible host
```sh
python -m pip install ansible-base
python -m pip install ansible
sudo pip install footmark 
sudo pip install ansible_alicloud
export ALICLOUD_ACCESS_KEY="your_accesskey"
export ALICLOUD_SECRET_KEY="your_accesskey_secret"
```
#### aliyun dynamic inventory
```text
https://help.aliyun.com/document_detail/106605.htm?spm=a2c4g.11186623.2.5.18b075f99dL5xf#concept-mhn-53t-pgb
```

#### debug
```text
1. Can not find aliyun modules
Modules of aliyun are download to /usr/local/lib/python3.6/dist-packages/ansible/modules/cloud/alicloud by default, and ansible can not find them.

Solution:
cd  /usr/local/lib/python3.6/dist-packages/ansible/modules/cloud/alicloud
cp *.py ../../

2. Can not find alicloud_ecs module when run alicloud.py
have no alicloud_ecs module

Solution:
git clone https://github.com/alibaba/alibaba.alicloud.git
cd alibaba.alicloud/lib/
copy python files under ansible/modules_utils to /usr/local/lib/python3.6/dist-packages/ansible/modules_utils

3. KeyPairName is invalid when create instance

Solution:
delete key_name parameter 
```

#### Try
```sh
ansible-playbook create-ecs.yml -vvv
ansible-playbook -i alicloud.py docker-nginx.yml -vvv -e ansible_ssh_pass=Test123456
ansible-playbook destory-all.yml
```

#### my env
system win10-wsl
```sh
python --version
Python 3.6.9

ansible --version
ansible [core 2.11.1]
  config file = /etc/ansible/ansible.cfg
  configured module search path = ['/root/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']
  ansible python module location = /usr/local/lib/python3.6/dist-packages/ansible
  ansible collection location = /root/.ansible/collections:/usr/share/ansible/collections
  executable location = /usr/local/bin/ansible
  python version = 3.6.9 (default, Jan 26 2021, 15:33:00) [GCC 8.4.0]
  jinja version = 3.0.1
  libyaml = True

pip -V
pip 9.0.1 from /usr/lib/python3/dist-packages (python 3.6)

pip list
aliyun-python-sdk-alidns (2.6.29)
aliyun-python-sdk-core (2.13.35)
aliyun-python-sdk-ecs (4.24.1)
aliyun-python-sdk-ess (2.3.3)
aliyun-python-sdk-kms (2.14.0)
aliyun-python-sdk-market (2.0.24)
aliyun-python-sdk-oos (1.5.0)
aliyun-python-sdk-ram (3.2.0)
aliyun-python-sdk-rds (2.5.11)
aliyun-python-sdk-ros (3.2.0)
aliyun-python-sdk-slb (3.3.7)
aliyun-python-sdk-sts (3.0.2)
aliyun-python-sdk-vpc (3.0.12)
ansible (4.0.0)
ansible-alicloud (1.19.0)
ansible-alicloud-module-utils (1.5.0)
ansible-base (2.10.10)
ansible-core (2.11.1)
asn1crypto (0.24.0)
certifi (2020.12.5)
cffi (1.14.5)
chardet (4.0.0)
crcmod (1.7)
cryptography (3.4.7)
footmark (1.20.0)
idna (2.6)
Jinja2 (3.0.1)
jmespath (0.10.0)
keyring (10.6.0)
keyrings.alt (3.0)
MarkupSafe (2.0.1)
oss2 (2.14.0)
packaging (20.9)
pip (9.0.1)
pycparser (2.20)
pycrypto (2.6.1)
pycryptodome (3.10.1)
pygobject (3.26.1)
pyparsing (2.4.7)
python-apt (1.6.5+ubuntu0.6)
pyxdg (0.25)
PyYAML (3.12)
requests (2.25.1)
resolvelib (0.5.5)
SecretStorage (2.3.1)
setuptools (39.0.1)
six (1.11.0)
style (1.1.0)
ubuntu-advantage-tools (27.0)
unattended-upgrades (0.1)
update (0.0.1)
urllib3 (1.26.5)
wheel (0.30.0)
```
