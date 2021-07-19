# Hot Module Replacement (HMR) Sample

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 11.2.14.

## Setup HMR (Hot Module Replacement)
Hot Module Replacement(HMR) is a feature of Webpack. The HMR updates your angular project without whole project recompile and reload.
You also check it out [this website](https://webpack.js.org/guides/hot-module-replacement/) for more information about HMR.

### Configuration
Add a file to `src/environments/environment.hmr.ts` and insert below contents:

``` javascript
export const environment = {
  production: false,
  hmr: true
};
```

After added above file, we need to update `src/environments/environment.*.ts` (prod and the default) and add the `hmr` property set to `false` like below.
``` javascript
// example for src/environments/environment.prod.ts 
export const environment = {
  production: true,
  hmr: false
};
```

After adding to environments this contents we should update angular.json file. We will enable hmr when the project build and serve. Add below contents to your `angular.json` file:
``` javascript
"build": {
    "configurations": {
    ...
      "hmr": {
        "fileReplacements": [
          {
            "replace": "src/environments/environment.ts",
            "with": "src/environments/environment.hmr.ts"
          }
        ]
      }
    }
  },
  ...
  "serve": {
    "configurations": {
    ...
    "hmr": {
      "hmr": true,
      "browserTarget": "<project-name>:build:hmr"
    }
  }
}
```

We should add types to `src/tsconfig.app.json` as node:
``` json
{
  ...
  "compilerOptions": {
    ...
    "types": ["node"]
  },
}
```

## Development server

Run `ng serve --configuration hmr` for a dev server. Navigate to `http://localhost:4200/`. The app will automatically update if you change any of the source files.

## Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory. Use the `--prod` flag for a production build.

## Running unit tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io).

## Running end-to-end tests

Run `ng e2e` to execute the end-to-end tests via [Protractor](http://www.protractortest.org/).

## Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI Overview and Command Reference](https://angular.io/cli) page.
