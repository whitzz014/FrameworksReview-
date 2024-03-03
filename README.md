# Frameworks Exam 1

## Week 1

### Getting Started 
--- 
#### Instructions:
- Angular is not like a standalone language and needs some prerequisites in order to run correctly 
- Node.js and NPM (node package manager) need to be installed 
- Angular uses NPM for package managment 

#### Installing angular cli 
- npm install -g @angular/cli

##### Create a Project 
- ng new learning-angular

##### Run first command
- cd in the project and npm start (visit http://localhost:4200)

### Angular 
--- 
There are a lot of packages automatically installed

#### important ones 
- Package.json 
- Tsconfig.json 
   - In tsconfig it is reccomneded to change "compileOnSave" to true 
### app.component.ts 
--- 
- @component aka a decorator 
    - the decorator will give info about the component 
- pointing at some selector called `app-root` 
- In this case it tells angular how this component will be used with the selector 
    - `app-root` is a tag name for this component that hold pointers to the `HTML & CSS` files are stored
```
@Component({
  selector: 'app-root',
  standalone: true,
  imports: [RouterOutlet, NgForOf, ContentListComponent, ContentListItemComponent],
  templateUrl: './app.component.html',
  styleUrl: './app.component.css'
})
```

### index.html 
```
<app-root></app-root>
```
- This is how it knows this is where it is going to generate the template to inject that right there on line 11  
`this tag repersents a key idea behind building templates, Angular allows use to define our own tags which can be used as another type of placeholder in an HTML file.`

### HTML saftey
- Angular data interpolation using handlebars tries it's very best to be safe
    - it does `NOT` allow HTML injection easily 
        ``` 
        title =  "<h1> Hello world! </h1>";
        ```
    This would display as `<h1> Hello world! </h1>` being printed to the screen

- We can get around this by a slighlty different way of displaying data
    ``` 
    Welcome to <span [innerHtml] = "title" ></span>!
    ```
    Now we can add HTML to our data in the TS file    
    - This method leverages the innerHtml property that span tags have 
This is another way to do `on-way data binding`

### SCSS vs CSS 

<strong>Syntax</strong>: Css follows a plain-text syntax, SCSS follows a more structured syntax  which allows us to use things like variables and nest and mixins.

<strong>Variable</strong>: SCSS allows you to define vars to store commonly use values such as colours, font sizes and spacing

<strong>Nesting</strong>: SCSS allows you to nest selectors within other selectors, making it easier to write and read complex stylesheets

<strong>Mixins</strong>: SCSS allows you to create reusable code snippets using mixins, which are like funcs in programming languages 

<strong>File Extensions</strong>: CSS.css SCSS.scss

<strong>Compilation</strong>: CSS files are interpreted by the web browser, SCSS file s must be preprocessed into standard CSS file using a preprocessor such as Sass 

### Refernces 
https://angular.io/

https://www.typescriptlang.org/docs/handbook/typescript-in-5-minutes.html


## Week 2 

### What is TypeScript?
--- 
- TypeScript is a strongly typed programming language that builds on JavaScript
- TypeScripts adds additional syntax to JavaScript to support a tighter integration with your editor 
- TypeScript code converts to JavaScript, which runs anywhere JavaScript runs: In a browser, on Node.js or Deno and in your apps 
- TypeScript understands JavaScript and uses type inference to give you great tooling without additional code 

![alt text](image.png)
![alt text](image-1.png)
![alt text](image-2.png)

### TypeScript 
---
- Since TS is type safe, you `CANNOT` change the type of this dynamically like you can in JS 
![alt text](image-3.png)

- Vars can still get there type implicitly (unfortunately)
![alt text](image-4.png)

### Default Types 
---
- number - integer and decimal number values 
- boolean - true or false , 0 and 1 are not valid 
- string  - any sequence of characters 
- void - usually used to describe the type of method when it has no return 
- any - this is what you can use to describe the type of any variable or method 
    - ex. it can desctibe a primitive we've outlined above or it can be an object 

### Interfaces 
- These allow us to make custom types, that would otherwise be nameless obj
- We can generate them with the following command using a schema built into TS 
``` 
ng generate interface models/IContent
```
- This is only an option if you can run ng commands in the terminal directly 
- In JS, the fundamental wat that we group and pass around data is through objs. In TS, we repersent those through obj types. 
![](image-5.png)
    - or they can be named by using either an interface: 
![alt text](image-6.png)
    - or a type alias :  
![alt text](image-7.png)
- All 3 examples above, we've written functions that take objects that contain the property name(string) and age(number)

#### TS Type Cheat Sheet 
https://www.typescriptlang.org/cheatsheets\

### Adding it to our package.json 
--- 
We could also add the generate interface command to our list of scripts in the package.json, to make it runnable through npm 
``` 
"generateInteface" : "ng generate interface"
```
Now we can run it in the terminal 
```
npm run-script generateInterface models/IContent
```

### The Resulting IContent Interface 
---
- It will generate an exported <i>Interface</i> of that same name
- We can add properties to the interface   
![alt text](image-8.png)

---

![alt text](image-9.png)

### TypeScript 
--- 
Some Variables can be set as optional 
` body?: string`   
- We can ever set default values by using an = sign 
    `public fName: string = "Luffy";`
### Example : Wish List 
--- 
- Create a class to store WishItem   
![alt text](image-10.png)
- Add into your WishItem.ts file:   
![](image-11.png)
- Go to app.component.ts and import WishItem Class   
![alt text](image-12.png)
- Add Data:   
![alt text](image-13.png)
- remove default stuff from app.component.html and add:    
![alt text](image-14.png)
### Looping in Angular 
---
- We are able to use what is called a <strong>directive</strong> inside the html to access a few of our JS loops.
- Traditonally you want to use a for loop `for(let i = 0; i<length; i++)` but that is really needed 
- We can make use of JS `For Of` loop to access each individual element and then iterate over the array until the end 
 ![alt text](image-15.png)
 #### Checkboxs 
 ![alt text](image-16.png)

 ### Conditional Logic 
 ![alt text](image-18.png)
    
#### app.component.ts 
- There is a couple ways to fix this. The Javascript approach would be to make our items array of type any. But, we’re better than Javascript, what would be a better type? 

 ![alt text](image-17.png)

