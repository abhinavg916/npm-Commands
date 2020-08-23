# NPM Guide
## Introduction
* npm is a package manager for JavaScript
* Modules - The individual files containing reusable code are called as Modules
![1]()
* Package - It is a directory that contains modules with a special file `package.json` is called as Package
`package.json` contains the meta data about the package.
![2]()

* It is way/medium/platform to share code with other developers and reuse the code to easily manage the different versions of code by other developers
* It also keeps the uniformity between developers by regular updates
* It maintains and handles compatibility changes very well
![3]()

## Getting npm
* npm is shipped with NodeJs
* Download and Install NodeJs (LTS)
* Check node version by
```
node -v
```
* Check npm version by
```
npm -v
```
* All commands of npm
```
npm help
```
* `npn install` is the most common and with `-h` gives the more options to install the packages
```
npm install -h
```
* `npm help-search <keyword>` npm searches for the keyword in its documentation and provides occurances of it
```
npm help-search update
```
* Below command, download the update documentation and opens up for the use in the browser
```
npm install update
```

## package.json
* It is recommeded to add in the project folder
* Benefits:
    * Lets to manage dependencies like Working on Node project that requires Express then it is must to specify Express and its version
    * Lets to add Scripts - Helps with initial project build
    ```
    npm int
    ```
* __package.json__
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
* To skip the question during `npm init`, we use 
```
`npm init --yes`
```

##  package.json defaults
* To set defaults like author, license, etc.
```
npm config set init-author-name "Abhinav"
npm set init-license "MIT"
npm init --yes
```
* __package.json__
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
* To know the default value
```
npm config get init-author-name
npm get init-license
```
* To delete the default value
```
npm config delete init-licese
npm config delete init-author-name
npm init --yes
```

## Installing Local Packages
* 
