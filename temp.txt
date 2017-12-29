#!/bin/bash
apt-add-repository -y ppa:ansible/ansible
apt-get update
apt-get -y install ansible git gosu
cd /home/ubuntu
git init
git remote add origin https://github.com/undead-ru/devops-classes.git
git fetch
git checkout -t origin/master
chown ubuntu:ubuntu /home/ubuntu -R
gosu ubuntu ansible-playbook -i "localhost," -c local app.yml
