# Quasar App (test-vue3-quasar-form)

Реализация на VUE3 в произвольной верстке модального окна, состоящего из полей:

- Имя (обязательное)
- Фамилия
- Телефон (обязательное)
- Почта (обязательное)
- Сообщение.

Также подключена валидация полей:
- Имя и фамилия - до 100 символов
- Телефон - только российские номера
- Сообщение: до 500 символов

## Install the dependencies
```bash
yarn
# or
npm install
```

### Start the app in development mode (hot-code reloading, error reporting, etc.)
```bash
quasar dev
```


### Lint the files
```bash
yarn lint
# or
npm run lint
```


### Format the files
```bash
yarn format
# or
npm run format
```



### Build the app for production
```bash
quasar build
```

### Customize the configuration
See [Configuring quasar.config.js](https://v2.quasar.dev/quasar-cli-vite/quasar-config-js).
