`name: Build and Save Docker Image`

Это просто название workflow, которое будет видно во вкладке Actions в GitHub.


`on:
  push:
    branches: [ main ]
  pull_request:`

Это триггеры. Workflow запускается:

- при `push` в ветку `main`

- при `pull_request` в `main` (например, при открытии PR)

Ты можешь изменить `main` на другую ветку, если нужно.

`jobs:
  build:
    runs-on: ubuntu-latest
`
Это описание job'а (задания):

- `build` — имя (можно любое)

- runs-on: `ubuntu-latest` — GitHub выделит виртуалку с Ubuntu

`    steps:
    - name:  Checkout repo
      uses: actions/checkout@v4`

Первый шаг — клонирование кода репозитория в CI-среду.
`uses:` указывает на готовую GitHub Action (в данном случае — `actions/checkout`).
`    - name: Set up Docker Buildx
      uses: docker/setup-buildx-action@v3
`
Подключаем `Buildx`, который нужен для продвинутой сборки Docker-образов. Даже если не используешь multi-arch, GitHub рекомендует использовать `buildx`.

`    - name: Cache Docker layers
      uses: actions/cache@v4
      with:
        path: /tmp/.buildx-cache
        key: ${{ runner.os }}-buildx-${{ github.sha }}
        restore-keys: |
          ${{ runner.os }}-buildx-
`

Кэширование слоёв Docker, чтобы ускорить сборку при повторных коммитах.

- `key:` — уникальный ключ кэша (по SHA коммита)

- `restore-keys:` — шаблоны для восстановления (если точно такого нет)

`    - name: Build Docker image
      run: |
        docker build -t my-fastapi-app ./app
`

Сборка Docker-образа:

- `-t my-fastapi-app` — задаёт имя образу

- `./app` — путь, где лежит Dockerfile (внутри папки app/)

Сохраняем собранный образ как `.tar.gz` (сжатый файл) — он пригодится для скачивания или деплоя.

`    - name: Upload Docker image as artifact
      uses: actions/upload-artifact@v4
      with:
        name: docker-image
        path: my-fastapi-app.tar.gz
`
Загружаем `.tar.gz` в `GitHub Artifacts`. После завершения workflow можно зайти в `Actions → ваш job → Artifacts` и скачать его.

