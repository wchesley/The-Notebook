# React.js

### React & React-dom CDN links: 

https://cdnjs.cloudflare.com/ajax/libs/react/16.7.0/cjs/react.production.min.js

https://cdnjs.cloudflare.com/ajax/libs/react-dom/16.7.0/umd/react-dom.production.min.js

Alternates: 

https://unpkg.com/react-dom@16/umd/react-dom.production.min.js

https://unpkg.com/react@16/umd/react.production.min.js

### JSX Preprocessor: 

Requires Node.js 

To run JSX Preprocessor

In root directory of app

Run `npm init -y` 

Run `npm install babel-cli@6 babel-preset-react-app@3`

Create a folder called src and run this terminal command: 

`npx babel --watch src --out-dir . --presets react-app/prod `

Were src is the JSX file to process and . is the directory for babel to output the js file

Note: npx in the last command, not npm

Spent forever getting JSX to go into browser... 

### Add JSX inline, in browser: 

The quickest way to try JSX in your project is to add this <script> tag to your page:

`<script src="https://unpkg.com/babel-standalone@6/babel.min.js"></script>`

Now you can use JSX in any <script> tag by adding type="text/babel" attribute to it. Here is an example HTML file with JSX that you can download and play with.

This approach is fine for learning and creating simple demos. However, it makes your website slow and isn’t suitable for production. When you’re ready to move forward, remove this new <script> tag and the type="text/babel" attributes you’ve added. Instead, in the next section you will set up a JSX preprocessor to convert all your <script> tags automatically.
Add JSX to a Project

Adding JSX to a project doesn’t require complicated tools like a bundler or a development server. Essentially, adding JSX is a lot like adding a CSS preprocessor. The only requirement is to have Node.js installed on your computer.

Go to your project folder in the terminal, and paste these two commands:

    Step 1: Run npm init -y (if it fails, here’s a fix)
    Step 2: Run npm install babel-cli@6 babel-preset-react-app@3

    Tip

    We’re using npm here only to install the JSX preprocessor; you won’t need it for anything else. Both React and the application code can stay as <script> tags with no changes.

Congratulations! You just added a production-ready JSX setup to your project.
Run JSX Preprocessor

Create a folder called src and run this terminal command:

npx babel --watch src --out-dir . --presets react-app/prod 

    Note

    npx is not a typo — it’s a package runner tool that comes with npm 5.2+.

    If you see an error message saying “You have mistakenly installed the babel package”, you might have missed the previous step. Perform it in the same folder, and then try again.

Don’t wait for it to finish — this command starts an automated watcher for JSX.

If you now create a file called src/like_button.js with this JSX starter code, the watcher will create a preprocessed like_button.js with the plain JavaScript code suitable for the browser. When you edit the source file with JSX, the transform will re-run automatically.

As a bonus, this also lets you use modern JavaScript syntax features like classes without worrying about breaking older browsers. The tool we just used is called Babel, and you can learn more about it from its documentation.

If you notice that you’re getting comfortable with build tools and want them to do more for you, the next section describes some of the most popular and approachable toolchains. If not — those script tags will do just fine!
