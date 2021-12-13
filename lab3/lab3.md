# Лабораторная работа №3
> Цель работы: Поиск и устранение XSS уязвимостей.
## 1. Войдем на сайт

![image](https://user-images.githubusercontent.com/79054264/145775373-6ec6a1f7-6d22-4b88-aa9d-373f8568e406.png)

## 2. Попробуем обнаружить уязвимости

### 2.1. Reflecting XSS

При вводе следующего кода в фильтр выполнится скрипт:

![image](https://user-images.githubusercontent.com/79054264/145845123-b39cc03f-71c9-4671-9ee1-c5b0745e34ae.png)

### 2.2. Persisted (Stored) XSS

![image](https://user-images.githubusercontent.com/79054264/145775690-9b6cee26-84d8-4b4a-9fdc-6d31ee6d2d51.png)

Браузер интерпретирует введенный HTML, значит таким образом мы можем внедрить JS:

![image](https://user-images.githubusercontent.com/79054264/145776708-d1a5317a-a810-4463-847a-f69df908357e.png)

![image](https://user-images.githubusercontent.com/79054264/145776798-c7e532d1-c99c-4f29-969c-254b68860c0a.png)


### 2.3. Cookie Injection

Заметим, что текст над фильтром отображает значение текущей cookie:

![image](https://user-images.githubusercontent.com/79054264/145839074-99c6912e-63c5-408a-b99f-6228511c9a61.png)

И интерпретирует код:

![image](https://user-images.githubusercontent.com/79054264/145839412-81dc7ad1-bd2b-425c-855f-133859dfb02b.png)

### 2.4. Session Hijacking

При помощи обнаруженных уязвимостей можно похитить cookie и таким образом захватить сессию:

Reflecting XSS:
> ![image](https://user-images.githubusercontent.com/79054264/145778665-54b49650-b0ce-454e-9851-79bc17e70782.png)

Persisted XSS:
>![image](https://user-images.githubusercontent.com/79054264/145777202-65e8dae1-3dcf-4f9c-aa42-277343a1d56a.png)
>![image](https://user-images.githubusercontent.com/79054264/145777163-b5b1f951-9434-4262-9803-bf44344f563c.png)

Cookie Injection:
> ![image](https://user-images.githubusercontent.com/79054264/145839713-e0b6f781-e3d1-4f5f-8628-606fa6be3a1c.png)


## 3. Исправим уязвимости

### 3.1. Session Hijacking
Для предотвращения захвата сессии установим атрибут httpOnly для cookie, что запретит доступ к ним из JS.

![image](https://user-images.githubusercontent.com/79054264/145850872-0ef6afe7-1420-46b4-b37d-a6db111fe3e2.png)

Теперь внедренный код все еще выполняется, но у него нет доступа к cookie:

![image](https://user-images.githubusercontent.com/79054264/145851295-07725f76-e8bd-4ec7-b085-b6964a3cbb9f.png)
![image](https://user-images.githubusercontent.com/79054264/145851180-e19577c5-1d2d-4c4c-977b-2b87860968c8.png)

### 3.2. Хранимая XSS
Включим экранирование в шаблонизаторе:

![image](https://user-images.githubusercontent.com/79054264/145777650-706e99fc-d377-4f66-984a-576947415e5a.png)

Теперь внедренный код не интерпретируется:

![image](https://user-images.githubusercontent.com/79054264/145851979-21f41f20-95eb-48eb-aba4-f6bdab39e09d.png)

### 3.3. Отраженная XSS и Cookie Injection
Чтобы исправить данные уязвимости добавим HTTP-заголовок Content-Security-Policy, в котором укажем безопасный источник загрузки скриптов:

![image](https://user-images.githubusercontent.com/79054264/145779319-18cb3d1c-2ba9-411e-9b71-2cb922853c4d.png)

Теперь данные уязвимости больше нельзя эксплуатировать:

![image](https://user-images.githubusercontent.com/79054264/145852448-fca8663c-f9b6-4477-a169-70e94398c595.png)
![image](https://user-images.githubusercontent.com/79054264/145852948-369d1b3d-8b2b-4d48-9e4d-e0bb6d978a5b.png)

