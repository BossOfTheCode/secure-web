# Лабораторная работа №1
> Цель работы: создание первого web приложения.
## Задание 1
1. Модифицируйте код в файле server_org.js таким образом, чтобы пользователи и пароли хранились в файле на диске.

![image](https://user-images.githubusercontent.com/79054264/148743087-9bbb2ed4-6fac-4325-88c5-f8ef4a57ef9c.png)
2. Замените примитивную проверку имени и пароля в строке 18 на проверку при помощи данных из пункта 1.

![image](https://user-images.githubusercontent.com/79054264/148743418-4f1f8c30-6afe-44dc-b9e1-32735e8a223f.png)

3. Подберите и отдавайте клиенту корректные HTTP коды в случае ошибок.

> 3.1. Если файл не найден или произошла ошибка при обработке нужно возвращать код из семейства 500.
> ![image](https://user-images.githubusercontent.com/79054264/148744802-69a1a9a8-208b-48e5-8944-f1fd2eac5ba5.png)
>
> 3.2. Если переданы пустой пользователь или пароль, то следует возвращать код 400.
> ![image](https://user-images.githubusercontent.com/79054264/148744925-6961f199-ebc8-4005-93b2-8ebd4fd58df6.png)
> 
> 3.3. Если переданы пользователь не найден или пароль не корректный, то следует возвращать код 403.
> ![image](https://user-images.githubusercontent.com/79054264/148745109-7e0a4108-cc7b-4b72-b90f-3206c1a45f79.png)
> ![image](https://user-images.githubusercontent.com/79054264/148745370-9b828960-a9ed-4539-aba8-5bb052aa7bf9.png)
> 
> 3.4. Если всё хорошо, то код 200.
>
>  ![image](https://user-images.githubusercontent.com/79054264/148745631-8cb98262-c8a7-4db0-9352-66a84669b8cf.png)

4. Запустите доработанный сервер node .\server_org.js и, пройдя по ссылке, http://127.0.0.1:8080/login.html убедитесь, что всё работает корректно: имена и пользователи хранятся во внешнем файле.

![image](https://user-images.githubusercontent.com/79054264/148745975-7911c059-ae0a-4e14-8492-4e763a261acd.png)

![image](https://user-images.githubusercontent.com/79054264/148745998-462ab795-245b-4549-a8a4-8d78ac39fceb.png)
