# Многопользовательский веб-интерфейс для управления базой данных компании, предоставляющей услуги коммуникаций и видеонаблюдения.

[![nextjs](https://img.shields.io/badge/next.js-v15.0.0-black?logo=next.js)](https://nextjs.org/)
[![typescript](https://img.shields.io/badge/typescript-5.4.4-blue?logo=typescript)](https://www.typescriptlang.org/)
[![tailwind](https://img.shields.io/badge/tailwindcss-3.4-teal?logo=tailwindcss)](https://tailwindcss.com/)
[![pnpm](https://img.shields.io/badge/pnpm-9.1.2-orange?logo=pnpm)](https://pnpm.io/)
[![license](https://img.shields.io/badge/license-MIT-green.svg)](#-license)

Многопользовательский веб-интерфейс для управления базой данных компании, предоставляющей услуги коммуникаций и видеонаблюдения.  
frontend собран на **next.js 15** (pages router), стилизован **tailwind css** и **shadcn/ui**, работает поверх api (fastapi + postgresql).  

> 🧪 проект выполнен в рамках курсовой работы на 3 курсе ИББД в университете ИТМО
> подробнее в ![курсовой работе](./course_project.pdf)
---

## Ключевые возможности

* адаптивный дашборд с role-based доступом;
* таблицы с сортировкой/фильтрацией (tanstack table);
* формы на react-hook-form + zod-schema валидации;
* авторизация next-auth, хранение jwt в httpOnly cookies;
* темная тема;
* instant-search, skeleton-loading и плавные framer-motion анимации;


---

## Стек и зависимост­и

| слой | пакеты |
|:---- |:------ |
| ui-kit | `shadcn/ui`, `lucide-react`, `tailwind-merge` |
| state/data | `@tanstack/react-query`, `zustand` |
| auth | `next-auth@5`, `jsonwebtoken`, `jose` |
| форматы | `zod`, `react-hook-form`, `react-hot-toast` |
| tooling | `pnpm`, `eslint`, `prettier`, `husky`, `lint-staged` |

---

## Структура проекта

```
├── frontend/                # next.js интерфейс
│   ├── src/                 # pages router
│   ├── components/          # общие компоненты
│   ├── hooks/               # хуки
│   ├── lib/                 # утилиты
│   └── public/              # статика
├── backend/                 # fastapi rest api
│   ├── main.py              # точка входа
│   ├── routers/             # эндпоинты
│   ├── models/              # sqlalchemy
│   └── migrations/          # alembic
├── nginx.conf               # nginx proxy конфиг
└── README.md

```

---

## backend API

в папке [`backend`](./backend) находится fastapi-приложение:

- REST API по всем сущностям (заявки, клиенты, сотрудники и пр.);
- авторизация через jwt;
- миграции через `alembic`;
- бд: PostgreSQL 15.

> главный файл входа — `main.py`  
> зависимости — `requirements.txt`

---

## Запуск проекта

```bash
# 1. клонируем репо
git clone https://github.com/x1r/cctv-company-management-dashboard.git
cd cctv-company-management-dashboard

docker-compose up --build
```


---

## .env.example

```env
# базовый api-endpoint
NEXT_PUBLIC_API_URL=http://localhost/api

# настройка next-auth
NEXTAUTH_URL=http://localhost:3000
NEXTAUTH_SECRET=supersecretkeyyoushouldchange

```

---

## npm-скрипты

| команда        | действие                |
| -------------- | ----------------------- |
| `pnpm dev`     | hot-reload dev-сервер   |
| `pnpm build`   | prod-сборка next js     |
| `pnpm lint`    | eslint + prettier       |
| `pnpm test`    | vitest                  |
| `pnpm prepare` | pre-install husky hooks |

