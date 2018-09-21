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



Angular Module
--------------

	- Angular Module is a container for cohesive block of code
	- Angular module is a collection of components, services, directives and pipes

	Angular NgModule
	------------------
		Angular apps are modular and Angular has its own modularity system called "NgModule".


		Every Angular app has at least one NgModule class, the root module, conventionally named AppModule.

		AppModule is the root module which bootstraps and launches the angular application

		While the root module may be the only module in a small application, most apps have many more feature modules, each a cohesive block of code dedicated to an application domain, a workflow, or a closely related set of capabilities.

		An NgModule, whether a root or feature, is a class with an @NgModule decorator.



		NgModule is a decorator function that takes a single metadata object whose properties describe the module. 



	NgModule "metadata" properties
	------------------------------

		declarations
		------------
			the view classes that belong to this module. Angular has three kinds of view classes: components, directives, and pipes.

		exports
		-------
			the subset of declarations that should be visible and usable in the component templates of other modules.

		imports
		-------
			other modules whose exported classes are needed by component templates declared in this module.

		providers
		---------
			creators of services that this module contributes to the global collection of services; they become accessible in all parts of the app.

		bootstrap
		---------
			the main application view, called the root component, that hosts all other app views. Only the root module should set this bootstrap property.


	src/app/app.module.ts
	---------------------

		import { NgModule }      from '@angular/core';
		import { BrowserModule } from '@angular/platform-browser';

		@NgModule({
			imports:      [ BrowserModule ],
			providers:    [ Logger ],
			declarations: [ AppComponent ],
			exports:      [ AppComponent ],
			bootstrap:    [ AppComponent ]
		})

	export class AppModule { }



Angular - Component
---------------------

	The Component is the main building block of an Angular Application. 

	A Component contains the definition of the View and the data that defines how the View looks and behaves.  

	The Angular Components are plain javascript classes and defined using @component Decorator. 

	This Decorator provides the component with the View to display & Metadata about the class


	Metadata Properties:
	-------------------
		selector - css selector that identifies this component in a template

		styleUrls - list of urls to stylesheets to be applied to this component's view

		styles - inline-defined styles to be applied to this component's view

		template - inline-defined template for the view

		templateUrl - url to an external file containing a template for the view

		viewProviders - list of providers available to this component and its view children

		inputs - list of class property names to data-bind as component inputs

		outputs - list of class property names that expose output events that others can subscribe to

		providers - list of providers available to this component and its children

		encapsulation - style encapsulation strategy used by this component

		animations - list of animations of this component

		changeDetection - change detection strategy used by this component

		entryComponents - list of components that are dynamically inserted into the view of this component

		exportAs - name under which the component instance is exported in a template

		host - map of class property to host element bindings for events, properties and attributes		

		interpolation - custom interpolation markers used in this component's template

		moduleId - ES/CommonJS module id of the file in which this component is defined		

		queries - configure queries that can be injected into the component

