# Домашнее задание к занятию 10 «Jenkins» - Михалёв Сергей
-----
## Подготовка к выполнению

1. Создать два VM: для jenkins-master и jenkins-agent.
2. Установить Jenkins при помощи playbook.
3. Запустить и проверить работоспособность.
4. Сделать первоначальную настройку.

**Решение**
Создал две ВМ чеорез Vagrant с фиксированными IP. Создал [`ansible.cfg`](infrastructure/ansible.cfg). Внёс информацию в ['inventory'](inventory/cicd/hosts.yml)</br>
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

1. Сделал Freestyle Job, который будет запускать `molecule test` из любого вашего репозитория с ролью</br>
   <img src="images/Task_1_1.png" alt="Task_1_1.png" width="700" height="auto"></br>
   Результат тестирования роли [`clickhouse`](https://github.com/sergeMMikh/role-clickhouse) в выводе консоли.</br>
   <img src="images/Task_1_2.png" alt="Task_1_2.png" width="700" height="auto"></br>



---
