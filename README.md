# myWebpackBuild

---

1. [Клонирование репозитория](#a-namerepo-clone-клонирование-репозитория-a)
2. [Версионность](#a-nameversions-версионность-a)
3. [Работа с npm](#a-namenpmcommands-работа-с-npm-a)
4. [Файловая структура](#a-namefile-structure-файловая-структура-a)
5. [Alias'ы](#a-namealias-aliasы-a)
6. [Советы и правила](#a-nametips-and-rules-советы-и-правила-a)
7. [История версий](#a-nameversion-history-история-версий-a)

   - [v.0.1.0](#a-name010-v010-a)
   - [v.0.2.0](#a-name020-v020-a)
   - [v.0.3.1](#a-name031-v031-a)
   - [v.0.3.2](#a-name032-v032-a)

---

## <a name='repo-clone'>Клонирование репозитория</a>

    git clone -b main git@github.com:hellsgor/myWebpackBuild.git

## <a name='versions'>Версионность</a>

- node js - v.18.7.0
- npm - 8.15.0

## <a name='npmcommands'>Работа с npm</a>

- установка пакетов - `npm i`;
- запуск dev-сервера - `npm start`;
- сборка билда dev - `npm run dev`;
- сборка билда prod - `npm run build`.

## <a name='file-structure'>Файловая структура</a>

- src/
  - assets/
    - favicon/ - фавиконки;
    - fonts/ - шрифты;
    - icons/ - иконки;
    - images/ - изображения;
    - json/ - для json-файлов;
    - pug/
      - mixins - для pug-миксинов 
    - styles/ - основные файлы стилей;
  - components/ - компоненты;
    - common/ - компоненты обязательные для всех страниц;
  - layouts/ - шаблоны страниц;
  - libs/ - библиотеки;
  - pages/ - страницы;
    - _partials/ - части страниц, которые не являются компонентами ввиду отсутствия необходимости в их переиспользовании;
    - main/ - файлы главной страницы;
    - ui-kit/ - файлы страницы uiKit;
  - ui-kit/ - микро-компоненты (кнопки, чек-боксы, инпуты и пр.);
  - utils/ - части js-кода используемые в проекте вынесены в отдельную папку, например, отправка или валидация полей формы и пр.

## <a name='alias'>Alias'ы</a>

- Img - './src/assets/image/';
- Icons - './src/assets/icons/';
- Fonts - './src/assets/fonts/';
- Components - './src/components/';
- Layouts - './src/layouts/';
- UIKit - './src/ui-kit/';
- Styles - './src/assets/styles/';
- Libs - './src/libs/' (на момент публикации не используется);
- NodeModules - './node_modules/';
- Partials - './src/pages/\_partials/';
- Utils - './src/utils/';
- Mixins (pug) - './src/assets/pug/mixins/';
- JSON - './src/assets/json'.

## <a name='tips-and-rules'>Советы и правила</a>

- файлы null следует удалить если в папке-родителе появятся файлы проекта. Файлы "null" требуются исключительно для сохранения файловой структуры в git;
- каждой новой странице после копирования кода pug:
  - в pug изменить:
    - значение переменной `header` если это необходимо (хедер нужен /не нужен);
    - значение переменной `footer` если это необходимо (футер нужен /не нужен);
    - значение переменной `pageClassName` (назначить правильный класс тегу <main> для управления страницей);

## <a name='version-history'>История версий</a>

### <a name='010'>v.0.1.0</a>

- Базовая настройка webpack

### <a name='020'>v.0.2.0</a>

- в pug-файл страницы добавлена переменная `- let withHeaderFooter = true;` обозначающая необходимость добавления на страницу хедера и футера. В main-layout.pug добавлены условия отвечающее за добавление хедера и футера на страницу

      if (withHeaderFooter)
        include Components/common/header/header.pug

  и

      if (withHeaderFooter)
        include Components/common/footer/footer.pug

- footer уже прижат к "полу" в `main-layout.scss`;
- в pug-файл страницы добавлена переменная `- let pageClassName = 'main-page';`. Её значение подставляется как класс `<main>` для удобства управления страницей;

### <a name='031'>v.0.3.1</a>

- модифицирован .gitignore;
- добавлен babel;
- добавлен и настроен source-map;
- добавлен и настроен ESLint;
- добавлен Prettier;
- добавлен Autoprefixer;
- доработана структура сборки и билда;
- доработан webpack.config.js.

### <a name='032'>v.0.3.2</a>

- изменён .gitignore - добавлен файл todo;
- доработано управление наличием хедера и футера на странице,  теперь с помощью двух переменных;
- devserver'у добавлено отслеживание всех файлов в папке `./src/UIKit/`;
- добавлены alias'ы Mixins, JSON, и соответствующие папки в структуру проекта;
- добавлено копирование всех файлов из папки `./src/assets/json/` в build;
- 
