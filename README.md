# 🔄 DO13_CICD_Pipeline – CI/CD пайплайн с GitLab

**Проект по построению полного CI/CD пайплайна для микросервисного приложения с использованием GitLab CI, Kaniko, Helm и GitLab Runner**

[![GitLab CI](https://img.shields.io/badge/GitLab_CI-FC6D26?logo=gitlab&logoColor=white)](https://docs.gitlab.com/ee/ci/)
[![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?logo=kubernetes&logoColor=white)](https://kubernetes.io/)
[![Helm](https://img.shields.io/badge/Helm-0F1689?logo=helm&logoColor=white)](https://helm.sh/)
[![Kaniko](https://img.shields.io/badge/Kaniko-2C5F2D?logo=google&logoColor=white)](https://github.com/GoogleContainerTools/kaniko)
[![Docker](https://img.shields.io/badge/Docker-2496ED?logo=docker&logoColor=white)](https://www.docker.com/)
[![Postman](https://img.shields.io/badge/Postman-FF6C37?logo=postman&logoColor=white)](https://www.postman.com/)
[![Java](https://img.shields.io/badge/Java-ED8B00?logo=java&logoColor=white)](https://www.java.com/)

## 📋 О проекте

Проект посвящён созданию полноценного CI/CD пайплайна в GitLab для микросервисного приложения бронирования отелей. Пайплайн включает:

- **Сборку** Java-микросервисов (Maven).
- **Модульные тесты** (Unit Tests).
- **Сборку Docker-образов** с помощью Kaniko (без Docker-демона).
- **Публикацию образов** в Docker Hub.
- **Развёртывание** в staging-окружение Kubernetes через Helm.
- **Функциональные тесты** Newman (Postman).
- **Ручное подтверждение** для продакшн-деплоя.

Всё выполняется на GitLab Runner, развёрнутом в Kubernetes (k3s).

## 📚 Документация

- [**Описание задания**](docs/README_RUS.md)
- [**Отчёт о выполнении**](src/report.md)

## 🏗️ Структура проекта
```
DO13_CICD_Pipeline/
├── README.md
├── docs/
│ └── README_RUS.md
├── src/
│ ├── report.md
│ ├── screen/ # Скриншоты
│ ├── GitLabRunner/ # Конфигурация раннера
│ │ ├── config.toml
│ │ └── values.yaml
│ ├── helm-chart/ # Helm-чарт приложения
│ │ ├── Chart.yaml
│ │ ├── values.yaml
│ │ └── templates/
│ ├── services/ # Dockerfile для сервисов
│ │ ├── booking-service/
│ │ │ ├── Dockerfile
│ │ │ └── wait-for-it.sh
│ │ ├── ...
│ │ └── database/
│ │ ├── Dockerfile
│ │ └── init.sql
│ ├── tests/postman/ # Коллекция тестов
│ │ ├── application_tests.postman_collection.json
│ │ └── staging-env.json
│ └── Vagrantfile
```
## 🛠️ Выполненные задачи

- **Установка и настройка GitLab Runner** в Kubernetes (k3s).
- **Создание `.gitlab-ci.yml`** с этапами:
  - `build` – сборка всех микросервисов (Maven).
  - `test` – запуск модульных тестов.
  - `docker-build` – сборка образов через Kaniko и пуш в Docker Hub.
  - `staging` – деплой в staging через Helm и запуск Newman-тестов.
- **Настройка кэширования** Maven-зависимостей.
- **Использование переменных окружения** GitLab для секретов.
- **Безопасное создание Secret** в Kubernetes.
- **Автоматический деплой** при коммите в основную ветку.
- **Ручное подтверждение** для продакшн-деплоя.

## 💡 Приобретённые навыки

- Построение **CI/CD пайплайнов** в GitLab.
- Работа с **Kaniko** для сборки образов без Docker.
- **Helm** для развёртывания в Kubernetes.
- **GitLab Runner** в кластере Kubernetes.
- **Функциональное тестирование** через Newman.
- **Управление секретами** и переменными.

## 🚀 Как использовать

### Предварительные требования
- Кластер Kubernetes (k3s).
- GitLab-репозиторий с проектом.
- Настроенный GitLab Runner в Kubernetes.

### Запуск пайплайна
При пуше в ветку `main` автоматически запускается пайплайн. Для продакшн-деплоя требуется ручное подтверждение.

## 📊 Результаты проекта

- **Полностью автоматизированный CI/CD пайплайн**.
- **Сборка и публикация Docker-образов** через Kaniko.
- **Автоматический деплой** в staging и тестирование.
- **Успешное прохождение** Newman-тестов.

## 🔗 Связанные проекты

- [**DO12 – Helm**](https://github.com/Swarthma/DO12_Helm) – управление чартами
- [**DO11 – Продвинутый Kubernetes**](https://github.com/Swarthma/DO11_AdvK8s)
- [**D06 – CI/CD с GitLab**](https://github.com/Swarthma/D06_CICD) – базовый CI/CD
- [**D07 – Docker Compose & Swarm**](https://github.com/Swarthma/D07_Docker_Compose)

---

**Проект выполнен в образовательных целях для освоения CI/CD и автоматизации развёртывания.**

## 👨‍💻 Автор

**Галиуллин Линар** – начинающий DevOps инженер

[![Email](https://img.shields.io/badge/Email-linar.9207@gmail.com-D14836?logo=gmail)](mailto:linar.9207@gmail.com)
[![Telegram](https://img.shields.io/badge/Telegram-@Linar9207-2CA5E0?logo=telegram&logoColor=white)](https://t.me/Linar9207)
[![GitHub](https://img.shields.io/badge/GitHub-Swarthma-181717?logo=github)](https://github.com/Swarthma)

---

**Технологии:** GitLab CI, Kubernetes, k3s, Helm, Kaniko, Docker, PostgreSQL, RabbitMQ, Java, Postman, Newman, Vagrant

**Статус проекта:** ✅ Завершён