#Setup
Package.json Module Type
`npm init -y`
`npm install -D typescript @types/node`
#####Update the package.json with a build script and change the type to module.
`package.json
{
  "type": "module",
  "scripts": {
    "build": "tsc"
  },
}`

#### TS Config

##### Create a tsconfig.json file.

`touch tsconfig.json`
Use the NodeNext option to handle ES Modules with interop between CommonJS modules. If you want a detailed explaination of why this option is needed, check out this Stack Overflow thread.

####tsconfig.json
`{
    "compilerOptions": {
      "module": "NodeNext",
      "moduleResolution": "NodeNext",
      "target": "ES2020",
      "sourceMap": true,
      "outDir": "dist",
    },
    "include": ["src/**/*"],
  }
 `

## Setting Running Server and restart, cleaning and updating the server when a change is made

##### install node mode mon as a dev depenency. Nodemon watches for changes on to server and then restarts it if a change has happned

` npm install --save-dev nodemon
`

#### rimraf npm package Will clear out the dist folder when we re build the server. This will get rid of any old and or unused files in that folder.

` npm install rimraf
`

##### Install rimraf Globally so the command will work in the terminal

`npm install -g rimraf`
concurrently package will allows us to run mutiple scripts at once. Install as dev dependency

` npm i concurrently -D
`

#####Install concurrently Globally so the command will work in the terminal

`npm install -g concurrently`

####Add this below to your package.json so only the `npm run serve` will be needed to start the server and watch for all changes

` "scripts": {
    "build": "rimraf dist && npx tsc",
    "prestart": "npm run build",
    "start": "node dist/index.js",
    "preserve": "npm run build",
    "serve": "concurrently \"npx tsc -w\"  \"nodemon dist/index.js\""
  },
`

# Acknowledges

This setup guide was create using a combination of the youtube videos [How to Setup Node.js with TypeScript in 2023]
(https://www.youtube.com/watch?v=H91aqUHn8sE) 
by Beyond Fireship and 
[How To Use TypeScript With Express & Node](https://www.youtube.com/watch?v=qy8PxD3alWw) by 

https://fireship.io/lessons/typescript-nodejs-setup/  by PedroTech

