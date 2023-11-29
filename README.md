# API Сервис заказа товаров для розничных сетей.

## Описание

Приложение предназначено для автоматизации закупок в розничной сети. Пользователи сервиса — покупатель (менеджер торговой сети, который закупает товары для продажи в магазине) и поставщик товаров.

**Клиент (покупатель):**

- Менеджер закупок через API делает ежедневные закупки по каталогу, в котором представлены товары от нескольких поставщиков.
- В одном заказе можно указать товары от разных поставщиков — это повлияет на стоимость доставки.
- Пользователь может авторизироваться, регистрироваться и восстанавливать пароль через API.
    
**Поставщик:**

- Регистрируется через отдельную точку входа, далее (после утверждения администратором) может авторизоваться и восстанавливать пароль как обычный клиент.
- Через API информирует сервис об обновлении прайса.
- Может включать и отключать прием заказов.
- Может получать список оформленных заказов (с товарами из его прайса).

**Администратор, через панель администратора Django:**

- Активирует впервые зарегистрировавшегося поставщика.
- Может изменить статус заказа, при этом клиент получает информационное письмо.
- Обновляет прайс, полученный от поставщика.

## Запуск проекта

1. Создать файл _.env_ на основе файла [orders/.env-example](orders/.env-example).
2. Перейти в директорию _orders_, где расположены файлы docker-compose.yml и Dockerfile.
3. Запустить docker-compose 

    <code>>> docker-compose up --build</code>

4. Для доступа к админстративной панели Django создаем суперпользователя

    <code>>> docker-compose exec backend python manage.py createsuperuser</code>

## Адреса сервиса 

- API сервис: [127.0.0.1:8000/api/v1/](http://127.0.0.1:8000/api/v1/)
- Админ панель Django: [127.0.0.1:8000/admin/](http://127.0.0.1:8000/admin/)
- Документация к API: [Swagger](http://127.0.0.1:8000/api/schema/swagger/), [Redoc](http://127.0.0.1:8000/api/schema/redoc/)
