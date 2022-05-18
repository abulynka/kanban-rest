## Heroku deploy

```bash
git clone ...
git switch source

heroku create --region eu kanban-rest-rss

heroku plugins:install heroku-config
heroku addons:create heroku-postgresql:hobby-dev
heroku pg:credentials:url DATABASE

heroku config:set NPM_CONFIG_PRODUCTION=false
heroku config:set LOG_CONSOLE=false
heroku config:set LOG_ERR_LEVEL=warn
heroku config:set LOG_INFO_LEVEL=info
heroku config:set JWT_SECRET_KEY=secret-key
heroku config:set SALT_SIZE=10
heroku config:set USE_FASTIFY=true
heroku config:set USE_NPM_INSTALL=true
heroku config:set NODE_ENV=development

heroku config:push --file=.env.production

heroku git:remote -a kanban-rest-rss
git push heroku source:master

heroku logs --tail
```

