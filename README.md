# ClickStore - Онлайн магазин на микросервисной архитектуре

Построен на микросервисах **Django REST Framework** и фронтенде **Vue.js**, демонстрирует современные паттерны архитектуры программного обеспечения и лучшие практики.

## Функциональность

- **Аутентификация и управление пользователями** - JWT авторизация с профилями пользователей
- **Каталог товаров** - Расширенный просмотр товаров с категориями и поиском
- **Корзина покупок** - Управление корзиной в реальном времени между сервисами
- **Обработка заказов** - Полный жизненный цикл заказа с отслеживанием статуса
- **API Gateway** - Централизованная маршрутизация с ограничением скорости
- **События в реальном времени** - Redis pub/sub для связи между сервисами
- **Отзывчивый интерфейс** - Современный Vue.js фронтенд с Tailwind CSS

## Запуск

### Требования
- Python 3.9+
- Node.js 16+
- Redis сервер

### 1. Клонирование и настройка
```bash
git clone <url-репозитория>
cd Microservices
```

### 2. Запуск сервисов
```bash
# Терминал 1 - Сервис пользователей
cd services/user-service
pip install -r requirements.txt
python manage.py migrate
python manage.py runserver 0.0.0.0:8004

# Терминал 2 - Сервис товаров
cd services/product-service
pip install -r requirements.txt
python manage.py migrate
python manage.py loaddata fixtures/products.json
python manage.py runserver 0.0.0.0:8001

# Терминал 3 - Сервис корзины
cd services/cart-service
pip install -r requirements.txt
python manage.py migrate
python manage.py runserver 0.0.0.0:8002

# Терминал 4 - Сервис заказов
cd services/order-service
pip install -r requirements.txt
python manage.py migrate
python manage.py runserver 0.0.0.0:8003

# Терминал 5 - API Gateway
cd api-gateway
pip install -r requirements.txt
python manage.py migrate
python manage.py runserver 0.0.0.0:8000

# Терминал 6 - Фронтенд
cd frontend
npm install
npm run dev
```

### 3. Доступ к приложению
- **Фронтенд**: http://localhost:3000
- **API Gateway**: http://localhost:8000
- **Сервисы**: 8001 (Товары), 8002 (Корзина), 8003 (Заказы), 8004 (Пользователи)

## Структура проекта

```
ClickStore/
├── frontend/                   # Vue.js 3 + Tailwind CSS
│   ├── src/components/         # Переиспользуемые UI компоненты
│   ├── src/views/              # Компоненты страниц
│   ├── src/store/              # Управление состоянием Pinia
│   └── src/services/           # API сервисы
├── api-gateway/                # Django API Gateway
│   └── apps/gateway/           # Маршрутизация запросов и ограничение скорости
├── services/
│   ├── user-service/          # Аутентификация и профили
│   ├── product-service/       # Каталог товаров и инвентарь
│   ├── cart-service/          # Управление корзиной покупок
│   └── order-service/         # Обработка и отслеживание заказов
└── databases/                 # SQLite базы данных
```

## Технологический стек

### Backend
- **Фреймворк**: Django REST Framework
- **Аутентификация**: JWT (Simple JWT)
- **База данных**: SQLite (легко заменяется)
- **Кэш и события**: Redis
- **Архитектура**: Микросервисы

### Frontend
- **Фреймворк**: Vue.js 3 (Composition API)
- **Состояние**: Pinia
- **Стили**: Tailwind CSS
- **HTTP клиент**: Axios
- **Маршрутизация**: Vue Router

## 📸 Интерфейс приложения

---

<h3 align="center">Главная страница</h3>
<p align="center">
  <img src="https://github.com/user-attachments/assets/b40ebda6-7827-4137-a08d-541ed6589875" width="800" alt="Home Page" style="border-radius: 8px; box-shadow: 0 4px 20px rgba(0,0,0,0.1);">
</p>

---

<h3 align="center">Каталог товаров</h3>
<p align="center">
  <img src="https://github.com/user-attachments/assets/cb686280-0183-46f3-8f34-5a1bb42b4f2e" width="800" alt="Product Catalog" style="border-radius: 8px; box-shadow: 0 4px 20px rgba(0,0,0,0.1);">
</p>
<p align="center"><em>Сетка товаров с удобными фильтрами и минималистичным дизайном.</em></p>

---

<h3 align="center">Профиль пользователя</h3>
<p align="center">
  <img src="https://github.com/user-attachments/assets/84c008f6-f552-4be9-84fb-884a0dcfe9a9" width="700" alt="User Profile" style="border-radius: 8px; box-shadow: 0 4px 20px rgba(0,0,0,0.1);">
</p>

---

<h3 align="center">Окно корзины и оформления заказа</h3>
<p align="center">
  <img src="https://github.com/user-attachments/assets/9be130f0-f41b-4f3a-8dd2-ebb93bda4993" width="700" alt="Cart Window" style="border-radius: 8px; box-shadow: 0 4px 20px rgba(0,0,0,0.1);">
</p>

---
