# [使用Kong和Konga管理微服务和API](https://segmentfault.com/a/1190000020375323)

# [kong学习][https://www.cnblogs.com/sunhongleibibi/tag/kong/]

# [kong][https://www.lijiaocn.com/tags/all.html#kong]

**1.Create a Docker network**

```
docker network create kong-net
```



**2.Start your database**

```
docker run -d --name kong-database \
               --network=kong-net \
               -p 5432:5432 \
               -e "POSTGRES_USER=kong" \
               -e "POSTGRES_DB=kong" \
               -e "POSTGRES_PASSWORD=kong" \
               postgres:9.6
```

**3.Prepare your database**

```
docker run --rm \
     --network=kong-net \
     -e "KONG_DATABASE=postgres" \
     -e "KONG_PG_HOST=kong-database" \
     -e "KONG_PG_USER=kong" \
     -e "KONG_PG_PASSWORD=kong" \
     kong:latest kong migrations bootstrap
```

**4.Start Kong**

```
docker run -d --name kong \
     --network=kong-net \
     -e "KONG_DATABASE=postgres" \
     -e "KONG_PG_HOST=kong-database" \
     -e "KONG_PG_USER=kong" \
     -e "KONG_PG_PASSWORD=kong" \
     -e "KONG_PROXY_ACCESS_LOG=/dev/stdout" \
     -e "KONG_ADMIN_ACCESS_LOG=/dev/stdout" \
     -e "KONG_PROXY_ERROR_LOG=/dev/stderr" \
     -e "KONG_ADMIN_ERROR_LOG=/dev/stderr" \
     -e "KONG_ADMIN_LISTEN=0.0.0.0:8001, 0.0.0.0:8444 ssl" \
     -p 8000:8000 \
     -p 8443:8443 \
     -p 127.0.0.1:8001:8001 \
     -p 127.0.0.1:8444:8444 \
     kong:latest
```

//不支持新版操作
**5.KONG Dashboard**`

```
docker run --rm --network=kong-net -p 8080:8080 -d --name kong-dashboard pgbi/kong-dashboard start \
  --kong-url http://kong:8001 \
  --basic-auth user1=password1 user2=password2
```

**5.konga prepare the database**

```
docker run --rm --network=kong-net pantsel/konga -c prepare -a postgres -u postgresql://kong:kong@kong-database:5432/konga_db
```

**6.start konga**

```
docker run -d -p 1337:1337 \
              --network kong-net \
              -e "DB_ADAPTER=postgres" \
              -e "DB_HOST=kong-database" \
              -e "DB_USER=kong" \
              -e "DB_PASSWORD=kong" \
              -e "DB_DATABASE=konga_db" \
              -e "KONGA_HOOK_TIMEOUT=120000" \
              -e "NODE_ENV=production" \
              --name konga \
              pantsel/konga
```


