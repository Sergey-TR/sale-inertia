1. npm install

2. в файле .env пишем:

  DB_CONNECTION=mysql
  DB_HOST=db
  DB_PORT=3306
  DB_DATABASE=purchase
  DB_USERNAME=root
  DB_PASSWORD=root

3. docker-compose up -d

4. проверем все ли контейнеры поднялись и работают, бывает нет ошибки, а контейнер не поднялся

  docker ps -a

5. если все Ок, смотрим в браузере localhost:8080 должен выдать красивую ошибку

  Unable to locate file in Vite manifest: resources/js/Pages/Example.vue.

6. настраиваем БД

  я пользуюсь dbeaver, но смысл один, имя бд purchase, порт 33061, пользователь root, пароль root, делаем тест подключения, может выскочить ошибка, в дебивере надо во вкладке свойства драйверов allowPublicKeyRetrieval сделать тру.

  если все ок, идем дальше, в терминале пишем 

  docker exec -it shop_php bash

  заходим в контейнер и делаем миграцию, чтобы можно было пользователя юзать

  php artisan migrate

  возвращаемся в дебивер или куда там, обновляем и видим нашу бд и таблицы по умолчанию в ларе, одна из них юзер

7. открываем второй терминал и делаем 

  npm run dev

  обновлям страницу и видим серый экран, а в верхнем правом углу ссылки они рабочие
  на странице home вернуться в зад нужно нажать на кнопку синенькую.

ну а дальше ковыряйте что хотите.