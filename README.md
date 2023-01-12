# angular-jest-wallaby-setup-sample-project

This repository serves as a sample project for this PR: [Unable to make Wallaby.js work with Angular CLI + Jest · Issue #3144 · wallabyjs/public](https://github.com/wallabyjs/public/issues/3144)

**Setup**

* OS: Linux Mint based on Ubuntu 20.04.5 LTS
* Editor: Visual Studio Code with Wallaby.js and some other extensions
* Node.js: version 16.17.0
* NPM: version 8.15.0
* Angular CLI: version 15.0.4

**Steps performed to get it to this state**

* `ng new angular-jest-wallaby-setup-sample-project`
  * Chose no router and plain CSS styling
* `ng add @briebug/jest-schematic`
  * Schematic that removes Karma+Jasmine testing setup and adds basic Jest setup
* Renamed `jest.config.js` to `jest.config.js` and modified as stated in the `jest-preset-angular` README
  * https://github.com/thymikee/jest-preset-angular#configuration
  * Created `setup-jest.ts`
  * Added line to `jest.config.js`: `setupFilesAfterEnv: ['<rootDir>/setup-jest.ts']`
* Modified `tsconfig.spec.json` as stated in the `jest-preset-angular` README
  * https://github.com/thymikee/jest-preset-angular#configuration
  * Added line to `tsconfig.spec.json`: `"module": "CommonJs",`
* Added some type annotations to `app.component.spec.ts` to check whether Jest setup knowns how to parse TypeScript
* Created `wallaby.js` config

**Result**

* `npx jest` works
* `ng test` works
* Wallaby.js fails with `Runtime error: Jest encountered an unexpected token​​` error
  * Looks like Wallaby.js uses different Jest setup that cannot parse TypeScript
