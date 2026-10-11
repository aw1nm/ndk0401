# ПР5 — «Автосалон»: разработка модулей и интеграция

Django-проект автосалона: 5 модулей (авторизация, каталог авто, клиенты, заказы, отчёты),
REST API на DRF с JWT-аутентификацией и Streamlit-дашборд.

## Структура
- apps/accounts — авторизация (JWT: регистрация, вход, профиль)
- apps/catalog  — каталог авто (марки, автомобили) + CRUD API
- apps/clients  — клиенты салона + CRUD API
- apps/orders   — заказы (покупка/тест-драйв/сервис) + бизнес-логика
- apps/reports  — отчёты/KPI (выручка, топ-модели, склад)
- dashboard/app.py — панель руководителя на Streamlit

## Запуск (Windows, VS Code)
1. Окружение и зависимости:
   ```
   python -m venv .venv
   .venv\Scripts\activate
   pip install -r requirements.txt
   ```
2. Поднять PostgreSQL (БД/пользователь `autosalon`), значения — в `.env`.
3. Миграции и администратор:
   ```
   python manage.py migrate
   python manage.py createsuperuser
   ```
4. Сервер API:
   ```
   python manage.py runserver
   ```
   Админка: http://127.0.0.1:8000/admin/ , API: http://127.0.0.1:8000/api/
5. Дашборд (в отдельном терминале):
   ```
   streamlit run dashboard/app.py
   ```

## Основные API-эндпоинты
- POST /api/auth/register/ , /api/auth/login/ , GET /api/auth/me/
- /api/brands/ , /api/cars/
- /api/clients/
- /api/orders/
- /api/reports/kpi/ , /revenue/ , /top-models/ , /manager-load/ , /stock/
