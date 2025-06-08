# 01. Kubernetes. Причины появления. Команда kubectl

### 1. Установка microk8s
Устанавливаем на ВМ Ubuntu 22.04

![tf](img/01-01-mikrok8s-install.png)

Включаем сервис dashboard:

![tf](img/01-02-mikrok8s-enable-dash.png)

Обновляем сертификат:

![tf](img/01-03-mikrok8s-update-certs.png)

### 2. Установка kubectl
Устанавливаем kubectl на локальную машину, копируем `config` с ноды и проверяем:

![tf](img/01-05-kubectl-install-config.png)
 
Получаем токен для dashboard и делаем портфорвард:

![tf](img/01-06-dashboard-portforward.png)

Проверяем:

![tf](img/01-06-dashboard-www.png)



