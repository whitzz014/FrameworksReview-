# Frameworks Exam 1

## Week One 

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



   