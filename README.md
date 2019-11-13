# react-starter-js

## 목차

1. [프로젝트 생성](#1-프로젝트-생성)
2. [lint 설치](#2-lint-설치)
3. [eslint 설정](#3-eslint-설정)
   <!-- - [추가 패키지 설치](#31-추가-패키지-설치) -->
   <!-- - [parser, extends, rules 추가](#32-parser-extends-rules-추가) -->
   <!-- - [script 추가](#33-script-추가) -->
4. [prettier 설정](#4-prettier-설정)
   <!-- - [vscode 설정](#41-vscode-설정) -->
   <!-- - [prettierrc 파일 생성 및 설정](#42-prettierrc-파일-생성-및-설정) -->
   <!-- - [script 추가](#43-script-추가) -->
5. [stylelint 설정](#5-stylelint-설정)
   <!-- - [추가 패키지 설치](#51-추가-패키지-설치) -->
   <!-- - [stylelintrc 파일 생성 및 설정](#52-stylelintrc-파일-생성-및-설정) -->
   <!-- - [script 추가](#53-script-추가) -->
6. [프로젝트 기본경로 설정](#6-프로젝트-기본경로-설정)
7. [styled-components](#7-styled-components)
   <!-- - [패키지 설치](#71-패키지-설치) -->
   <!-- - [stylelint에 styled-components 추가](#72-stylelint에-styled-components-추가) -->

## 1. 프로젝트 생성

```shell
$ npx create-react-app [프로젝트명]
```



## 2. lint 설치

- `eslint`
- `prettier`
- `stylelint`

```shell
$ yarn add --dev eslint pretiier stylelint
```



## 3. eslint 설정

```shell
$ npx eslint --init
```



```shell
? How would you like to use ESLint? To check syntax, find problems, and enforce code style
? What type of modules does your project use? JavaScript modules (import/export)
? Which framework does your project use? React
? Does your project use TypeScript? No
? Where does your code run? Browser
? How would you like to define a style for your project? Use a popular style guide
? Which style guide do you want to follow? Airbnb (https://github.com/airbnb/javascript)
? What format do you want your config file to be in? JSON
Checking peerDependencies of eslint-config-airbnb@latest
The config that you've selected requires the following dependencies:

eslint-plugin-react@^7.14.3 eslint-config-airbnb@latest eslint@^5.16.0 || ^6.1.0 eslint-plugin-import@^2.18.2 eslint-plugin-jsx-a11y@^6.2.3 eslint-plugin-react-hooks@^1.7.0
? Would you like to install them now with npm? Yes
```



### 3.1 추가 패키지 설치

- `babel-eslint`
- `eslint-config-prettier`

```shell
$ yarn add --dev babel-eslint eslint-config-prettier
```



### 3.2 parser,  extends, rules 추가

- `.eslintrc.json`

```json
// .eslintrc.json

{
  "parser": "babel-eslint",
  "env": {
    "browser": true,
    "es6": true,
    "commonjs": true,
    "node": true,
    "jest": true
  },
  "extends": ["airbnb", "prettier"],
  "globals": {
    "Atomics": "readonly",
    "SharedArrayBuffer": "readonly"
  },
  "parserOptions": {
    "ecmaFeatures": {
      "jsx": true
    },
    "ecmaVersion": 2018,
    "sourceType": "module"
  },
  "plugins": ["react", "react-hooks", "jsx-a11y", "import"],
  "rules": {
    // https://eslint.org/docs/rules/require-jsdoc
    "require-jsdoc": [
      0,
      {
        "require": {
          "FunctionDeclaration": true,
          "MethodDefinition": true,
          "ClassDeclaration": true,
          "ArrowFunctionExpression": false,
          "FunctionExpression": false
        }
      }
    ],
    // https://eslint.org/docs/rules/valid-jsdoc
    "valid-jsdoc": [
      1,
      {
        "requireReturn": false
      }
    ],
    "no-unused-vars": 1,
    // individual
    "react/jsx-filename-extension": 0,
    "react/jsx-one-expression-per-line": 0
  }
}
```



### 3.3 script 추가

- `package.json`

```json
"scripts": {
  // start, build, test, eject ...
  "format:es": "eslint src"
}
```



## 4. prettier 설정

### 4.1 vscode 설정

- `settings` 열기

`cmd+shift+p` => open settings(JSON)

- eslint, stylelint 설정 추가
  - `"prettier-eslintIntegration": true,`
  - ` "prettier-stylelintIntegration": true,`

```json
// settings.json

{
  // ...
  "prettier-eslintIntegration": true,
  "prettier-stylelintIntegration": true
}
```



### 4.2 prettierrc 파일 생성 및 설정

- `.prettierrc.json`

```json
// .prettierrc.json

{
  "singleQuote": true,
  "trailingComma": "all",
  "printWidth": 80,
  "arrowParens": "avoid",
  "tabWidth": 2,
  "rules": {
    "sort-imports": 2
  },
  "proseWrap": "preserve",
  "react/jsx-wrap-multilines": [
    "error",
    {
      "declaration": false,
      "assignment": false
    }
  ]
}
```



### 4.3 script 추가

- `package.json`

```json
"scripts": {
  // start, build, test, eject ...
  "format:pre-write": "prettier --write \"src/**/*\""
}
```



## 5. stylelint 설정

### 5.1 추가 패키지 설치

- `stylelint-config-airbnb`
- `stylelint-order`
- `stylelint-scss`

```shell
$ yarn add --dev stylelint-config-airbnb stylelint-order stylelint-scss
```



### 5.2 stylelintrc 파일 생성 및 설정

- `.stylelintrc.json`

```json
// .stylelintrc.json

{
  "extends": ["stylelint-config-airbnb"],
  "rules": {
    "rule-empty-line-before": "always"
  }
}
```



### 5.3 script 추가

- `package.json`

```json
"scripts": {
  // start, build, test, eject ...
  "format:style-fix": "stylelint --fix \"src/**/*\""
}
```



## 6. 프로젝트 기본경로 설정

- jsconfig.json 파일 생성 및 수정

```json
// jsconfig.json

{
  "compilerOptions": {
    "baseUrl": ".",
    "paths": {
      "*": ["*", "src/*"]
    }
  }
}
```



## 7. styled-components

### 7.1 패키지 설치

- `styled-components`

```shell
$ yarn add styled-components
```



- example

`

```javascript
// Create a Title component that'll render an <h1> tag with some styles
const Title = styled.h1`
  font-size: 1.5em;
  text-align: center;
  color: palevioletred;
`;

// Create a Wrapper component that'll render a <section> tag with some styles
const Wrapper = styled.section`
  padding: 4em;
  background: papayawhip;
`;

// Use Title and Wrapper like any other React component – except they're styled!
render(
  <Wrapper>
    <Title>
      Hello World!
    </Title>
  </Wrapper>
);
```

`

### 7.2 stylelint에 styled-components 추가

- 패키지 설치
  - `stylelint-processor-styled-components`
  - `stylelint-config-styled-components`
  - `stylelint-config-recommended`

```shell
$ yarn add --dev stylelint-processor-styled-components stylelint-config-styled-components stylelint-config-recommended
```



- .stylelintrc 수정

```json
// .stylelintrc.json

{
  "processors": ["stylelint-processor-styled-components"],
  "extends": [
    "stylelint-config-airbnb",
    "stylelint-config-recommended",
    "stylelint-config-styled-components"
  ],
  "rules": {
    "rule-empty-line-before": "always"
  }
}
```

