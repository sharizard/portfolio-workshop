# ATA Frontend - Introduction to React

Let's create a portfolio application together!

## Useful links

* [Getting Started with React](https://reactjs.org/docs/getting-started.html)

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
```

Then run the following commands to install necessary npm packages for this tutorial:
```
npm install node-sass-chokidar --save
npm install npm-run-all --save
npm install gh-page --save-dev
```

After installing npm packages, update your package.json file. 

1. Open Visual Studio Code. Tip: write the command ```code .``` If this works, skip 3-5.
2. Click “File”
3. Click “Open folder”
4. Select the folder named “portfolio-workshop” located in “C:\Users\<your.accenture.id\Desktop\repos\portfolio-workshop”
5. Open the file "package.json". Tip for opening file, inside VSCode press:```CTRL+P``` and write ```package.json``` 

#### Add homepage
Add the following snippet to package.json. You can place it below the private tag.
```
"homepage": "http://{USERNAME}.github.io/portfolio-workshop",
```

#### Update scripts block
Update the script block with the following snippet

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

### Step 3: Create Landing Page component

First of all, run the application locally by running ```npm start```.

1. Open Visual Studio Code. Tip: write the command ```code .``` If this works, skip 3-5.
2. Click “File”
3. Click “Open folder”
4. Select the folder named “portfolio-workshop” located in “C:\Users\<your.accenture.id\Desktop\repos\portfolio-workshop”. The project should be visible in VSCode. 
6. Navigate to public folder. Right click and create a new folder called "assets".
7. Add your desired image to the assets folder. You can for instance use the cartoon image provided by Ismar, or profile picture from Accenture.
8. Navigate to src folder. Right click on the folder and create a new folder called "components".
9. In src/components, create a new folder called pages.
10. In pages, create a new file called LandingPage.jsx
11. Add the following snippet of code to LandingPage.jsx:
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

12. Save your changes.
13. Create a new file under src/components/pages. Name it "index.js"
14. Add following snippet of code to index.js
```
export {default as LandingPage} from "./LandingPage";
```
15. Save file.
16. Open "App.js" under src/.
17. Remove everything inside the return statement in render-method.
18. Import LandingPage by adding ```import { LandingPage } from './components/pages';``` to your imports.
19. Add a new div inside return block in render method, then add the LandingPage component. App.js should look like this:
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

20. Save changes.
21. Go to the browser. Refresh page. You should now see the landing page including a picture, your name, and your title.
22. Congratulations. We can now move to step 4.

### Step 2: Adding items

Stash local changes and checkout branch Step-one_Creating-the-home-page, run the following command in terminal:

```
git stash && git checkout -f Step-one_Creating-the-home-page
```

1. Create the page for adding items to the ToDo list by typing the following commands in your Terminal: 
```cd ionic-workshop\ionic-todo\src\pages```
```ionic g page AddItem```
2. Open “src/app/app.module.ts” and add the following import: 
```ts
import { AddItemPage } from '../pages/add-item/add-item';
```
3. In the same file, add “AddItemPage” in the declarations and entryComponents array.
4. Open “src/pages/add-item/add-item.html” and replace its content with the following:
```html
<ion-header>
  <ion-toolbar color="secondary">
    <ion-title>
      Add Item
    </ion-title>
      <ion-buttons end>
        <button ion-button icon-only (click)="close()"><ion-icon name="close"></ion-icon></button>
      </ion-buttons>
    </ion-toolbar>
</ion-header>
 
<ion-content>
  <ion-list>
 
    <ion-item>
      <ion-label floating>Title</ion-label>
      <ion-input type="text" [(ngModel)]="title"></ion-input>
    </ion-item>
 
    <ion-item>
      <ion-label floating>Description</ion-label>
      <ion-input type="text" [(ngModel)]="description"></ion-input>
    </ion-item>
 
  </ion-list>
 
  <button full ion-button color="secondary" (click)="saveItem()">Save</button> 
 
</ion-content>
```
5. Open “add-item.ts” and add the following fields, under export class AddItemPage: 
```ts
title;
description;
```
6. In the same file, rename the class name (name appearing after “export class” to ```AddItemPage```
7. Replace the import statement "import { IonicPage, NavController, NavParams } from 'ionic-angular';" with:
```ts
import { NavController, ViewController } from 'ionic-angular';
```
8. In the same file, replace “public navParams: NavParams” parameter in the constructor with:
```ts
public view: ViewController
```
9. Remove “@IonicPage()” annotation.
10. Under the constructor, add the following functions:
```ts
saveItem(){
    let newItem = {
    title: this.title,
    description: this.description
    };

    this.view.dismiss(newItem);
}
 
close(){
    this.view.dismiss();
}
```
11. Remove “@IonicPage()” annotation.
12. Open the file “src/pages/home/home.ts”. ```CTRL+P``` then ```home.ts```
13. Replace its content with the following (we are now replacing the dummy data with logic for adding data dynamically):
```ts
import { Component } from '@angular/core';
import { ModalController, NavController } from 'ionic-angular';
import { AddItemPage } from '../add-item/add-item'
 
@Component({
    selector: 'page-home',
    templateUrl: 'home.html'
})
export class HomePage {
 
  	public items = [];
 
  	constructor(public navCtrl: NavController, public modalCtrl: ModalController) {
  	}
 
  	ionViewDidLoad(){
  	}
 
  	addItem(){
        let addModal = this.modalCtrl.create(AddItemPage);
   	 	addModal.onDidDismiss((item) => {
            if(item){
                this.saveItem(item);
            }
        });
        addModal.present();
  	}
 
  	saveItem(item){
    	this.items.push(item);
  	}
 
  	viewItem(item){
  	}
}
```
14. Tip: change app color by modifying hexadecimal color variables in the file “variables.scss”. Default variable is “secondary”.

### Step 3: Viewing items

We want to be able to click on an item in the list and see its description. This is what we are going to implement next.

Stash local changes and checkout branch Step-two_Adding-items, run the following command in terminal:

```
git stash && git checkout -f Step-two_Adding-items
```

1. Create an item-detail page by typing the following command: ```ionic g page ItemDetail```
2. In the file “app.module.ts”, add the following import statement:
```ts
import { ItemDetailPage } from '../pages/item-detail/item-detail';
```
3. In the same file, add “ItemDetailPage” to the declarations and entryComponents arrays.
4. Open the file “item-detail.html” and replace its content with the following:
```html
<ion-header>
    <ion-navbar color="secondary">
        <ion-title>
            {{title}}
        </ion-title>
    </ion-navbar>
</ion-header>
 
<ion-content>
    <ion-card>
        <ion-card-content>
            {{description}}
        </ion-card-content>
    </ion-card>
</ion-content>
```
5. Open “item-detail.ts” and add the following fields above the constructor:
```ts
 title;
 description”;
```
6. In the same file, replace the function body of “ionViewDidLoad()” with the following:
```ts
this.title = this.navParams.get('item').title;
this.description = this.navParams.get('item').description;
```
7. Remove annotation “@IonicPage()” in the file
8. Rename class name to “ItemDetailPage”
9. Open the file “home.ts” and add the following to the function body of “viewItem()”:
```ts
this.navCtrl.push(ItemDetailPage, {
    item: item
});
```
10. In the same file, add the following import statement: 
```ts
import { ItemDetailPage } from '../item-detail/item-detail';
```
### Step 4: Saving data permanently to storage

Now, the items in the todo-list will be cleared every time the application is closed. We are now going to improve this behavior by instead storing the items permanently. A data service will help us achieve this..

Stash local changes and checkout branch Step-three_Viewing-items, run the following command in terminal:

```
git stash && git checkout -f Step-three_Viewing-items
```

1. Install storage plugin by typing the following command in the terminal:
```npm install --save @ionic/storage```
2. Create a data service by typing the command:
```ionic g provider Data```
3. Open the file “data.ts” and replace its content with the following:
```ts
import { Storage } from '@ionic/storage';
import { Injectable } from '@angular/core';

@Injectable()
export class Data {

    constructor(public storage: Storage){
    }

    getData() {
        return this.storage.get('todos');  
    }

    save(data){
        let newData = JSON.stringify(data);
        this.storage.set('todos', newData);
    }
}
```
4. Open the file “app.module.ts” and add the following import statements:
```ts
import { IonicStorageModule } from '@ionic/storage';
import { Data } from '../providers/data';
```
5. In the same file, add the following to the imports array:
```ts
IonicStorageModule.forRoot()
```
6. Add the following to the providers array:
```ts
Data
```
7. Open the file “home.ts” and add the following import statement: 
```ts
import { Data } from '../../providers/data';
```
8. In the same file, add the following to the constructor: 
```ts
public dataService: Data
```
9. Add the following to the body of the constructor:
```ts
this.dataService.getData().then((todos) => {
    if(todos){
            this.items = JSON.parse(todos); 
    }
});
```
10. Add the following to the body of the “saveItem()” function:
```ts
this.dataService.save(this.items);
```
11. Refresh browser and try to add some items.

### Step 5: Deploy to your own phone












## Authors

[Shahariar Kabir Bhuiyan](https://github.com/sharizard)
