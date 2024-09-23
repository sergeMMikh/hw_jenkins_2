# Домашнее задание к занятию 10 «Jenkins» - Михалёв Сергей
-----
## Подготовка к выполнению

1. Создать два VM: для jenkins-master и jenkins-agent.
2. Установить Jenkins при помощи playbook.
3. Запустить и проверить работоспособность.
4. Сделать первоначальную настройку.

**Решение**
Создал две ВМ чеорез Vagrant с фиксированными IP. Создал [`ansible.cfg`](infrastructure/ansible.cfg). Внёс информацию в [`inventory`](infrastructure/inventory/cicd/hosts.yml)</br>
Установиk Jenkins при помощи playbook `ansible-playbook site.yml`</br>
<img src="images/Task_0_0.png" alt="Task_0_0.png" width="700" height="auto"></br>
Подключил `ansible agent` и отключил выполнение сборок на `master node`. Создал на ВМ `ansible agent` swap файл на 1Gb.</br>
<img src="images/Task_0_1.png" alt="Task_0_1.png" width="700" height="auto"></br>

-----

## Основная часть

1. Сделать Freestyle Job, который будет запускать `molecule test` из любого вашего репозитория с ролью.
2. Сделать Declarative Pipeline Job, который будет запускать `molecule test` из любого вашего репозитория с ролью.
3. Перенести Declarative Pipeline в репозиторий в файл `Jenkinsfile`.
4. Создать Multibranch Pipeline на запуск `Jenkinsfile` из репозитория.
5. Создать Scripted Pipeline, наполнить его скриптом из [pipeline](./pipeline).
6. Внести необходимые изменения, чтобы Pipeline запускал `ansible-playbook` без флагов `--check --diff`, если не установлен параметр при запуске джобы (prod_run = True). По умолчанию параметр имеет значение False и запускает прогон с флагами `--check --diff`.
7. Проверить работоспособность, исправить ошибки, исправленный Pipeline вложить в репозиторий в файл `ScriptedJenkinsfile`.
8. Отправить ссылку на репозиторий с ролью и Declarative Pipeline и Scripted Pipeline.
9. Сопроводите процесс настройки скриншотами для каждого пункта задания!!


### Решение

1. Сделал Freestyle Job, который будет запускать `molecule test` из репозитория с ролью.</br>
   <img src="images/Task_1_1.png" alt="Task_1_1.png" width="500" height="auto"></br>
   Результат тестирования роли [`clickhouse`](https://github.com/sergeMMikh/role-clickhouse) в выводе консоли.</br>
   <img src="images/Task_1_2.png" alt="Task_1_2.png" width="500" height="auto"></br>
   </br>
2. Сделаk Declarative Pipeline Job, который будет запускать `molecule test` из репозитория с ролью.</br>
   <img src="images/Task_2_2_.png" alt="Task_2_2.png" width="500" height="auto"></br>
   Так как данный Pipeline связан с репозиторием на GitHub, в списке шагов добавился `Checkout SCM`.</br>
   <img src="images/Task_2_1_.png" alt="Task_2_1.png" width="400" height="auto"></br>
   После установки [устаревшего](https://wiki.jenkins.io/JENKINS/Pipeline-Stage-View-Plugin.html) плагина [`Pipeline: Stage View`](https://plugins.jenkins.io/pipeline-stage-view/)стало нагляднее.</br>
   <img src="images/Task_2_1_1.png" alt="Task_2_1_1.png" width="350" height="auto"></br>
   Результат тестирования роли [`clickhouse`](https://github.com/sergeMMikh/role-clickhouse) в выводе консоли.</br>
   <img src="images/Task_2_3_.png" alt="Task_2_3.png" width="500" height="auto"></br>
3. Перенёс Declarative Pipeline в репозиторий в файл [`Jenkinsfile`](https://github.com/sergeMMikh/role-clickhouse/blob/master/Jenkinsfile).
4. Создал Multibranch Pipeline на запуск `Jenkinsfile` из репозитория.</br>
   <img src="images/Task_4_1.png" alt="Task_4_1.png" width="500" height="auto"></br>
5. Создал Scripted Pipeline, наполнить его скриптом из требуемого репозитория.</br>
   <img src="images/Task_5_1.png" alt="Task_5_1.png" width="400" height="auto"></br>
6. Внёс необходимые изменения, чтобы Pipeline запускал `ansible-playbook` без флагов `--check --diff`, если не установлен параметр при запуске джобы (prod_run = True). По умолчанию параметр имеет значение False и запускает прогон с флагами `--check --diff`.</br>
   <img src="images/Task_6_1.png" alt="Task_6_1.png" width="400" height="auto"></br>
   <img src="images/Task_6_2.png" alt="Task_6_2.png" width="400" height="auto"></br>
7. Проверить работоспособность, исправить ошибки, исправленный Pipeline вложить в репозиторий в файл [`ScriptedJenkinsfile`](ScriptedJenkinsfile).
8. Ссылку на [репозиторий с ролью](https://github.com/sergeMMikh/role-clickhouse) и [`Declarative Pipeline`](https://github.com/sergeMMikh/hw_jenkins_2/blob/main/Declarative%20Pipeline) и [`Scripted Pipeline`](https://github.com/sergeMMikh/hw_jenkins_2/blob/main/Scripted%20Pipeline).
---
