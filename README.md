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




Angular - Directives
--------------------
	The Angular directive helps us to manipulate the DOM. You can change the appearance, behaviour or a layout of a DOM element using the Directives. 

	They help you to extend HTML. 

	The Angular directives are classified into three categories based on how they behave.  

	They are Component, Structural and Attribute Directives



	Metadata Properties:
	--------------------
		exportAs - name under which the component instance is exported in a template

		host - map of class property to host element bindings for events, properties and attributes

		inputs - list of class property names to data-bind as component inputs

		outputs - list of class property names that expose output events that others can subscribe to

		providers - list of providers available to this component and its children

		queries - configure queries that can be injected into the component

		selector - css selector that identifies this component in a template


		Example:
		-------

			@Directive({
				selector: 'interval-dir',
				outputs: ['everySecond', 'five5Secs: everyFiveSeconds']
			})

			class IntervalDir {
				
				everySecond = new EventEmitter();
				five5Secs = new EventEmitter();

				constructor() {
					setInterval(() => this.everySecond.emit("event"), 1000);
					setInterval(() => this.five5Secs.emit("event"), 5000);
				}
			}

			@Component({
				selector: 'app',
				template: `<interval-dir (everySecond)="everySecond()" (everyFiveSeconds)="everyFiveSeconds()">	</interval-dir>`
			})

			class App {
				everySecond() { console.log('second'); }
				everyFiveSeconds() { console.log('five seconds'); }
			}




	We have three kinds of directives:
	----------------------------------

	1. Components: yes a component is a directive. (@Component)

		==> A component is a directive with a template.

		==> @Component decorator extends the @Directive

		==> In Angular applications the component is the main


	2. Structural Directives: 

		-	The "ngFor" is repeats a portion of HTML template once per each item from an iterable list (Collection). 

		-	The "ngSwitch" allows us to Add/Remove DOM Element. It is similar to switch statement.  

		-	The "ngIf" allows us to Add/Remove DOM Element. 


	3. Attribute Directives:

		-	The ngClass Directive is allows us to add or remove CSS classes to an HTML element. 

		-	The ngStyle directive allows you to modify the style of an HTML element using the expression.
		Using the ngStyle you can dynamically change the style of your HTML element.


	4. Create Custom Directives:




	Attribute Directives
	--------------------

		NgStyle Directive
		-----------------

			Angular provides a built-in directive, ngStyle, to modify a component or element's style attribute. Here's an example:

			Example-1
			---------
				@Component({
					selector: 'app-style-example',
					template: `
						<p style="padding: 1rem" [ngStyle]="{'color': 'red','font-weight': 'bold','borderBottom': borderStyle}">
							<ng-content></ng-content>
						</p>
					`
				})

				export class StyleExampleComponent {
					borderStyle = '1px solid black';
				}


			Example-2
			---------

				@Component({
					selector: 'app-style-example',
					template: `
						<p style="padding: 1rem" [ngStyle]="alertStyles">
							<ng-content></ng-content>
						</p>
					`
				})
				
				export class StyleExampleComponent {
				
					borderStyle = '1px solid black';

					alertStyles = {
						'color': 'red',
						'font-weight': 'bold',
						'borderBottom': this.borderStyle
					};
				}



			NgClass Directive
			-----------------

				It is used to add and remove CSS classes on an HTML element. We can bind several CSS classes to NgClass simultaneously that can be added or removed. There are different ways to bind CSS classes to NgClass that are using string, array and object.

				Binding a string
				----------------
					@Component({
						selector: 'app-class-as-string',

						template: `
							<p ngClass="centered-text underlined" class="orange">
								<ng-content></ng-content>
							</p>
						`,

						styles: [`
							.centered-text {
								text-align: center;
							}

							.underlined {
								border-bottom: 1px solid #ccc;
							}

							.orange {
								color: orange;
							}
						`]
					})

					export class ClassAsStringComponent {}



				Binding an array
				----------------
					@Component({
						selector: 'app-class-as-array',
						template: `
							<p [ngClass]="['warning', 'big']">
								<ng-content></ng-content>
							</p>
						`,

						styles: [`
							.warning {color: red; font-weight: bold;}
							.big {font-size: 1.2rem;}
						`]
					})

					export class ClassAsArrayComponent {}


				Binding an object
				-----------------
					@Component({
						selector: 'app-class-as-object',
						template: `
							<p [ngClass]="{ card: true, dark: false, flat: flat }">
								<ng-content></ng-content>
								<br>
								<button type="button" (click)="flat=!flat">Toggle Flat</button>
							</p>
						`,

						styles: [`
							.card {
								border: 1px solid #eee;
								padding: 1rem;
								margin: 0.4rem;
								font-family: sans-serif;
								box-shadow: 2px 2px 2px #888888;
							}

							.dark {
								background-color: #444;
								border-color: #000;
								color: #fff;
							}

							.flat {
								box-shadow: none;
							}
						`]
					})

					export class ClassAsObjectComponent {
						flat: boolean = true;
					}



	Structural Directives
	---------------------

		Structural directives are responsible for HTML layout. typically by adding, removing, or manipulating DOM. 

		Angular has a few built-in structural directives such as 'ngIf', 'ngFor', and 'ngSwitch'


		NgIf Directive
		--------------
			The ngIf directive conditionally adds or removes content from the DOM based on whether or not an expression is true or false.

			demo.html
			---------
				<button type="button" (click)="toggleExists()">Toggle Component</button>
				<hr>
				<app-if-example *ngIf="isReq">Hello</app-if-example>


			demo.ts
			-------
				isReq = true;

				toggleExists() {
					this.isReq = !this.isReq;
				}



			Example-2
			---------

			<h2 *ngIf="isReq; else isFalse">Condition is true, Hello! Q</h2> 	// Output

			<ng-template #isTrue>
				<h2>Condition is False</h2>	
			</ng-template>


			Example-3
			---------
				<div *ngIf="!isReq; then isTrue; else isFalse"></div>

				<ng-template #isTrue>
					<h2>Condition is true, Hello! Q</h2>
				</ng-template>

				<ng-template #isFalse>
					<h2>Condition is False</h2>	  // Output
				</ng-template>



		NgFor Directive
		---------------

			The NgFor directive is a way of repeating a template by using each item of an iterable as that template's context.

			@Component({
				selector: 'app-root',
				template: `
					<app-for-example *ngFor="let episode of episodes" [episode]="episode">{{episode.title}}</app-for-example>`
			})

			export class AppComponent {
				episodes = [
					{ title: 'Winter Is Coming', director: 'Tim Van Patten' },
					{ title: 'The Kingsroad', director: 'Tim Van Patten' },
					{ title: 'Lord Snow', director: 'Brian Kirk' },
					{ title: 'Cripples, Bastards, and Broken Things', director: 'Brian Kirk' },
					{ title: 'The Wolf and the Lion', director: 'Brian Kirk' },
					{ title: 'A Golden Crown', director: 'Daniel Minahan' },
					{ title: 'You Win or You Die', director: 'Daniel Minahan' },
					{ title: 'The Pointy End', director: 'Daniel Minahan' }
				];
			}


			Local Variables
			---------------

			NgFor also provides other values that can be aliased to local variables:

			index - position of the current item in the iterable starting at 0

			first - true if the current item is the first item in the iterable

			last - true if the current item is the last item in the iterable

			even - true if the current index is an even number

			odd - true if the current index is an odd number


			@Component({
				selector: 'app-root',
				template: `

					<app-for-example *ngFor="let episode of episodes; let i = index; let isOdd = odd" [episode]="episode" [ngClass]="{ odd: isOdd }"> {{i+1}}. {{episode.title}} </app-for-example>
					
					<hr>

					<h2>Desugared</h2>

					<template ngFor [ngForOf]="episodes" let-episode let-i="index" let-isOdd="odd">
						<for-example [episode]="episode" [ngClass]="{ odd: isOdd }">
							{{i+1}}. {{episode.title}}
						</for-example>
					</template>
				`
			})


			Please note : 
				1. ngFor is usually used to display an array of items
				2. Since ngFor is a structutal directive it is prefixed with *
				3. *ngFor='let employee of employees' - In this example 'employee' is called template input variable, which can be accessed by the 4. [tr] element and any of it's child elements.
				5. ngIf structural directive displays the row "No employees to display" when employees property does not exist or when there are ZERO employees in the array.

			Example
			-------
				<tr *ngFor=" hero in heroes">
					<td>{{hero.name}}</td>
				</tr>

				Finding the 'index' of a list element
				-----------------------------------
					<tr *ngFor="let hero of heroes; let i = index">
						<td>{{hero.name}}</td>
						<td>{{i}}</td>
					</tr>

				How to stripe a table using even and odd
				----------------------------------------
					<tr *ngFor="let hero of heroes; let even = even; let odd = odd" [ngClass]="{ odd: odd, even: even }">
						<td>{{hero.name}}</td>
					</tr>

					<table>

						<thead>
							<th>Name</th>
						</thead>

						<tbody>
							<tr class="even">
								<td>Superman</td>
							</tr>
							<tr class="odd">
								<td>Batman</td>
							</tr>
							...
						</tbody>
					</table>

				Identifying the 'first' and the 'last' element of a list
				--------------------------------------------------------
					<tr *ngFor="let hero of heroes; let first = first; let last = last" [ngClass]="{ first: first, last: last }">
						<td>{{hero.name}}</td>
					</tr>

				Angular ngFor trackBy
				---------------------
				Using trackyBy with ngFor directive : 
				ngFor directive may perform poorly with large lists
				A small change to the list like, adding a new item or removing an existing item may trigger a cascade of DOM manipulations


					Example
					-------
						1. At the moment we are not using trackBy with ngFor directive
						2. When the page initially loads we see the 4 employees
						3. When we click "Refresh Employees" button we see the fifth employee as well
						4. It looks like it just added the additional row for the fifth employee. That's not true, it effectively teared down all the [tr] and [td] elements of all the employees and recreated them.
						5. To prove this launch browser developer tools by pressing F12.
						6. Click on the "Elements" tab and expand the [table] and then [tbody] elements
						7. At this point click the "Refresh Emplyees" button and you will notice all the [tr] elements are briefly highlighted indicating they are teared down and recreated.



		NgSwitch Directives
		-------------------

			ngSwitch is actually comprised of two directives, an attribute directive and a structural directive. It's very similar to a switch statement in JavaScript and other programming languages, but in the template.+

			@Component({
				selector: 'app-root',
				template: `
					<div class="tabs-selection">
					<app-tab [active]="isSelected(1)" (click)="setTab(1)">Tab 1</app-tab>
					<app-tab [active]="isSelected(2)" (click)="setTab(2)">Tab 2</app-tab>
					<app-tab [active]="isSelected(3)" (click)="setTab(3)">Tab 3</app-tab>
					</div>

					<div [ngSwitch]="tab">
					<app-tab-content *ngSwitchCase="1">Tab content 1</app-tab-content>
					<app-tab-content *ngSwitchCase="2">Tab content 2</app-tab-content>
					<app-tab-content *ngSwitchCase="3"><app-tab-3></app-tab-3></app-tab-content>
					<app-tab-content *ngSwitchDefault>Select a tab</app-tab-content>
					</div>`
			})

			export class AppComponent {
				tab: number = 0;

				public selectColor ="green";

				setTab(num: number) {
					this.tab = num;
				}

				isSelected(num: number) {
					return this.tab === num;
				}
			}

			for switch case you need to add directive [ngSwitch] then pass the value to check conditions then you need to check that condition using *ngSwitchCase for different conditions & you add default case using *ngSwitchDefault.


			Example-2
			---------
			<div [ngSwitch]="selectColor">
				<div *ngSwitchCase="'red'">Red Color Select</div>
				<div *ngSwitchCase="'blue'">Blue Color Select</div>
				<div *ngSwitchCase="'yellow'">Yellow Color Select</div>
				<div *ngSwitchCase="'green'">Green Color Select</div>
			</div>



	Custom Directives
	-----------------

		Example-1
		---------

			# red-black.directive.ts

				import { Directive, ElementRef, OnInit } from '@angular/core';

				@Directive({
					selector: '[appRedBlack]'
				})

				export class RedBlackDirective implements OnInit {

					element: ElementRef;

					constructor(private _ef: ElementRef) {
						_ef.nativeElement.style.color = "black";
						_ef.nativeElement.style.backgroundColor = "blue";
						_ef.nativeElement.style.fontSize = "2rem";
						_ef.nativeElement.style.fontWeight = "bold";
						this.element = _ef

						console.log(_ef.nativeElement);
					}

					ngOnInit(): void {
						this.element.nativeElement.innerHTML += " - Hello! Mahesh";
					}

				}

			# red-black.component.html
			
				//Apply custom directive "appRedBlack"

				<p appRedBlack>items works!</p>




Dependency injection
--------------------

	Dependency injection is a coding pattern in which a class receives its dependencies form external sources rather than creating them itself

	Dependency injection is the ability to add the functionality of components at runtime.


	implement dependency injection
	------------------------------

	Step 1
	------
		Create a separate class which has the injectable decorator. The injectable decorator allows the functionality of this class to be injected and used in any Angular JS module.

		@Injectable() 
		export class classname {  

		}


	Step 2
	------
		Next in your appComponent module or the module in which you want to use the service, you need to define it as a provider in the @Component decorator.

		@Component ({  
			providers : [classname] 
		})

