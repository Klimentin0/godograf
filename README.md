# Проект ведения оффлайн курсов на Laravel/VUE

## (в разработке)

## Дневник

### Сетап для постгрес сервака

1. Сначала заходим в поднятый сервак постгреса 
    `sudo -u postgres psql`

2. Создаём юзера, который представляет проект 
    `CREATE USER project_username WITH PASSWORD 'password'`
    *имя пользователя без '', пароль внутри ''*

3. **Самое главное** - даём привилегии пользователю, представляющему проект (тут нужно только менять *your_username*)
GRANT USAGE ON SCHEMA public TO your_username;
GRANT CREATE ON SCHEMA public TO your_username;

GRANT SELECT, INSERT, UPDATE, DELETE ON ALL TABLES IN SCHEMA public TO your_username;
ALTER DEFAULT PRIVILEGES IN SCHEMA public GRANT SELECT, INSERT, UPDATE, DELETE ON TABLES TO your_username;

GRANT USAGE, SELECT ON ALL SEQUENCES IN SCHEMA public TO your_username;
ALTER DEFAULT PRIVILEGES IN SCHEMA public GRANT USAGE, SELECT ON SEQUENCES TO your_username;

4. Можно выходить из консоли постгреса
\q

### Настройка работы ларавель с постгрес

1. Направляемся в корневую попку проекта и ищем файл *.env*
2. Внутри находим и меняем значения
```    
DB_CONNECTION=pgsql
DB_HOST=127.0.0.1
DB_PORT=5432
DB_DATABASE=godograf_db
DB_USERNAME=morgan
DB_PASSWORD=testpass` 
```
