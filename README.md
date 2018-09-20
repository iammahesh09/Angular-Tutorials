"# Angular-Tutorials" 


Angular
*******
	Angular 2+ versions are simply called Angular. 

	It is a TypeScript-based open-source front-end web application platform.

	Angular is different from AngularJS as it is written completely in Typescript and includes the ES6 specification. 

	As it is not updated version of AngularJS so it is rewritten and has many changes.

	Angular is a Framework to build mobile and desktop application.

	Features
	--------
		- Module
		- Components
		- Directives
		- Services
		- Routers


	Core Features
	-------------
		- Components
		- Directives
		- templates





Angular Architecture
--------------------

	-> Angular is completely based on modular programming, Code is divided in reusable components. 

	-> Angular App - one or more modules

	-> Module - each module one or more components and services

	-> Components - component contains an HTML template and class to control the logic for that particular view

	-> services - module can also have services which contains the "Business login" of application

	-> Modules export and import code as and when required and finally render the view in the browser



Ng Self Commands
----------------
	-> start : "ng serve",

	-> build : "ng build --prod",

	-> test  : "ng test",

	-> lint  : "ng lint",

	-> e2e   : "ng e2e"



Angular - Highlights
--------------------

	- Angular is mobile oriented & better in performance.

	- Angular provides more choice for languages.

	- Angular implements web standards like components.

	- Angular is not easy to setup as AngularJS.

	- AngularJS controllers and $scope are gone.

	- Different ways to define local variables.

	- Structural directives syntax is changed.

	- Angular uses camelCase syntax for built-in directives.

	- Angular directly uses the valid HTML DOM element properties and events.

	- One-way data binding directive replaced with [property].

	- Two-way data binding: ng-model replaced with [(ngModel)]

	- Way of Bootstrapping Angular Application is changed:

	- Ways of Dependency Injection is Changed- syntax changed.

	- Way of routing is Changed- syntax changed.



Understanding the File Structure
--------------------------------

	- app/app.component.ts - this is where we define our root component

	- app/app.module.ts - the entry Angular Module to be bootstrapped

	- index.html - this is the page the component will be rendered in

	- app/main.ts - is the glue that combines the component and page together


	The bootstrap process loads 'main.ts' which is the main entry point of the application. The 'AppModule' operates as the root module of our application. The module is configured to use 'AppComponent' as the component to bootstrap, and will be rendered on any 'my-app' HTML element encountered.


	Angular syntax
	---------------

		src/main.ts
		-----------
			import { platformBrowserDynamic } from '@angular/platform-browser-dynamic';
			import { AppModule } from './app/app.module';

			platformBrowserDynamic().bootstrapModule(AppModule);


		app.module.ts
		-------------
			import { NgModule }      from '@angular/core';
			import { BrowserModule } from '@angular/platform-browser';
			import { FormsModule } 	from '@angular/forms';


			import { AppComponent }   from './app.component';
			import { testComponent }   from './custom.component';
			import { GreeterService } from './greeter.service';


			@NgModule({
				imports: [ BrowserModule , FormsModule ],
				declarations: [ AppComponent, testComponent ],
				providers: [GreeterService],
				bootstrap: [ AppComponent ]
			})

			export class AppModule { }


		app.component.ts
		----------------
			import { Component } from '@angular/core';

			@Component({
				selector: 'my-app',
				template: `<myform>Loading...</myform>`
			})

			export class AppComponent { }


		index.html (main)
		----------
			<body>
				<my-app>Loading...</my-app>
			</body>
