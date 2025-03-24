# DevOps Lab Project

## 🔧 Что входит

- Python-приложение (FastAPI)
- Docker + Docker Compose
- GitHub Actions (CI/CD)
- Ansible (удалённый деплой)
- SOPS (шифрование переменных)
- Telegram-уведомления
- Lint + Security анализ (bandit, trivy)

## 🚀 Как использовать

1. Настрой `.env` и зашифруй его:
   ```bash
   sops --encrypt --output .env.enc .env
   ```

2. Добавь в GitHub Secrets:
   - `GPG_PRIVATE_KEY`
   - `DEPLOY_USER`, `DEPLOY_HOST`
   - `TELEGRAM_TOKEN`, `TELEGRAM_CHAT_ID`

3. Сделай `git push` — CI сделает всё за тебя:
   - Проверит код
   - Построит Docker-образ
   - Проведёт security-проверки
   - Запустит Ansible-деплой
   - Уведомит в Telegram

## 📁 Структура проекта

- `app/` — Python FastAPI-приложение
- `nginx/` — конфигурация reverse-proxy
- `ansible/` — playbook для деплоя
- `.github/` — GitHub Actions CI/CD pipeline

Удачи в изучении DevOps! 💪
