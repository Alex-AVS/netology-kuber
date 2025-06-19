# 09. Управление доступом

### 1. 

Копируем с ноды корневой сертификат:

![tf](img/09-01-copy-ca.png)

Создаём запрос и подписываем сертификат:

![tf](img/09-2-create-cert.png)

Настраиваем конфигурацию kubectl: Создаём нового пользователя, использующего сертификат, контекст, проверяем, что он имеет доступ.

![tf](img/09-03-kubeconfig-set.png)

![tf](img/09-03-kubeconfig-use.png)

Включаем RBAC в кластере:

![tf](img/09-04-uk8s-rbac.png)

Создадим [роль](src/role.yaml) и [RoleBinding](src/rolebinding.yaml) для нашего пользователя:

```yaml
apiVersion: rbac.authorization.k8s.io/v1
kind: Role
metadata:
  name: pod-readonly
rules:
  - apiGroups: [""]
    resources: ["pods","pods/log"]
    verbs: ["get", "list"]
---

kind: RoleBinding
apiVersion: rbac.authorization.k8s.io/v1
metadata:
  name: pods-read
  namespace: default
subjects:
- kind: User
  name: reader
  apiGroup: rbac.authorization.k8s.io
roleRef:
  kind: Role 
  name: pod-readonly
  apiGroup: rbac.authorization.k8s.io
```

Применяем и проверяем, что теперь права есть:

![tf](img/09-05-rbac-test-1.png)

Просмотр логов:

![tf](img/09-05-rbac-test-3-logs.png)

Проверим, что другие действия и объекты недоступны:

![tf](img/09-05-rbac-test-2-restricted.png)


