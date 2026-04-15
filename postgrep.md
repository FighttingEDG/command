## ps数据库常用命令
- 查看版本：psql --version
- 登录：psql -U postgres (-d database)；-d指定数据库
- 查看数据库：\l
- 查看占用内存最多的表：
```
    SELECT
        schemaname,
        relname AS table_name,
        pg_size_pretty(pg_total_relation_size(relid)) AS total_size
    FROM pg_catalog.pg_statio_user_tables
    ORDER BY pg_total_relation_size(relid) DESC
    LIMIT 20;
```