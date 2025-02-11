# Steps for migrating from CRA to Vite

 1. remove "react-scripts" package from package.json
 2. install vite: "npm install vite @vitejs/plugin-react --save-dev"
 3. in Public/index.html, remove all references to "%Public_Url%".
    Ex: <link rel="icon" href="%Public_Url%/favicon.ico"></link>  will become  <link rel="icon" href="/favicon.ico"></link>
 4. replace all *.js, *.ts components files extensions with *.jsx, *.tsx
 5. move index.html to the root folder
 6. rename index.jsx file to main.jsx
 7. add <script type="module" src="/src/main.jsx"></script> to the <body> tag
 8. create in root the file vite.config.js file
 9. add the following minimal configuration to the vite.config.js file :
     `import { defineConfig } from 'vite'
     import react from '@vitejs/plugin-react'

       // https://vite.dev/config/
       export default defineConfig({
             plugins: [react()],
           })`
10. in package.json in the "scripts" section remove all references to react-scripts.
    Usually, you can find them in the "start, build, test, eject" commands,
    or you can have them replaced by the default Vite scripts
    and you can modify them later as you like
    `  "scripts": {
    "dev": "vite",
    "build": "tsc -b && vite build",
    "lint": "eslint .",
    "preview": "vite preview"
  }`
 
 Basically these are all the necessary steps in order to complete the migration.
    
