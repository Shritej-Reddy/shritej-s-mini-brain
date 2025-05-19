[NPM start](https://docs.npmjs.com/cli/v10/commands/npm-install)

1. https://nodejs.org/en/learn/getting-started/an-introduction-to-the-npm-package-manager
2. https://www.youtube.com/watch?v=jHDhaSSKmB0&ab_channel=TraversyMedia
3. [[Semantic Versioning]]
4. [[npx]]
5. https://medium.com/@rwijayabandu/do-we-need-nodemon-anymore-85a0296dfcc2




### Commands:

npm init -> to create a package.json file to install dependencies for your project.
npm init --yes / npm init -y -> To accept all defaults
npm config set init-author-name "Shritej"
npm set init-licence "MIT"
npm get init-author-name
npm config delete init-author-name
npm config delete init-license
npm i lodash
npm i gulp --save-dev
npm install --production
npm uninstall gulp --save-dev / npm remove gulp --save-dev / npm rm gulp --save-dev / npm un gulp --save-dev
npm i lodash@4.17.3
npm i -g nodemon -> globally install nodemon
npm i live-server -g
npm list
npm list --depth 0
npm list --depth 2


### Scripts

in package.json add below
"scripts": {
	"start": "node app.js",
	"dev": "live-server"
}
now u can run "npm run start / npm start" -> it means execute command "node app.js"
other one would be "npm run dev" -> it will start the live server