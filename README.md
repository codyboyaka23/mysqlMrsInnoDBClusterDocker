```bash
openssl x509 -in docker/mysql-router/certs/server.crt -out docker/mysql-router/certs/server.crt.pem
openssl rsa -in docker/mysql-router/certs/server.key -out docker/mysql-router/certs/server.key.pem
cat docker/mysql-router/certs/server.crt docker/mysql-router/certs/server.key > docker/mysql-router/certs/server.includeprivatekey.pem
```
```bash
docker compose restart mrs-router
docker exec -u root -ti mrs-mrs-router-1 mysql -u root -pcara55I0 -h mrs-server-1 --port 3301 < GRANT 'mysql_rest_service_admin' TO 'root'@'%';
docker exec -u root -ti mrs-mrs-router-1 mysql -u root -pcara55I0 -h mrs-server-1 --port 3301 < GRANT 'mysql_rest_service_meta_provider', 'mysql_rest_service_data_provider' TO 'restuser'@'%';
```



```bash
docker exec -u root -ti mrs-mrs-router-1 mysqlrouter -c /etc/mysqlrouter/mysqlrouter.conf
```


```bash
docker exec -u root -ti mrs-mrs-router-1 mysqlrouter_passwd set /etc/mysqlrouter/mysqlrouter.pwd webappuser
docker exec -u root -ti mrs-mrs-router-1 chown -R mysqlrouter:mysqlrouter /etc/mysqlrouter
docker exec -u root -ti mrs-mrs-router-1 mysqlrouter -a /etc/myrouter/mysqlrouter.conf
```

GRANT 'mysql_rest_service_admin' TO 'restuser'@'%';
GRANT 'mysql_rest_service_meta_provider', 'mysql_rest_service_data_provider' TO 'restuser'@'%';

/var/lib/mysqlrouter/.mysqlrouter.conf