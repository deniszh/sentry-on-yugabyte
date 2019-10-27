Sentry on YugaByte demo
-----------------------

1. `docker compose up -d`
2. `docker exec -it yb-master-n1 /home/yugabyte/bin/yb-admin --master_addresses yb-master-n1:7100 setup_redis_table`
3. `docker-compose exec sentry sentry upgrade`
4. `docker-compose restart sentry`

Sentry config reference - https://github.com/getsentry/onpremise/blob/master/sentry.conf.py

D-oh
----

```
django.db.utils.NotSupportedError: NotSupportedError('DEFERRABLE constraint not supported yet\nLINE 4: ...eger NOT NULL REFERENCES "auth_permission" ("id") DEFERRABLE...\n                                                             ^\nHINT:  See https://github.com/YugaByte/yugabyte-db/issues/1129. Click \'+\' on the description to raise its priority\n',)
SQL: CREATE TABLE "auth_group_permissions" (
    "id" serial NOT NULL PRIMARY KEY,
    "group_id" integer NOT NULL,
    "permission_id" integer NOT NULL REFERENCES "auth_permission" ("id") DEFERRABLE INITIALLY DEFERRED,
    UNIQUE ("group_id", "permission_id")
)
;
```
