# Лабораторная работа №2
> Цель работы: Поиск и устранение SQL Injection.
## Задание 1
1. Войти на сайт и увидеть список книг и авторов

![image](https://user-images.githubusercontent.com/79054264/142739332-3586fc30-9361-4bb2-8bb0-b872889ccefb.png)
2. Обнаружить sql инъекцию

При вводе символа апострофа ' в фильтр, в браузер выводится лог с сообщением об ошибке и запросом к базе данных

![image](https://user-images.githubusercontent.com/79054264/142739579-c4265fe5-5a88-49d1-acda-7b43bf7f210d.png)

2.1. Обход установленного фильтра

![image](https://user-images.githubusercontent.com/79054264/142739817-e0a06516-01af-4ba4-80f9-089126c2e503.png)

2.2. Получение данных из другой таблицы

![image](https://user-images.githubusercontent.com/79054264/142739841-a8982dad-e455-4c92-bea2-8b78d4952e8d.png)

2.3. Похищение пароля пользователя

![image](https://user-images.githubusercontent.com/79054264/142739917-768e5944-2f32-4afb-ad0b-679136343f6d.png)

3. Исправить уязвимость

Данная уязвимость исправляется параметризацией запроса, и еще по-хорошему не надо передавать в ответе лог ошибки:

![image](https://user-images.githubusercontent.com/79054264/142740071-01aa8d3f-3fbf-44d4-8e50-e4885bba7fe3.png)

![image](https://user-images.githubusercontent.com/79054264/142740197-8708106d-e834-45eb-8261-6529a8517d56.png)

![image](https://user-images.githubusercontent.com/79054264/142740212-60ea968f-d817-4696-b579-0c33b174f2b0.png)

![image](https://user-images.githubusercontent.com/79054264/142740230-821e3952-ae71-40e7-8ea2-10cab6f138ce.png)



