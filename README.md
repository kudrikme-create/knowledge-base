# База знаний команды

Документационный сайт на [MkDocs Material](https://squidfunk.github.io/mkdocs-material/), автоматически деплоится на GitHub Pages.

---

## Как устроен проект

```
docs/                    ← Весь контент (Markdown-файлы)
  index.md               ← Главная страница
  getting-started/       ← Раздел "Начало работы"
  policies/              ← Раздел "Политики"
  processes/             ← Раздел "Процессы"
  guides/                ← Раздел "Гайды"
  faq/                   ← Раздел "FAQ"
mkdocs.yml               ← Конфигурация: навигация, тема, плагины
.github/workflows/       ← GitHub Actions: авто-деплой при каждом коммите
```

---

## Как добавить новую статью (для всей команды)

1. Зайдите в нужную папку на GitHub (например `docs/guides/`)
2. Нажмите **Add file → Create new file**
3. Назовите файл: `название-статьи.md` (только латиница и дефисы)
4. Напишите содержимое в редакторе
5. Нажмите **Commit changes** — сайт обновится автоматически через ~90 секунд
6. Сообщите ответственному, чтобы он добавил статью в навигацию `mkdocs.yml`

## Как отредактировать существующую статью

1. Найдите нужный `.md` файл в папке `docs/`
2. Нажмите иконку карандаша (Edit this file)
3. Внесите правки
4. Нажмите **Commit changes** — готово

**Или:** нажмите кнопку **"Редактировать эту страницу"** прямо на сайте (правый верхний угол).

---

## Как добавить статью в навигацию (для ответственного)

Откройте `mkdocs.yml` и найдите блок `nav:`. Добавьте новую строку:

```yaml
nav:
  - Гайды:
      - guides/index.md
      - Новая статья: guides/new-article.md   ← добавить вот так
```

---

## Шпаргалка по Markdown (для нетехнических авторов)

```markdown
# Заголовок 1 (самый большой)
## Заголовок 2
### Заголовок 3

Обычный текст абзаца.

**Жирный текст**
*Курсив*

- Пункт маркированного списка
- Ещё один пункт

1. Первый шаг
2. Второй шаг
3. Третий шаг

[Ссылка](https://example.com)

| Колонка 1 | Колонка 2 |
|-----------|-----------|
| Ячейка    | Ячейка    |

!!! note "Примечание"
    Текст примечания (важная информация)

!!! warning "Внимание"
    Текст предупреждения

!!! tip "Совет"
    Полезная подсказка
```

---

## Первоначальная настройка (делается один раз администратором)

### 1. Обновите `mkdocs.yml`

Замените `YOUR-ORG` на ваш GitHub логин или название организации:

```yaml
site_url: https://ВАШ_ЛОГИН.github.io/team-knowledge-base/
repo_url: https://github.com/ВАШ_ЛОГИН/team-knowledge-base
```

### 2. Создайте репозиторий на GitHub

- Зайдите на [github.com](https://github.com) → New repository
- Название: `team-knowledge-base`
- Visibility: **Public** (обязательно для бесплатного GitHub Pages)
- Без README и .gitignore

### 3. Загрузите файлы на GitHub

```bash
cd team-knowledge-base
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/ВАШ_ЛОГИН/team-knowledge-base.git
git push -u origin main
```

### 4. Включите GitHub Pages

- Зайдите в репозиторий → **Settings → Pages**
- Source: **Deploy from a branch**
- Branch: `gh-pages` / root → **Save**

### 5. Дождитесь деплоя

- Перейдите во вкладку **Actions** репозитория
- Дождитесь зелёной галочки (1–2 минуты)
- Сайт будет доступен по адресу: `https://ВАШ_ЛОГИН.github.io/team-knowledge-base/`

---

## Локальный запуск (для разработчиков)

```bash
pip install mkdocs-material mkdocs-git-revision-date-localized-plugin
mkdocs serve
```

Сайт будет доступен на `http://localhost:8000`
