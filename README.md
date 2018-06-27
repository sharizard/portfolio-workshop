# ATA Frontend - Introduction to React

Let's create a portfolio application together! The goal of this workshop is to create an application that is similar to this:
[Sharizard Portfolio](https://sharizard.github.io/portfolio/)

## Useful links

* [Getting Started with React](https://reactjs.org/docs/getting-started.html)
* [Thinking in React](https://reactjs.org/docs/thinking-in-react.html)
* [React Gh Pages](https://github.com/gitname/react-gh-pages)
* [CSS Preprocessor](https://github.com/facebook/create-react-app/blob/master/packages/react-scripts/template/README.md#adding-a-css-preprocessor-sass-less-etc)

## Prerequisites

### Install Chrome

Install [Chrome](https://www.google.com/chrome/browser/desktop/index.html)

### Install Git for Windows

Install [Git for Windows](https://git-scm.com/download/win)

### Join Github

Register at [Github](https://github.com/join):

1. Use your Accenture email, _my.name@accenture.com_.
2. Plan: Unlimited public repositories for free.
3. Click "skip this step".

### Clone the project

1. Open Command Prompt. ```Windows Button``` ```Command Prompt```
2. Navigate to “C:\Users<your.accenture.id>\Desktop\Repos” or desired location.```cd Repos```
3. Clone the repository by typing: ```git clone https://github.com/sharizard/portfolio-workshop.git```
4. Navigate to repository folder by typing the command:```cd portfolio-workshop```

### Install Node

Install [Node.js Current / Latest](https://nodejs.org/en/)

Verify Node installation:

* ```node -v```

* ```npm -v```

### Install React

Install create-react-app:

```
npm install create-react-app -g
```

### Install Visual Studio Code

Install [Visual Studio Code](https://nodejs.org/en/) or your favorite IDE

## You first React App

First, navigate out of repository folder. You should now be at “C:\Users<your.accenture.id>\Desktop\Repos” or desired location. 

Then, run following command in the terminal: 
```
create-react-app my-app
```

This command will create a React app with no build configuration.

```
cd my-app
npm start
```

Then open http://localhost:3000/ to see your app.
When you’re ready to deploy to production, create a minified bundle with npm run build.

For more information, see [create-react-app](https://github.com/facebook/create-react-app)

## Creating a portfolio website

This tutorial will not focus on how to style your React app. In order to save time, we have decided to include the CSS files necessary for this tutorial so you can focus on writing JavaScript.

### Step 1: Checkout development branch, install following npm packages, and update package.json

Navigate to the folder you cloned earlier. In case your dont remember, 

1. Navigate to “C:\Users<your.accenture.id>\Desktop\Repos” or desired location.```cd Repos```
2. Clone the repository by typing: ```git clone https://github.com/sharizard/portfolio-workshop.git```
3. Navigate to repository folder by typing the command:```cd portfolio-workshop```

and run following command in the terminal: 
```
git fetch
git checkout development
npm install
```

Then run the following commands to install necessary npm packages for this tutorial:
```
npm install node-sass-chokidar --save
npm install npm-run-all --save
npm install gh-pages --save-dev
```

After installing npm packages, update your package.json file. 

1. Open Visual Studio Code. Tip: write the command ```code .``` If this works, skip 3-5.
2. Click “File”
3. Click “Open folder”
4. Select the folder named “portfolio-workshop” located in “C:\Users\<your.accenture.id\Desktop\repos\portfolio-workshop”
5. Open the file "package.json". Tip for opening file, inside VSCode press:```CTRL+P``` and write ```package.json``` 

#### Add homepage label
Add the following snippet to package.json. You can place it below the private tag.
```
"homepage": "http://{USERNAME}.github.io/portfolio-workshop",
```

#### Update scripts block
Update the script block with the following snippet. Since we're using SASS to style our portfolio, we need some tools to convert our sass files to css files. Using node-sass-chokidar is one way to achieve our goal.

For more information, please visit [Adding a CSS preprocessor](https://github.com/facebook/create-react-app/blob/master/packages/react-scripts/template/README.md#adding-a-css-preprocessor-sass-less-etc).

```
"scripts": {
    "start-js": "react-scripts start",
    "start": "npm-run-all -p watch-css start-js",
    "build-js": "react-scripts build",
    "build": "npm-run-all build-css build-js",
    "build-css": "node-sass-chokidar --include-path ./src --include-path ./node_modules src/ -o src/",
    "watch-css": "npm run build-css && node-sass-chokidar --include-path ./src --include-path ./node_modules src/ -o src/ --watch --recursive",
    "test": "react-scripts test --env=jsdom",
    "eject": "react-scripts eject",
    "predeploy": "npm run build",
    "deploy": "gh-pages -d build"
  },
```


### Step 2: Deploy React app to GitHub pages
To deploy your app to GitHub pages, we need to make sure that the app works locally.

Run following command to test the app local:

```
npm start
```

Visit http://localhost:3000. In case it does not look OK, ask an adult for help.

Deploying to GitHub Pages:
```
npm run predeploy
npm run deploy
```

Visit https://{USERNAME}.github.io/portfolio-workshop/ . If you are able to see your React app, then congratulations. If not, it's ok. It's not you. It's me. 

For more information, visit [React-GH-Pages](https://github.com/gitname/react-gh-pages).

#### Step 2.X: Create Landing Page component

Before we get started, we need to update our styling. As mentioned earlier, we are not going to focus on how to style components. Hopefully, we will walk through styling through another workshop in the future. In the meantime, you should

1. Rename "App.css" to "App.scss" inside src/ folder.
2. Replace content in App.scss with:
```
@import 'styles/reset';
@import 'styles/breakpoints';
@import 'styles/global';
@import 'styles/socialIcons';
@import 'styles/scrollToNext';
@import 'styles/landingPage';
@import 'styles/navBar';
@import 'styles/aboutPage';
@import 'styles/scrollTop';
@import 'styles/aboutPage';
@import 'styles/color';
@import 'styles/portfolioPage';
@import 'styles/portfolioItem';
```

3. Add 'App.css' in your .gitignore file.

### Step 3: Create Landing Page component

#### Step 3.1 (Optional): A bit theory

The goal for this step is to create a new component called LandingPage, the first page that is visible to the user. For now, we will only add your name, title, and an image. But in later step, we will expand this component by adding a navbar, scrolling buttons, and social media icons.

There are 3 ways to create React components:

* Using a Variable Function
* Using a Class
* Using a Stateless Functional Component

For more information, please visit [3 Ways to Create React Components](https://medium.com/@the.benhawy/3-ways-to-create-react-components-8b3620e4ea0)

#### Step 3.2: How to create Landing Page Component

First of all, run the application locally by running ```npm start```.

1. Open Visual Studio Code. Tip: write the command ```code .``` If this works, skip 3-5.
2. Click “File”
3. Click “Open folder”
4. Select the folder named “portfolio-workshop” located in “C:\Users\<your.accenture.id\Desktop\repos\portfolio-workshop”. The project should be visible in VSCode. 
5. Navigate to public folder. Right click and create a new folder called "assets".
6. Add your desired image to the assets folder. You can for instance use the cartoon image provided by Ismar, or profile picture from Accenture.
7. Navigate to src folder. Right click on the folder and create a new folder called "components".
8. In src/components, create a new folder called pages.
9. In pages, create a new file called LandingPage.jsx.
10. Add the following snippet of code to LandingPage.jsx:
```
import React from 'react';

const LandingPage = () => {
    return (
        <div className="landing-page">
            <main>
                <div className="intro-wrapper">
                    <img 
                        src="assets/IMAGE_FILE.png"
                        alt="avatar"
                        className="avatar-img" />
                    <div className="intro-name">YOUR_NAME</div>
                    <div className="tagline">
                        YOUR_TITLE
                    </div>
                </div>
            </main>
        </div>
    )
}

export default LandingPage;

```

NB! Remember to change IMAGE_FILE, YOUR_NAME, and YOUR_TITLE to something appropriate.

11. Save your changes.
12. Create a new file under src/components/pages. Name it "index.js"
13. Add following snippet of code to index.js
```
export {default as LandingPage} from "./LandingPage";
```
14. Save file.
15. Open "App.js" under src/.
16. Remove everything inside the return statement in render-method.
17. Import LandingPage by adding ```import { LandingPage } from './components/pages';``` to your imports.
18. Add a new div inside return block in render method, then add the LandingPage component. App.js should look like this:
```
import React, { Component } from 'react';
import './App.css';
import {
  LandingPage
} from './components/pages';

class App extends Component {
  render() {
    return (
      <div className="landing-page">
        <LandingPage />
      </div>
    );
  }
}

export default App;

```

19. Save changes.
20. Go to the browser. Refresh page. You should now see the landing page including a picture, your name, and your title.
21. Congratulations. We can now move to step 4.

### Step 4: Create compoonent for NavBar

To navigate between the different pages, we will need a navigation bar.

1. Go to components/ folder.
2. Right click and create a new folder called "navbar".
3. Right click on navbar/ folder, and create a new file: "NavBar.jsx"
4. Open NavBar.jsx and the following snippet of code:
```
import React, { Component } from 'react';
import { toElement as scrollToElement } from '../../utils/scroll';

class NavBar extends Component {
    constructor(props) {
        super(props);
        this.handleScroll = this.handleScroll.bind(this);
        this.state = {
            isSticky: false
        }
    }

    componentDidMount() {
        window.addEventListener('scroll', this.handleScroll);
    }

    handleScroll() {
        if (window.pageYOffset > this.nav.offsetTop) {
            this.setState({
                isSticky: true
            });
        } else {
            this.setState({
                isSticky: false
            });
        }
    }

    scrollToPage(pageSelector) {
        const nextPage = document.querySelector(pageSelector);
        scrollToElement(nextPage);
    }

    render() {
        const stickyClass = this.state.isSticky ? 'sticky' : '';
        return (
            <nav
            className={stickyClass}
            ref={(elem) => {
              this.nav = elem;
            }}
            >
                <div className="menu">
                    <div
                        className="menu__item active"
                        onClick={(e) => this.scrollToPage('.about-page')}
                    >
                        About
                    </div>
                    <div
                        className="menu__item"
                        onClick={(e) => this.scrollToPage('.portfolio-page')}
                    >
                        Portfolio
                    </div>
                </div>
            </nav>
        )
    }
}

export default NavBar;

```

5. Save file. 

FYI, this block of code won't work yet. As you see in the imports block, we are trying to import some components from utils/scroll. These components does not exist yet.

For more information about React Props, please visit [ReactJs - Props Overview](https://www.tutorialspoint.com/reactjs/reactjs_props_overview.htm)
For more information about React state, please visit [ReactJs - State](https://www.tutorialspoint.com/reactjs/reactjs_state.htm)

### Step 5: Scrolling support

Our navigation bar depends on scrolling support.

1. Navigate to src/ folder. Create a new folder called utils.
2. Add a new file in src/utils. Name it "scroll.js"
3. Add the following block of code:
```
const isSmoothScrollSupported = ((document || {}).documentElement || {}).style
  ? 'scrollBehavior' in document.documentElement.style
  : false;

export const toTop = () => {
  if (isSmoothScrollSupported) {
    window.scrollTo({
      top: 0,
      left: 0,
      behavior: 'smooth'
    });
  } else {
    window.scrollTo(0, 0);
  }
};

export const to = (ycoordinate) => {
  if (isSmoothScrollSupported) {
    window.scroll({
      top: ycoordinate,
      left: 0,
      behavior: 'smooth'
    });
  } else {
    window.scrollTo(0, ycoordinate);
  }
};

export const toElement = (element) => {
  if (element) {
    if (isSmoothScrollSupported) {
      element.scrollIntoView({
        behavior: 'smooth',
        block: 'start'
      });
    } else {
      element.scrollIntoView();
    }
  }
};

export default {
  toTop,
  to,
  toElement
};

```

We should now be able to use the NavBar component.

#### Step 5.1: Update LandingPage component with NavBar

It is time to add our NavBar component to our LandingPage.

1. Go to src/components/pages and open LandingPage.jsx
2. Import NavBar component and add it inside ```<div className="landing-page">```, before the ```<main>``` tag. 

Expected result:
```
import React from 'react';
import NavBar from '../../../components/navbar/NavBar';

const LandingPage = () => {
    return (
        <div className="landing-page">
            <NavBar />
            <main>
                <div className="intro-wrapper">
                    <img 
                        src="assets/IMAGE_FILE.png"
                        alt="avatar"
                        className="avatar-img" />
                    <div className="intro-name">YOUR_NAME</div>
                    <div className="tagline">
                        YOUR_TITLE
                    </div>
                </div>
            </main>
        </div>
    )
}

export default LandingPage;
```

3. Save your changes.
4. Go to the browser and refresh site. Navigation bar should be visible. Feel free to click correctly, but it wont work yet as we cant scroll between pages.

### Step 6: Create a component for social icons

What is a portfolio page without icons for the different social medias?

1. Go to src/components. Add a new folder named "socialIcons". 
2. Inside the folder, create a new file with following name: "SocialIcons.jsx".
3. Paste following snippet of code:
```
import React from 'react';

const SocialIcons = () => {
  return (
    <div className="social-icons animate-icons">
        <a target="_blank" rel="noopener noreferrer" href="https://github.com/"><i className="fa fa-github"></i></a>
        <a target="_blank" rel="noopener noreferrer" href="https://www.linkedin.com/"><i className="fa fa-linkedin"></i></a>
      </div>
  );
};

export default SocialIcons;
```
4. Remember to change "hrefs" with the appropriate URLs for your GitHub and LinkedIn page. 
4a (optional): You can also add social icons for other social medias like Instagram or Facebook. See [FontAwesome Icons](https://fontawesome.com/icons?d=gallery) to find icons for your social medias. Then update the className inside the ```<i>``` tag.

#### Step 6.1: Update LandingPage with Icons

1. Go to src/components/pages and open LandingPage.jsx
2. Import SocialIcons component and add it inside ```<div className="intro-wrapper">``` tag, below tagline div. 

Expected result:
```
import React from 'react';
import NavBar from '../../../components/navbar/NavBar';
import SocialIcons from '../../socialIcons/SocialIcons';

const LandingPage = () => {
    return (
        <div className="landing-page">
            <NavBar />
            <main>
                <div className="intro-wrapper">
                    <img 
                        src="assets/IMAGE_FILE.png"
                        alt="avatar"
                        className="avatar-img" />
                    <div className="intro-name">YOUR_NAME</div>
                    <div className="tagline">
                        YOUR_TITLE
                    </div>
                     <SocialIcons />
                </div>
            </main>
        </div>
    )
}

export default LandingPage;
```

3. Save your changes.
4. Go to the browser and refresh site. Social icons should now be visible.

### Step 7: Create buttons for scrolling

Navigation bar is good, but not that good. We want some fancy buttons on the bottom of the page that can scroll to next, previous, or to top page.

1. Create a new folder inside "src/components" called "scroll". 
2. Create a new file "ScrollToPage.jsx".
3. Add the following block of code:
```
import React, { Component } from 'react';
import { toElement as scrollToElement } from '../../utils/scroll';

class ScrollToPage extends Component {

  scrollToPage() {
    const { pageSelector } = this.props;
    const nextPage = document.querySelector(pageSelector);
    scrollToElement(nextPage);
  }

  render() {
    const faIcon = this.props.isFinal ? 'fa-chevron-up' : 'fa-chevron-down'; 
    const color = this.props.isRed ? 'white' : 'red';
    return (
      <div className="scroll-to-next" onClick={(e) => this.scrollToPage()}>
        <div className={`arrow bounce ${color}`}>
          <div className="scroll-text">Click Me</div>
          <i className={`fa ${faIcon} fa-2x`} href="#" />
        </div>
      </div>
    );
  }
}

export default ScrollToPage;


```

4. Save changes.
5. Create a new file "ScrollTop.jsx".
6. Add the following block of code:
```
import React, { Component } from 'react';
import { toTop as scrollToPageTop } from '../../utils/scroll';

class ScrollTop extends Component {
  constructor(props) {
    super(props);
    this.handleScroll = this.handleScroll.bind(this);
    this.state = {
      shouldShowScrollTopArrow: false
    };
  }

  handleScroll() {
    const boundingRect = ((document || {}).documentElement || {})
      .getBoundingClientRect;
    if (boundingRect) {
      if (document.documentElement.getBoundingClientRect().top * -1 > 100)
        this.setState({ shouldShowScrollTopArrow: true });
      else this.setState({ shouldShowScrollTopArrow: false });
    }
  }

  componentDidMount() {
    window.addEventListener('scroll', this.handleScroll);
  }

  render() {
    const colorPrimary = 'blue';
    const hideArrowClass = this.state.shouldShowScrollTopArrow ? '' : 'hide';
    return (
      <div className="scroll-top" onClick={(e) => scrollToPageTop()}>
        <div
          className={`arrow ${hideArrowClass}`}
          style={{ color: colorPrimary }}
        >
          <button className="fa fa-angle-double-up fa-2x" href="#" />
          <div className="to-top">To Top</div>
        </div>
      </div>
    );
  }
}

export default ScrollTop;

```

7. Save changes.
8. Create index.js inside src/components/scroll
9. Add following block of code:
```
export {default as ScrollToPage} from "./ScrollToPage";
export {default as ScrollTop} from "./ScrollTop";

```
10. Save changes.
11. Open LandingPage component.
12. Import ScrollToPage component by adding ```import { ScrollToPage } from '../../scroll';``` to your import block.
13. Add following block of code inside landing-page div, right below the closing main tag.
```
<ScrollToPage isFinal={false} pageSelector=".about-page" />
```
14. Save changes. Refresh browser. Try out the button.
15. Finally, add the ScrollTop component to App.js file inside src/ folder.
```
import React, { Component } from 'react';
import './App.css';
import {
  LandingPage
} from './components/pages';

import { ScrollTop } from './components/scroll';

class App extends Component {
  render() {
    return (
      <div className="landing-page">
        <LandingPage />
        <ScrollTop />
      </div>
    );
  }
}

export default App;

```

FYI, you can't test the ScrollTop component until step 8 is finished.

### Step 8: Create About Page

1. Create a new component called AboutPage.jsx inside src/components/pages.
2. Add the following block of code:

```
import React, { Component } from 'react';
import { ScrollToPage } from '../../scroll';

class AboutPage extends Component {

    render() {
        return (
            <div className="about-page">
                <div className="content-grid">
                    <h1>About</h1>
                    <div className="about-wrapper">
                    <div className="about-content">
                        <p>
                        I like and hate <span className="highlight">JavaScript</span> and
                        everything web.
                        </p>
                        <p className="text-emoji">
                        \ (•◡•) /
                        </p>
                    </div>
                    </div>
                </div>
                <ScrollToPage isFinal={false} isRed={true} pageSelector=".portfolio-page" />
            </div>
        )
    }
}

export default AboutPage;
```

3. Edit the description inside about-content div to something that fits you.
4. Update index.js inside src/components/pages to export AboutPage.
5. Open App.js inside src/. and add AboutPage component.

```
import React, { Component } from 'react';
import './App.css';
import {
  AboutPage,
  LandingPage
} from './components/pages';

import { ScrollTop } from './components/scroll';

class App extends Component {
  render() {
    return (
      <div className="landing-page">
        <LandingPage />
        <AboutPage />
        <ScrollTop />
      </div>
    );
  }
}

export default App;

```

6. Refresh app in the browser. Try to scroll to AboutPage. Use navbar and the different buttons.

### Step 9: Create Portfolio Page

1. Create a new component called PortfolioPage.jsx inside src/components/pages.
2. Add the following block of code:

```
import React, { Component } from 'react';
import { ScrollToPage } from '../../scroll';
import PortfolioItem from '../../portfolio/PortfolioItem';

class PortfolioPage extends Component {
    render() {
        return (
            <div className="portfolio-page">
                <div className="content-grid">
                    <h1>Portfolio</h1>
                    <div className="portfolio-wrapper">
                        <PortfolioItem />
                    </div>
                </div>
                <ScrollToPage isFinal={true} pageSelector=".about-page" />
            </div>
        );
    }
}

export default PortfolioPage;
```

3. Edit the description inside about-content div to something that fits you.
4. Update index.js inside src/components/pages to export PortfolioPage.
5. Open App.js inside src/. and add PortfolioPage component.

```
import React, { Component } from 'react';
import './App.css';
import {
  AboutPage,
  LandingPage,
  PortfolioPage
} from './components/pages';

import { ScrollTop } from './components/scroll';

class App extends Component {
  render() {
    return (
      <div className="landing-page">
        <LandingPage />
        <AboutPage />
        <PortfolioPage />
        <ScrollTop />
      </div>
    );
  }
}

export default App;


```

6. Refresh app in the browser. The code will not compile. Do you see why?
7. We are trying to import something called PortfolioItem in PortfolioPage component. This component does not exist yet. React is all about components, and we should always try to create generic reusable components if the use case allows us. It's normally for a portfolio to list multiple projects that one has worked on, and we should therefore have a generic component for our portfolio items so we can easily list multiple projects.
8. Create a new folder called "portfolio" inside components/ folder. 
9. Create a new file called "PortfolioItem.jsx" inside components/portfolio. 
10. Add the following block of code:
```
import React from 'react';

const PortfolioItem = () => {
    return (
        <div className="portfolio-item">
            <div className="portfolio-item__title">PROJECT NAME</div>

            <div className="portfolio-item__desc">
            PROJECT DESCRIPTION
            </div>
            <div className="portfolio-item__icon">
                <i className="fa fa-js" />
                <i className="fa fa-react" />
                <i className="fa fa-html5" />
            </div>
            <div className="portfolio-item__links">
            <a src="#">More</a>
            </div>
        </div>
        );
    
};

export default PortfolioItem;

```

11. Save changes. Refresh page now. You should now see that our portfolio page contains one item: "YOUR NAME".

#### Step 9.1: Challenge - Take project name and description as props in PortfolioItem
Our PortfolioItem component is not very generic. Project name and project description is currently static in the component. 

1. Change this component so it takes project name and description as props. 
2. Remember to send the props from the parent component.
3. Refresh page locally. The results should be same as before.
4. Update PortfolioPage with multiple PortfolioItems.
5. Refresh page locally. You should now have multiple items in your Portfolio Page.

### Step 10: Deploy page to GitHub Pages

Do you remember how we deploy a page do Github Pages?

### Step 11: Create Hobbies Page

Congratulations on coming so far!!!!!! :)
You should probably have an idea now on how to create new components and add it to your page. Try to add this page on your own.

## Authors

[Shahariar Kabir Bhuiyan](https://github.com/sharizard)
