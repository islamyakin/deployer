<!-- DO NOT EDIT THIS FILE! -->
<!-- Instead edit recipe/spiral.php -->
<!-- Then run bin/docgen -->

# How to Deploy a Spiral Project

```php
require 'recipe/spiral.php';
```

[Source](/recipe/spiral.php)

Deployer is a free and open source deployment tool written in PHP. 
It helps you to deploy your Spiral application to a server. 
It is very easy to use and has a lot of features. 

Three main features of Deployer are:
- **Provisioning** - provision your server for you.
- **Zero downtime deployment** - deploy your application without a downtime.
- **Rollbacks** - rollback your application to a previous version, if something goes wrong.

Additionally, Deployer has a lot of other features, like:
- **Easy to use** - Deployer is very easy to use. It has a simple and intuitive syntax.
- **Fast** - Deployer is very fast. It uses parallel connections to deploy your application.
- **Secure** - Deployer uses SSH to connect to your server.
- **Supports all major PHP frameworks** - Deployer supports all major PHP frameworks.

You can read more about Deployer in [Getting Started](/docs/getting-started.md).

The [deploy](#deploy) task of **Spiral** consists of:
* [deploy:prepare](/docs/recipe/common.md#deploy-prepare) – Prepares a new release
  * [deploy:info](/docs/recipe/deploy/info.md#deploy-info) – Displays info about deployment
  * [deploy:setup](/docs/recipe/deploy/setup.md#deploy-setup) – Prepares host for deploy
  * [deploy:lock](/docs/recipe/deploy/lock.md#deploy-lock) – Locks deploy
  * [deploy:release](/docs/recipe/deploy/release.md#deploy-release) – Prepares release
  * [deploy:update_code](/docs/recipe/deploy/update_code.md#deploy-update_code) – Updates code
  * [deploy:env](/docs/recipe/deploy/env.md#deploy-env) – Configure .env file
  * [deploy:shared](/docs/recipe/deploy/shared.md#deploy-shared) – Creates symlinks for shared files and dirs
  * [deploy:writable](/docs/recipe/deploy/writable.md#deploy-writable) – Makes writable dirs
* [deploy:vendors](/docs/recipe/deploy/vendors.md#deploy-vendors) – Installs vendors
* [spiral:encrypt-key](/docs/recipe/spiral.md#spiral-encrypt-key) – Generate new encryption key, if it doesn\'t exist
* [spiral:configure](/docs/recipe/spiral.md#spiral-configure) – Configure project
* [deploy:download-rr](/docs/recipe/spiral.md#deploy-download-rr) – Download RoadRunner
* [deploy:publish](/docs/recipe/common.md#deploy-publish) – Publishes the release
  * [deploy:symlink](/docs/recipe/deploy/symlink.md#deploy-symlink) – Creates symlink to release
  * [deploy:unlock](/docs/recipe/deploy/lock.md#deploy-unlock) – Unlocks deploy
  * [deploy:cleanup](/docs/recipe/deploy/cleanup.md#deploy-cleanup) – Cleanup old releases
  * [deploy:success](/docs/recipe/common.md#deploy-success) – Deploys your project
* [deploy:restart-rr](/docs/recipe/spiral.md#deploy-restart-rr) – Restart RoadRunner


The spiral recipe is based on the [common](/docs/recipe/common.md) recipe.

## Configuration
### shared_dirs
[Source](https://github.com/deployphp/deployer/blob/master/recipe/spiral.php#L10)

Overrides [shared_dirs](/docs/recipe/deploy/shared.md#shared_dirs) from `recipe/deploy/shared.php`.

Spiral shared dirs

```php title="Default value"
['runtime']
```


### writable_dirs
[Source](https://github.com/deployphp/deployer/blob/master/recipe/spiral.php#L13)

Overrides [writable_dirs](/docs/recipe/deploy/writable.md#writable_dirs) from `recipe/deploy/writable.php`.

Spiral writable dirs

```php title="Default value"
['runtime', 'public']
```


### roadrunner_path
[Source](https://github.com/deployphp/deployer/blob/master/recipe/spiral.php#L16)

Path to the RoadRunner server

```php title="Default value"
'{{release_or_current_path}}'
```


### dotenv_example
[Source](https://github.com/deployphp/deployer/blob/master/recipe/spiral.php#L18)

Overrides [dotenv_example](/docs/recipe/deploy/env.md#dotenv_example) from `recipe/deploy/env.php`.



```php title="Default value"
'.env.sample'
```



## Tasks

### spiral\:configure {#spiral-configure}
[Source](https://github.com/deployphp/deployer/blob/master/recipe/spiral.php#L58)

Configure project.

Spiral Framework console commands


### spiral\:cycle {#spiral-cycle}
[Source](https://github.com/deployphp/deployer/blob/master/recipe/spiral.php#L61)

Update (init) cycle schema from database and annotated classes.




### spiral\:migrate {#spiral-migrate}
[Source](https://github.com/deployphp/deployer/blob/master/recipe/spiral.php#L64)

Perform all outstanding migrations.




### spiral\:update {#spiral-update}
[Source](https://github.com/deployphp/deployer/blob/master/recipe/spiral.php#L67)

Update project state.




### spiral\:cache\:clean {#spiral-cache-clean}
[Source](https://github.com/deployphp/deployer/blob/master/recipe/spiral.php#L70)

Clean application runtime cache.




### spiral\:i18n\:reset {#spiral-i18n-reset}
[Source](https://github.com/deployphp/deployer/blob/master/recipe/spiral.php#L73)

Reset translation cache.




### spiral\:encrypt-key {#spiral-encrypt-key}
[Source](https://github.com/deployphp/deployer/blob/master/recipe/spiral.php#L76)

Generate new encryption key, if it doesn\'t exist.




### spiral\:views\:compile {#spiral-views-compile}
[Source](https://github.com/deployphp/deployer/blob/master/recipe/spiral.php#L79)

Warm-up view cache.




### spiral\:views\:reset {#spiral-views-reset}
[Source](https://github.com/deployphp/deployer/blob/master/recipe/spiral.php#L82)

Clear view cache.




### cycle\:migrate {#cycle-migrate}
[Source](https://github.com/deployphp/deployer/blob/master/recipe/spiral.php#L88)

Generate ORM schema migrations.

Cycle ORM and migrations console commands


### cycle\:render {#cycle-render}
[Source](https://github.com/deployphp/deployer/blob/master/recipe/spiral.php#L91)

Render available CycleORM schemas.




### cycle\:sync {#cycle-sync}
[Source](https://github.com/deployphp/deployer/blob/master/recipe/spiral.php#L94)

Sync Cycle ORM schema with database without intermediate migration (risk operation).




### migrate\:init {#migrate-init}
[Source](https://github.com/deployphp/deployer/blob/master/recipe/spiral.php#L97)

Init migrations component (create migrations table).




### migrate\:replay {#migrate-replay}
[Source](https://github.com/deployphp/deployer/blob/master/recipe/spiral.php#L100)

Replay (down, up) one or multiple migrations.




### migrate\:rollback {#migrate-rollback}
[Source](https://github.com/deployphp/deployer/blob/master/recipe/spiral.php#L103)

Rollback one (default) or multiple migrations.




### migrate\:status {#migrate-status}
[Source](https://github.com/deployphp/deployer/blob/master/recipe/spiral.php#L106)

Get list of all available migrations and their statuses.




### roadrunner\:serve {#roadrunner-serve}
[Source](https://github.com/deployphp/deployer/blob/master/recipe/spiral.php#L112)

Start RoadRunner server.

RoadRunner console commands


### roadrunner\:stop {#roadrunner-stop}
[Source](https://github.com/deployphp/deployer/blob/master/recipe/spiral.php#L117)

Stop RoadRunner server.




### roadrunner\:reset {#roadrunner-reset}
[Source](https://github.com/deployphp/deployer/blob/master/recipe/spiral.php#L120)

Reset workers of all services.




### deploy\:download-rr {#deploy-download-rr}
[Source](https://github.com/deployphp/deployer/blob/master/recipe/spiral.php#L126)

Download RoadRunner.

Download and restart RoadRunner


### deploy\:restart-rr {#deploy-restart-rr}
[Source](https://github.com/deployphp/deployer/blob/master/recipe/spiral.php#L132)

Restart RoadRunner.




### deploy {#deploy}
[Source](https://github.com/deployphp/deployer/blob/master/recipe/spiral.php#L146)

Deploys your project.

Main task


This task is group task which contains next tasks:
* [deploy:prepare](/docs/recipe/common.md#deploy-prepare)
* [deploy:vendors](/docs/recipe/deploy/vendors.md#deploy-vendors)
* [spiral:encrypt-key](/docs/recipe/spiral.md#spiral-encrypt-key)
* [spiral:configure](/docs/recipe/spiral.md#spiral-configure)
* [deploy:download-rr](/docs/recipe/spiral.md#deploy-download-rr)
* [deploy:publish](/docs/recipe/common.md#deploy-publish)
* [deploy:restart-rr](/docs/recipe/spiral.md#deploy-restart-rr)

