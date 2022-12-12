# myWebpackBuild

## Клонирование репозитория

    git clone -b main git@github.com:hellsgor/myWebpackBuild.git

## Версионность

- node js - v.18.7.0
- npm - 8.15.0

## Работа с npm

- установка пакетов - `npm i`;
- запуск dev-сервера - `npm start`;
- сборка билда dev - `npm run dev`;
- сборка билда prod - `npm run build`.

## Файловая структура

- src/
  - assets/
    - fonts/ - шрифты;
    - img/ - изображения и иконки;
      - favicon - фавиконки;
      - icons - иконки;
    - styles - основные файлы стилей;
  - components - компоненты;
    - common - компоненты обязательные для всех страниц;
  - layouts - шаблоны страниц;
  - libs - для хранения сторонних библиотек;
  - pages - страницы;
    - \_partials - части страниц, которые не являются компонентами ввиду отсутствия необходимости в их переиспользовании;
  - ui-kit - микро-компоненты (кнопки, чек-боксы, инпуты и пр.);
  - utils - сервисы используемые в проекте вынесены в отдельную папку, например, файл send-form.js или inputs-validation.js.

## Alias'ы

- Img - './src/assets/img/';
- Fonts - './src/assets/fonts/';
- Components - './src/components/';
- Layouts - './src/layouts/';
- UIKit - './src/ui-kit/';
- Styles - './src/assets/styles/';
- Libs - './src/libs/' (на момент публикации не используется);
- NodeModules - './node_modules/';
- Partials - './src/pages/\_partials/';
- Utils - './src/utils/';

## Советы и правила

- файлы null следует удалить если в папке-родителе появятся файлы проекта. Файлы "null" требуются исключительно для сохранения файловой структуры в git;
- каждой новой странице после копирования кода pug и scss-файлов:
  - в pug изменить:
    - значение переменной `withHeaderFooter` если это необходимо (хедер, футер нужны /не нужны);
    - значение переменно `pageClassName` (назначить правильный класс тегу <main> для управления страницей);

## История версий

### v.0.1.0

- Базовая настройка webpack

### v.0.2.0

- в pug-файл страницы добавлена переменная `- let withHeaderFooter = true;` обозначающая необходимость добавления на страницу хедера и футера. В main-layout.pug добавлены условия отвечающее за добавление хедера и футера на страницу

      if (withHeaderFooter)
        include Components/common/header/header.pug

  и

      if (withHeaderFooter)
        include Components/common/footer/footer.pug

- footer уже прижат к "полу" в `main-layout.scss`;
- в pug-файл страницы добавлена переменная `- let pageClassName = 'main-page';`. Её значение подставляется как класс `<main>` для удобства управления страницей;

### v.0.3.0

- модифицирован .gitignore;
- добавлен babel;
- добавлен и настроен source-map;
- добавлен и настроен ESLint;
- добавлен Prettier;
- добавлен Autoprefixer;
- доработана структура сборки и билда;
- доработан webpack.config.js.
