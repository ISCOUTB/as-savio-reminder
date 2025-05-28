# Savio App

## Acerca del Proyecto

SavioApp es una aplicación móvil que busca mejorar la accesibilidad y experiencia de los estudiantes al interactuar con la plataforma de aprendizaje Savio.
La aplicación es un fork de [moodleapp](https://moodledev.io/general/app), utiliza [Angular](https://angular.dev/) y el framework [Ionic](https://ionicframework.com/)(ionic cordova) para funcionar.
En [este documento](https://github.com/ISCOUTB/as-savio-reminder/blob/master/Arc42.md) se encuentra la información más detallada sobre el proyecto.

## Ejecutando el Proyecto

Se requiere tener node con la versión 20.18, normalmente configurado con algún administrador de versiones de node como [fnm](https://github.com/Schniz/fnm) o [nvm](https://github.com/nvm-sh/nvm).

1. `npm install`
2. `npm start` para la versión en el navegador, utilizará por defecto el port `8100`. `npm run dev:android` para la versión móvil/nativa. requiere un emulador de Android, [aquí](https://ionicframework.com/docs/developing/android) puedes encontrar la documentación para Android (también para [ios](https://ionicframework.com/docs/developing/ios)).

Los diferentes comandos se pueden encontrar en el archivo ./package.json en la sección de scripts.
