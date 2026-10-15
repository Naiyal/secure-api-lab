# Secure REST API with CI/CD

## Описание проекта
Защищенный REST API на Python/Flask с интеграцией в CI/CD для автоматической проверки безопасности. Проект демонстрирует защиту от OWASP Top 10 и практики DevSecOps.

## Стек технологий
- **Python 3.10** + **Flask** (веб-фреймворк)
- **SQLAlchemy** (ORM для защиты от SQLi)
- **Bcrypt** (хэширование паролей)
- **JWT** (аутентификация)
- **GitHub Actions** (CI/CD)
- **Bandit** (SAST), **Safety** (SCA)

## API Endpoints

| Метод | URL | Описание | Требует JWT |
|-------|-----|----------|-------------|
| POST | `/auth/register` | Регистрация нового пользователя | Нет |
| POST | `/auth/login` | Аутентификация и получение JWT | Нет |
| GET | `/api/data` | Получение защищенных данных | Да |

## Реализованные меры защиты

### 1. Защита от SQL Injection (SQLi)
Использование ORM (SQLAlchemy) вместо конкатенации строк. Все запросы параметризованы.
```python
user = User.query.filter_by(username=data['username']).first()




2. Защита от XSS
Все ответы возвращаются в формате JSON (jsonify), который автоматически экранирует HTML-символы.

3. Защита от Broken Authentication
Bcrypt для хэширования паролей с солью.

JWT-токены с временем жизни 1 час.

Декоратор @jwt_required() проверяет токен на защищенных эндпоинтах.

CI/CD Pipeline
Настроен GitHub Actions pipeline, который запускается при каждом push или pull request в ветку main.

Инструменты:
Bandit (SAST): Статический анализ кода Python на наличие уязвимостей.

Safety (SCA): Анализ зависимостей на известные уязвимости (CVE).


![alt text](https://user-images.githubusercontent.com/.../image.png)

![alt text](https://user-images.githubusercontent.com/.../2.jpg)

![alt text](https://user-images.githubusercontent.com/.../3.jpg)

Запуск проекта локально
bash
# Клонирование репозитория
git clone https://github.com/Naiyal/secure-api-lab.git
cd secure-api-lab

# Создание виртуального окружения
python -m venv venv
venvScripts activate  Windows

# Установка зависимостей
pip install -r requirements.txt

# Запуск
python app.py
Автор
Наял М.Фахд, группа 3410, ИТМО, 2026 г.