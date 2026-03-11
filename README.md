# Тестовое задание для стажёра технического писателя

---

## Раздел 1. О себе

### Ответы на вопросы:

1. **Ваше имя и контактные данные**

   [ИМЯ]
   
   [EMAIL]
   
   [ТЕЛЕФОН/TELEGRAM]

2. **Образование**

   [ВУЗ, СПЕЦИАЛЬНОСТЬ, ГОД ОКОНЧАНИЯ]

3. **Опыт в техническом письме**

   [ОПИСАНИЕ ОПЫТА]

4. **Опыт работы с Git**

   [ОТВЕТ]

5. **Знакомство с Markdown**

   [ОТВЕТ]

6. **Почему хотите стать техническим писателем**

   [ОТВЕТ]

7. **Интересующие технологии**

   [ОТВЕТ]

8. **Ситуация быстрого изучения нового**

   [ОТВЕТ]

9. **Уровень английского языка**

   [ОТВЕТ]

---

## Раздел 2. Технические вопросы

### 2.1. Kubernetes

**Вопрос 1. Что такое Kubernetes? Для чего его используют?**

Kubernetes (K8s) — это открытое программное обеспечение для автоматизации развёртывания, масштабирования и управления контейнеризированными приложениями. Его используют для оркестрации контейнеров (поддерживает containerd, CRI-O и другие CRI-совместимые рантаймы): Kubernetes управляет запуском приложений в контейнерах, следит за их состоянием, перезапускает при сбоях, масштабирует количество экземпляров в зависимости от нагрузки и обеспечивает балансировку трафика между ними. Это позволяет разработчикам сосредоточиться на написании кода, а не на ручном управлении инфраструктурой.

**Вопрос 2. Разница между Pod, Deployment и Service**

**Pod** — минимальная единица в Kubernetes, группа из одного или нескольких контейнеров, которые работают вместе и разделяют ресурсы (хранилище, сеть). Аналогия: Pod — это один жилец в квартире, который может жить один или с соседом.

**Deployment** — контроллер, который управляет созданием и обновлением Pod'ов. Он определяет, сколько реплик приложения должно работать, и следит за их состоянием. Аналогия: Deployment — это управляющий многоквартирным домом, который решает, сколько квартир занято и следит, чтобы пустующие квартиры были заселены.

**Service** — абстракция, которая предоставляет постоянный сетевой адрес для доступа к группе Pod'ов. Так как Pod'ы могут создаваться и удаляться динамически, Service обеспечивает стабильную точку входа. Аналогия: Service — это адрес многоквартирного дома. Жильцы (Pod'ы) могут меняться, но адрес дома остаётся неизменным.

**Вопрос 3. Что такое Namespace в Kubernetes?**

Namespace — это виртуальный кластер внутри одного физического кластера Kubernetes. Он позволяет разделить ресурсы между разными командами, проектами или окружениями (например, development, staging, production). В разных Namespace можно использовать ресурсы с одинаковыми именами, не опасаясь конфликтов. Также Namespace позволяет ограничивать доступ и квоты ресурсов для разных групп пользователей.

**Вопрос 4. Объяснение манифеста Kubernetes**

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-application
  labels:
    app: my-app
```
- `apiVersion: apps/v1` — версия API Kubernetes, используемая для создания объекта
- `kind: Deployment` — тип создаваемого ресурса (в данном случае Deployment)
- `metadata` — метаданные объекта:
  - `name: my-application` — имя Deployment'а
  - `labels` — метки для идентификации и выборки ресурсов

```yaml
spec:
  replicas: 3
```
- `spec` — желаемое состояние объекта
- `replicas: 3` — количество экземпляров (реплик) Pod'ов, которые должны работать

```yaml
  selector:
    matchLabels:
      app: my-app
```
- `selector` — определяет, какие Pod'ы принадлежат этому Deployment'у (поиск по меткам)

```yaml
  template:
    metadata:
      labels:
        app: my-app
```
- `template` — шаблон для создания Pod'ов
- Метки в шаблоне должны соответствовать селектору выше

```yaml
    spec:
      containers:
      - name: my-container
        image: my-registry/my-app:v1.2.0
        ports:
        - containerPort: 8080
```
- `containers` — список контейнеров в Pod'е
- `name` — имя контейнера
- `image` — Docker-образ для запуска (из реестра my-registry, версия v1.2.0)
- `containerPort` — порт, который контейнер слушает

```yaml
        resources:
          limits:
            memory: "512Mi"
            cpu: "500m"
```
- `resources.limits` — максимальные ресурсы, которые контейнер может использовать:
  - `memory: "512Mi"` — не более 512 мебибайт памяти
  - `cpu: "500m"` — не более 0.5 CPU (500 милли-CPU)

---

### 2.2. Frontend-разработка

**Вопрос 1. Что такое DOM?**

DOM (Document Object Model) — это программный интерфейс, представляющий HTML-документ в виде дерева объектов. Браузер парсит HTML-код и создаёт DOM-дерево, где каждый HTML-элемент становится узлом (node). JavaScript может обращаться к этому дереву, изменять содержимое элементов, их атрибуты, стили и структуру. Когда DOM изменяется, браузер перерисовывает страницу.

**Вопрос 2. Разница между HTML, CSS и JavaScript**

- **HTML** (HyperText Markup Language) — язык разметки, отвечает за структуру и содержимое страницы: заголовки, параграфы, списки, формы, изображения. Это «скелет» страницы.
- **CSS** (Cascading Style Sheets) — язык описания внешнего вида, отвечает за оформление: цвета, шрифты, отступы, расположение элементов, анимации. Это «одежда» страницы.
- **JavaScript** — язык программирования, отвечает за интерактивность и логику: обработка кликов, валидация форм, отправка запросов на сервер, динамическое изменение содержимого. Это «мозг» страницы.

**Вопрос 3. Что такое React? Почему он популярен?**

React — это JavaScript-библиотека для создания пользовательских интерфейсов, разработанная компанией Meta (ранее Facebook). React позволяет строить UI из независимых компонентов, которые управляют своим состоянием и эффективно обновляются при изменении данных.

Причины популярности:
- **Компонентный подход** — UI разбивается на переиспользуемые компоненты
- **Виртуальный DOM** — React обновляет только изменившиеся части интерфейса, что ускоряет работу
- **Однонаправленный поток данных** — упрощает отладку и понимание приложения
- **Большое сообщество и экосистема** — множество готовых библиотек и инструментов
- **JSX** — синтаксис, позволяющий писать HTML-подобный код внутри JavaScript

**Вопрос 4. Что такое компонент?**

Компонент — это независимый, переиспользуемый блок пользовательского интерфейса, который инкапсулирует разметку (HTML), стили (CSS) и логику (JavaScript). Компоненты могут быть простыми (кнопка, поле ввода) или сложными (форма регистрации, карточка товара).

Примеры компонентов на популярных сайтах:
- **YouTube**: карточка видео (превью, название, канал, просмотры) — переиспользуется для каждого видео в ленте
- **GitHub**: кнопка «Star», выпадающее меню навигации, список репозиториев
- **Gmail**: карточка письма в списке входящих, кнопка «Написать», панель с папками

**Вопрос 5. Что такое API? Взаимодействие frontend и backend**

API (Application Programming Interface) — это набор правил и протоколов, по которым программные компоненты взаимодействуют друг с другом. В веб-разработке чаще всего используется REST API или GraphQL — это HTTP-эндпоинты, через которые frontend отправляет запросы и получает данные.

Frontend и backend взаимодействуют так:
1. Frontend отправляет HTTP-запрос (GET, POST, PUT, DELETE) на определённый URL backend'а
2. Backend обрабатывает запрос, обращается к базе данных, выполняет бизнес-логику
3. Backend возвращает ответ в формате JSON
4. Frontend получает данные и отображает их пользователю

---

### 2.3. Unreal Engine

**Вопрос 1. Что такое Unreal Engine?**

Unreal Engine — это профессиональный игровой движок, разработанный компанией Epic Games. Он используется для создания видеоигр, виртуальной и дополненной реальности, архитектурных визуализаций, кинематографа и симуляций. Unreal Engine предоставляет инструменты для работы с 3D-графикой, физикой, анимацией, звуком, искусственным интеллектом и многим другим. Движок известен высококачественной графикой и системой визуального программирования Blueprints.

**Вопрос 2. Что такое Layer в Unreal Engine?**

Layer (слой) — это механизм организации объектов в сцене для удобства работы и управления видимостью. Слои позволяют группировать объекты по категориям (например, «Деревья», «Здания», «Персонажи») и управлять ими collectively: скрывать/отображать, блокировать редактирование, применять фильтры. Это упрощает работу над большими проектами, позволяя сфокусироваться на определённых элементах сцены.

**Вопрос 3. Разница между Actor и Object**

- **Object** (UObject) — базовый класс в Unreal Engine, от которого наследуются большинство объектов в движке. Object сам по себе не имеет положения в мире и не может быть размещён на уровне. Это контейнер для данных и функциональности.
- **Actor** — объект, который можно разместить в игровом мире (на уровне). Actor наследуется от Object и добавляет возможность иметь позицию, вращение, масштаб и компоненты (например, меш, коллизия, источники света). Примеры Actor'ов: персонаж, камера, источник света, триггер.

**Вопрос 4. Что такое Blueprint?**

Blueprint — это система визуального программирования в Unreal Engine, позволяющая создавать игровую логику без написания кода на C++. Программирование происходит путём соединения узлов (nodes) в граф, где каждый узел выполняет определённое действие.

Преимущества Blueprint перед обычным программированием:
- **Низкий порог входа** — не требует знания C++
- **Визуальное представление** — логику легче понять и отладить
- **Быстрая итерация** — изменения сразу видны без компиляции
- **Прототипирование** — позволяет быстро проверить идеи
- Blueprint может использоваться вместе с C++: основная логика на C++, а геймплей на Blueprint

---

## Раздел 3. Практическое задание: Документация Kubernetes

# Работа с Kubernetes-кластером

## Обзор кластера

Кластер Kubernetes — это набор машин (нод), на которых запускаются контейнеризированные приложения. Наш кластер предоставляет платформу для развёртывания и управления микросервисами.

### Основные компоненты кластера

Проверить состояние кластера можно командой:

```bash
kubectl cluster-info
```

Пример вывода:

```text
Kubernetes control plane is running at https://cluster.example.com:6443
CoreDNS is running at https://cluster.example.com:6443/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy

To further debug and diagnose cluster problems, use 'kubectl cluster-info dump'.
```

| Компонент | Описание |
|-----------|----------|
| Control Plane | Управляющий слой кластера, доступен по адресу `https://cluster.example.com:6443` |
| CoreDNS | Служба DNS для разрешения имён сервисов внутри кластера |

### Структура кластера

Кластер содержит следующие namespaces (пространства имён):

| Namespace | Назначение |
|-----------|------------|
| `default` | Пространство по умолчанию (системное) |
| `kube-system` | Системные компоненты Kubernetes |
| `kube-public` | Публичные ресурсы, доступные всем |
| `kube-node-lease` | Данные о состоянии нод |
| `development` | Окружение для разработки |
| `staging` | Предпроизводственное окружение |
| `production` | Производственное окружение |

---

## Работа с Namespaces

Namespace — это логическое разделение ресурсов внутри кластера. Использование разных namespace позволяет изолировать окружения (development, staging, production) и команды друг от друга.

### Просмотр списка namespaces

```bash
kubectl get namespaces
```

Пример вывода:

```text
NAME              STATUS   AGE
default           Active   365d
kube-node-lease   Active   365d
kube-public       Active   365d
kube-system       Active   365d
development       Active   180d
production        Active   180d
staging           Active   180d
```

Столбцы:
- **NAME** — имя namespace
- **STATUS** — текущее состояние (Active — активно)
- **AGE** — время с момента создания

### Создание нового namespace

```bash
kubectl create namespace <имя-namespace>
```

Пример создания namespace для нового проекта:

```bash
kubectl create namespace my-project
```

### Переключение между namespaces

Для переключения текущего контекста на определённый namespace используйте команду:

```bash
kubectl config set-context --current --namespace=<имя-namespace>
```

Пример переключения на namespace `development`:

```bash
kubectl config set-context --current --namespace=development
```

После этого все команды `kubectl` будут выполняться в выбранном namespace по умолчанию.

### Указание namespace в команде

Если нужно выполнить команду в конкретном namespace без переключения контекста, используйте флаг `-n`:

```bash
kubectl get pods -n development
```

---

## Деплойменты в кластере

Deployment — это контроллер, который управляет запуском и масштабированием приложений. Он обеспечивает нужное количество реплик (экземпляров) приложения и их обновление.

### Текущие деплойменты в namespace development

| Сервис | Реплики (Ready/Desired) | Статус | Возраст |
|--------|-------------------------|--------|---------|
| auth-service | 2/2 | Доступен | 45 дней |
| api-gateway | 3/3 | Доступен | 90 дней |
| user-service | 2/2 | Доступен | 60 дней |
| payment-service | 1/1 | Доступен | 30 дней |
| notification-service | 1/1 | Доступен | 15 дней |

### Просмотр деплойментов

```bash
kubectl get deployments -n development
```

Пример вывода:

```text
NAME                   READY   UP-TO-DATE   AVAILABLE   AGE
auth-service           2/2     2            2           45d
api-gateway            3/3     3            3           90d
user-service           2/2     2            2           60d
payment-service        1/1     1            1           30d
notification-service   1/1     1            1           15d
```

Столбцы в выводе:
- **NAME** — имя деплоймента
- **READY** — количество готовых реплик / желаемое количество
- **UP-TO-DATE** — количество реплик с актуальной версией
- **AVAILABLE** — количество доступных реплик
- **AGE** — время с момента создания

### Детальная информация о деплойменте

```bash
kubectl describe deployment <имя-деплоймента> -n development
```

---

## Работа с Pod'ами

Pod — это минимальная единица в Kubernetes, содержащая один или несколько контейнеров приложения.

### Просмотр списка подов

```bash
kubectl get pods -n development
```

Пример вывода:

```text
NAME                                      READY   STATUS    RESTARTS   AGE
auth-service-5f8d9c7b4d-x7k2m             1/1     Running   0          2d
auth-service-5f8d9c7b4d-p9n3q             1/1     Running   0          2d
api-gateway-6c7b8d9f5c-m4k8p              1/1     Running   0          5d
api-gateway-6c7b8d9f5c-n2w7r              1/1     Running   0          5d
api-gateway-6c7b8d9f5c-q1t5s              1/1     Running   0          5d
user-service-7d8e9f0a6d-k3j6h             1/1     Running   0          1d
user-service-7d8e9f0a6d-l5m9n             1/1     Running   0          1d
payment-service-8e9f0a1b7e-o2p4           1/1     Running   0          12h
notification-service-9f0a1b2c8f-r3s5t     1/1     Running   0          6h
```

Столбцы:
- **NAME** — имя пода (генерируется автоматически)
- **READY** — количество готовых контейнеров / всего контейнеров
- **STATUS** — текущее состояние пода
- **RESTARTS** — количество перезапусков
- **AGE** — время с момента создания

### Текущие поды в namespace development

| Pod | Статус | Перезапуски | Возраст |
|-----|--------|-------------|---------|
| auth-service-5f8d9c7b4d-x7k2m | Running | 0 | 2 дня |
| auth-service-5f8d9c7b4d-p9n3q | Running | 0 | 2 дня |
| api-gateway-6c7b8d9f5c-m4k8p | Running | 0 | 5 дней |
| api-gateway-6c7b8d9f5c-n2w7r | Running | 0 | 5 дней |
| api-gateway-6c7b8d9f5c-q1t5s | Running | 0 | 5 дней |
| user-service-7d8e9f0a6d-k3j6h | Running | 0 | 1 день |
| user-service-7d8e9f0a6d-l5m9n | Running | 0 | 1 день |
| payment-service-8e9f0a1b7e-o2p4 | Running | 0 | 12 часов |
| notification-service-9f0a1b2c8f-r3s5t | Running | 0 | 6 часов |

### Статусы подов

| Статус | Описание |
|--------|----------|
| Running | Под работает корректно |
| Pending | Под ожидает назначения на ноду |
| CrashLoopBackOff | Контейнер падает и перезапускается |
| ImagePullBackOff | Не удалось загрузить образ контейнера |
| Completed | Под завершил работу успешно |

### Детальная информация о поде

```bash
kubectl describe pod <имя-пода> -n development
```

---

## Просмотр логов приложения

Логи позволяют отслеживать работу приложения, находить ошибки и анализировать поведение системы.

### Просмотр последних логов

```bash
kubectl logs <имя-пода> -n development
```

### Просмотр последних N строк логов

Используйте флаг `--tail` для ограничения количества выводимых строк:

```bash
kubectl logs <имя-пода> -n development --tail=20
```

Пример просмотра логов auth-service:

```bash
kubectl logs auth-service-5f8d9c7b4d-x7k2m -n development --tail=20
```

Пример вывода:

```text
2024-01-15 10:23:45 INFO [main] Starting AuthService application
2024-01-15 10:23:46 INFO [main] Loading configuration from environment
2024-01-15 10:23:47 INFO [main] Connecting to database at postgres://db:5432/auth
2024-01-15 10:23:48 INFO [main] Database connection established
2024-01-15 10:23:49 INFO [main] Starting HTTP server on port 8080
2024-01-15 10:23:50 INFO [main] AuthService started successfully
2024-01-15 10:25:12 INFO [http-handler] POST /api/v1/login - 200 OK - 45ms
2024-01-15 10:25:45 INFO [http-handler] POST /api/v1/login - 200 OK - 38ms
2024-01-15 10:26:01 INFO [http-handler] POST /api/v1/refresh - 200 OK - 12ms
2024-01-15 10:26:33 INFO [http-handler] POST /api/v1/login - 401 Unauthorized - 5ms
2024-01-15 10:27:15 INFO [http-handler] POST /api/v1/login - 200 OK - 42ms
2024-01-15 10:28:00 INFO [http-handler] POST /api/v1/logout - 200 OK - 3ms
2024-01-15 10:28:45 INFO [http-handler] POST /api/v1/login - 200 OK - 51ms
2024-01-15 10:29:12 INFO [http-handler] POST /api/v1/refresh - 200 OK - 15ms
2024-01-15 10:29:55 INFO [http-handler] POST /api/v1/login - 200 OK - 39ms
2024-01-15 10:30:22 INFO [http-handler] POST /api/v1/login - 401 Unauthorized - 4ms
2024-01-15 10:31:00 INFO [http-handler] POST /api/v1/login - 200 OK - 44ms
2024-01-15 10:31:30 INFO [http-handler] POST /api/v1/logout - 200 OK - 2ms
2024-01-15 10:32:15 INFO [http-handler] POST /api/v1/login - 200 OK - 47ms
```

Для отслеживания логов в реальном времени используйте флаг `-f` (follow):

```bash
kubectl logs -f <имя-пода> -n development
```

### Просмотр логов контейнера с перезапусками

Если контейнер перезапускался, можно посмотреть логи предыдущего экземпляра:

```bash
kubectl logs <имя-пода> -n development --previous
```

---

## Сервисы в кластере

Service предоставляет постоянный сетевой адрес для доступа к группе подов.

### Текущие сервисы в namespace development

| Сервис | Тип | Cluster IP | Порт | Возраст |
|--------|-----|------------|------|---------|
| auth-service | ClusterIP | 10.96.100.20 | 8080 | 45 дней |
| api-gateway | ClusterIP | 10.96.100.30 | 8080 | 90 дней |
| user-service | ClusterIP | 10.96.100.40 | 8080 | 60 дней |
| payment-service | ClusterIP | 10.96.100.50 | 8080 | 30 дней |
| notification-service | ClusterIP | 10.96.100.60 | 8080 | 15 дней |

### Просмотр сервисов

```bash
kubectl get services -n development
```

Пример вывода:

```text
NAME                   TYPE        CLUSTER-IP     EXTERNAL-IP   PORT(S)    AGE
auth-service           ClusterIP   10.96.100.20   <none>        8080/TCP   45d
api-gateway            ClusterIP   10.96.100.30   <none>        8080/TCP   90d
user-service           ClusterIP   10.96.100.40   <none>        8080/TCP   60d
payment-service        ClusterIP   10.96.100.50   <none>        8080/TCP   30d
notification-service   ClusterIP   10.96.100.60   <none>        8080/TCP   15d
```

Столбцы:
- **NAME** — имя сервиса
- **TYPE** — тип сервиса (ClusterIP — доступен только внутри кластера)
- **CLUSTER-IP** — внутренний IP-адрес сервиса
- **EXTERNAL-IP** — внешний IP (если применимо)
- **PORT(S)** — порт и протокол
- **AGE** — время с момента создания

---

## Частые проблемы и их решения

### Проблема 1: Pod в статусе CrashLoopBackOff

**Симптомы:** Под постоянно перезапускается, статус меняется на CrashLoopBackOff.

**Возможные причины:**
- Ошибка в коде приложения
- Отсутствуют обязательные переменные окружения
- Неверная конфигурация подключения к базе данных
- Превышены лимиты ресурсов

**Решение:**
1. Проверьте логи пода:
   ```bash
   kubectl logs <имя-пода> -n development
   kubectl logs <имя-пода> -n development --previous
   ```
2. Проверьте детальную информацию о поде:
   ```bash
   kubectl describe pod <имя-пода> -n development
   ```
3. Убедитесь, что все необходимые секреты и конфигурации созданы

### Проблема 2: Pod в статусе Pending

**Симптомы:** Под долгое время находится в статусе Pending и не запускается.

**Возможные причины:**
- Недостаточно ресурсов на нодах (CPU, память)
- Несоответствие требованиям к ноде (node selector, affinity)
- PersistentVolume не может быть создан или привязан

**Решение:**
1. Проверьте события пода:
   ```bash
   kubectl describe pod <имя-пода> -n development
   ```
2. Проверьте доступные ресурсы на нодах:
   ```bash
   kubectl describe nodes
   ```
3. Проверьте, что запрашиваемые ресурсы соответствуют лимитам namespace

### Проблема 3: ImagePullBackOff / ErrImagePull

**Симптомы:** Под не может загрузить Docker-образ, статус ImagePullBackOff или ErrImagePull.

**Возможные причины:**
- Неверное имя образа или тега
- Отсутствие прав доступа к приватному реестру
- Реестр образов недоступен

**Решение:**
1. Проверьте имя образа в манифесте деплоймента:
   ```bash
   kubectl get deployment <имя> -n development -o yaml
   ```
2. Убедитесь, что секрет для доступа к реестру создан и привязан к ServiceAccount:
   ```bash
   kubectl get secrets -n development
   kubectl get serviceaccount default -n development -o yaml
   ```
3. Проверьте доступность реестра образов

---

## Полезные команды

| Команда | Описание |
|---------|----------|
| `kubectl cluster-info` | Информация о кластере |
| `kubectl get all -n development` | Все ресурсы в namespace |
| `kubectl get pods -o wide -n development` | Поды с дополнительной информацией |
| `kubectl exec -it <pod> -n development -- /bin/bash` | Вход в контейнер |
| `kubectl port-forward svc/<service> 8080:8080 -n development` | Проброс порта локально |
| `kubectl apply -f <файл.yaml> -n development` | Применение манифеста |
| `kubectl delete -f <файл.yaml> -n development` | Удаление ресурсов из манифеста |

---

## Ссылки на документацию

- [Официальная документация Kubernetes](https://kubernetes.io/ru/docs/home/)
- [Понятия Kubernetes](https://kubernetes.io/ru/docs/concepts/)
- [Справочник kubectl](https://kubernetes.io/ru/docs/reference/kubectl/)
- [Учебник по Kubernetes](https://kubernetes.io/ru/docs/tutorials/)
- [Документация по Deployments](https://kubernetes.io/ru/docs/concepts/workloads/controllers/deployment/)
- [Документация по Pods](https://kubernetes.io/ru/docs/concepts/workloads/pods/)
- [Документация по Services](https://kubernetes.io/ru/docs/concepts/services-networking/service/)
- [Документация по Namespaces](https://kubernetes.io/ru/docs/concepts/overview/working-with-objects/namespaces/)
- [Отладка подов](https://kubernetes.io/ru/docs/tasks/debug/debug-application/)

---

*Документация подготовлена для разработчиков, работающих с платформой Kubernetes.*
