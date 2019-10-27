Sentry on YugaByte demo
-----------------------

1. `docker compose up -d`
2. `docker exec -it yb-master-n1 /home/yugabyte/bin/yb-admin --master_addresses yb-master-n1:7100 setup_redis_table`
3. `docker-compose exec sentry sentry upgrade`
