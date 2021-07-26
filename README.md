# NPM Guide

![NPM Cover](https://upload.wikimedia.org/wikipedia/commons/thumb/d/db/Npm-logo.svg/1200px-Npm-logo.svg.png)

## Contents

- [Introduction](#introduction)
- [Getting npm](#getting-npm)
- [npm Help](#npm-help)
- [package.json File](#package.json-file)
- [package.json Defaults](#package.json-defaults)
- [Installing Local Packages](#installing-local-packages)
- [Uninstalling Local Packages](#uninstalling-local-packages)
- [Installing Global Packages](#installing-global-packages)
- [Uninstalling Global Packages](#uninstalling-global-packages)
- [Listing Packages](#listing-packages)
- [npm Versioning](#npm-versioning)
- [Installing from package.json](#installing-from-package.json)
- [Updating Packages](#updating-packages)
- [npm Prune](#npm-prune)
- [npm Shortcuts](#npm-shortcuts)
- [npm Scripts](#npm-scripts)

## Introduction

- npm is a package manager for JavaScript
- Modules - The individual files containing reusable code are called as Modules
  ![1](https://github.com/abhinavg916/npm-guide/blob/master/Resources/1.png)
- Package - It is a directory that contains modules with a special file `package.json` is called as Package
  `package.json` contains the meta data about the package.
  ![2](https://github.com/abhinavg916/npm-guide/blob/master/Resources/2.png)
- It is way/medium/platform to share code with other developers and reuse the code to easily manage the different versions of code by other developers
- It also keeps the uniformity between developers by regular updates
- It maintains and handles compatibility changes very well
  ![3](https://github.com/abhinavg916/npm-guide/blob/master/Resources/3.png)

---

## Getting npm

- npm is shipped with NodeJs
- Download and Install NodeJs (LTS)
- Check node version by

```
node -v
```

- Check npm version by

```
npm -v
```

---

## npm Help

- All commands of npm

```
npm help
```

- `npn install` is the most common command and with `-h` gives the more options to install the packages

```
npm install -h
```

- `npm help-search <keyword>` npm searches for the keyword in its documentation and provides occurances of it

```
npm help-search update
```

- Below command, download the update documentation and opens up for the use in the browser

```
npm install update
```

---

## package.json File

- It is recommeded to add in the project folder
- Benefits:
  - Lets to manage dependencies like Working on Node project that requires Express then it is must to specify Express and its version
  - Lets to add Scripts - Helps with initial project build
  ```
  npm init
  ```
- **package.json**

```javascript
{
  "name": "npm-implementation",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC"
}
```

- To skip the question during `npm init`, we use

```
npm init --yes
```

---

## package.json Defaults

- To set defaults like author, license, etc.

```
npm config set init-author-name "Abhinav"
npm set init-license "MIT"
npm init --yes
```

- **package.json**

```javascript
{
  "name": "npm-implementation",
  "version": "1.0.0",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "Abhinav",
  "license": "ISC",
  "keywords": [],
  "description": ""
}
```

- To know the default value

```
npm config get init-author-name
npm get init-license
```

- To delete the default value

```
npm config delete init-licese
npm config delete init-author-name
npm init --yes
```

---

## Installing Local Packages

- To install packages locally on the system by `npm install <package-name>`
- NOTE: Be inside the project folder before installing
- Moment is a JavaScript library

```
npm install moment
```

- All packages are installed in `node_modules` folder in current directory
- `package.json` helps track the dependencies used in the project
- To save the package as dependency in `package.json` file, we use

```
npm install moment --save
```

- **package.json**

```
{
  "name": "npm-implementation",
  "version": "1.0.0",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "Abhinav",
  "license": "ISC",
  "keywords": [],
  "description": "",
  "dependencies": {
    "moment": "^2.27.0"
  }
}
```

- To install packages only for development and not for production purposes then we use

```
npm install lodash --save-dev
```

- By doing this, it creates a separate dependencie in `package.json` as `devDependencies`
- **package.json**

```javascript
{
  "name": "npm-implementation",
  "version": "1.0.0",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "Abhinav",
  "license": "ISC",
  "keywords": [],
  "description": "",
  "dependencies": {
    "moment": "^2.27.0"
  },
  "devDependencies": {
    "lodash": "^4.17.20"
  }
}
```

- From above, moment is the production dependency and lodash is development dependency

---

## Uninstalling Local Packages

- To uninstall the local packages by `npm uninstall <package-name>` but this not remove the dependency from the `package.json`

```
npm uninstall moment
```

- To remove the dependency as well with the package

```
npm uninstall moment --save
```

- To remove dev dependency

```
npm uninstall lodash --save-dev
```

- **package.json**

```javascript
{
  "name": "npm-implementation",
  "version": "1.0.0",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "Abhinav",
  "license": "ISC",
  "keywords": [],
  "description": "",
  "dependencies": {},
  "devDependencies": {}
}
```

---

## Installing Global Packages

- Some packages like grunt and gulp need to be used from the command line and in such scenarios package is preferred to be installed globally. So that it's binaries end up in the PATH environmnet variable. But after the installation the package is not found to be **node_modules** that because it's not locally

```
npm install moment -g
```

---

## Uninstalling Global Packages

```
npm uninstall moment -g
```

---

## Listing Packages

- To view the list of all locally and globally installed packages by
- Locally

```
npm list
```

- Global

```
npm list --global true
```

- NOTE: All the global packages are stored in `C:\Users\<Username>\AppData\Roaming\npm\node_modules`
- To limit the depth view of the list on console

```
npm list --global true --depth 1
npm list --depth 1
```

- 1 means immediate dependencies of the package, not the full tree
- 0 means no dependencies of the package is not shown, only the package name is shown

---

## npm Versioning

- It is important to know the working of versioning with the packages
- Semantic Versioning is a specification where a version is represented by three numbers that mean the same thing for every developer.
- For Example: `"lodash": "4.16.1"`
  - 4 represents the major version number
  - 16 represents the minor version number
  - 1 represents the patch version number
- Patch version number is updated when a bug is fixed or performance improvement
- Minor version number is updated when a new feature is introduced and does not break any existing functionality
- Major version number is updated when there's a break in the existing functionality
- To install a specific version of a package, `@` symbol is used

```
npm install lodash@3.3.0 --save
```

- **package.json**

```javascript
{
  "name": "npm-implementation",
  "version": "1.0.0",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "Abhinav",
  "license": "ISC",
  "keywords": [],
  "description": "",
  "dependencies": {
    "lodash": "^3.3.0"
  },
  "devDependencies": {}
}
```

- To install the latest patch version but specific major and minor version then

```
npm install lodash@4.14 --save
```

- **package.json**

```javascript
{
  "name": "npm-implementation",
  "version": "1.0.0",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "Abhinav",
  "license": "ISC",
  "keywords": [],
  "description": "",
  "dependencies": {
    "lodash": "^4.14.2"
  },
  "devDependencies": {}
}
```

- Similarly, to install the latest minor and patch version but specific major version then

```
npm install lodash@4 --save
```

- **package.json**

```javascript
{
  "name": "npm-implementation",
  "version": "1.0.0",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "Abhinav",
  "license": "ISC",
  "keywords": [],
  "description": "",
  "dependencies": {
    "lodash": "^4.17.20"
  },
  "devDependencies": {}
}
```

---

## Installing From package.json

- To install the packages through `package.json` is done using

```
npm install
```

- With `^` symbol in front of package name like `"lodash": "^4.17.20"` lets the npm to install the latest minor and patch version but keeping the specific major version
- With `~` symbol in front of pacakge name like `"lodash": "~4.17.20"` lets the npm to install the latest patch version only but keeping the specific major and minor version
- With `*` symbol in front of pacakge name like `"lodash": "*"` lets the npm to install the current latest version
- With no symbol in front of pacakge name like `"lodash": "4.17.20"` lets the npm to install the complete exact specific version

---

## Updating Packages

- To update the packages

```
npm update <package-name>
```

- To update only the development dependencies

```
npm update --dev --save-dev
```

- To update all the packages including development and production dependencies

```
npm update
```

- To update all the packages globally

```
npm update -g
```

- To update the latest npm then (but run cmd with adminstrative privileges)

```
npm install npm@latest -g
```

---

## npm Prune

- To remove the unused dependency, on seeing the extraneous packages through `npm list`

```
npm list
npm prune
```

---

## npm Shortcuts

- To create package with default values

```
Before: npm init --yes
After: npm init -y
```

- To install package locally

```
Before: npm install lodash
After: npm i lodash
```

- To save the package installed in the `package.json` during installation

```
Before: npm i lodash --save
After: npm i lodash -S
```

- To save the package as dev dependency

```
Before: npm install moment --save-dev
After: npm i moment -D
```

- Miscellaneuous
  - `--global` to `-g`
  - `npm -version` to `npm -v`
- More Shortcuts at - [NPM Shortcuts](https://docs.npmjs.com/misc/config)

---

## npm Scripts

- To run the application

```
node app.js
```

- Writing script to do the task automatically, replace `test` in scripts with the your keyword along with the command to execute
- **package.json**

```javascript
{
  "name": "npm-implementation",
  "version": "1.0.0",
  "main": "index.js",
  "scripts": {
    "start": "node App.js"
  },
  "author": "Abhinav",
  "license": "ISC",
  "keywords": [],
  "description": "",
  "dependencies": {
    "lodash": "^4.17.20"
  },
  "devDependencies": {}
}
```

```
npm start
```

- Scripts help in fasten and easier the work for developer

---

## Author

- Name - Abhinav
- GitHub - [github.com/abhinavg916](https://github.com/abhinavg916)
