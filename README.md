What is Angular
---------------
	Angular 2+ versions are simply called Angular. 

	It is a TypeScript-based open-source front-end web application platform.

	Angular is written completely in Typescript and includes the ES6 specification. 

	Angular is a Framework to build mobile and desktop application.

	Angular Architecture & Features
	-------------------------------
		- Modules

		- Components

		- Templates

		- Metadata

		- Data binding

		- Directives

		- Services

		- Dependency injection



Ng Self Commands
----------------
	-> start : "ng serve",

	-> build : "ng build --prod",

	-> test  : "ng test",

	-> lint  : "ng lint",

	-> e2e   : "ng e2e"



Angular Project Structure
-------------------------
	- package.json ::
		package.json comes from traditional nodejs projects and it defines all the npm based dependencies , dev-dependencies and npm scripts etc required for the angular project.
	
	- tsconfig.json ::
		if there's a tsconfig file in a directory , that means that directory is a root directory of a typescript project , moreover it is also used to define different typescript compilation related options.

	- .angular.json ::
		.angular.json is a file used by @angular/cli tool which is used to automate the angular workflow by automating different operations related to development and testing of angular apps. .angular-cli serves as a blueprint to the @angular/cli tool.

	# src directory::
		this is perhaps one of the most important directory in our angular project and it will be the topic of discussion in the rest of the article , this is where we define the actual source code for our application along with all the assets etc. In the following sections , we'll look into this directory and will cover files and folders it contains
			

			# assets directory::
				as the name suggests , this directory contains all the static assets of our app like images etc.

			# environments directory::
				environments directory hold our environment specific settings , e.g. different configuration files for development , testing and staging etc.


			- index.html ::
				index.html is the landing page or the main page of our application and this is where our angular app bootstraps.

			- main.ts ::
				Bootstrapping an Application
					main.ts is the main typescript file which is used to bootstrap the angular module. The check for environment is also performed here as shown in the following code snippet.

				src/main.ts
				-----------
					import { platformBrowserDynamic } from '@angular/platform-browser-dynamic';
					import { AppModule } from './app/app.module';

					platformBrowserDynamic().bootstrapModule(AppModule);

			# app directory::

				app directory is where we place the building blocks of our angular app including modules , components , component styles , component templates , services and so on.

				- app.module.ts :: 

					In this file , we declare our angular module , the @NgModule decorator is used to initialize different aspects of the angular app , observe that AppComponent is also declared.

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


			- app.components.ts 

				this file simply defines an angular component and this is where we have defined our app-root selector also

				import { Component } from '@angular/core';

				@Component({
					selector: 'app-root',
					templateUrl: './app.component.html',
					styleUrls: ['./app.component.css']
				})

				export class AppComponent {
					title = 'app'; // this is used in the template 
				}


			- app.component.html

				<div style="text-align:center">
				  <h1>Welcome to {{title}}!!</h1>				  
				</div>
				<h2>Here are some links to help you start: </h2>



Angular - Modules
-----------------
		
	- Angular apps are modular
	
	- Angular has its own modularity system called Angular modules or NgModules.
	
	- Every Angular app has at least one Angular module class, the root module, conventionally named AppModule.

	- Angular module is a collection of components, services, directives and pipes



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

		import { NgModule } from '@angular/core';
		import { BrowserModule } from '@angular/platform-browser';
		import { HttpClientModule } from '@angular/common/http';
		import { FormsModule } from '@angular/forms'

		import { AppComponent } from './app.component';
		import { MainComponent } from './main/main.component';

		@NgModule({
			declarations: [
				AppComponent,
				HomeComponent
			],
			imports: [
				BrowserModule,
				FormsModule,
				HttpClientModule
			],
			providers: [],
			bootstrap: [AppComponent]
		})

	export class AppModule { }



Angular - Component
-------------------

	The Component is a classes that interact with the View (UserInterface)

	which is decorated by @Component class decorator

	The Component has four important parts

		Import Statement 
			- The Import statement imports the dependencies required by this component.
		
		Classes 
			- The class contains the application logic. It is decorated by the @Component class decorator.
		
		Template 
			- The template defines the Layout of the View and defines what is rendered on the page.  Without the template,  there is nothing for Angular to render to the DOM.
		
		Metadata 
			S- Metadata Provides additional information about the component to the Angular. 

	  


	Component Metadata Properties:
	-----------------------------
		selector - css selector that identifies this component in a template

		styleUrls - list of urls to stylesheets to be applied to this component's view

		styles - inline-defined styles to be applied to this component's view

		template - inline-defined template for the view

		templateUrl - url to an external file containing a template for the view

		viewProviders - list of providers available to this component and its view children

		inputs - list of class property names to data-bind as component inputs

		outputs - list of class property names that expose output events that others can subscribe to

		providers - The Providers are the services, that our component going to use.

		encapsulation - style encapsulation strategy used by this component

		animations - list of animations of this component

		changeDetection - change detection strategy used by this component

		entryComponents - list of components that are dynamically inserted into the view of this component

		exportAs - name under which the component instance is exported in a template

		host - map of class property to host element bindings for events, properties and attributes		

		interpolation - custom interpolation markers used in this component's template

		moduleId - ES/CommonJS module id of the file in which this component is defined		

		queries - configure queries that can be injected into the component


		# Create the Component file
			
			- Import the required external Classes/Functions
			- Create the Component class and export it
			- Add @Component decorator
			- Add metadata to @Component decorator
			- Create the Template
			- Create the CSS Styles
			- Register the Component in Angular Module


		Example :

			import { Component } from '@angular/core';
			 
			@Component({
			    selector: 'bank-app',
			    template: '<h1>Hello & Welcome to ABC Bank Ltd. </h1>',
			    styleUrls:['style.css']
			})

			export class BankComponent{ }



Angular - Template
------------------
	The Component needs a View to display. The Template defines that View.

	The Template is just a subset of HTML, that tells Angular how to display the view. It is created using the normal HTML tags like h1, h2 etc. 

	It also uses the Angular-specific markup like 

	{{}} for interpolation, 

	[] for Property binding, 

	() for Event binding ...etc



Angular - Metadata
------------------
	Metadata tells angular how to Process the class.

	The Metadata is attached to the class using a class decorator. When we attach @Component class decorator to the class, then it becomes Component class.

	The class Decorator uses the configuration object, which provides the Angular information it needs to create the component. 

		- @Component
		
		- @Directive
		
		- @Injectible
		
		- @NgModule
		
		- @Pipe

	For Example, 

		@Component directives come with configuration options like selector, templateURL, directives ..etc

		@Directive directives come with configuration options like selector, providers, exportAs ..etc



Angular - Directives
--------------------
	
	The Angular directive helps us to manipulate the DOM. You can change the appearance, behaviour or a layout of a DOM element using the Directives. They help you to extend HTML

	There are three kinds of directives in Angular:

		Component Directive
		Structural directives
		Attribute directives

	# Component directive is used to create HTML template. 
		This is most commonly used directive in angular project. 

	# Attribute directive changes the appearance or behavior of DOM element. 
		- The ngClass Directive is allows us to add or remove CSS classes to an HTML element. 

		- The ngStyle directive allows you to modify the style of an HTML element using the expression.
		Using the ngStyle you can dynamically change the style of your HTML element.


	# Structural directive is used to change the DOM layout by adding and removing DOM elements. 

		- The "ngFor" is repeats a portion of HTML template once per each item from an iterable list (Collection).

		- The "ngSwitch" allows us to Add/Remove DOM Element. It is similar to switch statement.  

		- The "ngIf" allows us to Add/Remove DOM Element. 


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



	Attribute Directives
	--------------------
		- Attribute directive changes the appearance or behavior of DOM element.

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
							.centered-text { text-align: center; }
							.underlined { border-bottom: 1px solid #ccc; }
							.orange{ color: orange; }
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

		- Structural directive is used to change the DOM layout by adding and removing DOM elements.

		- Angular has a few built-in structural directives such as 'ngIf', 'ngFor', and 'ngSwitch'


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



	Custom Structural Directive
	---------------------------
		We can create custom attribute directives and custom structural directives using @Directive decorator.

		# TemplateRef and ViewContainerRef
		----------------------------------
			To change DOM layout we should use TemplateRef and ViewContainerRef in our structural directive. 
				
				- TemplateRef : 
					It represents an embedded template that can be used to instantiate embedded views. 

				- ViewContainerRef: 
					It represents a container where one or more views can be attached. 




	Custom Attribute Directive
	--------------------------
		- Implement attribute directives with @Directive, @HostBinding and @HostListener.

		- @HostBinding lets you set properties on the element or component that hosts the directive, and @HostListener lets you listen for events on the host element or component.

		- Use Renderer2, ElementRef and NativeElement to change the appearance and behavior of DOM elements.


		ElementRef
		----------
			The ElementRef object gives you direct access to the DOM element for the directive through the nativeElement property.

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



		@HostBinding
		------------
			We can use attribute directives to affect the value of properties on the host node by using the @HostBinding decorator.

			The @HostBinding decorator allows us to programatically set a property value on the directive's host element. 

			It works similarly to a property binding defined in a template, except it specifically targets the host element. 

			The binding is checked for every change detection cycle, so it can change dynamically if desired.


				import { Directive, HostBinding, HostListener } from '@angular/core';

				@Directive({
					selector: '[appButtonPress]'
				})
				
				export class ButtonPressDirective {
					
					@HostBinding('attr.role') role = 'button';
					
					@HostBinding('class.pressed') isPressed: boolean;

					@HostListener('mousedown') hasPressed() {
						this.isPressed = true;
					}

					@HostListener('mouseup') hasReleased() {
						this.isPressed = false;
					}
				}


			Notice that for both use cases of @HostBinding we are passing in a string value for which property we want to affect. If we don't supply a string to the decorator, then the name of the class member will be used instead.

			Tip: Though less common, @HostBinding can also be applied to Components if required.

		
		@HostListener 
		-------------
			we can also use @HostListener if we'd like to register listeners on the host element of a Component.



viewEncapsulation 
------------------
	ViewEncapsulation defines whether the template and styles defined within the component can affect the whole application. Angular provides three encapsulation strategies

	- Emulated: styles from other HTML spread to the component.

		# encapsulation: ViewEncapsulation.Emulated

			- Angular will not create a Shadow DOM for the component.
			- Style will be scoped to the component.
			- This is the default value for encapsulation.

	- Native: styles from other HTML do not spread to the component.

		# encapsulation: ViewEncapsulation.Native

			- is browsers supports "shadow DOM" ("shadow-root" open).
			- Angular will create Shadow DOM for the component.
			- Style is scoped to the component.

	- None: styles defined in a component are visible to all components.

		# encapsulation: ViewEncapsulation.none

			- is completly disabled (attributes, ex:_nghost-atr-1, ngcontent-atr-1, ... etc) the encapsulation.
			- There is no shadow DOM.
			- Style is not scoped to the component.


		Ex:-
		---
			import { Component, ViewEncapsulation } from '@Angular/core';

			@Component({
				selector:'my-movies',
				template:'<h3>Movies List</h3>',
				encapsulation: ViewEncapsulation.Emulated
			})



Angular - Data Binding
----------------------
	- Data Binding is a process where data is passed from Angular Component to view (Template) and vice versa.

	- The Data Binding is used to bind DOM Elements to Component properties. 

	- Binding can be used display component class property values to the user, change element styles, respond to a user event etc.

		Interpolation, Property Bindings, Event Bindings & Two Way Bindings.


	Interpolation (OR) Expression
	-----------------------------	
		Angular uses double-curly braces {{ }} to represent interpolation. Interpolation executes expression. Suppose we want to do mathematical calculation, we can perform it as follows within HTML template.

		- Interpolation is one way from component to View

		- interpolation is a special syntax that angular converts into a property binding

		- To concatenate string we must use interpolation instead of property binding 
			
			<img src="{{imgPath}}">	


	Property Binding
	----------------
		Property binding is performed as one-way from data source to view target. especially in case of styles and attribute bindings. It has a syntax [Property]="expression"

		In property binding there is source and target.

		Using square brackets "[]"
		Using "bind-" Keyword		

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

		Event Binding is used to Perform an action in the component when the user clicks a button in the view.
 
			<button (click)=’ClickPressed()’>

			<button (click)="isValid=true">True</button>  

			<button on-click="isValid=true">True</button>  
		
		Call component method on event binding.

			<input (change) = "changeText($event.target.value)">  


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
	-----------------------
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

			<p class="{{condition ? 'alret-success' : 'alret-danger'}}">

			<p [ngClass]="condition ? 'alret-success' : 'alret-danger'">

			<p [ngClass]="[condition ? 'alret-success' : 'alret-danger']">

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



One way Data Binding & Two way Data Binding in Angular
--------------------------------------------------------

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

			<p [ngStyle]="{ 'color': value }">Hello</p>

			<p [ngStyle]="{ 'color': (value ? 'white' : 'red') }">Hello</p>



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



Angular - Pipes "|"
-------------------

	The Angular pipes are used to Transform the Data. 

	For Example, the Date pipe formats the date according to locale rules. We can pass arguments to pipe and chain pipes. The Angular also allows us to create the Custom Pipe

	Built-in pipes
	--------------

		"date", "uppercase", "lowercase", "currency", "json", decimal, async, slice and "percent". 

		They are all available for use in any template.

		To apply a pipe on a bound property use the pipe character " | "

		Syntax :
			
			Expression | pipeOperator[:pipeArguments]


	lowercase
	---------
		{{employee.code | lowercase}}

	uppercase
	---------
		{{employee.code | uppercase}}

	slice
	-----
		SlicePipe creates the new Array or String containing the subset of given elements. It works same as JavaScript API Array.prototype.slice() and String.prototype.slice()
		
		Syntax
			{{ value_expression | slice : start [ : end ] }}

		Ex :
			<ul>
		   		<li *ngFor = "let obj of animalArray | slice:2:4">{{obj}}</li>
		  	</ul>


	json
	----
		JSON Pipe is used to convert a value into its JSON format, which is mostly useful in debugging.

		Syntax:
			{{ value_expression | json }}

		Ex:
			export class AppComponent {
			  	obj: object = {name: 'Yatendrasinh', lastName: 'Joddha', Degrees: {Graduations: 'BCA', Masters: 'MCA'}};
			}

			<p> {{obj | json}}</p>


			//Output: 
				{ "name": "Yatendrasinh", "lastName": "Joddha", "Degrees": { "Graduations": "BCA", "Masters": "MCA" } }



	async
	-----
		It is used to opens a value from an asynchronous primitive. The async pipe subscribes to an Observable or Promise and returns the latest value it has produced. When a new value is produced, the async pipe marks the component to be checked for changes. When the component gets destroyed, the async pipe unsubscribes automatically to avoid possible memory leaks.

		Syntax:

			{{ value_expression | async}}

		Ex:-
			export class AppComponent {
				greeting: Promise<string>|null = null;
				arrived: boolean = false;

				private resolve: Function|null = null;

				constructor() { this.reset(); }

				reset() {
					this.arrived = false;
					this.greeting = new Promise<string>((resolve, reject) => { this.resolve = resolve; });
				}

				clicked() {
					if (this.arrived) {
						this.reset();
					} else {
						this.resolve !('hi there!');
						this.arrived = true;
					}
				}
			}

			<div>
				<code>promise|async</code>: 
				<button (click)="clicked()">{{ arrived ? 'Reset' : 'Resolve' }}</button>
				<span>Wait for it... {{ greeting | async }}</span>
			</div>


	percent
	-------
		{{ value_expression | percent [ : digitsInfo [ : locale ] ] }}

		  a: number = 0.259;
		  b: number = 1.3495;

		<p>A: {{a | percent}}</p>	//26%
 
	    <p>B: {{b | percent:'4.3-5'}}</p>	//0,134.950%
	 
	    <p>B: {{b | percent:'4.3-5':'fr'}}</p>	//0 134,950 %


	decimal
	-------
		Transforms a number into a string, formatted according to locale rules that determine group sizing and separator, decimal-point character, and other locale-specific configurations.

		{{ value_expression | number [ : digitsInfo [ : locale ] ] }}
    
		Ex:-		    
		    <p>e (no formatting): {{e | number}}</p>
		    <!--output '2.718'-->

		    <p>e (3.1-5): {{e | number:'3.1-5'}}</p>
		    <!--output '002.71828'-->


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
				a: number = 0.259;
  				b: number = 1.3495;
			}



	Custom pipes
	-------------
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

			export class mobilePipe implements PipeTransform {
				
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



	Async Pipe in Angular
	---------------------
		- The async pipe subscribes to an Observable or Promise and returns the latest value it has emitted.

		- When a new value is emitted, the async pipe marks the component to be checked for changes. 

		- When the component gets destroyed, the async pipe unsubscribes automatically to avoid potential memory leaks.

		- It is used to perform the asynchronous operation for the observable and the subscribe, unsubscribe operation can be automatically done by AsyncPipe.



Angular - Forms
---------------
	Angular comes with two different ways of building forms in our applications. 

		1. Template Driven Forms -ngForm, ngModel
		2. Model Driven Forms - FormBuilder, FormGroup, FormControl, Validators


	# Angular Template Driven Forms

		Angular 2 Template Driven Forms are and how to build a simple Template driven forms

		we need to tell our @NgModule to use the FormsModule from @angular/forms. In the app.module.ts file. 
		
		we used ngModel & ngModelGroup directive on the HTML elements,

		ngForm
		------
		 	The ngForm directive is what makes the Angular Template driven Forms work.


		Built-in Validators
		-------------------
			The Angular Built-in validators use the HTML5 validation attributes like required, minlength, maxlength & pattern. Angular 2 interprets these validation attributes and add the validator functions to FormControl.

			The list of HTML5 validation attributes supported in Angular

			- required: There must be a value
			- minlength: The number of characters must be more than the value of the attribute.
			- maxlength: The number of characters must not exceed the value of the attribute.
			- pattern: The value must match the pattern.

			<form #contactForm="ngForm" (ngSubmit)="onSubmit(contactForm)">

				<div class="form-group">

					<label for="username">username</label> 
					<input type="text" class="form-control" name="username" ngModel #username="ngModel" required minlength="10">

					<div *ngIf="!contactForm.controls.username?.valid && (contactForm.controls.username?.dirty || myForm.controls.username?.touched)" class="alert alert-danger">
						<div [hidden]="!contactForm.controls.username.errors.required">username is required</div>
					</div>

				</div>

				<div class="form-group">
					<label for="email">Last Name</label> 
					<input type="email" class="form-control" name="email" ngModel #email="ngModel" required >

					<div *ngIf="!contactForm.controls.email?.valid && (contactForm.controls.email?.dirty || myForm.controls.emailemail?.touched)" class="alert alert-danger">
						<div [hidden]="!contactForm.controls.email.errors.required">email is required</div>
					</div>
				</div>

				<div class="form-group">
					<button type="submit" [disabled]="!contactForm.valid">Submit</button>
				</div>
			</form>


	# Angular Model Drive forms

		We need to import 'ReactiveFormsModule'

		which created the FormGroup & FormControl instances behind the scene.

		it is our responsibility to create the FormGroup and FormControl

		
		# FormGroup :
			- The FormGroup takes 3 arguments. 
			- a collection of child FormControl, a validator, and an asynchronous validator. 
			- The Validators are optional.

			contactForm = new FormGroup({})

		# FormControl
			- The first argument to FormGroup is the collection of child FormControl. 
			- They are added using the FormControl method as shown

			contactForm = new FormGroup({
			    firstname: new FormControl(),
			    lastname: new FormControl()
			})

		import { ReactiveFormsModule } from '@angular/forms';


		we need to import FormGroup, FormControl & Validator from the angular/forms. 

		import { FormGroup, FormControl, Validators } from '@angular/forms';


		<form [formGroup]="contactForm" (ngSubmit)="onSubmit()">
			<div class="form-group">
			    <label for="firstname">First Name</label> 
			    <input type="text" class="form-control" name="firstname" formControlName="firstname">
			</div>

			<div class="form-group">
			    <label for="lastname">Last Name</label> 
			    <input type="text" class="form-control" name="lastname" formControlName="lastname">
			</div>

			<div class="form-group">
			     <button type="submit">Submit</button>
			</div>
		</form>

		onSubmit() {
		    console.log(this.contactForm.value);
		}



		Angular provides two ways to work with forms: template-driven forms and reactive forms, the latter also sometimes called model-driven forms. With template-driven forms, the default way to work with forms in Angular, template directives are used to build an internal representation of the form. With reactive forms, by contrast, you build your own representation of a form in the component class.

		Here are some examples of things that are easy to do with reactive forms:

			Using custom validators
			Changing validation dynamically
			Dynamically adding form fields



Angular - Components Communcations
---------------------------------- 

	Inputs and Outputs
	------------------

		Use property binding and the '@Input' decorator to pass data into a component, and '@Output' and 'EventEmitter' to pass data out and bind to an event.

			- @Input is attached to a property that can be used for property binding - [ex_property]

			- @Output is attached to a property that can be used for event binding - (ex_event)

		@Input
		------

			@Input decorator Communicate from Parent Component to Child Component. This is one way communication from parent to child. The component property should be annotated with @Input decorator to act as input property. A component can receive a value from another component using component property binding. Now we will see how to use @Input. It can be annotated at any type of property such as number, string, array or user defined class. To use alias for the binding property name we need to assign an alias name as @Input(alias). 

			Find the use of @Input with string data type.

			Example
			-------
				Parent Component
				----------------
					import {Component} from '@angular/core';

					@Component({
						selector: 'parentComponent',
						template: ` 

							<div class="jumbotron">
								<h1>Hello! {{name}}</h1>
								<input type="text" class="col-sm-3 form-control" [(ngModel)]="bindParentData">

								// <input type="text" class="col-sm-3 form-control" #bindParentData (keyup)="0">
							</div>							

							<ChildComponent [bindParentToChild]="bindParentData">Loading... </ChildComponent>
						`,
					})
					export class AppComponent {

						public name = "Parent Component";

					}


				Child Component
				---------------
					import {Component, Input} from '@angular/core';

					@Component({
						selector:'ChildComponent',

						template:`<p>{{bindParentToChild}}</p>`,

						inputs:['bindAppToSec'],
					})

					export class maheshComponent{

						// @Input() bindParentToChild;  //this another option

						// @Input('bindParentToChild') ParentToChild ;  //this another option
					}



		@Output
		-------
			- @Output decorator Communicate from Child Component to Parent Component.

			- @Output decorator binds a property of a component to send data from one component (child component) to calling component (parent component). 

			- This is one way communication from child to parent component. 

			- @Output binds a property of the type of angular EventEmitter class. 

			- Our EventEmitter object has an emit() method that pushes the event up to the parent component.

			- This property name becomes custom event name for calling component. 

			- @Output decorator can also alias the property name as @Output(alias) and now this alias name will be used in custom event binding in calling component. 

			EventEmitter
			------------
				its only purpose is to emit events in components

				EventEmitter is really an Angular abstraction, and should be used pretty much only for emitting custom Events in components.


			Example
			-------
				Parent Component
				----------------
					import {Component} from '@angular/core';

					@Component({

						selector: 'parentComponent',

						template: ` 	
							<div class="jumbotron">

							<h1>Hello! {{name}}</h1>								

							<p>{{bindChildData}}</p>

							</div>							

							<ChildComponent (bindChildEvent)="bindChildData=$event">Loading ... </ChildComponent>
						`,

					})

					export class AppComponent {

						public name = "Parent Component";

					}


				Child Component
				---------------
					import {Component, EventEmitter, Output} from '@angular/core';

					@Component({

						selector:'ChildComponent',

						template:`
							<div class="jumbotron br-black">
							<h1>Hello! {{name}}</h1>

							<input type="text" #bindChildData (keyup)="onChange(bindChildData.value)">

							</div>
						`,

						outputs:['bindChildEvent']
					})

					export class maheshComponent{

						public name = "Child Component";

						// @Output() bindChildEvent;  //this another option

						bindChildEvent = new EventEmitter<string>();

						onChange(data:string){
							this.bindChildEvent.emit(data)
						}
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

				@ViewChild(AlertComponent) alertMsg: AlertComponent;

				showAlert() {
					this.alertMsg.showAlertMsg();
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

	Using Services
	---------------



Angular - Template Reference Variable
-------------------------------------
	A template reference variable is a reference to a DOM element or directive within a template. Using template reference variable we access the values of DOM element properties. 

	Template reference variable is declared using '#' and 'ref-' as prefix, 

	Template Reference Variable Syntax

		1. Using #

			<input type="text" #myVar>  

			Here myVar will be a template reference variable. 

		2. Using ref-

			<input type="text" ref-myVar>  

			Here myVar will be a template reference variable.


	Template Reference Variable using Select Box
	--------------------------------------------
		Here we will discuss template reference variable with select box.

		<select #myColor (change) = "setData(myColor.value)"></select> 

		Look at the code snippet, #myColor is a template reference variable. The selected value of select box can be accessed by myColor.value .


	Template Reference Variable using Input Text Box
	------------------------------------------------
		
		Template reference variable is a variable using which we can access DOM properties. In our example we are using following DOM properties of input box. 

		1. placeholder 
		2. type 
		3. value Now find the code snippet.

			<input type="text" #mobile placeholder="Enter Mobile Number">  

			In the above input text box #mobile is a template reference variable. To fetch DOM properties

				mobile.placeholder : It will give placeholder of our text box if we have specified. 
				mobile.value : It will give value of our text box. 
				mobile.type : It will give type of input element. In our example type is text.


	Template Reference Variable with NgForm
	---------------------------------------
		how to access NgForm directive using template reference variable. We are creating a sample form here.

		<form (ngSubmit)="onSubmitPersonForm(myForm)" #myForm="ngForm">
			<input name="name" required [(ngModel)]="person.pname">
			<button type="submit" [disabled]="!myForm.form.valid">Submit</button>
		</form>  

		ngSubmit
		--------
			It enables binding angular expressions to onsubmit event of the form. Here on form submit onSubmitPersonForm component method will be called. 

		ngForm
		------
			It is the nestable alias of form directive 

			Here we are using template reference variable for ngForm as #myForm="ngForm" . Now we can use myForm in place of ngForm such as to check form validity and we can also use it in our angular expressions.



Angular - Routing and Routes 
----------------------------
	
	The Angular Router enables navigation from one view to the next as users perform application tasks.

	RouterModule and Routes
	-----------------------
		- RouterModule is a separate module in angular that provides required services and directives to use routing and navigation in angular application. 

		- Routes defines and array of roots that map a path to a component. Paths are configured in module to make available it globally. 

	
		To use RouterModule and Routes in module,

		Step-1
		------
			Set base tag in index.html

				<base href="/"> 


		Step-2
		-------
			- import RouterModule and Routes

			import { RouterModule, Routes } from '@angular/router'; 

		Step-3 
		------
			Create Array of Routes :

			- Mapping a Route to a Component 

				{ path: 'manage-book', component: ManageBookComponent } 

			- Configure Parameters

				{ path: 'update-book/:id', component: UpdateBookComponent } 

			- Redirect to a URL

				{ path: '', redirectTo: '/manage-book ', pathMatch: 'full' }  

			- Handling "Page Not Found"

				{ path: '**', component: PageNotFoundComponent } 

			Example
			-------
				const routes: Routes = [
					{ path: 'home', component: homeComponent },
					{ path: 'about/:id', component: aboutComponent }, 
					{ path: '', redirectTo: '/conatct ', pathMatch: 'full' },
					{ path: '**', component: PageNotFoundComponent }
				] 

		Step-4
		------
			Using RouterModule.forRoot() 

			Now we need to import RouterModule.forRoot(routes) using imports metadata of @NgModule. Here argument routes is our constant that we have defined above as array of Routes to map path with component.

			imports: [ RouterModule.forRoot(routes) ] 



	Example-1
	---------
		'app.route.ts'
		-------------
			import { NgModule } from '@angular/core';
			import { RouterModule, Routes } from '@angular/router';

			import { homeComponent } from './home/app.home';
			import { aboutComponent } from './about/app.about';

			const routes: Routes =[
				{path:'Home', component:homeComponent},
				{path:'About', component:aboutComponent},
			];

			@NgModule({
				imports: [ RouterModule.forRoot(routes)],
				exports: [ RouterModule ]
			})

			export class AppRouterModule{}

			export const routerComponets = [homeComponent, aboutComponent ]


		app.component.html
		---------------
			<nav>

				<ul>
					<li><a routerLink="/Home" routerLinkActive="active">Home</a></li>
					<li><a routerLink="/About" routerLinkActive="active">About</a></li>
				</ul>

				<router-outlet></router-outlet>

			</nav>


	pathMatch
	---------
		The pathMatch property, which is required for redirects, tells the router how it should match the URL provided in order to redirect to the specified route. Since pathMatch: full is provided, the router will redirect to component-one if the entire URL matches the empty path ('').
		
			export const routes: Routes = [
			  { path: '', redirectTo: 'component-one', pathMatch: 'full' },
			  { path: 'component-one', component: ComponentOne },
			  { path: 'component-two', component: ComponentTwo }
			];


	Angular - Route Parameters
	--------------------------
		Say we are creating an application that displays a product list. When the user clicks on a product in the list, we want to display a page showing the detailed information about that product. To do this you must:
			
			- add a route parameter ID
			- link the route to the parameter
			- add the service that reads the parameter.


			# Declaring Route Parameters

				The route for the component that displays the details for a specific product would need a route parameter for the ID of that product. We could implement this using the following Routes:
				
				export const routes: Routes = [
					{ path: '', redirectTo: 'product-list', pathMatch: 'full' },
					{ path: 'product-list', component: ProductList },
					{ path: 'product-details/:id', component: ProductDetails }
				];


				Note :
					id in the path of the product-details route, which places the parameter in the path. For example, to see the product details page for product with ID 5, 

					you must use the following URL: localhost:3000/product-details/5

			# Linking to Routes with Parameters
			
				In the ProductList component you could display a list of products. Each product would have a link to the product-details route, passing the ID of the product:
			
					<a *ngFor="let product of products" [routerLink]="['/product-details', product.id]">
						{{ product.name }}
					</a>

				Note:
					the routerLink directive passes an array which specifies the path and the route parameter. 


				Alternatively we could navigate to the route programmatically:

					goToProductDetails(id) {
						this.router.navigate(['/product-details', id]);
					}



			# Reading Route Parameters
			
				The ProductDetails component must read the parameter, then load the product based on the ID given in the parameter.
			
				The ActivatedRoute service provides a params Observable which we can subscribe to to get the route parameters (see Observables).
			

				import { Component, OnInit, OnDestroy } from '@angular/core';
				import { ActivatedRoute } from '@angular/router';

				@Component({
					selector: 'product-details',
					template: `<div>Showing product details for product: {{id}}</div>`,
				})

				export class LoanDetailsPage implements OnInit, OnDestroy {
					id: number;
					private sub: any;

					constructor(private route: ActivatedRoute) {}

					ngOnInit() {
						this.sub = this.route.params.subscribe(params => {
							this.id = +params['id']; 
							// (+) converts string 'id' to a number

							// In a real app: dispatch action to load the details here.
						});
					}

					ngOnDestroy() {
						this.sub.unsubscribe();
					}
				}

			The reason that the params property on ActivatedRoute is an Observable is that the router may not recreate the component when navigating to the same component. In this case the parameter may change without the component being recreated.


		Defining Child Routes
		---------------------
			When some routes may only be accessible and viewed within other routes it may be appropriate to create them as child routes.

				localhost:3000/product-details/3/overview


				export const routes: Routes = [
					{ path: '', redirectTo: 'product-list', pathMatch: 'full' },
					{ path: 'product-list', component: ProductList },
					{ path: 'product-details/:id', component: ProductDetails,
						children: [
							{ path: '', redirectTo: 'overview', pathMatch: 'full' },
							{ path: 'overview', component: Overview },
							{ path: 'specs', component: Specs }
						]
					}
				];


			Where would the components for these child routes be displayed? 

			Just like we had a <router-outlet></router-outlet> for the root application component, we would have a router outlet inside the ProductDetails component. 

			The components corresponding to the child routes of product-details would be placed in the router outlet in ProductDetails.
			
			import { Component, OnInit, OnDestroy } from '@angular/core';
			import { ActivatedRoute } from '@angular/router';

			@Component({
				selector: 'product-details',
				template: `
					<p>Product Details: {{id}}</p>
					<!-- Product information -->
					<nav>
					<a [routerLink]="['overview']">Overview</a>
					<a [routerLink]="['specs']">Technical Specs</a>
					</nav>
					<router-outlet></router-outlet>
					<!-- Overview & Specs components get added here by the router -->
				`
			})

			export default class ProductDetails implements OnInit, OnDestroy {
			
				id: number;

				constructor(private route: ActivatedRoute) {}

				ngOnInit() {
					this.sub = this.route.params.subscribe(params => {
						this.id = +params['id']; // (+) converts string 'id' to a number
					});
				}

				ngOnDestroy() {
					this.sub.unsubscribe();
				}
			}

			Alternatively, we could specify overview route URL simply as:
			
			localhost:3000/product-details/3
			
			export const routes: Routes = [

				{ path: '', redirectTo: 'product-list', pathMatch: 'full' },
				{ path: 'product-list', component: ProductList },
				{ path: 'product-details/:id', component: ProductDetails,
					children: [
						{ path: '', component: Overview },
						{ path: 'specs', component: Specs }
					]
				}

			];

			Componentless Routes
			--------------------
				const routes: Routes = [
					{ path: '', component: ParentComponent, children: [
						{ path: 'red-pill', children: [
							{ path: 'knock-knock', component: SubChildComponent, children: [
								{ path: 'neo', component: SubSubChildComponent }
							]},
						]},
						{ path: 'blue-pill', component: AnotherChildComponent }
					]}
				];



		Accessing a Parent's Route Parameters
		-------------------------------------

			export default class Overview {
				parentRouteId: number;
				private sub: any;

				constructor(private router: Router,
				private route: ActivatedRoute) {}

				ngOnInit() {
					// Get parent ActivatedRoute of this route.
					this.sub = this.router.routerState.parent(this.route)
					.params.subscribe(params => {
						this.parentRouteId = +params["id"];
					});
				}

				ngOnDestroy() {
					this.sub.unsubscribe();
				}
			}

			Alternatively, we could specify overview route URL simply as:
			
			localhost:3000/product-details/3
			
			export const routes: Routes = [
				{ path: '', redirectTo: 'product-list', pathMatch: 'full' },
				{ path: 'product-list', component: ProductList },
				{ path: 'product-details/:id', component: ProductDetails,
					children: [
						{ path: '', component: Overview },
						{ path: 'specs', component: Specs }
					]
				}
			];


		Passing Optional Parameters ( Query parameters )
		---------------------------
			Query parameters allow you to pass optional parameters to a route such as pagination information.

				localhost:3000/product-list?page=2

			The key difference between query parameters and route parameters is that route parameters are essential to determining route, whereas query parameters are optional.


			# Passing Query Parameters

				Use the [queryParams] directive along with [routerLink] to pass query parameters. 

				For example:
					<a [routerLink]="['product-list']" [queryParams]="{ page: 99 }">Go to Page 99</a>

				Alternatively, we can navigate programmatically using the Router service:
				
				goToPage(pageNum) {
					this.router.navigate(['/product-list'], { queryParams: { page: pageNum } });
				}


			# Reading Query Parameters
				
				Similar to reading route parameters, the Router service returns an Observable we can subscribe to to read the query parameters:
				
				import { Component } from '@angular/core';
				import { ActivatedRoute, Router } from '@angular/router';

				@Component({
					selector: 'product-list',
					template: `<!-- Show product list -->`
				})
				
				export default class ProductList {
					constructor( private route: ActivatedRoute, private router: Router) {}

					ngOnInit() {
						this.sub = this.route
							.queryParams
							.subscribe(params => {
								// Defaults to 0 if no query param provided.
								this.page = +params['page'] || 0;
							});
					}

					ngOnDestroy() {
						this.sub.unsubscribe();
					}

					nextPage() {
						this.router.navigate(['product-list'], { queryParams: { page: this.page + 1 } });
					}
				}



	Defining Links Between Routes
	-----------------------------
		# RouterLink
			
			Add links to routes using the RouterLink directive.
		
			For example the following code defines a link to the route at path component-one.
				<a routerLink="/component-one">Component One</a>
		
		# Navigating Programmatically
		
			Alternatively, you can navigate to a route by calling the navigate function on the router:
			
			this.router.navigate(['/component-one']);



	Create Multiple Router Outlets
	------------------------------
		You can have multiple outlets in the same template:

			<router-outlet></router-outlet>  
			<router-outlet  name="sidebar"></router-outlet> 
    		<router-outlet name="userList"></router-outlet>
    		<router-outlet name="userInfo"></router-outlet>

			const routes: Routes = [
				{ path: '', redirectTo: 'home', pathMatch: 'full' },
				{ path: 'home', component: HomeComponent },
				{ path: 'menu', component: MenuComponent, outlet: "sidebar" },
				{ path: 'user', component: userComponent, children: [
				{ path: 'userList', component: userListComponent, outlet: 'userList' },
				{ path: ':id', component: userInfoComponent, outlet: 'userInfo' }]
			}];

			@NgModule({
				imports: [RouterModule.forRoot(routes)],
				exports: [RouterModule],
				providers: []
			})

			export class RoutingModule { }

		
		- The unnamed outlet is the primary outlet.
		
		- Except for the primary outlet, all other outlets must have a name.



	What is An Auxiliary Route?
	---------------------------
		A component has one primary route and zero or more auxiliary routes.. Auxiliary routes allow you to use and navigate multiple routes. To define an auxiliary route you need a named router outlet where the component of the auxiliary route will be rendered.

		The name that we're giving to the second outlet suggests that the outlet will be used as a sidebar for the app. Now let's create a sidebar component that will be rendered in the sidebar outlet:

			# ng g component sidebar
		
		We want the sidebar component to be rendered with each other component, in the same time. So we'll add an empty path and a sidebar outlet:

			{
			   path: "",
			   component: SidebarComponent,
			   outlet: "sidebar"
			}

		Navigating Inside Auxiliary Outlets
		-----------------------------------
			You can navigate inside an auxiliary outlet by using the outlets property:

			router.navigate([{outlets: {primary: 'path' ,sidebar: 'path'}}]);
			Or also using the routerLink directive


			<a [routerLink]="[{ outlets: { primary: ['path'],sidebar: ['path'] } }]">
			    Products List
			</a>


		Primary and Auxiliary Angular Router Outlets by Example
		-------------------------------------------------------

			So let's say, we want to render a different sidebar component when the user navigates to the /products URL. This way, the ProductListComponent will be rendered in the primary outlet and in the same time the ProductListSidebarComponent will be rendered in the auxiliary sidebar outlet.

			We can easily achieve this scenario by creating the ProductListSidebarComponent component (ng g component ProductListSidebar) and adding the following auxiliary route configuration:

				{ path: "products", component: ProductListSidebarComponent, outlet: "sidebar" }
			

			This is the complete routing configuration for our example:

				import { RouterModule, Routes } from "@angular/router";
				import { ModuleWithProviders } from "@angular/core";
				import { ProductListComponent } from "./product-list/product-list.component";
				import { ProductDetailComponent } from "./product-detail/product-detail.component";
				import { SidebarComponent } from "./sidebar/sidebar.component";
				import { ProductListSidebarComponent } from "./product-list-sidebar/product-list-sidebar.component";

				const routes: Routes = [
					{ path: "products", component: ProductListComponent },
					{ path: "product/:id", component: ProductDetailComponent },
					{
						path: "",
						component: SidebarComponent,
						outlet: "sidebar"
					},
					{
						path: "products",
						component: ProductListSidebarComponent,
						outlet: "sidebar"
					}
				];

			export const routingModule: ModuleWithProviders = RouterModule.forRoot(routes);

			You also need to update the navigation link in our AppComponent:

			<a [routerLink]="[{ outlets: { primary: ['products'],sidebar: ['products'] } }]">
			    Products List
			</a>
			
			This says, when the user clicks on the Products List link. Both routes with the /products path will be activated in the primary and auxiliary sidebar outlets.

			You need to specify all the outlets where you want the navigation to take place including the primary outlet.



	Route Guards
	------------
		- The Angular router’s navigation guards allow to grant or remove access to certain parts of the navigation. 

		- Another route guard, the CanDeactivate guard, even allows you to prevent a user from accidentally leaving a component with unsaved changes.

		- Here are the 4 types of routing guards available:

			# CanActivate:
				- Controls if a route can be activated.
			
			# CanActivateChild:
				- Controls if children of a route can be activated.

			# CanLoad: 
				- Controls if a route can even be loaded. This becomes useful for feature modules that are lazy loaded. They won’t even load if the guard returns false.

			# CanDeactivate: 
				- Controls if the user can leave a route. Note that this guard doesn’t prevent the user from closing the browser tab or navigating to a different address. It only prevents actions from within the application itself.

		can-activate-route.guard.ts
		---------------------------
			import { Injectable } from '@angular/core';
			import { CanActivate, ActivatedRouteSnapshot, RouterStateSnapshot } from '@angular/router';
			import { AuthService } from './auth.service';

			@Injectable()
			export class CanActivateRouteGuard implements CanActivate {

				constructor(private auth: AuthService) {}

				canActivate(route: ActivatedRouteSnapshot, state: RouterStateSnapshot): boolean {
					return this.auth.isUserAuthenticated();
				}
			}


	CanActivate and CanActivateChild
	--------------------------------
		-> In the Angular application in which authentication and authorization is required to navigate a route

		-> CanActivate and CanActivateChild. Both API works in the same way.

		->. CanActivate and CanActivateChild are interfaces and have methods canActivate() and canActivateChild() respectively. These methods return "Boolean" value.

		-> CanActivate is used for "authentication" and CanActivateChild is used for "authorization"

		-> Angular Route interface provides canActivate and canActivateChild properties to configure service class which is implementing CanActivate and CanActivateChild interfaces. 



Angular - Http
--------------

	Http Service will help us fetch external data, post to it, etc, now the request is going to hit a web service or a Web APi,	which will fetch the data from a database and send it back as an HTTP response and the responcse we get form the HTTP service is called an observable.

	In the HTTP protocol describes a set of verbs for each URL. For a given URL we can perform a GET, PUT, POST, DELETE, HEAD and OPTIONS request.

	# GET with data

		getData() {

			let url = 'localhost:8000/api/get`;

			this._http.get(url).subscribe(res => console.log(res.json()));

		}

		GET with query params
		---------------------

			We can pass to the get function a set of optional query parameters as the second argument.


			import {URLSearchParams} from '@angular/http';
				.
				.
				.

			getData() {

				let url = 'localhost:8000/api/get`;

				let search = new URLSearchParams();

				search.set('foo', 'moo');

				search.set('limit', 25);

				this._http.get(url, {search: search}).subscribe(res => console.log(res.json())); 

			}

	# POST with data

		postData(data) {

			let url = 'localhost:8000/api/post`;

			this.http.post(url, {data}).subscribe(res => console.log(res.json()));

		}

	# DELETE

		deleteData() {

			let url = 'localhost:8000/api/post`;

			let search = new URLSearchParams();

			search.set('foo', 'moo');

			search.set('limit', 25);

			this.http.delete(url, {search}).subscribe(res => console.log(res.json()));

		}


	# Promises

		doGetAsPromise() {
			let url = 'localhost:8000/api/get`;

			this.http.get(url)
			.toPromise()
			.then(
				res => console.log(res.json()),
				msg => console.error(`Error: ${msg.status} ${msg.statusText}`) 
			);
		}	


	# Observable 

		doGetAsObservable() {

			let url = 'localhost:8000/api/post`;

			this.http.get(url).subscribe(
				res => console.log(res.json()),
				msg => console.error(`Error: ${msg.status} ${msg.statusText}`)
			);
		}


	# Headers

		HTTP headers are bits of meta-data which the browser attaches to your HTTP requests when it sends them to the server. Things like your IP address, the type of browser you are using and so on are added to your headers.

		doGETWithHeaders() {

			let headers = new Headers();

			headers.append('Authorization', btoa('username:password'));

			let opts = new RequestOptions();

			opts.headers = headers;

			let url = 'localhost:8000/api/get';

			this.http.get(url, opts).subscribe(
				res => console.log(res.json()),
				msg => console.error(`Error: ${msg.status} ${msg.statusText}`)
			);
		}

			Note :
				This is a really poor way to authenticate with your server, we are just using it as an example. We covert username:password to a base64 string and pass that to the server via a header called Authorization


	map operator
	------------
	the map operator that can be used to convert data to the desired fromat 

	catch operator
	--------------
	we can also have a catch operator that works on an observable and that is used to handle exceptions



	Angular - Http Error Handling
	-----------------------------

		catch operator
		--------------
		we can also have a catch operator that works on an observable and that is used to handle exceptions


			add catch operater

				import 'rxjs/add/operator/catch';



		Exapmle
		-------
			import { Injectable } from '@angular/core';
			import {Http, Response } from '@angular.http';

			import 'rxjs/add/operator/map';
			import 'rxjs/add/operator/catch';

			@Injectable()

			export class dataService{

				private _url:string = "apiDatabase/data.json";

				constructor(private _http:Http){}

				myService(){
					return this._http.get(this._url)
						.map((dataResponse:Response)=> dataResponse.json())
						.catch(_errorHandler);
				}

				_errorHandler(error:Response){
					console.error(error);				
				}

			}

	Explain Authentication and Authorization
	----------------------------------------
		- Authentication: The user login credentials are passed to an authenticate API (on the server). On the server side validation of the credentials happens and a JSON Web Token (JWT) is returned. JWT is a JSON object that has some information or attributes about the current user.  Once the JWT is given to the client, the client or the user will be identified with that JWT.

		-Authorization: After logging in successfully, the authenticated or genuine user does not have access to everything. The user is not authorized to access someone else’s data,  he/she is authorized to access some data.

	HttpInterceptors
	----------------
		- HttpInterceptors allow us to modify HTTP requests within our application. 

		-A common use case is to add an Authorization header to each request.

		To implement an interceptor, you’ll want to create a class that’s injectable and that implements HttpInterceptor. The class should define an intercept method to correctly implement HttpInterceptor. The intercept method takes two arguments, req and next, and returns an observable of type 'HttpEvent'.

			- 'req' is the request object itself and is of type HttpRequest.
			- 'next' is the http handler, of type 'HttpHandler'. The 'handler' has a handle method that returns our desired HttpEvent observable.


		# Auth-http-interceptor.ts

			import { Injectable } from '@angular/core';
			import { HttpInterceptor, HttpEvent, HttpHandler, HttpRequest} from '@angular/common/http';
			import { Observable } from 'rxjs/Observable';

			@Injectable()

			export class AuthHttpInterceptor implements HttpInterceptor {
				intercept(req: HttpRequest<any>, next: HttpHandler): Observable<HttpEvent<any>> {
		
					const newRequest = req.clone({
						headers: req.headers.set('Authorization', 'token YOUR-TOKEN-HERE'),
					});
					
					return next.handle(newRequest);

				}
			}



Angular Services
----------------
	Services allow us to create a reusable code and use it every component that needs it. 

	The Services can be injected into components and other services using the dependency injection system. 

	The dependencies are declared in the Module using the Providers metadata. 

	The Angular creates a tree of injector & Providers which resembles the Component Tree. 

	This is called the hierarchical pattern.


	@Injectable() decorator
	-----------------------
		To inject the service into component, Angular provides an Injector decorator : @Injectable().

		a class with a specific purpose.

		1) Implements any business logic (independent and any Component)
		2) Access to shared data
		3) External Interactions (Connection Database)


	Step-1: Create Service 
	-------
	
	-> Create a class decorated with @Injectable()

		import { Injectable } from '@angular/core';

		@Injectable()

		export class ItemService {
			myServiceMsg(){
				return "Hello!, This is Service";
			}
		} 


	Step-2: Use service
	-------
	-> Select Component and import service class

		import { mySevice } from './app.services';

		@Component({
			selecter:'mydiv',
			template:'<h1>{{msg}}</h1>',
			provider:[mySevice],
		})

		export class myDivComponent{

			constructor(private _myMsg:mySevice ){}

			ngOnInit(){
				this.msg = this._myMsg.myServiceMsg();
			}

		}


	
	Dependency injection
	--------------------

		Dependency injection is a coding pattern in which a class receives its dependencies form external sources rather than creating them itself

		Dependency injection is the ability to add the functionality of components at runtime.

		(OR)

		Dependency Injection (DI) is a technique in which we provide an instance of an object to another object, which depends on it. This is technique is also known as “Inversion of Control” (IoC)


	 	# created  ProductService : 
	 	-------------------------
			export class ProductService{
			 
			    public getProducts() {
			 
			        let products:Product[];
			 
			        products=[
			            new Product(1,'Memory Card',500),
			            new Product(1,'Pen Drive',750),
			            new Product(1,'Power Bank',100)
			        ]
			 
			        return products;
			    }
			}

			WithOut Dependency injection
			-----------------------------

			We instantiated the "productService" directly in our component as shown below.

				export class AppComponent{
			    
				    products:Product[];

				    getProducts() {

				        let productService=new ProductService();

				        this.products=productService.getProducts();

				    }
				}

			With Dependency injection
			-------------------------
		export class AppComponent{

		    products:Product[];
		 
		    constructor(private _productService:ProductService) {}

		    getProducts() {
		        this.products=this._productService.getProducts();
		    }

		} 


	Angular Providers
	-----------------
		Reference link -> https://www.concretepage.com/angular-2/angular-2-4-providers-example


		Providers are usually singleton (one instance) objects, that other objects have access to through dependency injection (DI).

 		- Injector injects the objects provided by provider into components and services. 

 		- Only those classes which are configured by providers are available for dependency injection (DI).
 		
 		- Angular provides different types of providers such as class provider, alias provider, value provider and factory provider. 
 		
 		- Injector creates singleton object of a class configured by providers. 
 		
 		- Providers can be configured at module level as well component level. 

 		- If a service class is configured using provider in module then it will be available for all the components configured in module for dependency injection. 

 		- If a service is configured using provider in component then it will be available in current component and its children component up to the bottom component. 

 		- In our application if we have configured a service using providers in root component then it will be available everywhere in the application components and services for dependency injection. 

 		- It is better to configure service using provider only in that component that itself and its children up to the bottom component can use the service for dependency injection. 



 	Example:
		app.component.ts
		----------------
			import { Component } from '@angular/core';
			import { WeatherApiService } from './weather-api.service';
			import { AuthService } from './auth.service';

			@Component({
				...,
				providers: [WeatherApiService, AuthService]
			})
			export class AppComponent {
				constructor( public weatherApi: WeatherApiService, public auth: AuthService ) {}
			}

		app.module.ts
		-------------
		...
		import { WeatherApiService } from './weather-api.service';
		import { AuthService } from './auth.service';

		@NgModule({
			declarations: [
				AppComponent
			],
			imports: [
				...
			],
			providers: [WeatherApiService, AuthService],
			bootstrap: [AppComponent]
		})

		export class AppModule { }


	Class Providers
	---------------
		By default Angular will inject a provider with the same class name and token, but 'useClass' allows to use a different class. For example, the following will provide a service with the Auth token, but the UserAuth class:

			providers: [{ provide: Auth, useClass: UserAuth }]


	Aliased Providers
	-----------------
		If you want to alias an old provider to be handled by a new provider, you can do so with 'useExisting'. This would be useful if, for example, a component needs to be still be using the old provider, but the logic should still be handled by the new provider:

			providers: [{ provide: OldService, useExisting: NewService }]


	Value Providers
	---------------
		Most of the time classes are used as providers, but simple values can also be used instead with useValue:

			const AUTH_CONFIG = {
				apiKey: "...",
				authDomain: "..."
			};

			providers: [{ provide: AuthConfig, useValue: AUTH_CONFIG }]






RxJS Tutorial
-------------

	- import { Observable, Subscription, Subject, ErrorObserver, asapScheduler, pipe, of, from, interval, merge, fromEvent, fromPromise } from 'rxjs';
	
	- import { map, first, filter, scan } from 'rxjs/operators';

	- Renamed Operators 

		do() => tap()

		catch() => catchError()

		finally() => finalize()

		switch() => switchAll()

		throw() => throwError()

		fromPromise() => from()


	The new Angular 'HttpClient' works with 'Observables' by default. Methods such as get(), post(), put() and delete() return an instance of the Observable interface. HTTP requests are only sent when we subscribe to the Observable
	
	This is an example of making an HTTP request

		constructor(private _httpClient:HttpClient){}

		getItems(): Observable<Item[]> {
		   return this._httpClient.get<Item[]>(this.itemUrl);
		}

		We suppose that we've injected the 'HttpClient' class as '_httpClient'.


	Using Observable with AsyncPipe
	-------------------------------
		Angular AsyncPipe subscribes to Observable and returns the emitted data. 

		# For example:

			getItems(): Observable<Item[]> {
			   this.items$ = this._httpClient.get<Item[]>(this.itemUrl);
			}

		The 'items$'' variable is of type 'Observable<Item[]>'.


		After calling the getItems() method on the component we can use the async pipe in the component template to subscribe to the returned Observable:

			<ul>
			  <li *ngFor="let item of items$ | async" >

			  </li>
			</ul>  


	Subscribing to Observables
	--------------------------
		- Observables are used for better support of event handling, asynchronous programming, and handling multiple values. 

		- When you define an Observable to publish some values for a consumer, the values are not emitted until you actually subscribe to the Observable.


	Using the 'map()' Operator
	--------------------------

		The map() operator is similar to the Array.map() method. It lets you map observable responses to other values. 

		# For example:

			import { Observable} from 'rxjs';
			import { map } from 'rxjs/operators';

			getItems(): Observable<Array<any>> {

			  return this.aService.getItems()
			    .pipe(map(response => response.data));
			} 

		The 'getItems()' method returns an Observable. We're using the 'map()' operator to return the data property of the response object. The operator enables us to map the response of the Observable stream to the data value.

		We import the pipeable operator 'map()' from the 'rxjs/operators' package and we use the 'pipe()' method (which takes a variable number of pipeable operators) to wrap to wrap the operator.


	Using the filter() Operator
	---------------------------

		The filter() operator is similar to the Array.filter() method. It lets you filter the observable stream and returns another observable. 

		# For example:

			import { Observable} from 'rxjs';
			import { filter } from 'rxjs/operators';

			filter(): Observable<Array<any>> {

			  return this.aService.getItems()
			    .pipe( filter(response => response.code === 200) );
			}

		We use the filter() operator to only emit a notification to observers of the observable stream when the status code of the HTTP response is 200.



	RxJs Subjects
	-------------
	a subject can emit data, on top of having the capability to be subscribed to. 

		let subject = new Subject<string>();

		// We subscribe to the subject
		subject.subscribe((data) => {
		  console.log("Subscriber got data >>>>> "+ data);
		});

		// We use the subject to emit data
		subject.next("Eureka");

		// Console result: Subscriber got data >>>>> Eureka


	A regular observable does not have the next() method as regular observables are not observers. So that’s the first super power of a subject: Data emission.


	# Subjects are multicast

		The second super power of subjects is that they support multiple subscriptions. In other words, they are multicast.

			Subjects are like EventEmitters: They maintain a registry of many listeners.


				let subject = new Subject<string>();

				subject.subscribe((data) => {
					console.log("Subscriber 1 got data >>>>> "+ data);
				});

				subject.subscribe((data) => {
					console.log("Subscriber 2 got data >>>>> "+ data);
				});

				subject.next("Eureka");

				// Console result:
				// Subscriber 1 got data >>>>> Eureka
				// Subscriber 2 got data >>>>> Eureka

			As a result, you can use a Subject in a service to fetch some data, and send the result to all components that subscribed to that Subject.


		There is one thing I would recommend though: Do not expose the Subject object directly to your components. Instead, return a good old Observable version of it:

		// Don't do that or you subscribers will be able to "mess" with your // subject
		getData(): Subject<Data> {  
		    return this.subject;
		}

		// Do this instead:
		getData(): Observable<Data> {  
		    return this.subject.asObservable();
		}

	Behavior Subjects
	-----------------
		Behavior Subjects are another cool thing about subjects. When you subscribe to a behavior subject, it will give you the last emitted value right away.

			// Behavior subjects need a first value
			let subject = new BehaviorSubject<string>("First value");

			subject.asObservable().subscribe((data) => {
				console.log("First subscriber got data >>>>> "+ data);
			});

			subject.next("Second value")

			// Console result:
			// First subscriber got data >>>>> First value
			// First subscriber got data >>>>> Second value

	Replay Subjects
	---------------
		Replay Subjects keep a given number of historical values so that those values can be replayed to new subscribers.

			// We tell the ReplaySubject how many values should be kept in      // history

			let subject = new ReplaySubject<string>(2);

			subject.next("First value");
			subject.next("Second value");
			subject.next("Third value");

			subject.asObservable().subscribe((data) => {
				console.log("First subscriber got data >>>>> "+ data);
			});

			subject.next("Fourth value");

			//Console result:
			// First subscriber got data >>>>> Second value
			// First subscriber got data >>>>> Third value
			// First subscriber got data >>>>> Fourth value



	Angular - Promise vs Observable
	-------------------------------

		A Promise handles a 'single event' when an async operation completes or fails.

		An Observable allows to pass 'one or more events' where the callback is called for each event.

		Often Observable is preferred over Promise because it provides the features of Promise and more.

		Observable also has the advantage over Promise to be cancelable.

		Promises vs Observables
		-----------------------

			Promises:
			---------
				-> returns a single value
				-> not cancellable
				-> more readable code with try/catch and async/await
				
			Observables:
			------------
				-> works with multiple values over time
				-> cancellable
				-> supports map, filter, reduce and similar operators
				-> proposed feature for ES 2016
				-> use Reactive Extensions (RxJS)
				-> an array whose items arrive asynchronously over time

		(OR)


		1. 	Observable is a more powerful way of handling HTTP asynchronous requests. Whereas, 
		A promise handles a single event when an asynchronous operation completes or fails.

		2. An observable is like a stream which allows passing zero or more events where the callback is called for each event. Whereas, A promise eventually calls the success or failed callback even when you don’t need the notification or the result it provides anymore.

		3. Observable works with multiple values for a particular time. Whereas, Promises works with and even returns a single value at a time.

		4. Observables can be canceled. Whereas, Promises cannot be canceled.

		5. Observable supports map, filter, reduce and similar operators. Whereas, Promises have more readable codes with try/catch and async/await.

		6. In observable, one operator ‘retry’ can be used to retry whenever needed. Whereas, Promises cannot be retried. A promise should have access to the original function that returned the promise in order to have a retry capability.



	HTTP, Observable and Rxjs
	-------------------------

		HTTP, Observable
		----------------

			1. HTTP Get request from AppService

			2. Receive the observable and cast it into an employee array

			3. Subscribe to the Observable from ComponetOne and ComponentTwo

			4. Assign the employee arry to a local variable


		Rxjs
		----
			- Reacive Extensions for JavaScript
			- External library to work with Observable 



	Observable and Subscribe
	------------------------

		- Observable belogs to RxJS library. Observables are used for better support of event handling, asynchronous programming, and handling multiple values. When we send and receive data over HTTP we need to deal it asynchronously because fetching data over HTTP may take time. Observable is subscribed by using async pipe or by using subscribe method

		- Some methods of Observable class are subscribe, map, mergeMap, switchMap, debounceTime, of, retry, catch, throw ....etc.



		Step-1) Make 'HTTP' get call from EmpService

		Step-2)Receive the observable and map it (to JSON Format)

		Step-3) Subscrible to the 'obsevable' form the Components that require this data

		Step-4) we are going to assign that receive the data to a local variable in the view so that we can display it to the user

		Rxjs - Reactive Extensions for JavaScript

		this is an external library that we use to work with observables and this is not the react from Facebook, that's a completely different thing, this is just an external library to work with observables



		Step-1) Make 'HTTP' get call from EmpService
		--------------------------------------------

			-> first import 'HttpModule' in 'app.module.js'

				import { HttpModule } from '@angular/http';


			-> second import "Http" in 'serviceComponent.ts'

				import { Injectable } from '@angular/core';					
				import {Http} from '@angular.http';

				@Injectable()

				export class dataService{
					private _url:string = "apiDatabase/data.json";

					constructor(private _http:Http){}

					myService(){
						return this._http.get(this._url);
					}
				}

			-> Third create 'JSON' file

				[
					{"id":100,"name":"Mahesh","desc":"UI"},
					{"id":200,"name":"Suresh","desc":"UX"},
					{"id":300,"name":"Rajech","desc":"Java"},
					{"id":400,"name":"Mukesh","desc":"PHP"}
				];


		Step-2) Receive the observable and map it (to JSON Format)
		----------------------------------------------------------

			-> import "Response" from Http
			-> import the 'map' operator from Rxjs 

				import 'rxjs/add/operator/map';

			-> call map operator (useing arrow function and arguments)


				import { Injectable } from '@angular/core';
				import { Http, Response } from '@angular.http';
				import 'rxjs/add/operator/map';

				@Injectable()


				export class dataService{

					private _url:string = "apiDatabase/data.json";
					constructor(private _http:Http){}

					myService(){
						return this._http.get(this._url)
							.map((dataResponse:Response)=> dataResponse.json());
					}
				}


		Step-3 and  Step-4
		------------------
		-> Subscrible to the 'obsevable' form the Components


			import { Component, OnInit } from '@angular/core';
			import { dataService } from './app.services';

			@Component({
				selector: 'app-root',
				templateUrl:'./app.component.html',
				styleUrls:['./app.component.css'],
				providers:[dataService]
			})

			export class AppComponent implements OnInit {

				empDatalist:any;

				constructor(private _empService:dataService){}

				ngOnInit(){
					this._empService.myService().subscribe(
							resEmpData => this.empDatalist = resEmpData
						);
				}

			}


		<ul *ngFor="let emp of empDatalist">
			<li>{{emp.id}} {{emp.name}} {{emp.desc}}</li>
		</ul>



Angular Animations
------------------
	- Animation is defined as the transition from an initial state to a final state. 
	- It is an integral part of any modern web application. 
	- Animation not only helps us to create a great UI but it also makes the application interesting and fun to use. 
	- A well-structured animation keeps the user glued to the application and enhances the user experience.

	Understanding Angular Animation States
	--------------------------------------
		Animation is a transition from one state of the element to another state. Angular defines three different states for an element.

		#Void state:
			The void state represents the state of an element which is not a part of the DOM. This state occurs when an element is created but not yet placed in the DOM or the element is removed from the DOM. This state is useful when we want to create animations while adding or removing an element from our DOM. To define this state in our code we use the keyword void.

		# The wildcard state: 
			This is also known as the default state of the element. The styles defined for this state is applicable to the element regardless of its current animation state. To define this state in our code we use the * symbol.

		# Custom state: 
			This is the custom state of the element and it needs to be defined explicitly in the code. To define this state in our code we can use any custom name of our choice.


	Angular Animation Syntax
	------------------------
	import { BrowserAnimationsModule } from '@angular/platform-browser/animations';

	import { trigger, style, transition, animate, group } from '@angular/animations';

	Ex-1:
	----
		@Component({
			// other component properties.
			animations: [
				trigger('triggerName'), [
					state('stateName', style())
					transition('stateChangeExpression', [Animation Steps])
				]
			]
		})

	Ex-2:
	----
		@Component({
			animations: [
				trigger('changeDivSize', [
					state('initial', style({
						backgroundColor: 'green',
						width: '100px',
						height: '100px'
					})),
					state('final', style({
						backgroundColor: 'red',
						width: '200px',
						height: '200px'
					})),
					transition('initial=>final', animate('1500ms')),
					transition('final=>initial', animate('1000ms'))
				]),
			]
		})


		#class
			currentState = 'initial';

			changeState() {
				this.currentState = this.currentState === 'initial' ? 'final' : 'initial';
			}


		#html
			<button (click)="changeState()">Change Size</button>
			<br />
			<div [@changeDivSize]=currentState></div>


	Ex-3
	----
		@Component({
			animations: [
				trigger('balloonEffect', [
					state('initial', style({
						backgroundColor: 'green',
						transform: 'scale(1)'
					})),
					state('final', style({
						backgroundColor: 'red',
						transform: 'scale(1.5)'
					})),
					transition('final=>initial', animate('1000ms')),
					transition('initial=>final', animate('1500ms'))
				])
			]
		})

		# Html
			<div (click)="changeState()" style="width:100px; height:100px; border-radius:100%; margin: 3rem; background-color: green" [@balloonEffect]=currentState></div>


	Ex-4
	----
		animations: [
			trigger('itemAnim', [
				transition(':enter', [
					style({transform: 'translateX(-100%)'}),
					animate(350)
				]),
				transition(':leave', [
					group([
						animate('0.2s ease', style({
							transform: 'translate(150px,25px)'
						})),
						animate('0.5s 0.2s ease', style({
							opacity: 0
						}))
					])
				])
			])
		]

	# Html
		<input #itemInput (keyup.enter)="addItem(itemInput.value); itemInput.value=''">

		<button (click)="addItem(itemInput.value); itemInput.value=''"> Add </button>

		<ul *ngIf="items">
			<li *ngFor="let item of items" (click)="removeItem(item)" [@itemAnim]>{{ item }}</li>
		</ul>



Explain lazy loading in Angular
-------------------------------

	- Lazy loading is a module which is used to decrease the start-up time. 

	- When lazy is used, then our system application does not need to load everything at once. 

	- It only needs to load what the user expects to see when the application first loads. 

	- The modules which are lazily loaded will only be loaded when the user navigates to their routes. 

	-Lazy loading improves the performance of our system applications. 

	- It keeps the initial payload small and these smaller payloads lead to faster download speeds. It helps in lowering the resource cost especially on mobile networks. 

	- If a user doesn’t visit a section of the application, they won’t ever download those resources. 

	- The concept of lazy loading in angular requires us to format the application in a certain way. 
	
	- All the assets that are to be lazy loaded should be added to its own module. 

	- Lazy loading is setup in the main routing file. 

	- Lazy loading overcomes the problem of slow loading of applications in their own way which hence improves the loading time of the application.

	
	Lazy loading can be done only in four steps: –

	- Update your route file
	- Install angular-router-loader and add the loader to your webpack configuration file.
	- Define the lazy routes
	- Import the routes to the module.	


		# shop/shop.module.ts

			import { NgModule } from '@angular/core';
			import { CommonModule } from '@angular/common';
			import { Routes,RouterModule RouterModule } from '@angular/router';

			import { CartComponent } from './cart/cart.component';
			import { CheckoutComponent } from './checkout/checkout.component';
			import { ConfirmComponent } from './confirm/confirm.component';

			const routes: Routes = [
				{ path: '', component: CartComponent },
				{ path: 'checkout', component: CheckoutComponent },
				{ path: 'confirm', component: ConfirmComponent },
			];

			@NgModule({
				imports: [
					RouterModule.forChild(routes)
				],
				declarations: [CartComponent, CheckoutComponent, ConfirmComponent]
			})
			export class LegalModule { }


		# routing.ts

			import { Routes } from '@angular/router';

			// BoutiqueComponent is a normal, eager loaded component
			import { BoutiqueComponent } from './boutique/boutique.component';

			export const routes: Routes = [
				{ path: '', component: BoutiqueComponent, pathMatch: 'full' },
				//Lazy Module
				{ path: 'shop', loadChildren: './shop/shop.module#ShopModule' },
				{ path: '**', component: BoutiqueComponent }
			];



	
	With out lazy loading
	---------------------
		By defulat, Angular load all the components any time we launch the application, all components are inportes from app.module.ts and are added into declarations array, this means that angular will load all of this components in the declarations array when stating up the application

	With lazy loading 
	-----------------
		Lazy Loading loads only what we need to use when frst starting up the application. If user navigate to a new page, then the component for that paqe will load immediately. However, this does not mean that it loads the component all the time we change page. In fact, it loads only for the first visit page, it will not load when we revisit that page again.



What is Angular Component lifecycle hooks
-----------------------------------------
	the life cycle hooks are the methods that angular invokes on directives and components as it creates, changes, and destroys them. Using life-cycle hooks we can fine-tune the behaviour of our components during creation, update, and destruction.

	For example

		- When component is initialized, Angular invokes ngOnInit
		- When a component’s input properties change, Angular invokes ngOnChanges
		- When a component is destroyed, Angular invokes ngOnDestroy

	Angular lifecycle hooks

		- ngOnChanges
		- ngOnInit
		- ngDoCheck
			- ngAfterContentInit
			- ngAfterContentChecked
			- ngAfterViewInit
			- ngAfterViewChecked
		- ngOnDestroy


	ngOnChanges
	-----------
		The Angular invokes this life cycle hook whenever any data-bound property of the component or directive changes.

		The parent component can communicate with the child component, if child component exposes a property decorated with @Input decorator. This hook is invoked in the child component, when the parent changes the Input properties. We use this to find out details about which input properties have changed and how they have changed.


		# Note :
			- Called before ngOnInit() and whenever one or more data-bound input properties change.
			
			
			ngOnChanges(changes: SimpleChanges) {
				// changes.prop contains the old and the new value...
			}
		

	ngOnInit
	--------
		This hook is called when the component is created for the first time. This hook is called after the constructor and first ngOnChanges hook.

		This is a perfect place where you want to add any initialisation logic for your component.

		Note that ngOnChanges hook is fired before ngOnInit. Which means all the input properties are available to use when the ngOnInit is hook is called

		This hook is fired only once

		This hook is fired before any of the child directive properties are initialized.

		# Note :
			- Called once, after the first ngOnChanges().


	ngDoCheck
	---------
		This event is called immediately after the ngOnInit. There after it is called on every change made to the component properties,  When ever the event is raised or any operations that may result in change in value of properties.

		Basically This hook is executed for every change detection in cycles even there is no properties change

		The Angular ngOnChanges hook does not detect all the changes made to the input properties. It Only detects when the Input Property is a primitive type or  reference to the Input property changes

		This hook is provided so as to Implement custom change detection, whenever Angular fails to detect the changes made to Input properties

		(OR)
			- Called during all change detection runs
			- A run through the view by Angular to update/detect changes

		# Note:
			- Called during every change detection run, immediately after ngOnChanges() and ngOnInit().


	ngAfterContentInit
	------------------
		This Life cycle hook is called after the Component’s content has been fully initialized. This hook is called after the properties marked with ContentChild and ContentChildren are fully initialized

		The Angular Component can include the external content from the child Components by transcluding them using the <ng-content></ng-content> element. This hook is fired after these projected contents are initialized

		This is a component only hook and Called Only once.

		(OR)
			- Called only once after first ngDoCheck()
				* Called after the first run through of initializing content

		# Note:
			- Respond after Angular projects external content into the component's view / the view that a directive is in.

			- Called once after the first ngDoCheck().


	ngAfterContentChecked
	---------------------
		This life cycle hook is called after the Components Content is checked by the Angular’s Change detection module. It is called immediately after ngAfterContentInit and after every subsequent ngDoCheck().

		This is a component only hook

		(OR)
			- Called after every ngDoCheck()
			- Waits till after ngAfterContentInit() on first run through

		# Note:
			- Respond after Angular checks the content projected into the directive/component.

			- Called after the ngAfterContentInit() and every subsequent ngDoCheck().


	ngAfterViewInit
	---------------
		Similar to ngAfterContentInit, but invoked after Angular initializes the component’s views and all its child views.  This is  Called once after the first ngAfterContentChecked.

		A component-only hook.

		(OR)
			- Called after Angular initializes component and child component content.
			- Called only once after view is initialized

		# Note:
			- Respond after Angular initializes the component's views and child views / the view that a directive is in.

			- Called once after the first ngAfterContentChecked().


	ngAfterViewChecked
	------------------
		The Angular fires this hook after it checks the component’s views and child views. This event is fired after the ngAfterViewInit and after that for every subsequent ngAfterContentChecked hook.

		This is a component only hook.
		
		(OR)
			- Called after all the content is initialized and checked. (Component and child components).
			- First call is after ngAfterViewInit()
			- Called after every ngAfterContentChecked() call is completed

		# Note:
			- Respond after Angular checks the component's views and child views / the view that a directive is in.

			- Called after the ngAfterViewInit and every subsequent ngAfterContentChecked().

	ngOnDestroy
	-----------
		This hook is called just before the Component/Directive instance is destroyed by Angular

		You can Perform any cleanup logic for the Component here. This is the correct place where you would like to Unsubscribe Observables and detach event handlers to avoid memory leaks.
		
		(OR)		
			- Used to clean up any necessary code when a component is removed from the DOM.
				* Fairly often used to unsubscribe from things like services.
			- Called only once just before component is removed from the DOM.

		# Note:
			- Cleanup just before Angular destroys the directive/component. Unsubscribe Observables and detach event handlers to avoid memory leaks.

			- Called just before Angular destroys the directive/component.


	The Order of Execution of Life Cycle Hooks
	------------------------------------------
		The Angular hooks are executed in this order:

		# When the Component is Created

			- OnChanges
			- OnInit
			- DoCheck
			- AfterContentInit
			- AfterContentChecked
			- AfterViewInit
			- AfterViewChecked

		# When the Component with Child Component is created

			- OnChanges
			- OnInit
			- DoCheck
			- AfterContentInit
			- AfterContentChecked
				- Child Component -> OnChanges
				- Child Component -> OnInit
				- Child Component -> DoCheck
				- Child Component -> AfterContentInit
				- Child Component -> AfterContentChecked
				- Child Component -> AfterViewInit
				- Child Component -> AfterViewChecked
			- AfterViewInit
			- AfterViewChecked

		# After The Component is Created

			- OnChanges
			- DoCheck
			- AfterContentChecked
			- AfterViewChecked



What is CLI, Write the CLI command to generate 
----------------------------------------------
	Command Line Interface (CLI) can be used to create our angular application. It also helps in creating a unit and end-to-end tests for the application.

		Component 	-	ng generate component [name]

		Directive 	-	ng generate directive [name]

		Pipe 		-	ng generate pipe [name]

		Service 	-	ng generate service [name]

		Class 		-	ng generate class [name]

		Guard 		-	ng generate guard [name]

		Interface 	-	ng generate interface [name] <type>

		Enum 		-	ng generate enum [name]

		Module 		-	ng generate module [name]



What is AOT Compilation?
------------------------
	- Every angular application gets compiled internally. 

	- The angular compiler takes javascript code, compiles it and produces javascript code again. 

	- Ahead-of-Time Compilation does not happen every time or for every user, as is the case with Just-In-Time (JIT) Compilation.



Angular - Unit Testing
----------------------
	https://codecraft.tv/courses/angular/unit-testing/jasmine-and-karma/#_jasmine


	Jasmine
	-------
		Jasmine is a javascript testing framework that supports a software development practice called Behaviour Driven Development (BDD). It’s a specific flavour of Test Driven Development (TDD).

		Jasmine, and BDD in general, attempts to describe tests in a human readable format so that non-technical people can understand what is being tested. However even if you are technical reading tests in BDD format makes it a lot easier to understand what’s going on.

		For example :

			# test.ts

				function helloWorld() {
					return 'Hello world!';
				}		
			
			# test.spec.ts (We would write a jasmine test spec like so:)
			
				describe('Hello world', () => { 
					it('says hello', () => { 
						expect(helloWorld()).toEqual('Hello world!'); 
					});
				});
				

		# describe 
			- The describe(string, function) function defines what we call a Test Suite, a collection of individual Test Specs.

		# it 
			- The it(string, function) function defines an individual Test Spec, this contains one or more Test Expectations.

		# expect
			- The expect(actual) expression is what we call an Expectation. In conjunction with a Matcher it describes an expected piece of behaviour in the application.

		# matcher
			- The matcher(expected) expression is what we call a Matcher. It does a boolean comparison with the expected value passed in vs. the actual value passed to the expect function, if they are false the spec fails.





	Built-in matchers
	-----------------
		Jasmine comes with a few pre-built matchers like so:

		expect(array).toContain(member);
		expect(fn).toThrow(string);
		expect(fn).toThrowError(string);
		expect(instance).toBe(instance);
		expect(mixed).toBeDefined();
		expect(mixed).toBeFalsy();
		expect(mixed).toBeNull();
		expect(mixed).toBeTruthy();
		expect(mixed).toBeUndefined();
		expect(mixed).toEqual(mixed);
		expect(mixed).toMatch(pattern);
		expect(number).toBeCloseTo(number, decimalPlaces);
		expect(number).toBeGreaterThan(number);
		expect(number).toBeLessThan(number);
		expect(number).toBeNaN();
		expect(spy).toHaveBeenCalled();
		expect(spy).toHaveBeenCalledTimes(number);
		expect(spy).toHaveBeenCalledWith(...arguments);



	Setup and teardown
	------------------
		Sometimes in order to test a feature we need to perform some setup, perhaps it’s creating some test objects. Also we may need to perform some cleanup activities after we have finished testing, perhaps we need to delete some files from the hard drive.

		These activities are called setup and teardown (for cleaning up) and Jasmine has a few functions we can use to make this easier:

		beforeAll
			- This function is called once, before all the specs in describe test suite are run.

		afterAll
			- This function is called once after all the specs in a test suite are finished.

		beforeEach
			- This function is called before each test specification, it function, has been run.

		afterEach
			- This function is called after each test specification has been run.



	We might use these functions like so:

		describe('Hello world', () => {

			let expected = "";

			beforeEach(() => {
				expected = "Hello World";
			});

			afterEach(() => {
				expected = "";
			});

			it('says hello', () => {
				expect(helloWorld()).toEqual(expected);
			});

		});


	Karma
	-----
		Karma is a browser test runner.

		The idea is that browsers do not have natively a concept of loading tests files, running them, and reporting results. What karma does is (roughly) :

		starting a small web server to serve "client-side" javascript files to be tested (1)
		also serve the "client-side" javascript files with the tests (or Specs, as they're often called) (2)
		serve a custom web page that will run javascript code for the tests (3)
		start a browser to load this page (4)
		report the results of the test to the server (5)
		karma can then again report the results to text files, the console, anything your CI server likes, etc...
		

		Looking at each part :

			(1) Those files will be your actual js files ; you will tell karma how to load them. If you use requirejs, there is a karma plugin, and some config is needed.

			(2) Those tests can be written in a variety of Javascript testing framework (Jasmine, QUnit, Mocha) ; this is JS code that is run in the browser.

			(3) The custom web page will be a bit different for each testing framework ; this is why karma has plugins for different frameworks.

			(4) Karma can launch the page in many browsers (FF, Chrome, or headless browsers like PhantomJs.)

			(5) Reporting to karma is, again, framework-dependant, and dealt with karma plugins.


		Karma can be used for both unit test (with jasmine / qunit / whatever) and integration tests (which will use another API, like webdriver, to drive the browser)



Building a Real Time Search in Angular With RxJS
------------------------------------------------

	https://alligator.io/angular/real-time-search-angular-rxjs/









Angular Update Guide | 4.2 -> 6.1 for Basic Apps
------------------------------------------------

	- Faster and Compact

	- Pipe 

	- View Engine Improvements

	- Typescript verstion

	- *ngIf and *ngFor Improvements

	- Rename 

		template => ng-template

		do() => tap()

		catch() => catchError()

		finally() => finalize()

		switch() => switchAll()

		throw() => throwError()

		fromPromise() => from()

	- witch from "HttpModule" and the "Http" service to "HttpClientModule" and the "HttpClient"

	- RxJS 

	- exportAs

	- Refistering Service Provider (providerIn)

	- New Router Lifecyle

	- ngModelChange






Angular 4
---------
	
	# Smaller & Faster Apps 
		- Angular 4 applications is smaller & faster in comparison with Angular 2.
	
	# View Engine:
		- In Angular 4, a lot of improvements made to reduce the size of the AOT (Ahead-of-time) compiler generated code.
		- improved the compilation time. These changes reduce around 60% size in most cases.
	
	# TypeScript 
		- In Angular 2 only TypeScript 1.8 version was supported, whereas, in Angular 4, it supports TypeScript 2.1 and 2.2 compatibility, which means now we can use all new features supported in TypeScript 2.1 and TypeScript 2.2 can be used in Angular 4 application.

	# Animation Package
		Animations now have their own package i.e. @angular/platform-browser/animations

	# Improvement - *ngIf and *ngFor.
		- NgIf with Else
		- In Angular 4, else block newly introduced. I mean, along with *ngif, we can use else block as well. 

	# Template 
		- The template is now ng-template. You should use the "ng-template" tag instead of "template". Now Angular has its own template tag that is called "ng-template".

		-> Angular 2

			<div *ngIf="yourCondition">  
			    <h2>Condition true!</h2>  
			</div>  

			<div *ngIf="!yourCondition">  
			    <h2>Condition false!</h2>  
			</div>  

		-> Angular 4

			<div *ngIf="yourCondition; else myFalsyTemplate">  
			    <h2>Condition true!</h2>  
			</div>  

			<ng-template #myFalsyTemplate>  
			    <h2>Condition false!</h2>  
			</ng-template> 


	# AS keyword 
		– A new addition to the template syntax is the "as keyword" is use to simplify to the "let" syntax.
		
		<div *ngFor="let user of users | slice:0:2 as total; index as = i">
		    {{i+1}}/{{total.length}}: {{user.name}}
		</div>
		
		- async

			<div *ngIf="users | async as usersModel">
			    <h2>{{ usersModel.name }}</h2> <small>{{ usersModel.age }}</small>
			</div>

	# Pipes
		- Angular 4 introduced a new "titlecase" pipe "|" and use to changes the first letter of each word into the uppercase. 

		The example as,
			<h2>{{ 'anil singh' | titlecase }}</h2> //Anil Singh


	# Http 
		- Adding search parameters to an "HTTP request" has been simplified as,

		//Angular 4 -
			http.get(`${baseUrl}/api/users`, { params: { sort: 'ascending' } });

		//Angular 2-
			const params = new URLSearchParams();
			params.append('sort', 'ascending');
			http.get(`${baseUrl}/api/users`, { search: params });


	# Service
		- A new service has been introduced to easily get or update "Meta Tags" i.e.

		@Component({
		    selector: 'users-app',
		    template: `<h1>Users</h1>`
		})
		export class UsersAppComponent {
		    constructor(meta: Meta) {
		        meta.addTag({ name: 'Blogger', content: 'Anil Singh' });
		    }
		}

	# Router 
		- A new interface “paramMap” and “queryParamMap” has been added and it introduced to represent the parameters of a URL. 


	# CanDeactivate 
		- This “CanDeactivate” interface now has an extra (optional) parameter and it is containing the next state.



Angular 5
---------
	- When Angular 5 was released, it came with a whole bunch of new features, service improvements, and bug fixes from version 4. 

	- They have added very interesting features like the main focus of Angular version 5 is to make angular faster, with improved loading time as well as execution time. 


	- HttpClient, HttpClientModule

		Version 4.3 was launched with HttpClient within @angular/common as a smaller,

		4.3 @angular/HTTP

		5.0 @angular/common/HTTP


	- Preserve Whitespace

		In earlier versions of Angular, unnecessary new lines, tabs and white spaces were created during the build. With the new Angular 5, one can now choose whether or not to restrict newlines, tabs, and white spaces coming from your components and your application.

		If you want to restrict them only for DemoComponent  then below is the sample code,

			@Component({ 
				templateUrl: 'demo.component.html', 
				preserveWhitespaces: false 
			} 

			export class demoComponent {}

		If you want to restrict them throughout the application level then below is the sample code in tsconfig.json file.

			"angularCompilerOptions": { 
				"preserveWhitespaces": false 
			}


Angular 6
---------
	# ng update & ng add

		- ng update, updating an Angular app is now just a command away

			$ ng update @angular/cli
			$ ng update @angular/core
			$ ng update @angular/material
			$ ng update rxjs
		
		- ng add, 3rd-party libraries can create their own schematics for it.
			
			$ ng add @angular/material

	# Other CLI changes
		Angular projects that use the CLI historically had a configuration file called '.angular-cli.json'. With version 6 of the CLI, this file is now renamed to 'angular.json' and its structure also changes.

	# TypeScript 2.7 & RxJS 6

	// creation and utility methods
		import { Observable, Subject, pipe } from 'rxjs';

	// operators all come from `rxjs/operators`
		import { map, takeUntil, tap } from 'rxjs/operators';


		// before
			myObs
				.do(console.log)
				.map(x => x * 2)
				.subscribe(x => {
					console.log('Value is', x);
				});

		// after
			myObs
				.pipe(
					tap(console.log),
					map(x => x * 2)
				)
				.subscribe(x => {
					console.log('Value is', x);
				});


	Ex-2
		// before
			this.myObs
				.do(x => console.log('The do operator is the do operator!'))
				.filter(x => x.length > 8)
				.map(x => x.toUpperCase())
				.subscribe(x => console.log(x));

		// after
		this.myObs
			.pipe( 
				tap(x => console.log('The do operator is now tap!')),
				filter(x => x.length > 8),
				map(x => x.toUpperCase())
			)
			.subscribe(x => console.log(x));





1. RxJS

	Angular 5
	---------
		import { Observable } from 'rxjs/Observable';
		import { Subject } from 'rxjs/Subject';
		import { of } from 'rxjs/observable/of';
		import 'rxjs/add/operator/catch';
		import 'rxjs/add/observable/throw';

	Angular 6
	---------
		import {throwError as observableThrowError, Observable, Subject, pipe , of } from 'rxjs';
		import { tap, catchError, map } from 'rxjs/operators';



	Example-1
	---------
		@Injectable()
		export class EmployeeService {
			getEmployees(): Observable<IEmployee[]>{
				return this.http.get<IEmployee[]>(this._url)
						
						//Angular 5
						.map(res => res.json())
						.catch(this.errorHandler);
						
						//Angular 6
						.pipe(map(data => alert(JSON.stringify(data))) , catchError(this.errorHandler))

			}
			
			errorHandler(error: HttpErrorResponse){
				//Angular 5
				return Observable.throw(error.message || "Server Error");

				//Angular 6
				return observableThrowError(error.message || "Server Error");
			}
		 }

	Example-2
	---------
		Angular 5
		---------
			source.map(x => x + x)
				.mergeMap(n => of(n+1, n+2)
					.filter(x => x % 1 == 0)
					.scan( (acc, x)=> acc + x, 0)
				)
				.catch(err => of('error found'))
				.subscribe(printResult)

		Angular 6
		---------
			source.pipe(
				map(x => x + x),
				mergeMap(n => of(n+1, n+2).pipe(
					filter(x => x % 1 == 0),
					scan( (acc, x)=> acc + x, 0)
				)),
				catchError(err => of('error found'))
			).subscribe(printResult)


	Example
	-------
		Angular 5
		---------
			source			  
			  .map(data  => { return data.map( res => ({ title:res.title, body:res.body })) })
			  .catch( error => { return Observable.throw('Something went wrong') } )
			  .subscribe( transformeData => this.blogPosts = transformeData )

		Angular 6
		---------
			source.pipe(
				filter( data => data.price > 30),
				map( data  => { return data.map( res => ({ title:res.title, body:res.body })) })
			  	catchError( error => { return observableThrowError(error.message || "Server Error"); } )
			).subscribe( transformeData => this.blogPosts = transformeData )

	Example
	-------
		Angular 5
		---------
			source
			  .filter(quote => quote.price > 30)
			  .map(quote => quote.price)

		Angular 6
		---------
			source.pipe(
				filter(quote => quote.price > 30),
				map(quote => quote.price),
			)

	Example-3
	---------
		# Catching Rejections

			this.http.post(`${ BASE_URL }/auth/login`, payload)
				.map(response => response.json())
				.subscribe(
					authData => this.storeToken(authData.id_token),
					(err) => console.error(err),
					() => console.log('Authentication Complete')
				);
			}

		# Catch and Release

			search(term: string) {

			    return this.http.get('https://api.spotify.com/v1/dsds?q=' + term + '&type=artist')
			    	.map((response) => response.json())
			     	.catch((e) => {
			       		return Observable.throw(
			          		new Error(`${ e.status } ${ e.statusText }`)
			        	);
			      	});

			  }

		# Cancel a Request

			search() {

				const request = this.searchService.search(this.searchField.value)
					.subscribe(
						result => { this.result = result.artists.items; },
						err => { this.errorMessage = err.message; },
						() => { console.log('Completed'); }
					);

					request.unsubscribe();
			}

		# Retry

			There are times when you might want to retry a failed request. For example, if the the user is offline you might want to retry a few times or indefinitely.

			Use the RxJS retry operator. It accepts a retryCount argument. If not provided, it will retry the sequence indefinitely.

			search(term: string) {

				let tryCount = 0;

				return this.http.get('https://api.spotify.com/v1/dsds?q=' + term + '&type=artist')
					.map(response => response.json())
					.retry(3);

			}

		# flatMap 

			By using flatMap we can transform our event stream (the keypress events on the text field) into our response stream (the search results from the HTTP request).


				constructor(private searchService:SearchService, private fb:FormBuilder) {
					
					this.searchField = new FormControl();
					this.coolForm = fb.group({search: this.searchField});

					this.searchField.valueChanges
						.debounceTime(400)
						.flatMap(term => this.searchService.search(term))
						.subscribe((result) => {
							this.result = result.artists.items
						});
				}


2. interface
	
	//Angular 5
		export interface IEmployee {
		    id: number,
		    name: string,
		    age: number
		} 
		
	//Angular 6
		export interface IEmployee {
		    id: number;
		    name: string;
		    age: number;
		}



1.
	Angular 5
	---------
		<input [(ngModel)]="name" (ngModelChange)="onChange($event)">

		onChange(value){
			console.log(value)
		}


	Angular 6
	---------
		<input #modelDir="ngModel" [(ngModel)]="name" (ngModelChange)="onChange(modelDir)">

		onChange(ngModel:NgModel){
			console.log(ngModel.value)
		}



List of Modules
---------------
	- NgModule (Main Module)
	- BrowserModule
	- BrowserAnimationsModule
	- HttpClientModule
	- RouterModule
	- FormsModule
	- ReactiveFormsModule
	- BrowserTestingModule
	- CommonModule


List import Paths
-----------------
	Core:
		- import { 
			NgModule, 
			Injectable, 
			ErrorHandler,
			Component,
			Output, 
			Input, 
			Pipe,
			Attribute,
			Directive,
			AfterViewInit, 
			ElementRef,
			Renderer,
			ViewChild
			AfterContentChecked, 
			AfterContentInit, 
			AfterViewChecked, 
			AfterViewInit ,  
			DoCheck, 
			OnChanges, 
			OnDestroy, 
			OnInit,
			SimpleChanges
		} from '@angular/core';


	HTTP:
		- import { HttpClient, HttpErrorResponse, HttpHandler, HttpHeaders, HttpRequest, HttpHeaderResponse, HttpInterceptor } from '@angular/common/http';

		- import { CommonModule } from '@angular/common'

	ROUTER:
		- import { 
			Routes, 
			RouterModule, 
			Router, 
			ActivatedRoute, 
			Params, 
			CanActivate, 
			ActivatedRouteSnapshot, 
			RouterStateSnapshot, 
			CanDeactivate
		} from '@angular/router';

	Forms:
		- import { FormBuilder, FormGroup, Validators } from '@angular/forms';

	Rxjs:
		- import { 
			Observable, 
			Subscription, 
			Subject, 
			ErrorObserver, 
			asapScheduler,
			pipe, 
			of, 
			from, 
			interval,
			merge, 
			fromEvent, 
			fromPromise 
		} from 'rxjs';


		- import { map, first, filter, scan } from 'rxjs/operators';


	Animations:
		- import { BrowserAnimationsModule } from '@angular/platform-browser/animations';
		
		- import { 
			trigger, 
			CSSstyle, 
			state, 
			style, 
			transition,
			Timetransition, 
			animate, 
			somekeyframes, 
			generatedquery, 
			stagger 
		} from '@angular/animations';



List of Decorator's
-------------------

	1. import { NgModule } from '@angular/core';
		@NgModule({ 
			providers?: Provider[]
			declarations?: Array<Type<any>|any[]>
			imports?: Array<Type<any>|ModuleWithProviders|any[]>
			exports?: Array<Type<any>|any[]>
			entryComponents?: Array<Type<any>|any[]>
			bootstrap?: Array<Type<any>|any[]>
			schemas?: Array<SchemaMetadata|any[]>
			id?: string
		})

	2. import { Attribute } from '@angular/core';

		@Attribute({ 
			attributeName?: string
		})


	3. import { Component } from '@angular/core';

		@Component({ 
			changeDetection?: ChangeDetectionStrategy
			viewProviders?: Provider[]
			moduleId?: string
			templateUrl?: string
			template?: string
			styleUrls?: string[]
			styles?: string[]
			animations?: any[]
			encapsulation?: ViewEncapsulation
			interpolation?: [string, string]
			entryComponents?: Array<Type<any>|any[]>
			preserveWhitespaces?: boolean
			// inherited from core/Directive
			selector?: string
			inputs?: string[]
			outputs?: string[]
			host?: {[key: string]: string}
			providers?: Provider[]
			exportAs?: string
			queries?: {[key: string]: any}
		})


	4. import { Directive } from '@angular/core';

		@Directive({ 
			selector?: string
			inputs?: string[]
			outputs?: string[]
			host?: {[key: string]: string}
			providers?: Provider[]
			exportAs?: string
			queries?: {[key: string]: any}
		})


		@Directive({
			selector: 'my-directive',
		})

		export class MyDirective {	}



	5. import { ContentChild } from '@angular/core';

		@Directive({selector: 'child-directive'})
			class ChildDirective {
		}

		@Directive({selector: 'someDir'})

		class SomeDir implements AfterContentInit {
			@ContentChild(ChildDirective) contentChild: ChildDirective;

			ngAfterContentInit() {
				// contentChild is set
			}
		}


	6. import { Injectable } from '@angular/core';

		@Injectable()

		export class ItemService {
			myServiceMsg(){
				return "Hello!, This is Service";
			}
		} 


	7. import { Pipe } from '@angular/core';

		@Pipe({ 
			name: string
			pure?: boolean
		})


	8. import { ViewChild } from '@angular/core';

		import {AfterViewInit, Component, Directive, ViewChild} from '@angular/core';

		@Directive({selector: 'child-directive'})
			class ChildDirective {}

		@Component({selector: 'someCmp', templateUrl: 'someCmp.html'})
		
		class SomeCmp implements AfterViewInit {
		
			@ViewChild(ChildDirective) child: ChildDirective;

			ngAfterViewInit() {
				// child is set
			}
		}


	9. import { Input } from '@angular/core';

		@Input({ 
			bindingPropertyName?: string
		})


	10. import { Output } from '@angular/core';

		@Output({ 
			bindingPropertyName?: string
		})


	11. import { Optional } from '@angular/core';

		@Injectable()
			class Car {
			constructor(@Optional() public engine:Engine) {}
		}



Routing
-------

	app-routing.module.ts
	---------------------
		import { NgModule } from '@angular/core';
		import { Routes, RouterModule } from '@angular/router';
		import { DepartmentListComponent } from './department-list.component';
		import { EmployeeListComponent } from './employee-list.component';
		import { DepartmentDetailComponent } from './department-detail.component';

		 
		const routes: Routes = [
			{ path: 'departments', component: DepartmentListComponent },
			{ path: 'employees', component: EmployeeListComponent },
			//Passing Parameters
			{ path: 'department/:id', component: DepartmentDetailComponent }
		]

		@NgModule({
			imports: [
				RouterModule.forRoot(routes)
			],
			exports: [
				RouterModule
			]
		})

		export class AppRoutingModule {}

		export const routingComponents = [ 
			DepartmentListComponent, 
			EmployeeListComponent, 
			DepartmentDetailComponent 
		]; 


	app.html
	--------
		<router-outlet></router-outlet>

 		<h3>Department List</h3>
         <ul class="items">
            <li *ngFor="let department of departments" (click)="onSelect(department)">
              {{department.name}}
            </li>
         </ul>


		nav a.router-link-active {
		  color: #039be5;
		}


	app.ts
	------

		import { Router } from '@angular/router';

		departments = [
			{"id": 1, "name": "Angular"},
			{"id": 2, "name": "Node"},
			{"id": 3, "name": "MongoDB"},
			{"id": 4, "name": "Ruby"},
			{"id": 5, "name": "Bootstrap"}
		]
		constructor(private _router: Router) { }

		onSelect(department) {
			this._router.navigate(['/department', department.id]);
		}


		Redirects Routing
		-----------------

		The "redirectTo" property describes the path we want to redirect this user to if they navigate to this URL.

			const routes:Routes = [
				{path: '', redirectTo: 'home', pathMatch: 'full'}, 
				{path: 'find', redirectTo: 'search'}, 
				{path: 'home', component: HomeComponent},
				{path: 'search', component: SearchComponent}
			];


			# Note:

				For the special case of an empty URL we also need to add the " pathMatch: 'full' " property so Angular knows it should be matching exactly the empty string and not partially the empty string.


			We’ve also added a redirect from /find to /search, since this isn’t empty we don’t need to add the pathMatch property.

			

Receiving Parameters
--------------------

	<h3>You selected department with id = {{departmentId}}</h3>


	import { Router, ActivatedRoute } from '@angular/router';

  	
  	public departmentId;

	constructor(private _activatedRoute: ActivatedRoute){}
	
	ngOnInit() {
		let id = parseInt(this._activatedRoute.snapshot.params['id']);
		this.departmentId = id;
	}



Params Observable
-----------------
	import { Router, ActivatedRoute, Params } from '@angular/router';

	@Component({  
	  template: `
	  		<h3>You selected department with id = {{departmentId}}</h3>
	        <a (click)="goPrevious()">Previous</a>
	        <a (click)="goNext()">Next</a>
	        <a (click)="gotoDepartments()">Back</a>
	  	`
	})



	constructor(private _router: Router){}


	ngOnInit() {
		this._router.params.subscribe(
			(_params: Params) => {
				let id = parseInt(_params['id']); 
				this.departmentId = id;
			});
	}

	goPrevious(){
		let previousId = this.departmentId - 1;
		this._router.navigate(['/department', previousId]);
	}

	goNext(){
		console.log('Clicked next');
		let nextId = this.departmentId + 1;    
		this._router.navigate(['/department', nextId]);
	}

	
	gotoDepartments(){
		//Optional Params
	    let selectedId = this.departmentId ? this.departmentId : null;
	    this._router.navigate(['/departments', {id: selectedId}]);
  	}



Angular 6 Alert Component (Subscription)
-------------------------

	<div *ngIf="status" [ngClass]="{ 'alert': status, 'alert-success': status.type === 'success', 'alert-danger': status.type === 'error' }">{{status.text}}</div>


	alert.component.ts
	------------------
		import { Component, OnInit, OnDestroy } from '@angular/core';
		import { Subscription } from 'rxjs';
		 
		import { AlertService } from '../_services';
		 
		@Component({
		    selector: 'alert',
		    templateUrl: 'alert.component.html'
		})
		 
		export class AlertComponent implements OnInit, OnDestroy {
		    private subscription: Subscription;
		    status: any;
		 
		    constructor(private alertService: AlertService) { }
		 
		    ngOnInit() {
		        this.subscription = this.alertService.getMessage().subscribe(status => { 
		            this.status = status; 
		        });
		    }
		 
		    ngOnDestroy() {
		        this.subscription.unsubscribe();
		    }
		}



App.module.ts
-------------

	import { BrowserModule } from '@angular/platform-browser';
	import { NgModule } from '@angular/core';

	import { AppRoutingModule } from './app-routing.module';
	import { AppComponent } from './app.component';

	@NgModule({
	  declarations: [
	    AppComponent
	  ],
	  imports: [
	  	BrowserModule,
	    AppRoutingModule
	  ],
	  providers: [],
	  bootstrap: [AppComponent]
	})
	export class AppModule { }



data.service.ts
---------------

	import { Injectable } from '@angular/core';

	@Injectable({
	  providedIn: 'root'
	})

	export class DataService {
	  constructor() { }
	}



Angular 6 Animation
-------------------

	> npm install @angular/animations@latest --save


	app.module.ts
	-------------
		import { BrowserAnimationsModule } from '@angular/platform-browser/animations';

		@NgModule({
		  ...
		  imports: [
		    BrowserAnimationsModule
		  ],
		})


	Angular 6 Animation Syntx:
	--------------------------

	import { trigger, CSSstyle, Timetransition, animate, somekeyframes, generatedquery, stagger } from '@angular/animations';

	@Component({
			animations: [
			  trigger('changeDivSize', [
			    state('initial', style({
			      backgroundColor: 'green',
			      width: '100px',
			      height: '100px'
			    })),
			    state('final', style({
			      backgroundColor: 'red',
			      width: '200px',
			      height: '200px'
			    })),
			    transition('initial=>final', animate('1500ms')),
			    transition('final=>initial', animate('1000ms'))
			  ]),
			]
		})


		#class
			currentState = 'initial';

			changeState() {
			  this.currentState = this.currentState === 'initial' ? 'final' : 'initial';
			}


		#html
			<button (click)="changeState()">Change Size</button>
			<br />
			<div [@changeDivSize]=currentState></div>
			


Angular 6 Http Request Methods
------------------------------

	import { HttpHeaders } from '@angular/common/http';

	const httpOptions = {
		headers: new HttpHeaders({
			'Content-Type':  'application/json',
			'Authorization': 'Your-angular6-Live-auth-token'
		})
	};

	 // POST: httprequest - Http post and get request in angular 6
		addusername (user: username): Observable<username> {
			return this.http.post<username>(this.useresUrl, user, httpOptions).pipe(
		      catchError(this.handleError('addusername', user))
		    );
		}


	// POST: Angular 6 Http Post Method with Parameters Example
		addUser (user: User): Observable<User> {
			return this.http.post<User>(this.useresUrl, user, httpOptions).pipe(
				catchError(this.handleError('addUser', user))
			);
		}
	// GET Angular 6 Http GET Method with Parameters Example
		getUsers (): Observable<User[]> {
			return this.http.get<User[]>(this.useresUrl).pipe(
				catchError(this.handleError('getUsers', []))
			);
		}



Angular 6 Auth & Authentication Service (Create Token and get Token)
---------------------------------------

	sign-in.component.html
	----------------------
		<div *ngIf="loginError" [class]="loginResult?['alert alert-danger']:['alert alert-success']">{{loginResultMsg}}</div>
		
		<form novalidate #loginForm="ngForm">
			
			<div class="form-group">
				<input type="email" placeholder="Enter email" [(ngModel)]="_user.username" #username="ngModel" name="username">		
			</div>
			
			<div class="form-group">
				<input type="password" placeholder="Password" [(ngModel)]="_user.password" #password="ngModel" name="password">
			</div>
			
			<button type="submit" class="btn btn-success" [disabled]="loginForm.invalid" (click)="userLogin()">Submit</button>

		</form>



	sign-in.component.ts
	--------------------
		import { Component, OnInit } from '@angular/core';
		import { AuthService } from '../services/auth.service';
		import { Router } from '@angular/router';

		@Component({
			selector: 'app-sign-in',
			templateUrl: './sign-in.component.html',
			styleUrls: ['./sign-in.component.css']
		})

		export class SignInComponent implements OnInit {

			_user: any = {}

			loginResult: boolean;
			loginResultMsg: string;
			loginError: boolean = false;
			constructor(private _authService: AuthService, private _router: Router) { }

			userLogin() {

				this._authService.login(this._user).subscribe(
					res => {
						this.loginResult = true;
						this.loginError = true;
						this.loginResultMsg = "Successfully login"
						this._authService.saveToken(res["token"])
						this._router.navigate(["/dashborad"]);
					},
					error => {
						this.loginResult = true;
						this.loginError = true;
						this.loginResultMsg = "Error! Please check username and password details"
						this._router.navigate(['/sign-in'])
					}
				)
			}

			ngOnInit() {
			}

		}


	auth.service.ts
	---------------
		import { Injectable } from '@angular/core';
		import { HttpClient, HttpErrorResponse } from '@angular/common/http';
		import { User } from '../models/user.model';
		import { Router } from '@angular/router';
		import { Subject, throwError } from 'rxjs';
		import { map, catchError } from 'rxjs/operators';

		@Injectable({
			providedIn: 'root'
		})
		
		export class AuthService {

			loginUrl: string = "http://localhost:9001/api/users/login";

			constructor(private _http: HttpClient, private _router: Router) { }

			login(userData: User) {
				return this._http.post(this.loginUrl, userData);
			}

			saveToken(token: string) {
				return sessionStorage.setItem("token", token)
			}

			getToken() {
				return sessionStorage.getItem('token')
			}

			isLoggedin() {
				return !!sessionStorage.getItem("token");
			}

			logout() {
				localStorage.removeItem("token");
				this._router.navigate(['/sign-in'])
			}

			isAuthenticated(): boolean {
				const GetToken = sessionStorage.getItem('token');
				
				if (GetToken && GetToken.length > 0) {
					return true;
				} else {
					return false;
				}
			}

		}


	auth.guard.ts
	-------------
		import { Injectable } from '@angular/core';
		import { CanActivate, ActivatedRouteSnapshot, RouterStateSnapshot, CanDeactivate, Router } from '@angular/router';
		import { Observable } from 'rxjs';
		import { AuthService } from './auth.service';

		@Injectable({
			providedIn: 'root'
		})
		export class AuthGuard implements CanActivate {

		constructor(private _authService: AuthService, private _router: Router) { }

			canActivate( next: ActivatedRouteSnapshot, state: RouterStateSnapshot): Observable<boolean> | Promise<boolean> | boolean {
			
				let url: string = state.url;
				console.log("Satte Url = " + url)
				
				if (this._authService.isAuthenticated()) {
					return true;
				} else {
					this._router.navigate(['/sign-in']);
					return false
				}

			}
		}

	
	token.interceptor.ts
	--------------------
		import { Injectable, Injector } from '@angular/core';
		import { HttpRequest, HttpHandler, HttpEvent, HttpInterceptor } from '@angular/common/http';
		import { AuthService } from './auth.service';
		import { Observable } from 'rxjs/Observable';

		@Injectable()

		export class TokenInterceptor implements HttpInterceptor {

			constructor(private _authService: AuthService) { }

			intercept(request: HttpRequest<any>, next: HttpHandler): Observable<HttpEvent<any>> {
			    const TokenRequest = request.clone({
			        setHeaders: {
			            Authorization: `${this._authService.getToken()}`
			        }
			    });
			    return next.handle(TokenRequest);
			}

		}


	app.module.ts
	-------------
		import { FormsModule } from '@angular/forms';
		import { HttpClientModule, HTTP_INTERCEPTORS } from '@angular/common/http';

		@NgModule({
		    declarations: [
				...
		    ],
		    imports: [
		        .....
		    ],
		    providers: [{
		        provide: HTTP_INTERCEPTORS,
		        useClass: TokenInterceptor,
		        multi: true
		    }],
		    bootstrap: [AppComponent]
		})
		export class AppModule { }




	product.service.ts (get Token)
	------------------

		import { Injectable } from '@angular/core';
		import { HttpClient } from '@angular/common/http';
		import { AuthService } from './auth.service';
		import { Product } from "../models/product.model";

		@Injectable({
			providedIn: 'root'
		})
		
		export class productService {

			constructor(private _http: HttpClient, private _authService: AuthService) { }

			getProductData() {

				// Using direct apply token
				
				let hder = { 'authorization': this._authService.getToken() };

				return this._http.get<Product[]>("http://localhost:9001/api/products/", { headers: hder })
			}
			
			saveProduct(data) {
				return this._http.post<Product[]>("http://localhost:9001/api/products/", data)
			}

		}



Angular 6 Service (Student)
-------------------------
	import { Injectable } from '@angular/core';
	import { HttpClient } from '@angular/common/http';
	 
	import { Student } from '../_models';
	 
	@Injectable({
	  providedIn: 'root'
	})

	export class StudentService {
	    constructor(private http: HttpClient) { }
	 
	    getAll() {
	        return this.http.get('/api/students');
	    }
	 
	    getById(id: number) {
	        return this.http.get('/api/students/' + id);
	    }
	 
	    create(student: Student) {
	        return this.http.post('/api/students', student);
	    }
	 
	    update(student: Student) {
	        return this.http.put('/api/students/' + student.id, student);
	    }
	 
	    delete(id: number) {
	        return this.http.delete('/api/students/' + id);
	    }
	}



Angular Basic Form Validation
-----------------------------

	form.component.ts
	-----------------
		import { Component, OnInit } from '@angular/core';

		@Component({
		  selector: 'app-basic-form',
		  templateUrl: './basic-form.component.html',
		  styleUrls: ['./basic-form.component.css']
		})
		export class BasicFormComponent implements OnInit {

		  _user: any = {};

		  constructor() { }

		  ngOnInit() {
		  }

		  onSubmit() {
		    console.log(this._user)
		  }
		}


	form.html
	---------
	    <form novalidate #basicForm="ngForm">

	      <div class="form-group">
	        <label>First Name</label>
	        <input type="text" class="form-control" required minlength="4" name="firstName" [(ngModel)]="_user.firstName"
	          #firstName="ngModel" placeholder="First Name">

	        <div *ngIf="firstName.invalid && (firstName.dirty || firstName.touched)" class="text-danger">
	          <div *ngIf="firstName.errors.required">First Name is required.</div>
	          <div *ngIf="firstName.errors.minlength">Name must be at least 4 characters long.</div>
	        </div>
	      </div>

	      <div class="form-group">
	        <label>Last Name</label>
	        <input type="text" class="form-control" required [(ngModel)]="_user.lastName" #lastName="ngModel" name="lastName"
	          placeholder="Last Name" />
	        <div *ngIf="lastName.invalid && (lastName.dirty || lastName.touched)" class="text-danger">
	          <div *ngIf="lastName.errors.required">Last Name is required.</div>
	        </div>
	      </div>

	      <div class="form-group">
	        <label>Email</label>
	        <input type="text" class="form-control" required [(ngModel)]="_user.email" #email="ngModel" name="email"
	          placeholder="Email" />

	        <div *ngIf="email.invalid && (email.dirty || email.touched)" class="text-danger">
	          <div *ngIf="email.errors.required">Email is required.</div>
	        </div>
	      </div>

	      <div class="form-group">
	        <label>Password</label>
	        <input type="password" class="form-control" minlength="6" required [(ngModel)]="_user.password" #password="ngModel"
	          name="password" placeholder="password" />

	        <div *ngIf="password.invalid && (password.dirty || password.touched)" class="text-danger">
	          <div *ngIf="password.errors.required">Password is required</div>
	          <div *ngIf="password.errors.minlength">Password must be at least 6 characters</div>
	        </div>

	      </div>
	      <button type="submit" [disabled]="basicForm.invalid" (click)="onSubmit()" class="btn btn-primary">Register</button>

	    </form>


	    
		Template Driven Forms Validation
		--------------------------------

			State 							Class if true 		Class if flase	
			-------------------------		-------------		--------------
			Control has been visited		ng-touched 			ng-untouched

			Control value has changed		ng-dirty 			ng-pristine

			Control value is valid 			ng-valid 			ng-invalid



		Validation Example
		------------------

		<div class="from-group">

			<label>First Name</label>

			<input type="text" required #firstnameRef="ngModel" class="form-control" name="firstname" ngModel>
			
			<div [hidden]="firstnameRef.valid || firstnameRef.pristine" class="alert alert-danger">Enter Your Name</div>

		</div>

		minlength
		---------
			<div class="from-group">
				
				<label>First Name</label>

				<input type="text" required minlength="3" [(ngModel)]="firstnameRef" #firstnameRef="ngModel" class="form-control" name="firstnameRef" >

				<div *ngIf="firstnameRef.errors && (firstnameRef.dirty || firstnameRef.touched)" class="alert alert-danger">

					<div [hidden]="!firstnameRef.errors.required">Enter Your Name</div>

					<div [hidden]="!firstnameRef.errors.minlength">Please enter minmum 4 length charater</div>				
				</div>

			</div>


		Submitt button Valid Form
		-------------------------
			<button [disabled]="!dataFrom.form.valid" type="submit" class="btn btn-primary">Submit</button>



Angular Reactive Form Validation
--------------------------------
	
	form.component.ts
	-----------------
		import { Component, OnInit } from '@angular/core';
		import { FormBuilder, FormGroup, Validators } from '@angular/forms';

		@Component({
		  selector: 'app-reactive-forms',
		  templateUrl: './reactive-forms.component.html',
		  styleUrls: ['./reactive-forms.component.css']
		})

		export class ReactiveFormsComponent implements OnInit {

		  registerForm: FormGroup;
		  submitted = false;

		  constructor(private formBuilder: FormBuilder) { }

		  ngOnInit() {
		    this.registerForm = this.formBuilder.group({
		      firstName: ['', Validators.required],
		      lastName: ['', Validators.required],
		      email: ['', [Validators.required, Validators.email]],
		      password: ['', [Validators.required, Validators.minLength(6)]]
		    });
		  }

		  // convenience getter for easy access to form fields
		  get f() { return this.registerForm.controls; }

		  onSubmit() {
		    this.submitted = true;

		    // stop here if form is invalid
		    if (this.registerForm.invalid) {
		      return;
		    }

		    alert(JSON.stringify(this.registerForm.value))

		    //Reset Form
		    this.registerForm.reset()

		  }

		}


	Form.html
	---------
	    <form [formGroup]="registerForm" (ngSubmit)="onSubmit()">

	      <div class="form-group">
	        <label>First Name</label>
	        <input type="text" formControlName="firstName" class="form-control" [ngClass]="{ 'is-invalid': submitted && f.firstName.errors }" />
	        <div *ngIf="submitted && f.firstName.errors" class="invalid-feedback">
	          <div *ngIf="f.firstName.errors.required">First Name is required</div>
	        </div>
	      </div>

	      <div class="form-group">
	        <label>Last Name</label>
	        <input type="text" formControlName="lastName" class="form-control" [ngClass]="{ 'is-invalid': submitted && f.lastName.errors }" />
	        <div *ngIf="submitted && f.lastName.errors" class="invalid-feedback">
	          <div *ngIf="f.lastName.errors.required">Last Name is required</div>
	        </div>
	      </div>

	      <div class="form-group">
	        <label>Email</label>
	        <input type="text" formControlName="email" class="form-control" [ngClass]="{ 'is-invalid': submitted && f.email.errors }" />
	        <div *ngIf="submitted && f.email.errors" class="invalid-feedback">
	          <div *ngIf="f.email.errors.required">Email is required</div>
	          <div *ngIf="f.email.errors.email">Email must be a valid email address</div>
	        </div>
	      </div>

	      <div class="form-group">
	        <label>Password</label>
	        <input type="password" formControlName="password" class="form-control" [ngClass]="{ 'is-invalid': submitted && f.password.errors }" />
	        <div *ngIf="submitted && f.password.errors" class="invalid-feedback">
	          <div *ngIf="f.password.errors.required">Password is required</div>
	          <div *ngIf="f.password.errors.minlength">Password must be at least 6 characters</div>
	        </div>
	      </div>

	      <div class="form-group">
	        <button [disabled]="loading" class="btn btn-primary">Register</button>
	      </div>

	    </form>



Angular 6 Making an Observable
------------------------------
	import { Observable } from 'rxjs';
	
	// Make observable	
	const memberObservable = new Observable((observer) => {
		//Angular 6 observable execution
		observer.next('Hello Observable');
		observer.complete();
	});

	// subscribe Simple Angular 6 Observables Example
	memberObservable.subscribe();



Lazy Loading
------------

	movie.lazy.module.ts
	--------------------
		import { NgModule } from "@angular/core";
		import { CommonModule } from "@angular/common";
		import { HttpClientModule } from "@angular/common/http";
		import { FormsModule } from "@angular/forms";
		import { RouterModule, Routes } from "@angular/router";

		import { MovieslistComponent } from "./movieslist/movieslist.component";
		import { MovieDetailsComponent } from "./movie-details/movie-details.component";

		const routes: Routes = [
		    { path: '', component: MovieslistComponent },
		    { path: 'movies/:imdbID', component: MovieDetailsComponent },
		]

		@NgModule({
		    declarations: [
		        MovieslistComponent,
		        MovieDetailsComponent
		    ],
		    imports: [
		        CommonModule,
		        HttpClientModule,
		        FormsModule,
		        RouterModule.forChild(routes)
		    ],
		    exports: [],
		    providers: [],
		})
		export class MovieLazyModule { }



	Main.Routing.ts
	---------------
		import { NgModule } from '@angular/core';
		import { RouterModule, Routes } from '@angular/router';

		import { AuthGuard } from './services/auth.guard'

		import { SignInComponent } from './sign-in/sign-in.component';
		import { MenuComponent } from './menu/menu.component';

		const childRoutes: Routes = [
			{ path: 'movies', loadChildren: './movies/movie.lazy.module#MovieLazyModule' }
		]

		const appRouters: Routes = [
			{ path: '', component: MenuComponent, canActivate: [AuthGuard], children: childRoutes },
			{ path: 'sign-in', component: SignInComponent },
			{ path: '**', redirectTo: '/' }
		]

		@NgModule({
			imports: [
				RouterModule.forRoot(appRouters)
			],
			exports: [RouterModule]
		})

		export class AppRoutingModule {}



Angular - Communicating Between Components
--------------------------------------------

	- Parent to Child

	- Child to Parent

	- Sibling Component's communication (Use Services)
		
		> BehaviorSubject

		> Observable & Subject




	Parent to Child
	---------------

		#Parent.html

			<section>
	          	<input type="text" class="form-control" #parentMsg>
	          	<button (click)="sharedData(parentMsg.value)">Send</button> 
			</section>
			<hr />
			<app-child [childMessage]="parentValue"></app-child>

		#Parent.ts
		
			export class ParentComponent implements OnInit {
				parentValue: any;

				sharedData(data) {
					this.parentValue = data;
				}
			}

		#Child.ts

			import { Component, OnInit, Input } from '@angular/core';

			export class ChildComponent implements OnInit {
				@Input() childMessage: any;
			}


		#Child.html

			<p class="card-text">{{childMessage}}</p>



	Child to Parent
	---------------


		#Child.html

    		<input type="text" class="form-control" #childMsg>

          	<button (click)="sharedData(childMsg.value)">Send</button>


		#Child.ts

			import { Component, OnInit, EventEmitter, Output } from '@angular/core';

			export class ChildComponent implements OnInit {

			@Output() bindChildEvent = new EventEmitter<any>()

				sharedData(data) {
					this.bindChildEvent.emit(data)
				}

			}
 


        #Parent.html
      	
      		<p class="card-text">{{childMsg}}</p>
    
			<hr />
			<app-child (bindChildEvent)="recevieMsgData($event)"></app-child>


		#Parent.ts  

			childMsg: any;

			recevieMsgData($event) {
				this.childMsg = $event;
			}



	Sibling Component's communication (BehaviorSubject)
	---------------------------------------------------

		#Sahred.Service.ts

			import { Injectable } from '@angular/core';
			import { BehaviorSubject } from 'rxjs/BehaviorSubject';

			@Injectable({
				providedIn: 'root'
			})

			export class SharedService {

				private messageSource = new BehaviorSubject<any>("Default Meassage");

				currentMsg = this.messageSource.asObservable();

				changeMsg(msg) {
					this.messageSource.next(msg)
				}

				constructor() { }
			}


		#ComponentOne.html

			<input type="text" #msg>

			<button (click)="sharedData(msg)">Send</button>

			<p class="card-text">{{SahreMsg}}</p>


		#ComponentOne.ts

			import { Component, OnInit } from '@angular/core';
			import { SharedService } from '../shared.service';

			export class ComponentOne implements OnInit {

				SahreMsg: any;

				constructor(private _sharedSrc: SharedService) { }

				ngOnInit() {
					this._sharedSrc.currentMsg.subscribe(res => this.SahreMsg = res)
				}

				sharedData(data) {
					this._sharedSrc.changeMsg(data.value)
				}

			}



		#ComponentTwo.ts

			import { Component, OnInit } from '@angular/core';
			import { SharedService } from '../shared.service';

			export class ComponentTwo implements OnInit {

				SahreMsg: any;

				constructor(private _sharedSrc: SharedService) { }

				ngOnInit() {
					this._sharedSrc.currentMsg.subscribe(res => this.SahreMsg = res)
				}

				sharedData(data) {
					this._sharedSrc.changeMsg(data.value)
				}

			}


		#ComponentTwo.html

			<input type="text" #msg>

			<button (click)="sharedData(msg)">Send</button>

			<p class="card-text">{{SahreMsg}}</p>



	Sibling Component's communication (Observable & Subject)
	--------------------------------------------------------

		# Observable.subscribe()

			- The observable subscribe method is used by angular components to subscribe to messages that are sent to an observable.

		# Subject.next()

			- The subject next method is used to send messages to an observable which are then sent to all angular components that are subscribers (a.k.a. observers) of that observable.
		



Service Worker 
--------------
	– Optimizing the Performance of an Angular App
	
	- a service worker intercepts all outgoing http requests sent by your application on the browser. 
	
	-You can choose which request to respond to by using a set of rules (policies) to guide the service worker on how to handle different requests.


How to run Angular application locally during development?
-----------------------------------------------------------

	- "ng serve" command is used to run Angular5 application locally during development.

	- To start development server on specific port "ng serve --port aPortNumber" command is used.



What is ng-content Directive ?
------------------------------ 
	The HTML elements like p (paragraph) or h1 (heading) have some content between the tags. 

	For example, <p>this is a paragraph</p> and <h1>this is a heading</h1>. 

	Now, similar to this, what if we want to have some custom text or content between the angular tags like  <app-tax> some tax-related content </app-tax> This will not work the way it worked for HTML elements.  

	Now, in such cases, the <ng-content> tag directive is used.



Explain Decorators in Angular
-----------------------------
	- Decorators are used to attach metadata to program elements such as class and properties.

	- Metadata is used to specify details about program entities. 

	- Decorators give special meaning to program elements.

	- Here we will look at some of the most commonly used Decorators in Angular.

		There are 4 different types of decorators:
			- Class decorators
			- Property decorators
			- Method decorators
			- Parameter decorators

	A decorator is a function that is invoked with a prefixed "@" symbol and is immediately followed by a class, parameter, method, or property. A decorator returns the same thing which was given as an input but in an augmented form.

	Commonly used Decorators
	------------------------
		@NgModule Specifies that a class is Angular module.

		@Component Specifies that a class is Angular class.

		@Directive Attaches behaviour to HTML DOM or changes its appearance.

		@Injectable Informs Angular that decorated class can be used with dependency injector.

		@ViewChild Parent component can access child component by using this decorator.



Explain the component Directory structure of angular.
----------------------------------------------------
	Here are the elements which are present in the component directory structure anf modules:-

		- module.ts
			in this, the angular module is declared. @NgModule decorator is used which initializes the different aspects of angular applications. AppComponent is also declared in it.

		- components.ts
			it simply defines the components in angular and this is the place where the app-root sector is also defined. A title attribute is also declared in the component.

		- component.html
			it is the template file of the application which represents the visual parts of our components.



Differences between Angular components vs directives
-----------------------------------------------------
	1. 
		- We create Component with the help of @Component meta-data annotation 
		- we create Directive with the help of @Directive meta-data annotation.
	2. 
		- a component is a directive with a view 
		- a directive is a decorator with no view. 
	3.	
	 	- The components are used to create UI widgets.
		- The directives are used to add behavior to existing DOM elements.
	4.
		- @Component is used to create reusable components
		- @Directive is used to create reusable behaviour
	5. 
		- Only one component is used per DOM element.
		- More than one directive are used per DOM element.
	6. 
	 	- In the components, @View, template and templateUrl are mandatory in the components.
		- The directive do not have @View etc.



When ngOnChanges event get called in Angular Application Lifecycle?
---------------------------------------------------------------------
	- Called every time a data-bound input property changes. 

	- It’s called a first time before the ngOnInit hook. 

	- The hook receives a SimpleChanges object that contains the previous and current values for the data-bound inputs properties. 

	- This hook gets called often, so it’s a good idea to limit the amount of processing it does.



When ngOnInit event get called in Angular Application Lifecycle?
------------------------------------------------------------------
	This is called whenever the initialization of the directive/component after Angular first displays the data-bound properties happens.



When ngDoCheck event get called in Angular Application Lifecycle?
-------------------------------------------------------------------
	- Use this hook instead of ngOnChanges for changes that Angular doesn’t detect. 

	- It gets called at every change detection cycle, so keeping what it does to a minimum is important for performance.

Lifecycle Hooks in Angular
--------------------------
	# ngOnChanges: 
		Called every time a data-bound input property changes. It’s called a first time before the ngOnInit hook. The hook receives a SimpleChanges object that contains the previous and current values for the data-bound inputs properties. This hook gets called often, so it’s a good idea to limit the amount of processing it does.

	# ngOnInit: 
		Called once upon initialization of the component.
	
	# ngDoCheck: 	
		Use this hook instead of ngOnChanges for changes that Angular doesn’t detect. It gets called at every change detection cycle, so keeping what it does to a minimum is important for performance.
	
	# ngAfterContentInit: 
		Called after content is projected in the component.
	
	# ngAfterContentChecked: 
		Called after the projected content is checked.
	
	# ngAfterViewInit: 
		Called after a component’s view or child view is initialized.
	
	# ngAfterViewChecked: 
		Called after a component’s view or child view is checked.
	
	# ngOnDestroy: 
		Called once when the component is destroyed and a good hook to use to cleanup and unsubscribe from observables.


What's the difference between BrowserModule and platformBrowserDynamic?
-----------------------------------------------------------------------

	=> import { BrowserModule } from '@angular/platform-browser';
		
			"BrowserModule" is a module that provides all kinds of services and directives one usually wants to use in an Angular application like "ngIf".

	=> import { platformBrowserDynamic } from '@angular/platform-browser-dynamic';

			"platformBrowserDynamic" is a function used to bootstrap an Angular application



How routing works in Angular.
-------------------------------
	- Routing helps a user in navigating to different pages using links. 

	- Routing is a mechanism which enables user to navigate between views/components. 

	- Angular simplifies the routing and provide flexibility to configure and define at module level (Lazy loading). 

	- ngRoute module is used when you want to navigate through different pages

	The angular application has single instance of the Router service and whenever URL changes, corresponding Route is matched from the routing configuration array. On successful match, it applies redirects and the router builds a tree of ActivatedRoute objects and contains the current state of the router. Before redirection, the router will check whether new state is permitted by running guards (CanActivate). Route Guards is simply an interface method that router runs to check the route authorization. After guard runs, it will resolve the route data and activate the router state by instantiation the required components into <router-outlet> </router-outlet>.



Angular Router: Navigation Using RouterLink, Navigate or NavigateByUrl
----------------------------------------------------------------------

	RouterLink
	----------
		- A basic example of using the RouterLink directive can look like this:

			<a routerLink="/red-pill/neo">Go!</a>

		- The different url segments can also be passed in an array like this:

			<a [routerLink]="['/', 'red-pill', 'neo']">Go!</a>

		- You can go up to higher levels in the navigation using something like this:

			<a [routerLink]="['../', 'blue-pill', 'neo']">Go!</a>

			In that example, if the user is at /red-pill/neo, the navigation will change to /blue-pill/neo.

		- You can pass-in parameters to the navigation with an object in the list of url segments:

			<a [routerLink]="['/', 'red-pill', {x: 'white-rabbit'}, 'neo']">Param!</a>

			With that example, the router will navigate to /red-pill;x=white-rabbit/neo.

		# Named Outlets

			You can tell the router what to place in a named outlet with something like this:

			<a [routerLink]="['/', 'red-pill', { outlets: { side: ['neo'] } }]">Nav with a named outlet			</a>
			
			In that example, the neo segment will be placed in the outlet named side. Here’s another example, where in addition the trinity segment goes in the footer named outlet:

			<a [routerLink]="['/', 'red-pill', { outlets: { side: ['neo'], footer: ['trinity'] } }]">
			Nav with a named outlet</a>


	Navigating Imperatively
	-----------------------
		- There are two methods available on Angular’s Router class to navigate imperatively in your component classes: Router.navigate and Router.navigateByUrl. 

		- Both methods return a promise that resolve to true if the navigation is successful, null if there’s no navigation, false if the navigation fails or is completely rejected if there’s an error.

		- You pass-in an array of url segments to Router.navigate or a string to Router.navigateByUrl, just like you would using the RouterLink directive.


			import { Component } from '@angular/core';
			import { Router } from '@angular/router';

			@Component({
			  // ...
			})
			export class AppComponent {

			  constructor(private _router: Router) {}

			  // ...
			}

		# Router.navigate

			goPlaces() {
			  this._router.navigate(['/', 'red-pill']);
			}

			And here’s an example demonstrating how navigate is thenable:

			goPlaces() {
				this.router.navigate(['/', 'red-pill']).then(
					nav => {
						console.log(nav); // true if navigation is successful
					}, 
					err => {
						console.log(err) // when there's an error
					}
				);
			}

		# Router.navigateByUrl

			Router.navigateByUrl is basically the same as Router.navigate, except that a string is passed-in instead of url segments and the navigation should be absolute and start with a /:

			goPlaces() {
				this.router.navigateByUrl('/red-pill;x=white-rabbit/neo');
			}


What do you understand by Services with reference to Angular?
-------------------------------------------------------------

	- Services in angular are used to organize and share code across your application. 

	- These are the suitable objects which are wired together with the help of dependency injection. 

	- The angular services are lazily instantiated. 

	- The service is only instantiated by angular only when the application component depends on it. 

	- In angular, new services can be made or can even be used in other built-in services. 
		Over 30 built-in services are present in angular.



What are EventEmitters and how it works in Angular?
------------------------------------------------------

	In Angular, any change occurred in the component always gets propagated from the current component to all its children in hierarchy. If the change from one component needs to be reflected to any of its parent component in hierarchy, we can emit the event by using Event Emitter api.

	EventEmitter is class defined in @angular/core module which can be used by components and directives to emit custom events.

	@output() somethingChanged = new EventEmitter();

	We use somethingChanged.emit(value) method to emit the event. This is usually done in setter when the value is being changed in the class.

	This event emit can be subscribed by any component of the module by using subscribe method.

	myObj.somethingChanged.subscribe(val) => this.myLocalMethod(val));



What is the use of codelyzer in Angular application.
------------------------------------------------------

	All enterprise applications follows a set of coding conventions and guidelines to maintain code in better way. Codelyzer is an open source tool to run and check whether the pre-defined coding guidelines has been followed or not. Codelyzer does only static code analysis for angular and typescript project.

	Codelyzer runs on top of tslint and its coding conventions are usually defined in tslint.json file. Codelyzer can be run via angular cli or npm directly. Editors like Visual Studio Code and Atom also supports codelyzer just by doing a basic settings.

	To set up the codelyzer in Visual Studio code, we can go to File -> Preferences -> User Settings and add the path for tslint rules.
	
		{
		  "tslint.rulesDirectory": "./node_modules/codelyzer",
		  "typescript.tsdk": "node_modules/typescript/lib"
		}

	To run from cli: ng lint. 

	To run from npm: npm run lint



What are the security threats should we be aware of in Angular application?
-----------------------------------------------------------------------------
	-> Avoid using/injecting dynamic Html content to your component.
	
	-> If using external Html, that is coming from database or somewhere outside the application, sanitize it.
	
	-> Try not to put external urls in the application unless it is trusted. Avoid url re-direction unless it is trusted.
	
	-> Consider using AOT compilation or offline compilation.
	
	-> Try to prevent XSRF attack by restricting the api and use of the app for known or secure environment/browsers.



What is transpiling
-------------------
	- Transpiling is a process of converting code from one language to another (typescript into javascript, using Traceur, a JS compiler). 

	- In Angular, Traceur compiler is used for converting TypeScript to JavaScript so that browsers can understand.



What Is the Angular Compiler? Why we need Compilation in Angular
----------------------------------------------------------------
	The Angular compiler converts our applications code (TypeScript) into JavaScript code + HTML before browser downloads and runs that code.

	The Angular offers two ways to compile our application code-

		- Just-in-Time (JIT) – JIT compiles our app in the browser at runtime (compiles before running).
		
		- Ahead-of-Time (AOT) – AOT compiles our app at build-time (compiles while running).



What is AOT compilation
-----------------------

	AOT compilation stands for Ahead Of Time compilation, in which the angular compiler compiles the angular components and templates to native JavaScript and HTML during the build time. The compiled Html and JavaScript is deployed to the web server so that the compilation and render time can be saved by the browser.

	Advantages

		-> Faster download: Since the app is already compiled, many of the angular compiler related libraries are not required to be bundled, the app bundle size get reduced. So, the app can be downloaded faster.

		-> Lesser No. of Http Requests: If the app is not bundled to support lazy loading (or whatever reasons), for each associated html and css, there is a separate request goes to the server. The pre-compiled application in-lines all templates and styles with components, so the number of Http requests to the server would be lesser.

		-> Faster Rendering: If the app is not AOT compiled, the compilation process happens in the browser once the application is fully loaded. This has a wait time for all necessary component to be downloaded, and then the time taken by the compiler to compile the app. With AOT compilation, this is optimized.

		-> Detect error at build time: Since compilation happens beforehand, many compile time error can be detected, providing a better degree of stability of application.

	Disadvantages

		-> Works only with HTML and CSS, other file types need a previous build step
		-> No watch mode yet, must be done manually (bin/ngc-watch.js) and compiles all the files
		-> Need to maintain AOT version of bootstrap file (might not be required while using tools like cli)
		-> Needs cleanup step before compiling



What Is the difference between JIT compiler and AOT compiler
------------------------------------------------------------
	
	1.
		JIT – JIT compiles our app in the browser at runtime.

		AOT - AOT compiles our app code at build time.
	
	2. 
		JIT - Compiles before running

		AOT - Compiles while running

	3. 
		JIT – Each file compiled separately

		AOT - Compiled by the machine itself, via the command line (Faster)

	4.
		JIT – No need to build after changing our app code and it automatically reflects the changes in your browser page

		AOT - All code compiled together, inlining HTML/CSS in the scripts

	5.		
		JIT – Highly secure

		AOT - Highly secure

	6.
		JIT – Very suitable for local development

		AOT - Very suitable for production builds



What do you understand by Isolated Unit Tests
---------------------------------------------
	- As the name implies, unit test is all about testing individual units of code. 

	- In order to answer some questions, isolating the unit of code under test is really important. 

	- When we do this, we are not forced into creating related pieces such as DOM elements for sorting. 

	- With the help of isolated unit tests, it becomes easier to implement everything. 

	- To simulate the requests, dependency injections are also provided. 

	- The individual sort function can be tested in isolation. 

	- And not only the sort function, any function can be tested in isolation.



What are DSL Animation Functions in Angular
-------------------------------------------

	DSL Animation functions are used for crafting animations in Angular js. Below are list of DSL Animation functions in angular js.
		- trigger()
		- state()
		- transition()
		- group()
		- sequence()
		- style()
		- animate()
		- keyframes()



List some new features comes with Angular6
------------------------------------------
	Latest Key features of Angular 6

		- Added support for creating Custom Elements based on Angular Components.

		- Animations: 
			expose element and params within transition matchers.

		- Bazel: 
			change ng_package rule to APF v6

		- singleline, multiline and jsdoc comments are now supported

		- compiler-cli : add resource inlining to ngc

		- support for TypeScript 2.7

		- Require node 8 as runtime engine



Which of the Angular life cycle component execution happens when a data-bound input value updates?
--------------------------------------------------------------------------------------------------
	ngOnChanges is the life cycle hook that gets executed whenever a change happens to the data that was bound to an input. 



 What is ng-content Directive? 
 -----------------------------
	The HTML elements like p (paragraph) or h1 (heading) have some content between the tags. 

	For example, 

		<p>this is a paragraph</p> and <h1>this is a heading</h1>. Now, similar to this, what if we want to have some custom text or content between the angular tags like  <app-tax>some tax-related content</app-tax> This will not work the way it worked for HTML elements.  Now, in such cases, the <ng-content> tag directive is used. 



 What does a router.navigate do?
 -------------------------------
	When we want to route to a component we use router.navigate.  

		Syntax: this.router.navigate(['/component_name']); 



What is the purpose of using package.json in the angular project?
-----------------------------------------------------------------
	- With the existence of package.json, it will be easy to manage the dependencies of the project. 

	- If we are using typescript in the angular project then we can mention the typescript package and version of typescript in package.json.



What does a Subscribe method do in Angular? 
-------------------------------------------
	- It is a method which is subscribed to an observable. 

	- Whenever the subscribe method is called, an independent execution of the observable happens.  



Differentiate between Observables and Promises
----------------------------------------------
	
	Promise
		- Promises are only called once and It can return only a single value at a time and the Promises are not cancellable.
	
	Observables
		- Observables handle multiple values over time and it can return multiple values and the Observables are cancellable.
	
		-The Observables are more advanced than Promises.



What Are The Ngmodule Metadata Properties?
-------------------------------------------
	The NgModule decorator identifies AppModule as a NgModule class.

	The NgModule takes a metadata object that tells Angular how to compile and launch the application.

	The NgModule importance metadata properties are as follows –

		- providers
		- declarations
		- imports
		- exports
		- entryComponents
		- bootstrap
		- schemas
		- id



What Types Of Ngmodules?
------------------------
	There are four types of NgModules –

		- Features Module
		- Routing Module
		- Service Module
		- Widget Module
		- Shared Module



What Is Bootstrapping in Angular?
--------------------------------
	main.ts is the entry point of your application, compiles the application with just-in-time and bootstrap the application.The Bootstrap is the root AppComponent that Angular creates and inserts into the "index.html" host web page.The bootstrapping process creates the components listed in the bootstrap array and inserts each one into the browser (DOM).

	The bootstrapping process sets up the execution environment, digs the root AppComponent out of the module’s bootstrap array, creates an instance of the component and inserts it within the element tag identified by the component ’s.selector



How to Pass URL Parameters (Query Strings) in Angular
-----------------------------------------------------
	
	https://alligator.io/angular/query-parameters/

	HttpParams()
	------------
		The Query parameters are added using the helper class HttpParams. The HttpParams is passed as one of the argument to HttpClient.get method.

		To use HttpParams, you need to import it first as shown below.

			import { HttpClient,HttpParams } from '@angular/common/http';

		Then create an instance of the HttpParams class.

			const params = new HttpParams()
			  .set('page', PageNo)
			  .set('sort', SortOn);

		And then call the httpClient.get method passing the params as the argument.

			return this._http.get<repos[]>(this.baseURL + 'users/' + userName + '/repos',{params})



ElementRef vs Renderer - Angular
--------------------------------

	In Angular 'Renderer' and 'ElementRef' are used for DOM Manipulation and Renderer and ElementRef are used together to get full platform abstraction.

	# Renderer –
		Renderer is a class that is a partial abstraction done the DOM manipulations and the DOM manipulating is not breaking server side rendering or web workers.

	# ElementRef –
		ElementRef is a class that is a partial abstraction done the DOM Manipulations without breakable environments and it also can hold a reference to a DOM elements.


		If "ElementRef" is injected to a component, the injected instance is a reference to the host element of the current component.

		The ways to get an ElementRef instance looks like,
			1. @ViewChild()
			2. @ViewChildren()
			3. @ContentChild()
			4. @ContentChildren()



How do we display errors in a component view with Angular?
----------------------------------------------------------
	we can use the properties "pristine" and "touched" to display error messages.

		1. If we want to display errors after the user fills something in a field, use the pristine property.
		2. If we want to display errors after the user put the focus on a field, use the touched property.

		<div *ngIf="(!loginForm.controls.email.valid && !loginForm.controls.email.pristine)">
			**Email is required.
		</div>



@Inject and @Injectable
-----------------------
	# @Inject decorator
		
		- @Inject() is a manual mechanism for letting Angular know that a parameter must be injected
		
		import { Component, Inject } from '@angular/core';
		import { ChatWidget } from '../components/chat-widget';

		@Component({
			selector: 'app-root',
			template: `Encryption: {{ encryption }}`
		})
		export class AppComponent {
			encryption = this.chatWidget.chatSocket.encryption;
			constructor(@Inject(ChatWidget) private chatWidget) { }
		}

	# @Injectable decorator



Angular Template Reference Variable
-----------------------------------

	A template reference variable is a way of capturing a reference to a specific element, component, directive, and pipe so that it can be used someplace in the same template HTML.

	Template Reference Variable Syntax –
		You can use a template reference variable by two ways.
		1.      Using hash symbol (#)
		2.      Using reference symbol (ref-)

	<input type="text" ref-cellnumber> //cellnumber will be a template reference variable.

	<input #cellnumber placeholder="Cell number">

	//cellnumber refers to the input element
	<button (click)="show(cellnumber)">click to see</button>

	show(cellnumber: HTMLInputElement){
		console.log(cellnumber.value);
	}



What Is Angular HttpInterceptor?
--------------------------------

	- HttpInterceptors is an interface which uses to implement the intercept method.
	
	- Intercepts HttpRequest and handles them.
	
	- Intercepts is an advanced feature that allows us to intercept each request/response and modify it before sending/receiving.

	- Interceptors can be used in two different phases in a life cycle of an HTTP request to a server, 

	- which are:

		# 1. Before making the request server:	
			- This happens before the call is made to server. It can be used change the request configuration of HTTP call. The most common use case for this is to add an Access Token to be sent to the server with each HTTP request so that it can be validated at server end.

		# 2. After Getting the response from server: 
			- This happens once we get the response from the server. It can be used change the response before it is being passed to the code block from where HTTP call was made. The most common use case for this is to Handle Global Error Handling across the app.


		my-interceptor.ts
		-----------------

			import { Injectable } from "@angular/core";
			import { tap } from "rxjs/operators";
			import { HttpRequest, HttpHandler, HttpEvent, HttpInterceptor, HttpResponse, HttpErrorResponse } from "@angular/common/http";
			import { Observable } from "rxjs/Observable";

			@Injectable()

			export class MyInterceptor implements HttpInterceptor {
				
				constructor() { }
				
				//function which will be called for all http calls
				intercept( request: HttpRequest<any>, next: HttpHandler ): Observable<HttpEvent<any>> {
					
					//how to update the request Parameters
					const reqHeader = request.clone({
						headers: request.headers.set("Authorization", "MyAuthToken")
					});
				
					return next.handle(reqHeader).pipe(
						tap( 
							event => {
								//logging the http response to browser's console in case of a success
								if (event instanceof HttpResponse) {
									console.log("api call success :", event);
								}
							},
							error => {
								//logging the http response to browser's console in case of a failuer
								if (event instanceof HttpResponse) {
									console.log("api call error :", event);
								}
							}
						)
					);
				}
			}

			After that you can configure your own interceptor service 'MyInterceptor' and 'HTTP_INTERCEPTORS' in the app Module.

		app.module.ts
		-------------
			import { NgModule } from '@angular/core';
			import { BrowserModule } from '@angular/platform-browser';
			import { HttpClientModule, HTTP_INTERCEPTORS } from '@angular/common/http';
			import { AppComponent } from './app.component';
			import { MyInterceptor } from './my-interceptor';

			@NgModule({
				imports: [BrowserModule, HttpClientModule],
				declarations: [AppComponent],
				bootstrap: [AppComponent],
				providers: [{ 
					provide: HTTP_INTERCEPTORS,
					useClass: MyInterceptor,
					multi: true
				}]
			})

			export class AppModule { }

	# HTTP_INTERCEPTORS 
		-	A multi-provider token which represents the array of HttpInterceptors that are registered.



List out the differences between ActivatedRoute and RouterState, with reference to Angular.
-------------------------------------------------------------------------------------------
	1.
		- ActivatedRoute consists of the information about a route associated with a component loaded in an outlet. 
		- RouterState represents the state in which the writer actually is.

	2.
		- We need ActivatedRouteSnapchat to traverse all the activated routes. 
		- during a navigation, after redirects have been applied, the router creates a RouterStateSnapshot.
	
	3.
		- ActivatedRouteSnapshot has old data. When route changes, ActivateRouteSnapshot has data from previous route.
		- the RouterState cares about application components, or, to be more specific, about their arrangements.



What would you have in a shared module in Angular?
-------------------------------------------------

	https://alligator.io/angular/providers-shared-modules/

	- Shared module is used to import the services in both eager and lazy loaded module.

	- We all know that lazy loaded modules create their own branch on the dependency injection tree. 

	- Shared module consists of the services that are registered by the angular in the root app injector. 

	- For this, we need not import it in the lazy module because lazy loaded modules already have access to the services defined at the root. 

	- Components, pipes and directives are also defined in the shared module. 

	- Other modules that import the shared module can use it in their templates. 

	- This means that the modules can be imported normally in the lazy loaded module. 

	- The shared module contains the code that will be used across the applications and featured modules. 

	- It also consists of the common template components. 

	- "Dumb components" should also be present in the shared module. 

	- It typically consists of some common angular modules too. 

	- When you are importing the shared module, you will also need to import the module with its providers, because there is no app module in the test.



What do you mean by a structural directive in Angular
-------------------------------------------------
	- Structural directives are used to manipulate DOM in angular. 

	- Structural directives are responsible for HTML layout. 

	- By adding, removing, or manipulating LMNs in angular, they shape or reshape the structure of DOM. 

	- This structural directive is applied to a host element with the help of other directives. 

	- The directives then do whatever it is supposed to do with that host element and its descendants.

	- Structural directives can be easily recognized. 

	- It can also delay the instantiation of a component or an element. 

	- It can also be used for cosmetic effect or manually handling the timing of the loading of components.

	- Structural directives are bound to a template. 

	- The two most common structural directives are "ngIf" and "ngFor". 

	- The process occurring in a structural directive is dynamic.



What is the difference between constructor and ngOnlnit in Angular
------------------------------------------------------------------
	1.
		- ngonInit is just a method in a class which structurally is not different to any other method in a class. 
		- a constructor is a completely different thing. It will be called when an instance of a class is created.
	
	2.
		- A class constructor in angular is used to inject dependencies, which is called constructor injection pattern.
		- when ngOnInit is called, it has finished creating a component DOM, injected all required dependencies through constructor and processed input bindings.
	
	3.
		- A constructor is a default method of the class that is executed when the class is instantiated. 
		- ngOnInit is a life cycle hook called by Angular 2 to indicate that angular is done creating the component.
	
	4.
		- ngOnInit relies on the binding of the component.
		- it is not the case when a constructor is used.



How to cache an observable data in Angular
------------------------------------------
	- Caching of an observable data is done with the help of "observable.cache". 

	- We can use caching in order to cache the response in the memory and then, on the next subscription, instead of requesting the remote server again. 

	- This operator is used at the end of the string. Caching is important for the performance, especially on bandwidth restricted devices and slow networks. 

	- You should have a good understanding of caching while working with promises but while translating it to observable, it is a bit difficult. Therefore, when interacting with observables, we typically set up a subscription on the consumer side and react to values coming through the pipe. 

	- We can easily add caching to the observables by adding publishReplay(1) and refCount.



CommonModule
------------
	- Exports all the basic Angular directives and pipes, such as NgIf, NgForOf, DecimalPipe, and so on. 

	- Re-exported by BrowserModule, which is included automatically in the root AppModule when you create a new app with the CLI new command.

	- The providers options configure the NgModule's injector to provide localization dependencies to members.
	
	- The exports options make the declared directives and pipes available for import by other NgModules.



Getting & Setting HTML Meta Tags in Angular
-------------------------------------------
	Angular's Meta service makes it easy to get or set different meta tags depending on the current active route in your app.

	addTag & addTags
	----------------
		Using the Meta service is as easy as importing it from @angular/platform-browser and injecting it in a component or service of yours.

		import { Component } from '@angular/core';
		import { Meta } from '@angular/platform-browser';

		@Component({
			selector: 'app-home',
			templateUrl: './home.component.html',
			styleUrls: ['./home.component.css']
		})
		export class HomeComponent {
			constructor(private _meta: Meta) {
				this._meta.addTag({ name: 'twitter:card', content: 'summary_large_image' });
				this._meta.addTag({ name: 'twitter:site', content: '@alligatorio' });
				this._meta.addTag({ name: 'twitter:title', content: 'Front-end Web Development, Chewed Up' });
				this._meta.addTag({ name: 'twitter:description', content: 'Learn frontend web development...' });
				this._meta.addTag({ name: 'twitter:image', content: 'https://alligator.io/images/front-end-cover.png' });
			}
		}


		With multiple meta tags like the example above, you can use the addTags method instead to set them all in the same call:

		this.meta.addTags([
		  { name: 'twitter:card', content: 'summary_large_image' },
		  { name: 'twitter:site', content: '@alligatorio' },
		  // ...
		]);


	getTag & getTags
	----------------

		- getTag takes an attribute selector string and returns an 'HTMLMetaElement'. 

		- getTags also takes an attribute selector, but returns an array with potentially multiple HTMLMetaElements that match the selector.

		constructor(private meta: Meta) {
			const viewport = this.meta.getTag('name=viewport');
			console.log(viewport.content); // width=device-width, initial-scale=1
		}


	updateTag
	---------
		- Given a new meta tag definition and a selector, the updateTag method will update any tag that matches the selector. 

		- In the following somewhat contrived example, we first set a meta tag with a content of summary_large_image and then update it to just summary:

		constructor(private meta: Meta) {
			this.meta.addTag(
				{ name: 'twitter:card', content: 'summary_large_image' }
			);

			this.meta.updateTag(
				{ name: 'twitter:card', content: 'summary' },
				`name='twitter:card'`
			);
		}


	removeTag & removeTagElement
	----------------------------

		The removeTag method takes a string for an attribute selector and removes the tag. Not that you’d ever want to do this, but here’s how you could remove the charset meta tag:

			constructor(private meta: Meta) {
				this.meta.removeTag('charset');
			}

		The removeTagElement is similar, but instead takes an HTMLTagElement directly instead of a string selector. Here’s the same example, but here we first get the charset meta tag element:

			constructor(private meta: Meta) {
				const chartsetTag = this.meta.getTag('charset');
				this.meta.removeTagElement(chartsetTag);
			}



E2E Testing Angular Applications
--------------------------------
	https://alligator.io/angular/e2e-testing-testcafe/



Animating Route Changes in Angular
----------------------------------
	https://alligator.io/angular/animating-route-changes/


What is RESTful API
-------------------
	An architectural style called REST (Representational State Transfer) advocates that web applications should use HTTP as it was originally envisioned. Lookups should use GET requests. PUT, POST, and DELETE requests should be used for mutation, creation, and deletion respectively.

