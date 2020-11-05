# BORO-CMS

Максимальная простая CMS для школы.

## Задачи

У школы должен быть сайт с юридической, правовой и прочей информацией о ней (требования Минобразования). Кроме того, учителя хотят рассказывать о своей школе: 
писать новости, рассказывать о себе, давать какую-то дополнительную информацию детям и родителям.

Большинство существующих решений либо тяжеловесны и их сложно развёртывать и обслуживать (полностью статический сайт на FTP, Joomla), либо чересчур просты и 
в долгосрочном периоде усложняют работу над сайтом (Wix и другие конструкторы сайтов), либо не предоставляют достаточно возможностей по управлению 
постоянно меняющимся контентом (Tilda). Кроме того, неподготовленному пользователю сложно администрировать такие решения.

Данная CMS - попытка создать простое и максимально понятное решение для создания школьного сайта с нуля. Здесь для большинства случаев должны быть реализованы 
заранее заготовленные шаблоны, создавать и редактировать новости можно через простую веб-форму, а для документов можно проставлять теги и использовать их в
любом месте сайта.

## Типы страниц сайта

1. Новости с пагинацией
2. Документы и опциональный комментарий
3. Педколлектив (галерея с фото и информацией о педагогах)

## Администрирование

1. Создание новостей с HTML-редактурой и прикреплением фото.
2. Редактирование и удаление существующих новостей.
3. Загрузка документов и копирование ссылок на них для вставки в новости и на кастомные страницы.
4. Создание документальных страниц с описанием.
5. Создание кастомных страниц для учительских хотелок.

## Основные принципы

- Стек: Flask, jQuery, Bootstrap, Postgres
- Хранение всей статики в БД (ограничения Heroku, в будущем можно будет дописать код под статическое хранение в файловой системе).
- Публичный сайт составляется из отдельных элементов, каждый из которых может быть кастомизирован как угодно.
- Разделение API фронтенда и бэкенд-кода. Flask не должен знать о реализации загрузки и хранения изображений и документов.
- Защита от учителя. Весь ввод админа должен валидироваться: картинки должны сжиматься сервером, их названия должны конвертироваться из кириллицы в ASCII и быть
урлобезопасными.
- Жизнеспособная мобильная версия.
- QoL: докстринги для всех функций, комментирование нюансов, вынос JS в статические подключаемые файлы.

## Планируемые фазы

0. Начата работа над CMS.
1. Систему может администрировать разработчик, реализованы базовые функции, сайт полноценно работает.
2. Систему может администрировать любой учитель, у администратора есть доступ ко всему контенту сайта и возможность его редактировать.
3. Система может быть развёрнута и сконфигурирована сторонним пользователем в своём окружении.

## Планируемые релизы

0.0 <-- вы находитесь здесь

**0.1. Новости**
- можно создать новость, отредактировать или удалить существующую
- к новости можно прикрепить до 10 картинок, одну из этих картинок можно повесть в верхний правый угол новости и обтечь об неё текст
- можно получить список новостей при редактировании и пагинироваться, как на главной. Для этого можно использовать уже готовый темплейт news, просто подвесить туда id новости. Опционально сделать поиск-фильтр.
- при редактировании новости также можно редактировать или удалять картинки
- при удалении новости удаляются также и все прикреплённые к ней картинки.

**0.2. Документы**
- можно загрузить один или несколько документов в БД, редактировать их поля и удалять их
- можно получить список документов и фильтровать его, иметь возможность редактировать файлы (как метадату, так и заменять сам файл).
- можно получать ссылки для вставки, например, в новости. Это должны быть красиво оформленные элементы, условно, спаны со своим фоном и иконкой формата файла в начале, поэтому нужно уметь вставлять HTML-код в TinyMCE; либо оформлять их на стороне сервера автоматически.

**0.3. WYSIWYG-генерация страниц**
- визуальный редактор для меню: у сайта должна быть иерархическая карта, новую страницу можно перетащить мышкой на нужное место и сделать её родителем/потомком существующей страницы. Все страницы будут показывать основное меню и своё подменю. Также страницы можно открывать для редактирования и удалять из этого меню.
- создание своей страницы для вставки на сайт. Это должен быть статический элемент, чтобы отделить разработку от генерации контента. Можно загружать и искать картинки/документы и вставлять на лету в редактор. Это будет тот же элемент, что и в новостях, но более свободный...
- ЛИБО создание редактора-конструктора а-ля тильда с готовыми блоками, где будет сложнее ошибиться. https://editorjs.io/ выглядит хорошо.

**1.0b. Подготовка к релизу**
- создание всех нужных шаблонов
- создание всех нужных кастомных страниц через WYSIWYG
- отлов багов

**1.0. Релиз**
- можно загружать и редактировать новости
- можно загружать и редактировать документы
- можно загружать и редактировать изображения
- можно создавать и редактировать кастомные страницы
- все нужные шаблоны готовы и данные перенесены
