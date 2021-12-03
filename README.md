# Dashio Test Project Install Guide.

## Project setup
```
npm install
```

## Setup API END POINT
#### As default, it indicates http://localhost:8000/api since we use laravel backend API.
#### You can define it again in .env file on root level.
```
VUE_APP_API_END_POINT=http://localhost:8000/api/
```

### Compiles and hot-reloads for development
```
npm run serve
```

### This command will compile the frontend with api, you will see the link for checking as follow.
App running at:
  - Local:   http://localhost:8080/ 
  - Network: http://192.168.1.204:8080/
#### Go to browser and paste either of above ones.
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
