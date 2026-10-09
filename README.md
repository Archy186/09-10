# Задача 1
Сценарий выполнения задачи:

Установите docker и docker compose plugin на свою linux рабочую станцию или ВМ.
Если dockerhub недоступен создайте файл /etc/docker/daemon.json с содержимым: {"registry-mirrors": ["https://mirror.gcr.io", "https://daocloud.io", "https://c.163.com/", "https://registry.docker-cn.com"]}
Зарегистрируйтесь и создайте публичный репозиторий с именем "custom-nginx" на https://hub.docker.com (ТОЛЬКО ЕСЛИ У ВАС ЕСТЬ ДОСТУП);
скачайте образ nginx:1.29.0;
Создайте Dockerfile и реализуйте в нем замену дефолтной индекс-страницы(/usr/share/nginx/html/index.html), на файл index.html с содержимым:
<html>
<head>
Hey, Netology
</head>
<body>
I will be DevOps Engineer!</h1>
</body>
</html>
Соберите и отправьте созданный образ в свой dockerhub-репозитории c tag 1.0.0 (ТОЛЬКО ЕСЛИ ЕСТЬ ДОСТУП).
Предоставьте ответ в виде ссылки на https://hub.docker.com/<username_repo>/custom-nginx/general .

# ответ 
[https://hub.docker.com/r/archy186/custom-nginx/tags](https://hub.docker.com/layers/archy186/custom-nginx/1.0.0/images/sha256-a8ef502f7931ab23250851195c254f6facfae02410cee884b73506f8d5b739c0)

# Задача 2
Запустите ваш образ custom-nginx:1.0.0 командой docker run в соответвии с требованиями:
имя контейнера "ФИО-custom-nginx-t2"
контейнер работает в фоне
контейнер опубликован на порту хост системы 127.0.0.1:8080
Не удаляя, переименуйте контейнер в "custom-nginx-t2"
Выполните команду date +"%d-%m-%Y %T.%N %Z" ; sleep 0.150 ; docker ps ; ss -tlpn | grep 127.0.0.1:8080  ; docker logs custom-nginx-t2 -n1 ; docker exec -it custom-nginx-t2 base64 /usr/share/nginx/html/index.html
Убедитесь с помощью curl или веб браузера, что индекс-страница доступна.
В качестве ответа приложите скриншоты консоли, где видно все введенные команды и их вывод.
# Ответ 
<img width="945" height="406" alt="задание 2" src="https://github.com/user-attachments/assets/db10e728-b8c4-418b-87a9-8d3887e8daff" />

# Задача 3
Воспользуйтесь docker help или google, чтобы узнать как подключиться к стандартному потоку ввода/вывода/ошибок контейнера "custom-nginx-t2".
Подключитесь к контейнеру и нажмите комбинацию Ctrl-C.
Выполните docker ps -a и объясните своими словами почему контейнер остановился.
Перезапустите контейнер
Зайдите в интерактивный терминал контейнера "custom-nginx-t2" с оболочкой bash.
Установите любимый текстовый редактор(vim, nano итд) с помощью apt-get.
Отредактируйте файл "/etc/nginx/conf.d/default.conf", заменив порт "listen 80" на "listen 81".
Запомните(!) и выполните команду nginx -s reload, а затем внутри контейнера curl http://127.0.0.1:80 ; curl http://127.0.0.1:81.
Выйдите из контейнера, набрав в консоли exit или Ctrl-D.
Проверьте вывод команд: ss -tlpn | grep 127.0.0.1:8080 , docker port custom-nginx-t2, curl http://127.0.0.1:8080. Кратко объясните суть возникшей проблемы.
Это дополнительное, необязательное задание. Попробуйте самостоятельно исправить конфигурацию контейнера, используя доступные источники в интернете. Не изменяйте конфигурацию nginx и не удаляйте контейнер. Останавливать контейнер можно. пример источника
Удалите запущенный контейнер "custom-nginx-t2", не останавливая его.(воспользуйтесь --help или google)
В качестве ответа приложите скриншоты консоли, где видно все введенные команды и их вывод.
# Ответ 
<img width="950" height="840" alt="Задание 3" src="https://github.com/user-attachments/assets/c20357da-b225-4fe1-a30c-240db33fa9d4" />
<img width="926" height="303" alt="Задание 3-1" src="https://github.com/user-attachments/assets/8ac8fc65-21c0-4571-83fe-6589dd39e2ac" />
<img width="928" height="1002" alt="Задание 3-2" src="https://github.com/user-attachments/assets/a11fe622-31dd-46a3-a6ff-9276b7a920aa" />
<img width="926" height="1021" alt="Задание 3-3" src="https://github.com/user-attachments/assets/89d50344-803b-4dae-ad13-725e158ad372" />
<img width="949" height="250" alt="Задание 3-4" src="https://github.com/user-attachments/assets/79694d8f-8aa5-4bc0-aea5-02210b0d21fe" />
