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



viewEncapsulation 
------------------

	viewEncapsulation decides whether the styles defined in a component can affect the entire application or not.

	- Emulated: styles from other HTML spread to the component.

		"viewEncapsulation.Emulated" is completly defulat (attributes) the encapsulation.

	- Native: styles from other HTML do not spread to the component.

		"viewEncapsulation.Native" is browsers supports "shadow DOM" ("shadow-root" open).

	- None: styles defined in a component are visible to all components.

		"viewEncapsulation.none" is completly disabled (attributes, ex:_nghost-atr-1, ngcontent-atr-1, ... etc) the encapsulation.


	Ex:-
	---
		import { Component, ViewEncapsulation } from '@Angular/core';

		@Component({
			selector:'my-movies',
			template:'<h3>Movies List</h3>',
			encapsulation: ViewEncapsulation.Emulated
		})



One way Data Binding & Two way Data Binding in Angular
------------------------------------------------------

	One way Data Binding
	--------------------
		@Component({ 
			selector: 'my-app', 
			template: ` Name : <input [value]='username'> <br>
			You entered : {{username}} `
		})

		export class AppComponent { 
			username: string = 'Tom Jhon';
		}

		- [input [value]='username'] : Binds component class "username" property to the input element’s value property

		- You entered : {{username}} : Interpolation displays the value we have in "username" property on the web page


		At the moment when we change the value in the textbox, that changed value is not reflected in the browser. One way to achieve this is by binding to the input event of the input control as shown below.


	Two way Data Binding
	--------------------

		Data binding is the synchronization of data between the model and view components.

		Two-way data binding merges property and event binding in a single notation using the directive "ngModel"

		<input type="text" [(ngModel)]="name">

		<h1>{{name}}</h1>

			Example
			-------
				Ex1: -	
					<input [(ngModel)]="username">

					<p>Hello {{username}}!</p>


				Ex2: -	
					<input [value]="username" (input)="username = $event.target.value">

					<p>Hello {{username}}!</p>


						->	[value]="username" - Binds the expression username to the input element’s value property

						-> (input)="expression" - Is a declarative way of binding an expression to the input element’s input event (yes there’s such event)

						-> username = $event.target.value - The expression that gets executed when the input event is fired

						-> $event - Is an expression exposed in event bindings by Angular, which has the value of the event’s payload


				Ex3: -	
					<input [ngModel]="username" (ngModelChange)="username = $event">

					<p>Hello {{username}}!</p>




Angular - Data Binding
----------------------
	We use Data Binding to help co-ordinate communication between a component and it’s Template


	Interpolation (OR) Expression
	-----------------------------	
		Angular uses double-curly braces {{ }} to represent interpolation. Interpolation executes expression. Suppose we want to do mathematical calculation, we can perform it as follows within HTML template.


		- interpolation is a special syntax that angular converts into a property binding

		- To concatenate string we must use interpolation instead of property binding 
			
			<img src="{{imgPath}}">	


	Property Binding
	----------------
		Property binding is performed as one-way from data source to view target. especially in case of styles and attribute bindings. It has a syntax []

		In property binding there is source and target.

		Using square brackets []
		Using bind- Keyword		

		Ex:-
			<img src="{{ Logo }}">
			<img [src]="Logo">
			<img bind-src="Logo">

		For the example we can define it as [href]="website.url". 
		Here 'href' is a 'target' that is a property of anchor tag and 'source' is a component property i.e website.url. 

		There are three types of property binding. 
			1. Element property 
			2. Directive property 
			3. Component property 


			Component property binding is performed as below.

				<my-msg  prefixMsg= "Website name is" [siteName] = "website.name"> </my-msg> 


			Element property binding is performed as below.

				<a [href]="website.url" [textContent]="website.name"> </a> 


			Directive property binding is performed as below.

				<p [ngClass]="'one two'"> Angular Property Binding Example </p> 


			- Angular data binding sanitizes malicious content before displaying it


	Angular Event Binding
	----------------------

		Event binding is a data binding from an event to a component, The events are standard browser events such as Click, DoubleClick etc.


		For example the following is the syntax for binding to the click event of a button. Within parentheses on the left of the equal sign we have the target event, (click) in this case and on the right we have the template statement. In this case the onClick() method of the component class is called when the click event occurs.

			<button (click)="isValid=true">True</button>  

		canonical form And event binding using on- keyword is achieved as follows.

			<button on-click="isValid=true">True</button>  

		Call component method on event binding.

			<input (change) = "changeText($event.target.value)">  


		very time we click the button, 'Button Clicked' message is logged to the console. You can see this message under the Console tab, in the browser developer tools.

		Another Example : Initially when the page loads we want to display only the First Name and Last of Employee. We also want to display "Show Details" button.

		When we click "Show Details" button, we want to display "Gender" and "Age" as well. The text on the button should be changed to "Hide Details". When we click "Hide Details" button, "Gender" and "Age" should be hidden and the button text should be changed to "Show Details".

		To achieve this we will make use of event binding in Angular. We will also make use of one of the structural directives "ngIf" in angular.

		Code in employee.component.ts : Notice we have introduced "showDetails" boolean property. The default value is false, so when the page first loads, we will have "Gender" and "Age" hidden. We also have a method, toggleDetails(), which toggles the value of showDetails. 


		@Component({ 
			selector: 'my-employee', 
			templateUrl: 'app/employee/employee.user.html', 
			styleUrls: ['app/employee/employee.user.css']
		})

		export class EmployeeComponent { 

			columnSpan: number = 2; 

			firstName: string = 'Tom'; 

			lastName: string = 'Hopkins'; 

			gender: string = 'Male'; 

			age: number = 20; 

			showDetails: boolean = false;

			toggleDetails(): void { 
				this.showDetails = !this.showDetails; 
			}
		}


		<table class="table table-striped">
			<thead class="table-inverse">
				<tr>
					<th>FirstName</th>
					<th>LastName</th>
					<th *ngIf="showDetails">Gender</th>
					<th *ngIf="showDetails">Age</th>
					<th></th>
				</tr>
			</thead>	
			<tbody>
				<tr *ngFor="let mobile of mobiles; let i='index'">
					<td>{{firstName}}</td>
					<td>{{lastName}}</td>
					<td *ngIf="showDetails">{{gender}}</td>
					<td *ngIf="showDetails">{{age}}</td>
				</tr>
			</tbody>	
		</table>

		<button (click)="toggleDetails()">{{showDetails? 'Hide':'Show'}} Details</button>

		
	Explain $event in Angular
	-------------------------
	 
		- In Angular $event is a reserved keyword that represents the data emitted by an event (event data).
		- It is commonly used as a parameter for event based methods.



	Angular Attribute binding
	-------------------------

		Interpolation and Propertybinding that deal with binding Component class properties to HTML element properties and not Attributes. 

		However, in some situations we want to be able to bind to HTML element attributes. 

		For example, colspan and aria attributes does not have corresponding DOM properties. So in this case we want to be able to bind to HTML element attributes. 


			<th attr.colspan="{{colSpan}}"></th> //interpolation

			<th [attr.colspan]="colSpan"></th>  //Property binding


	
	Angular - Class Binding
	---------------------------
		We can add and remove CSS class names from the HTML element class attribute using CSS class binding. CSS class binding is same as property binding. But we need to add a prefix "class." with CSS class name in class binding. The CSS class added by class binding will override the existing CSS class properties if any property will be common. CSS class binding removes CSS class when expression returns false and adds it when expression returns true.

		To add or remove more than one CSS class dynamically we should use NgClass directive. 

		CSS file
		--------

			.text-green{
				color: green;
				font-size: 30px;
			}
			.text-danger{
				color: red;
				background-color: cyan;
				font-family: cursive;
			} 


		Html Page
		---------
			<div class="text-green">Hello Wordl!</div>

			<div [class.text-green]="isReq">Hello Wordl!</div>

			<div class="text-green" [class.text-danger]="isOptional('yes')">Hello Wordl!</div>

			<div class="text-green" [class.text-danger]="isOptional('no')">Hello Wordl!</div>

			<div class="text-green text-danger" [class.text-danger]="isOptional('no')">Hello Wordl!</div> 


		style.ts
		--------
			isReq = true;

			isOptional(data) {
				if (data == 'yes') {
					return true;
				} else {
					return false;
				}
			}


	Style binding in Angular
	--------------------------


		The following example sets a single style (font-weight). If the property 'isBold' is true, then font-weight style is set to bold else normal.

			import { Component } from '@angular/core';

			@Component({ 
				selector: 'my-app', 
				template: ` <button style='color:red' [style.font-weight]="isBold ? 'bold' : 'normal'">My Button </button> `
			})

			export class AppComponent { 
				isBold: boolean = true;
			}


		style property name can be written in either dash-case or camelCase. For example, font-weight style can also be written using camel case - fontWeight.

		Some styles like font-size have a unit extension. To set font-size in pixels use the following syntax. This example sets font-size to 30 pixels.

			import { Component } from '@angular/core';

			@Component({ 
				selector: 'my-app', 
				template: ` <button style='color:red' [style.font-size.px]="fontSize">My Button </button> `
			})

			export class AppComponent { 
				fontSize: number = 30;
			}


		To set multiple inline styles use NgStyle directive

			1. Notice the color style is added using the style attribute
			2. ngStyle is binded to addStyles() method of the AppComponent class
			3. addStyles() method returns an object with 2 key/value pairs. The key is a style name, and the value is a value for the respective style property or an expression that returns the style value.
			4. let is a new type of variable declaration in JavaScript.
			5. let is similar to var in some respects but allows us to avoid some of the common “gotchas” that we run into when using var. 
			6. The differences between let and var are beyond the scope of this video. For our example, var also works fine.
			7. As TypeScript is a superset of JavaScript, it supports let


			import { Component } from '@angular/core';

			@Component({ 
				selector: 'my-app', 
				template: ` <button style='color:red' [ngStyle]="addStyles()">My Button</button> `
			})

			export class AppComponent { 
				
				isBold: boolean = true; 
				
				fontSize: number = 30; isItalic: boolean = true; 
				
				addStyles(){ 
				
				let styles = { 
					'font-weight': this.isBold ? 'bold' : 'normal', 
					'font-style': this.isItalic ? 'italic' : 'normal', 
					'font-size.px': this.fontSize 
				}; 

				return styles; 
				}
			}




Angular - NgStyle and Style Binding
-----------------------------------
	Style binding binds an inline style property with a given value and NgStyle sets more than one inline styles dynamically. Style binding is used in the same way as property binding is used. Style binding can bind only one inline CSS property at one time. When we want to use more than one style property at one time dynamically then the role of NgStyle directive comes into picture. NgStyle and style property binding both can be used with bracket [] and bind- keyword. Here on this page we are providing the example for style binding and NgStyle with style properties such as color, font-size, background-image. 


	Style Binding
	-------------
		Style binding binds an inline style property with a given value. Style binding is used in the same way as property binding is used. Style binding can bind only one inline CSS property at one time.

		Here style is a prefix and style-property is a name of a CSS style property. style prefix and style property are concatenated using dot (.) . Style property binding can be achieved with bracket [], bind- keyword and interpolation {{}}. Now find the code to use style binding.

			<p [style.color] = "result"> Hello Color World! </p>

			<p bind-style.color = "result"> Hello Color World! </p>

			<p style.color = "{{result}}"> Hello Color World! </p> 



	NgStyle Binding
	---------------
		NgStyle directive is used to set many inline styles dynamically. Setting styles using NgStyle works as key:value pair. key is the style property name and value is the style value.

		Example-1
		---------
			<p [ngStyle]="myStyles1">You say tomato, I say tomato</p>

			<p [ngStyle]="['myStyles1','myStyles2']">You say tomato, I say tomato</p>

			myStyles1 = {
				'background-color': 'lime',
				'font-size': '20px',
			}
			myStyles2 = {
				'color':'blue',
				'font-weight': 'bold'
			}

		Example-2
		---------
			<p [ngStyle]="{'background-color': 'lime','font-size': '20px','font-weight': 'bold'}">
				You say tomato, I say tomato
			</p>

		Example-3
		---------
			<p [ngStyle]="setMyStyles()">You say tomato, I say tomato</p>


			setMyStyles() {

				let styles = {
					'background-color': 'red',
					'font-weight': 'bold'
				};

				return styles;

			}



Conditional (ternary) Operator
------------------------------

	Conditional operator that is also called ternary operator, is used as a short cut of if else statement.

	# condition ? expr1 : expr2

		When the condition is true then expr1 will be returned otherwise expr2 will be returned

			<p [style.color] = "result > 30 ? 'blue' : 'green'"> Hello Color World! </p>

			<p bind-style.color = "result > 30 ? 'blue' : 'green'"> Hello Color World! </p>

			<p style.color = "{{result > 30 ? 'blue' : 'green'}}"> Hello Color World! </p>  


		myStyles = {
			'color': this.colorFlag ? 'black' : 'yellow',
			'font-size.em': this.isSmall ? this.small/5 : this.big/5,
			'background-image': !this.isBackgroundRed ? 'url(\'images/red.gif\')' : 'url(\'images/green.gif\')'
		}; 


		getMyStyles() {

			let myStyles = {
				'color': this.colorFlag ? 'black' : 'yellow',
				'font-size.em': this.isSmall ? this.small/5 : this.big/5,
				'background-image': !this.isBackgroundRed ? 'url(\'images/red.gif\')' : 'url(\'images/green.gif\')'
			};

			return myStyles;

		}



@ViewChild and @ViewChildren ( Accessing Child Component Classes )
------------------------------------------------------------------
	
	The @ViewChild and @ViewChildren decorators provide access to the class of child component from the containing component.


	@ViewChild
	----------
		The @ViewChild is a decorator function that takes the name of a component class as its input and finds its selector in the template of the containing component to bind to. @ViewChild can also be passed a template reference variable.

		For example, we bind the class AlertComponent to its selector <app-alert> and assign it to the property alert. This allows us to gain access to class methods, like show().


		import { Component, ViewChild } from '@angular/core';
		import { AlertComponent } from './alert.component';

		@Component({
			selector: 'app-root',
			template: `
				<app-alert>My alert</app-alert>
				<button (click)="showAlert()">Show Alert</button>
			`
		})
		
		export class AppComponent {

			@ViewChild(AlertComponent) alert: AlertComponent;

			showAlert() {
				this.alert.show();
			}
		}


	@ViewChildren
	-------------
		When there are multiple embedded components in the template, we can also use @ViewChildren. It collects a list of instances of the Alert component, stored in a QueryList object that behaves similar to an array.

		import { Component, QueryList, ViewChildren } from '@angular/core';
		import { AlertComponent } from './alert.component';

		@Component({
			selector: 'app-root',
			template: `
				<app-alert ok="Next" (close)="showAlert(2)">
					Step 1: Learn angular
				</app-alert>

				<app-alert ok="Next" (close)="showAlert(3)">
					Step 2: Love angular
				</app-alert>

				<app-alert ok="Close">
					Step 3: Build app
				</app-alert>

				<button (click)="showAlert(1)">Show steps</button>
			`
		})

	export class AppComponent {
		
		@ViewChildren(AlertComponent) alerts: QueryList<AlertComponent>;
		
		alertsArr = [];

		ngAfterViewInit() {
			this.alertsArr = this.alerts.toArray();
		}

		showAlert(step) {
			this.alertsArr[step - 1].show(); // step 1 is alert index 0
		}
	}



@ContentChild and @ContentChildren
----------------------------------
	@ContentChild and @ContentChildren work the same way as the equivalent @ViewChild and @ViewChildren, however, the key difference is that @ContentChild and @ContentChildren select from the projected content within the component.



Angular - Pipes "|"
-------------------

	The Angular pipes are used to Transform the Data. 

	For Example, the Date pipe formats the date according to locale rules. We can pass arguments to pipe and chain pipes. The Angular also allows us to create the Custom Pipe

	Built-in pipes
	--------------
		Angular comes with a stock of pipes such as 

		"date", "uppercase", "lowercase", "currency", "json" and "percent". 

		They are all available for use in any template.

		To apply a pipe on a bound property use the pipe character " | "

	lowercase
	---------
		{{employee.code | lowercase}}

	uppercase
	---------
		{{employee.code | uppercase}}


	decimal
	-------

	date
	----
		date_expression | date[:format]

		{{employee.dateOfBirth | date:'dd/MM/y'}}

		{{employee.dateOfBirth | date:'fullDate'}}

	format 
	------
		'medium': equivalent to 'yMMMdjms' (e.g. Sep 3, 2010, 12:05:08 PM for en-US)
		'short': equivalent to 'yMdjm' (e.g. 9/3/2010, 12:05 PM for en-US)
		'fullDate': equivalent to 'yMMMMEEEEd' (e.g. Friday, September 3, 2010 for en-US)
		'longDate': equivalent to 'yMMMMd' (e.g. September 3, 2010 for en-US)
		'mediumDate': equivalent to 'yMMMd' (e.g. Sep 3, 2010 for en-US)
		'shortDate': equivalent to 'yMd' (e.g. 9/3/2010 for en-US)
		'mediumTime': equivalent to 'jms' (e.g. 12:05:08 PM for en-US)
		'shortTime': equivalent to 'jm' (e.g. 12:05 PM for en-US)

	currency
	--------
		{{employee.annualSalary | currency:'USD':true:'1.3-3'}}

		Example:
		--------
			@Component({

			selector:"my-pipes",

			template:` 	
				<h2>Hello {{name | uppercase }}</h2> 
				//Hello MAHESH

				<h2>Hello {{name | lowercase }}</h2>	
				//Hello mahesh

				<h2>Hello {{name | slice:'2' }}</h2>	
				//Hello hesh

				<h2>Hello {{name | slice:'2':'5' }}</h2> 	
				//Hello hes

				<h2>Hello {{name | replace:'Mahesh':'Manoj' }}</h2>		
				//Hello Manoj

				<h2>{{num}}</h2>	// 2.569							

				<h2>{{num | number:'1.2-2'}}</h2>	
				//2.57

				<h2>{{num | number:'2.2-2'}}</h2>	
				//02.57

				<h2>{{num | number:'2.4-5'}}</h2>	
				//02.5690

				<h2>American Currency - {{num | currency:'USD':true}}</h2>	
				//American Currency - $2.569

				<h2>British Currency - {{num | currency:'GBP':true}}</h2>	
				//British Currency - £2.569				

				<h2>Inidan Currency - {{num | currency:'INR':true}}</h2>	
				//Inidan Currency - ₹2.569

				<h2>Current Date - {{date}}</h2>	
				//Current Date - Thu May 04 2017 19:25:08 GMT+0530 (India Standard Time)

				<h2>Current Full Date - {{date | date:"fullDate"}}</h2>		
				//Current Full Date - Thursday, May 4, 2017

				<h2>Current Short Date - {{date | date:"shortDate"}}</h2>	
				//Current Full Date - 5/4/2017

				<h2>Current Short Time - {{date | date:"shortTime"}}</h2>	
				//Current Full Date - 7:25 PM

				<h2>Current "MM/dd/yy" Date Type - {{date | date:"MM/dd/yy"}}</h2>
			`,
			})


			export class testComponent{
				public name ="Mahesh";
				public num =2.569;
			}



Custom pipes
------------

	- Create custom pipe.
	- Transforming the value. 
	- Override transform() method. 
	- Returning the new value 
	- Accepting arguments 

	(OR)


	Step 1 : 
	--------
		To achieve this let's create a custom pipe called employeeTitlePipe. Right click on the "employee" folder and add a new TypeScript file. Name it "employeeTitle.pipe.ts". Copy and paste the following code.

		Code Explanation : 
		----------------
		
		1. Import Pipe decorator and PipeTransform interface from Angular core

		2. Notice "EmployeeTitlePipe" class is decorated with Pipe decorator to make it an Angular pipe

		3. name property of the pipe decorator is set to employeeTitle. This name can then be used on any HTML page where you want this pipe functionality.

		4. EmployeeTitlePipe class implements the PipeTransform interface. This interface has one method transform() which needs to be implemented.

		5. Notice the transform method has 2 parameters. value parameter will receive the name of the employee and gender parameter receives the gender of the employee. The method returns a string i.e Mr. or Miss. prefixed to the name of the employee depending on their gender.


		import {Pipe, PipeTransform } from '@angular/core'

		@Pipe({
			name:'PriceDiff',
		})

		export class mobilePipe implements PipeTransform{
			
			priceChange(value: string, gender: string): string { 
			
				if (gender.toLowerCase() == "male") {

					return "Mr." + value; 

				} else {
				
					return "Miss." + value; 
				}
			}
		}


	Step 2 : 
	--------
		Register "EmployeeTitlePipe" in the angular module where we need it. In our case we need it in the root module. So in app.module.ts file, import the EmployeeTitlePipe and include it in the "declarations" array of NgModule decorator

		import { EmployeeTitlePipe } from './employee/employeeTitle.pipe'

		@NgModule({ 
			imports: [BrowserModule], 
			declarations: [AppComponent, EmployeeComponent, EmployeeListComponent, EmployeeTitlePipe], 
			bootstrap: [AppComponent]
		})
		
		export class AppModule { }

	Step 3 : 
	--------
		In "employeeList.component.html" use the "EmployeeTitlePipe" as shown below. Notice we are passing employee gender as an argument for the gender parameter of our custom pipe. Employee name gets passed automatically.


	Step 4 :
	-------
		employee.name | employeeTitle:employee.gender
