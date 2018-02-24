

# Dapp Standard for the Hotelbyte platform

This standard is for each new Dapp, like B2C, Intranet, and any idea.
Any pull request that doesn't follow this guidelines could be rejected.

## Why we need the Standard?

Because we want to create functionally interfaces **robust and very fast**, it's the main reason for that.

## Main frameworks

This frameworks are the main, so if you need to use another one you can do it, but always if it's compatible with the main frameworks.
Please use always **the last stable version** for each framework. If you find breaker changes fix them!

+ Meteor
+ React

## Creating a new project

First create the root project folder with a good identifier name for the new project

For example, if your project is a booking restaurant interface.

> #### Bad
> + rs-app
> + meteor-restaurant
> + dapp-restaurant
> + dapp-booking

> #### Good
> + dapp-booking-restaurant
> + dapp-restaurant-booking

1. Create the main folder `mkdir dapp-restaurant-booking` 
2. `cd dapp-restaurant-booking` and create the base of the meteor project `meteor create app`
3. Check that everything is fine, `cd app && meteor`

## Installing dependencies

1. `cd dapp-restaurant-booking/app`
+ meteor update
+ meteor npm install --save react react-dom
+ meteor npm install --save react-mounter
+ meteor npm install --save jquery popper.js
+ meteor npm install --save bootstrap
+ meteor npm install --save @babel/runtime
+ meteor npm install --save web3
+ meteor npm install --save react-timestamp
+ meteor npm install --save react-time-format
+ meteor npm install --save bignumber.js
+ meteor npm install --save @types/bignumber.js
+ meteor npm install --save react-loading
+ meteor npm install --save axios (HTTP requests)
+ meteor add kadira:flow-router
+ meteor add universe:i18n

## Meteor guidelines

The main javascript file must be called `main.js` and it has the general imports like bootstrap, jquey, like this one:
``` js
	import React from 'react';
	import { Meteor } from 'meteor/meteor';
	import { render } from 'react-dom';

	// Styles
	import 'bootstrap/dist/css/bootstrap.min.css';
	import $ from 'jquery';
	import 'bootstrap';
	 
	import App from '../imports/ui/App.js';
	import Header from '../imports/ui/singles/Header.js';
	import Footer from "../imports/ui/singles/Footer";

	Meteor.startup(() => {
	    render(<Header />, document.getElementById('render-header'));
	    render(<App />, document.getElementById('render-main'));
	    render(<Footer />, document.getElementById('render-footer'));
	});
```
Note: use the last version of fontawesome from the CDN.

## React guidelines

Please follow the official guide of meteor-react [react guide from scratch](https://www.meteor.com/tutorials/react/components) before start your implementation.

### Views
Please the views must be on the `dapp-restaurant-booking/app/imports/ui` folder, you need to create it.
+ Prefix for generic components like header of the page `Dapp`so the final name must be like `DappHeader`

### Dev. Tools
+ https://reactjs.org/blog/2015/09/02/new-react-developer-tools.html#installation

### Environment

You need to create an `environment` folder inside of your `dapp-restaurant-booking/app` folder.
Here you will have the different files for you environment configuration.

+ settings.json - Production settings (default)
+ settings-dev.json - Local settings (`meteor --settings environments/settings-dev.json`)


## How to deploy a Dapp

We are get in touch with the IPFS movement, but for now we can't married with them, while the Dapp will be deploy with the travis.yml in each merge on the main branch (always master) will be deployed automatelly.

+ Create `travis.yml` file
+ Tell to travis how to create the build folder with `meteor-build-client ../build`

## TODO

Create a base project with all the dependencies and automate the creation.