# Jenkins course repo

This web app is to be used alongside the https://www.lernard.com Jenkins course.
It was created very quickly using an automated tool, and although the details of how this was done do not relate to the course, if you're interested in creating you own, you can learn more below from the automatically generated readme that accompanies the app. 

## Using the Jenkinsfiles

The jenkinsfiles for each section all live in the root of the repo, but as the chapter progresses they get renamed to be suffixed with their appropriate section name. 
Only the jenkinsfile with the exact name "Jenkinsfile" will be picked up by Jenkins, so if you are copying this repo to follow along with a section without having to write your own code, you will need to rename the appropriate file, eg:

```rm Jenkinsfile-section4 Jenkinsfile```

## Creation

This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).

## Available Scripts

In the project directory, you can run:

### `npm start`

Runs the app in the development mode.<br />
Open [http://localhost:3000](http://localhost:3000) to view it in the browser.

The page will reload if you make edits.<br />
You will also see any lint errors in the console.

### `npm test`

Launches the test runner in the interactive watch mode.<br />
See the section about [running tests](https://facebook.github.io/create-react-app/docs/running-tests) for more information.

### `npm run build`

Builds the app for production to the `build` folder.<br />
It correctly bundles React in production mode and optimizes the build for the best performance.

The build is minified and the filenames include the hashes.<br />
Your app is ready to be deployed!

See the section about [deployment](https://facebook.github.io/create-react-app/docs/deployment) for more information.

