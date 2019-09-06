# Репозиторий состоит из двух playbook:
#  k8s-deploy.yml - развернет на ваших серверах Kubernetes по принципу Мастер-Слейв 
#  k8s-purge.yml - удалит на ваших серверах Kubernetes

Для того, чтобы playbooks отработали вам необходимо:
   
  1. Изменить инвентори файл, находящийся в папке roles/inventory, указав ваш ip в параметре ansible_host={{ ip_host }} 

  2.
    2.1 Забросить публичный ssh ключ на ваши сервера командой:
      ssh-copy-id -i ssh-key/vm_rsa.pub
    2.2 Либо сгенероировать свои ключи:
      ssh-keygen
       и положить их в дирректорию ssh-key

  3. Потом указать явно ваш приватный ssh ключ командой:
      eval `ssh-agent -s`; ssh-add ssh-key/vm_rsa
  
  4. После чего запустить одну из playbook например:
      ansible-playbook k8s-deploy.ym


