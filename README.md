# Проект ведения оффлайн курсов на Laravel/VUE

## (в разработке)
Нумного красивого маркдауна
## Дневник

### Сетап для постгрес сервака

>**создаём базу** 

`CREATE DATABASE имя_базы`

1. Сначала заходим в поднятый сервак постгреса 
    `sudo -u postgres psql`

2. Создаём юзера, который представляет проект 
    `CREATE USER project_username WITH PASSWORD 'password'`
    >*имя пользователя без кавычек, пароль внутри - 'пароль'*

3. **Самое главное** - даём привилегии пользователю, представляющему проект
```
GRANT USAGE ON SCHEMA public TO your_username;
GRANT CREATE ON SCHEMA public TO your_username;

GRANT SELECT, INSERT, UPDATE, DELETE ON ALL TABLES IN SCHEMA public TO your_username;
ALTER DEFAULT PRIVILEGES IN SCHEMA public GRANT SELECT, INSERT, UPDATE, DELETE ON TABLES TO your_username;

GRANT USAGE, SELECT ON ALL SEQUENCES IN SCHEMA public TO your_username;
ALTER DEFAULT PRIVILEGES IN SCHEMA public GRANT USAGE, SELECT ON SEQUENCES TO your_username;
```
4. Можно выходить из консоли постгреса
`\q`

### Настройка работы ларавель с постгрес

1. Направляемся в корневую попку проекта и ищем файл *.env*
2. Внутри находим и меняем значения
```    
DB_CONNECTION=pgsql
DB_HOST=(айпи сервака базы (127.0.0.1 если локальная разработка))
DB_PORT=(дефолтный 5432, можно проверить в консоли ПОСТГРЕСА)
DB_DATABASE=(название базы)
DB_USERNAME=(Логин юзера проекта)
DB_PASSWORD=(Пароль юзера проекта) 
```
