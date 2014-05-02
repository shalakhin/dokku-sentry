# dokku-sentry

To install sentry you can also add Dokku plugins like memcached or redis.

- PostgreSQL plugin: https://github.com/Kloadut/dokku-pg-plugin
- Memcached plugin: https://github.com/jezdez/dokku-memcached-plugin
- Redis plugin: https://github.com/luxifer/dokku-redis-plugin

Update sentry.conf.py following [sentry instructions](http://sentry.readthedocs.org/en/latest/quickstart/#install-sentry).
sentry.conf.py is prepared for usage with dokku. You only have to update hostname, secret key and email settings.

```
git push production
```

First push will create app on dokku server and you'll be able to add plugins. Then:

```
dokku run [your app name] /bin/bash
sentry --config=sentry.conf.py upgrade
sentry --config=sentry.conf.py createsuperuser
```

Then restart dokku app (i.e. update README or *docker stop* and *dokku run*) and you get your sentry server.

