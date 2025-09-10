# Практичне заняття №1

## Тема: Проходження інтерактивного курсу «Git How To»

**Мета:** ознайомитися з базовими командами та принципами роботи з системою контролю версій Git шляхом проходження інтерактивного навчального курсу. Сформувати практині навички використання Git у консольному середовищі для виконання основних операцій.

## Хід роботи:

### Частина 1. Робота в соло

### Введення в контроль версій

**Система контролю версій** — це програма, яка відстежує всі зміни у файлах з часом. Вона дозволяє повернутися до попередніх версій, порівнювати зміни, бачити, хто і коли щось змінював, а також виявляти джерело проблем.

**Переваги системи контролю версій (Version Control System):**

- **Відстеження змін:** Система зберігає детальну інформацію про те, хто, що і коли змінював. Це дозволяє легко відстежувати розвиток проєкту.
- **Скасування змін:** Помилився? Легко повернутися до попереднього стану файлів. Можна експериментувати без страху втратити щось важливе.
- **Резервне копіювання та відновлення:** Файли можуть зберігатися в хмарі або на віддаленому сервері. Якщо щось трапиться з основним комп’ютером — дані можна відновити.
- **Синхронізація в команді:** У командній роботі всі зміни синхронізуються, що забезпечує злагоджену співпрацю.
- **Контроль якості:** Підтримуються перевірки коду — як вручну (рецензії від колег), так і автоматично (тести, лінтери). Це допомагає уникати помилок перед тим, як код потрапить у головну гілку.
- **Оновлення та сумісність:** Система допомагає керувати залежностями між частинами проєкту. Можна тестувати нові зміни, не порушуючи вже працюючий функціонал — як у пазлі, де частини змінюють форму, але загальна картина залишається цілісною.

**Git** — це система контролю версій, створена Лінусом Торвальдсом у 2005 році для розробки ядра Linux. Вона швидка, надійна та підходить як для маленьких, так і для великих проєктів.

Git керує файлами проєкту та відстежує зміни як знімки (snapshots) всієї файлової системи, а не окремих файлів.

**Три стани файлів:**

1.  **Working tree** — робоча директорія, де ти редагуєш файли.
2.  **Staging area** — проміжна зона, куди додаєш зміни перед комітом.
3.  **Repository** — база даних усіх комітів, зберігається в прихованій папці `.git`.

**Типовий Git-процес:**

1.  Редагуєш файли (working tree)
2.  Додаєш зміни до staging area (`git add`)
3.  Фіксуєш коміт (`git commit`)
4.  (Опціонально) Синхронізуєш з GitHub або іншим сервером (`git push` / `git pull`)

### Налаштування Git

**Git** - це текстовий інструмент командного рядка, який використовується через програмне забезпечення під назвою термінал.

- Команди `git -` без параметрів показує список доступних команд, як і `git help`.
- Щоб отримати детальну довідку по конкретній команді, використовуй `git help [команда]`. Наприклад, `git help commit` покаже документацію по команді `commit`.

Вводжу своє ім'я командою `git config --global user.name "Notmy Actualname"`, щоб налаштувати ідентифікацію автора змін в Git.

Вводжу свою електронну пошту командою `git config --global user.email "instantubique@gmail.com"`, щоб налаштувати її для ідентифікації.

![placeholder](https://markdowntoword.io/placeholder.png)

Вводимо команди для налаштування обробки кінців рядків у Git для Windows:

```bash
git config --global core.autocrlf true
git config --global core.safecrlf warn
```

- `git config --global core.autocrlf true` — автоматично конвертує кінці рядків у формат LF при коміті, щоб у репозиторії була уніфікована система.
- `git config --global core.safecrlf warn` — попереджатиме, якщо конвертація може призвести до незворотних змін у файлі.

![placeholder](https://markdowntoword.io/placeholder.png)

Налаштування виконано. Це допоможе уникнути проблем з форматуванням тексту при спільній роботі з людьми на різних ОС.

Вводимо команду `git config --global init.defaultBranch main`, щоб налаштувати гілку за замовчуванням з назвою `main` при створенні нового репозиторію.

![placeholder](https://markdowntoword.io/placeholder.png)

Налаштування виконано. Це узгоджує локальні налаштування Git з сучасними стандартами хмарних сервісів.

#### Запис змін до репозиторію

Перевіряємо поточну директорію командою `pwd`.

![placeholder](https://markdowntoword.io/placeholder.png)

Якщо потрібно, переходимо в кореневу директорію проекту командою `cd "шлях/до/директорії"`.

Ініціалізуємо новий порожній репозиторій Git командою `git init` у поточній директорії.

![placeholder](https://markdowntoword.io/placeholder.png)

Репозиторій успішно створено. Тепер поточна папка знаходиться під версійним контролем Git.

Створюємо файл `hello.html` з текстом "Hello, World!" командою:

```bash
echo "Hello, World!" > hello.html
```

![placeholder](https://markdowntoword.io/placeholder.png)

Відкриваємо файл у VS Code командою:

```bash
code hello.html
```
![placeholder](https://markdowntoword.io/placeholder.png)
![placeholder](https://markdowntoword.io/placeholder.png)

Файл створено та готовий для роботи з Git.

Додаємо файл `hello.html` до staging area (індекс) командою:

```bash 
git add hello.html
```

Створюємо коміт з повідомленням `"Initial commit"` командою:

```bash
git commit -m "Initial commit"
```

![placeholder](https://markdowntoword.io/placeholder.png)

Файл `hello.html` тепер під версійним контролем Git. Перший коміт у репозиторії створено.

Перевіряємо стан репозиторію командою `git status`.

![placeholder](https://markdowntoword.io/placeholder.png)

Це означає, що у робочій директорії немає незафіксованих змін, і репозиторій "чистий".

#### Скидання небажаних змін

Перевіряємо стан репозиторію командою `git status`.

![placeholder](https://markdowntoword.io/placeholder.png)

Результат покаже, що файл `hello.html` було змінено.

![placeholder](https://markdowntoword.io/placeholder.png)

Переглядаємо конкретні зміни у файлі командою `git diff`.

![placeholder](https://markdowntoword.io/placeholder.png)

У виводі побачимо рядки, видалені котом (-) та додані ним рядки (+).

Зміни виявлено. Готові відновити оригінальний стан файлу.

Відновлюємо файл `hello.html` до останнього закоміченого стану командою:

```bash
git restore hello.html
```

Перевіряємо стан репозиторію командою `git status`.

![placeholder](https://markdowntoword.io/placeholder.png)

Зміни кота успішно скасовано. Робоча директорія чиста.

Змінюємо файл `hello.html`, обернувши текст тегами `<head>`:

```bash
echo "<head>Hello, World!</head>" > hello.html
```

![placeholder](https://markdowntoword.io/placeholder.png)

Додаємо зміни до staging area командою:

```bash
git add hello.html
```

Видаляємо зміни з staging area (відміняємо додавання) командою:

```bash
git restore --staged hello.html
```

Перевіряємо статус:

![placeholder](https://markdowntoword.io/placeholder.png)

Зміни все ще у робочій директорії, але не в staging.

Повністю відкидаємо зміни у файлі командою:

```bash
git restore .
```

Фінальна перевірка статусу:

![placeholder](https://markdowntoword.io/placeholder.png)

Файл повернуто до оригінального стану. Помилка виправлена.

Змінюємо файл `hello.html`, обернувши текст у теги `<h1>`:

```bash
echo "<h1>Hello, World!</h1>" > hello.html
```

![placeholder](https://markdowntoword.io/placeholder.png)

Додаємо зміни до staging area:

```bash
git add hello.html
```

Створюємо коміт з повідомленням `"Added HTML tags to hello.html"`:

```bash
git commit -m "Added HTML tags to hello.html"
```

Виправляємо повідомлення останнього коміту командою:

```bash
git commit --amend -m "Added H1, HTML, and BODY tags to hello.html"
```

Додаємо HTML-структуру до файлу:

![placeholder](https://markdowntoword.io/placeholder.png)

Додаємо оновлені зміни до staging area:

```bash
git add hello.html
```

Вносимо зміни до останнього коміту з оновленим повідомленням:

```bash
git commit --amend -m "Added H1, HTML, and BODY tags to hello.html"
```

![placeholder](https://markdowntoword.io/placeholder.png)

Всі зміни об'єднано в один коміт з точним описом.

### Мітки та гілки
Переглядаємо історію комітів командою `git log`.

![placeholder](https://markdowntoword.io/placeholder.png)

Кожен коміт має унікальний SHA-1 хеш (наприклад, 346ca09...), який використовується для посилання на конкретную версію.

Також існують зручні скорочені форми посилань: короткий хеш (7 символів), теги, назви гілок, HEAD (останній коміт) тощо.

Створюємо тег версії 1.0 для останнього коміту:

```bash
git tag 1.0
```

Переглядаємо список усіх тегів у репозиторії:

```bash
git tag
```

![placeholder](https://markdowntoword.io/placeholder.png)

Тег успішно додано. Тепер коміт можна легко знайти за зрозумілою назвою версії замість SHA-1 хешу.

Переглядаємо список гілок у репозиторії командою:

```bash
git branch
```

![placeholder](https://markdowntoword.io/placeholder.png)

Зараз у нас є лише одна гілка `main` (позначена зірочкою як поточна).

**Основні поняття:**

- **Гілки** — це покажчики на коміти, які дозволяють працювати паралельно, не зачіпаючи стабільну версію.
- **HEAD** — покажчик на останній коміт поточної гілки.

**Стратегії роботи з гілками:**

- **Centralized Workflow** — всі працюють однією гілкою (наприклад, main).
- **Feature Branch Workflow** — кожна нова функція розробляється в окремій гілці.
- **Gitflow Workflow** — структурована система з довгостроковими (наприклад, main, develop) та короткостроковими гілками.
- **Forking Workflow** — кожен розробник має власну копію (fork) репозиторію.

Створюємо нову гілку `style` і переходимо на неї:

![placeholder](https://markdowntoword.io/placeholder.png)

Створюємо файл `style.css` з вмістом:

![placeholder](https://markdowntoword.io/placeholder.png)

Додаємо файл до staging area та комітимо:

![placeholder](https://markdowntoword.io/placeholder.png)

Оновлюємо `hello.html`, додаючи посилання на CSS:

![placeholder](https://markdowntoword.io/placeholder.png)

Додаємо зміни до staging area та комітимо.

Повертаємося на гілку `main`:

```bash
git switch main
```

Файл `style.css` зникає — це нормально, оскільки зміни є лише в гілці `style`.

Повертаємося на гілку `style`:

```bash
git switch style
```

Файл `style.css` знову присутній.

Переходимо на гілку `main`. Виконуємо злиття гілки `style` у `main`:

![placeholder](https://markdowntoword.io/placeholder.png)

Перевіряємо наявність файлу `style.css` за допомогою команди `ls`:

![placeholder](https://markdowntoword.io/placeholder.png)

Файл `style.css` тепер у гілці `main`.

Переглядаємо історію комітів:

```bash
git log
```

Тепер у історії `main` є коміти з гілки `style`.

Видаляємо гілку `style` (як непотрібну):

```bash
git branch -d style
```

![placeholder](https://markdowntoword.io/placeholder.png)

Гілка `style` успішно злита з `main` і видалена.

Переглядаємо історію комітів у компактному вигляді:

```bash
git log --oneline
```

![placeholder](https://markdowntoword.io/placeholder.png)

Експериментуємо з фільтрами та форматуванням:

- Обмежити кількість комітів: `git log --oneline --max-count=2`
- Фільтр за автором: `git log --oneline --author="Your Name"`
- Фільтр за часом: `git log --oneline --since="5 minutes ago"`

Створюємо власний формат виводу:

```bash
git log --format="%h %ad | %s%d [%an]" --date=short
```

![placeholder](https://markdowntoword.io/placeholder.png)

Встановлюємо цей формат за замовчуванням для поточного репозиторію:

```bash
git config format.pretty "%h %ad | %s%d [%an]"
git config log.date short
```

![placeholder](https://markdowntoword.io/placeholder.png)

Тепер історія комітів виводиться зручно та інформативно.

### Перегляд історії

Переглядаємо історію змін для конкретного файлу `hello.html`:

```bash
git log hello.html
```

Переглядаємо історію для `style.css`:

```bash
git log style.css
```

![placeholder](https://markdowntoword.io/placeholder.png)

Порівнюємо зміни між тегом `1.0 `та поточним станом (`HEAD`):

```bash
git diff 1.0 HEAD
```

![placeholder](https://markdowntoword.io/placeholder.png)

- `-` — видалені рядки (у старій версії 1.0).

- `+` — додані рядки (у поточній версії HEAD).

Порівняння показує, що у `hello.html` додано секцію `<head>` з посиланням на CSS, а також створено новий файл `style.css`.

Це допомагає аналізувати, як саме змінився код між версіями!

Додаємо "баг" до `hello.html`:

Додаємо рядок `<p>This is a bug!</p>` у тіло документа.

![placeholder](https://markdowntoword.io/placeholder.png)

Стейджимо та комітимо зміни:

```bash
git add hello.html
git commit -m "Introduced a bug"
```

Додаємо ще один коміт (DOCTYPE):

![placeholder](https://markdowntoword.io/placeholder.png)

```bash
git add hello.html
git commit -m "Added HTML5 doctype"
```

Знаходимо хеш коміту, який вніс баг:

```bash
git log --oneline
```

Відкатуємо коміт з багом:

```bash
git revert <commit>
```

(У редакторі зберігаємо стандартне повідомлення коміту revert).

![placeholder](https://markdowntoword.io/placeholder.png)

Перевіряємо зміни після revert:

```bash
git diff HEAD^ HEAD
```

Або скорочено:

```bash
git diff HEAD^
```

![placeholder](https://markdowntoword.io/placeholder.png)
![placeholder](https://markdowntoword.io/placeholder.png)

Створюємо гілку `experiment` і переходимо на неї:

```bash
git switch -c experiment
```

Створюємо файл `experiment.html` з вмістом `"This is an experiment."`:

```bash
echo "This is an experiment." > experiment.html
git add experiment.html
git commit -m "Add experiment file"
```

Видаляємо `<!DOCTYPE html>` з `hello.html`:

```bash
git add hello.html
git commit -m "Remove DOCTYPE"
```

Скидаємо гілку `experiment` до стану `main` (м'який скид — soft reset):

```bash
git reset --soft main
```

Зміни залишаються у робочій директорії та staging area.

Повністю скасовуємо всі зміни (жорсткий скид — hard reset):

```bash
git reset --hard main
```

Це видаляє всі зміни у робочій директорії та staging area.

Видаляємо файл `experiment.html` (який залишився як untracked):

```bash
rm experiment.html
```

![placeholder](https://markdowntoword.io/placeholder.png)

Перевіряємо статус:

```bash
git status
```

![placeholder](https://markdowntoword.io/placeholder.png)

Тепер гілка `experiment` чиста і ідентична `main`.

Повертаємося на гілку `main`:

```bash
git switch main
```

**Коротко про git reset vs git restore:**

- `git reset` — потужніший, рухає покажчик гілки та може скидати зміни.
- `git restore` — безпечніший, тільки відновлює файли (не змінює історію).

`git restore` треба використовувати для скасування змін у файлах, а `git reset` — для перемотування історії гілки.

### Пульти керування та GitHub

**Віддалений репозиторій** - це копія вашого проекту, що зберігається на сервері (наприклад, GitHub, GitLab).

**Віддалений репозиторій дозволяє:**

- Ділитися кодом з іншими.
- Робити резервні копії вашої роботи.
- Працювати з будь-якого пристрою через синхронізацію.

**Як віддалений репозиторій працює:**

1. Ви створюєте локальний репозиторій (як ми робили).
2. Створюєте віддалений репозиторій на GitHub.
3. Пушите (відправляєте) ваші коміти на сервер: `git push`.
4. Інші люди можуть клонувати ваш репозиторій: `git clone`.
5. Вони можуть вносити зміни і пропонувати їх вам через pull request.

**Чому це корисно:**

- Наприклад, Linux, Python розробляються саме так!
- Ви можете брати участь у відкритих проектах.

Додаємо GitHub-репозиторій як віддалене джерело (remote):

```bash
git remote add origin https://github.com/gn4r4/gitbybit.git
```

![placeholder](https://markdowntoword.io/placeholder.png)

Перевіряємо успішність додавання:

```bash
git remote -v
```

![placeholder](https://markdowntoword.io/placeholder.png)

Тепер локальний репозиторій пов'язано з віддаленим на GitHub!

Відправляємо локальні коміти на GitHub:

```bash
git push origin main
```

![placeholder](https://markdowntoword.io/placeholder.png)

Після успішного виконання:

- Коміти та файли з'являться у вашому репозиторії на GitHub.
- Гілка `main` починає відстежувати віддалену гілку (tracking).

Отримуємо оновлення з GitHub (якщо є):

```bash
git pull origin main
```

![placeholder](https://markdowntoword.io/placeholder.png)

Ця команда:

1. Завантажує зміни з віддаленого репозиторію (fetch).
2. Зливає їх з вашою поточною гілкою (merge).

**Базовий workflow роботи з GitHub:**

1. `git pull` — отримати свіжі зміни.
2. Зробити свою роботу локально.
3. `git add` & `git commit` — зафіксувати зміни.
4. `git push` — опублікувати зміни на сервер.

Якщо працюємо в команді, завжди починаємо з `git pull`, щоб уникнути конфліктів.

Для безпеки GitHub вимагає токени замість паролів для аутентифікації.

**Чому небезпечно переписувати історію в публічних репозиторіях:**

Якщо ви вже запушили коміти на GitHub, а інші люди встигли їх скопіювати (pull), то зміна історії (наприклад, через `git rebase`, `git amend`, `git reset`) створить конфлікт у їхніх локальних копіях.

Їхні гілки перестануть відповідати віддаленій версії, і синхронізація стане складною.

**Золоте правило:** Ніколи не переписуйте історію публічних гілок (які вже були опубліковані).

**Як робити безпечно:**

- Якщо потрібно скасувати зміни — використовуйте `git revert`, який створює новий коміт-антуляцію, не видаляючи старий.
- Якщо переписування необхідне (наприклад, випадково закомітили пароль):
>1.Попередьте всіх колег.
>
>2.Виконайте зміни локально.
>
>3.Використовуйте `git push --force-with-lease` замість` --force` (це безпечніший вариант, який перевіряє, чи не були додані нові коміти іншими).

`git push --force` — небезпечний, може видалити чужі коміти.
`git push --force-with-lease` — безпечніший, перевіряє відповідність віддаленої гілки перед перезаписом.

### Кінець

![placeholder](https://markdowntoword.io/placeholder.png)


