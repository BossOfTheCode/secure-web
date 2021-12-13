# Лабораторная работа №3
> Цель работы: Поиск и устранение хранимой XSS.
## 1. Войдем на сайт

![image](https://user-images.githubusercontent.com/79054264/145775373-6ec6a1f7-6d22-4b88-aa9d-373f8568e406.png)

## 2. Попробуем обнаружить XSS

![image](https://user-images.githubusercontent.com/79054264/145775690-9b6cee26-84d8-4b4a-9fdc-6d31ee6d2d51.png)

Браузер интерпретирует введенный HTML, значит таким образом мы можем внедрить JS:

![image](https://user-images.githubusercontent.com/79054264/145776708-d1a5317a-a810-4463-847a-f69df908357e.png)

![image](https://user-images.githubusercontent.com/79054264/145776798-c7e532d1-c99c-4f29-969c-254b68860c0a.png)

Украдем куки пользователя:

![image](https://user-images.githubusercontent.com/79054264/145777202-65e8dae1-3dcf-4f9c-aa42-277343a1d56a.png)

![image](https://user-images.githubusercontent.com/79054264/145777163-b5b1f951-9434-4262-9803-bf44344f563c.png)

## 3. Исправим данную уязвимость

Включим экранирование в шаблонизаторе:

![image](https://user-images.githubusercontent.com/79054264/145777650-706e99fc-d377-4f66-984a-576947415e5a.png)

Теперь внедренный код не интерпретируется:

![image](https://user-images.githubusercontent.com/79054264/145777849-98e0b0a2-8469-458c-9fa7-6c5f8f4c5678.png)

Но все еще по-прежнему можно украсть куки при помощи отраженной XSS:

![image](https://user-images.githubusercontent.com/79054264/145778665-54b49650-b0ce-454e-9851-79bc17e70782.png)

Чтобы исправить данную уязвимость добавим HTTP-заголовок Content-Security-Policy, в котором укажем безопасный источник загрузки скриптов:

![image](https://user-images.githubusercontent.com/79054264/145779319-18cb3d1c-2ba9-411e-9b71-2cb922853c4d.png)

Теперь код, введенный в адресную строку, либо в фильтр, не выполняется.

