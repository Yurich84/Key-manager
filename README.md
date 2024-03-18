<p align="center">
<img height="80" src="https://laravel.com/img/logomark.min.svg">
<img height="80" src="https://vuejs.org/images/logo.png" alt="Vue logo">
<img height="80" src="https://cdn.worldvectorlogo.com/logos/element-ui-1.svg">
</p>

<div align="center">

[![MIT Licensed](https://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat)](LICENSE)
[<img alt="GitHub Workflow Status (main)" src="https://img.shields.io/github/actions/workflow/status/Yurich84/key-manager/laravel-unit-testing.yml?branch=main&label=Tests">](https://github.com/Yurich84/key-manager/actions)
[<img alt="GitHub Workflow Status (main)" src="https://img.shields.io/github/actions/workflow/status/Yurich84/key-manager/php-cs-fixer.yml?branch=main&label=CodeStyle">](https://github.com/Yurich84/key-manager/actions)

</div>

## Extensions

- Back-End: [Laravel 11](https://laravel.com/)
- Front-End: [Vue3 Composition Api](https://vuejs.org) + [VueRouter](https://router.vuejs.org) + [Pinia](https://pinia.vuejs.org) + [VueI18n](https://kazupon.github.io/vue-i18n/)
- Login using [Vue-Auth](https://websanova.com/docs/vue-auth/home), [Axios](https://github.com/mzabriskie/axios) and [Sanctum](https://laravel.com/docs/8.x/sanctum).
- The api routes, are separate for each module, in **Modules/{ModuleName}/routes_api.php**
- [ElementPlus](https://element-plus.org/) UI Kit 
- [Lodash](https://lodash.com) js utilities
- [Day.js](https://dayjs.com) time manipulations
- [FontAwesome 6](http://fontawesome.io/icons/) icons

## Install
- `git clone https://github.com/Yurich84/key-manager.git`
- `cd /key-manager`
- `composer install`
- `cp .env.example .env` - copy .env file
- set your DB credentials in `.env`
- `php artisan key:generate`
- `php artisan migrate`
- `yarn install`

## Testing

### Unit Testing
`php artisan test`

## Usage
- `npm run dev` for hot reloading
- `php artisan serve` and go [localhost:8000](http://localhost:8000)
- Create new user and login.

### Creating module
You can easily create module with CRUD functionality.
 
`php artisan make:module {ModuleName}`

This will create: 

- **migration** `database/migrations/000_00_00_000000_create_{ModuleName}_table.php`

- **model** `app/Models/{ModuleName}.php`

- **factory** `database/factories/{ModuleName}Factory.php`

- **tests** `tests/Feature/{ModuleName}Test.php`

- **backend module** `app/Modules/{ModuleName}/`
```
{ModuleName}/
│
├── routes_api.php
│
├── Controllers/
│   └── {ModuleName}Controller.php
│
├── Requests/
│   └── {ModuleName}Request.php
│
└── Resources/
    └── {ModuleName}Resource.php
```

- **frontend module** `resources/js/modules/{moduleName}/`
```
{moduleName}/
│
├── routes.js
│
├── {moduleName}Api.js
│
├── {moduleName}Store.js
│
├── components/
    ├── {ModuleName}List.vue
    ├── {ModuleName}View.vue
    └── {ModuleName}Form.vue
```


> After creating module, you can edit model and migration by adding fields you need. 
> Also you can add this fields into view.
> Don't forget run php artisan migrate.

Every module loads dynamically.
