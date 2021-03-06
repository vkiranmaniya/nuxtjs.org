---
title: Публикация приложения на хостинге
description: Публикация приложения на хостинге
position: 2
category: features
---

## Статический хостинг

Nuxt.js также работает, как генератор статических сайтов.
Сгенерировав статическую версию Nuxt.js приложения, вы получаете все преимущества универсального приложения (SPA) работающего без сервера.

При помощи команды `nuxt generate` можно сгенерировать статическую версию вашего сайта.
Nuxt.js создаст HTML файл, для каждого из ваших маршрутов, и поместит их в папку `dist/`.

Это оптимизирует SEO, а также улучшает производительность и &laquo;offline&raquo; поддержку.

<base-alert type="info">

Динамические маршруты также будут сгенерированы благодаря [Nuxt Crawler](/docs/2.x/configuration-glossary/configuration-generate#crawler)

</base-alert>

Если вы хотите генерировать только статические сайты, нужно добавить настройку `target: 'static'` в конфигурационный файл `nuxt.config.js`

```js{}[nuxt.config.js]
export default {
  target: 'static' // По умолчанию значение 'server'
}
```

**Запуск `nuxt dev` в статическом режиме, позволяет улучшить качество разработки приложения:**

- Обработать на клиентской стороне: 404 ошибки, редиректы и прочие ошибки [Подробнее о SPA fallback](/docs/2.x/concepts/static-site-generation#spa-fallback)
- Удалить `req` и `res` из `context`
- Учесть особенности `$route.query`, который всегда будет равен `{}` при рендеринге на стороне сервера
- Значение `process.static` всегда будет равно `true`

<base-alert type="info">

Мы также предоставляем доступ к "process.target" авторам модулей, для добавления логики в зависимости от пользовательских целей.

</base-alert>

## Серверный хостинг

Серверный хостинг — это хостинг, который требует наличия сервера и предназначен для &laquo;SSR&raquo; приложений, где используют [serverMiddleware](/docs/2.x/configuration-glossary/configuration-servermiddleware).

Рендеринг на стороне сервера, известный как &laquo;SSR&raquo;, означает, что ваша страница сгенерируется на сервере по запросу пользователя.

Когда пользователь открывает вашу страницу в браузере, браузер отправляет запрос на сервер, запрашивая эту страницу.
Страница генерируется на сервере и отправляется обратно в браузер со всем своим содержимым.

Для размещения сайта на серверном хостинге, используйте `target: 'server'` в конфигурационном файле `nuxt.config.js`. Данное значение выставлено по умолчанию.

При помощи команды `nuxt build` можно сгенерировать SSR версию вашего сайта.

```js{}[nuxt.config.js]
export default {
  target: 'server'
}
```
