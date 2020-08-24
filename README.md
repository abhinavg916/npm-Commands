# NPM Guide

## Introduction

- npm is a package manager for JavaScript
- Modules - The individual files containing reusable code are called as Modules
  ![1]()
- Package - It is a directory that contains modules with a special file `package.json` is called as Package
  `package.json` contains the meta data about the package.
  ![2]()
- It is way/medium/platform to share code with other developers and reuse the code to easily manage the different versions of code by other developers
- It also keeps the uniformity between developers by regular updates
- It maintains and handles compatibility changes very well
  ![3]()

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

## Package.json File

- It is recommeded to add in the project folder
- Benefits:
  - Lets to manage dependencies like Working on Node project that requires Express then it is must to specify Express and its version
  - Lets to add Scripts - Helps with initial project build
  ```
  npm int
  ```
- **package.json**

```
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
`npm init --yes`
```

---

## Setting up Package.json Defaults

- To set defaults like author, license, etc.

```
npm config set init-author-name "Abhinav"
npm set init-license "MIT"
npm init --yes
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
  },
  "devDependencies": {
    "lodash": "^4.17.20"
  }
}
```

- From above, moment is the production dependency and lodash is development dependency

---

## Uninstalling local packages

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
  "dependencies": {},
  "devDependencies": {}
}
```

---

## Installing Global Packages

- Some packages like grunt and gulp need to be used from the command line and in such scenarios package is preferred to be installed globally. So that it's binaries end up in the PATH environmnet variable. But after the installation the package is not found to be __node_modules__ that because it's not locally 
```
npm install moment -g
```
