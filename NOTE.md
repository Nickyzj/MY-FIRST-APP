# Study notes for Angular 4 

## 02 The Baisc
```
[sudo] npm install -g @angular/cli
```

```
ng new my-first-app
```

```
ng serve
```

[http://localhost:4200](http://localhost:4200)

### app.component.html
```html
<input type="text" [(ngModel)]="name">
<h1>
  {{name}}
</h1>
```

### app.component.ts

```javascript
@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  title = 'App works! Does this change?';
  name;
}
```

```
npm install --save bootstrap
```

### app.module.ts

```javascript
@NgModule({
  declarations: [
    AppComponent,
    ServerComponent
  ],
  imports: [
    BrowserModule,
    FormsModule,
    HttpModule
  ],
  providers: [
    
  ],
  bootstrap: [AppComponent]
})
export class AppModule { }
```

`ng generate component servers`

* select by tag
```
selector: 'app-servers',
```
* select by class
```
selector: '.app-server',
```

### 12 string-interpolation
```html
    <p>Server with ID {{ serverId }} is {{ serverStatus }}</p>

    call a method:
    <p>Call serverStatus(): {{ getServerStatus() }}</p>
```

### 13 property binding
```html
()
disable the button:
    <button 
        class="btn btn-primary" 
        [disabled]="!allowNewServer" 
        (click)="onCreateServer()">Add Server</button>

```

### 14 property binding instead of string inerpolation
```html
<p>{{ allowNewServer }}</p>
OR
<p [innerText]="allowNewServer"></p>
```

### 15 event binding
```javascript
onCreateServer() {
    this.serverCreationStatus = "Server was created.";
}
```

```html    
<button 
  class="btn btn-primary" 
  [disabled]="!allowNewServer" 
  (click)="onCreateServer()">Add Server</button>
<p>{{ serverCreationStatus }}</p>
```

### 16 event binding passing and using data
```html
use $event to fetch data:
<input
    type="text"
    class="form-control"
    (input)="onUpdateServerName($event)">
```
```javascript
onUpdateServerName(event: Event) {
    //console.log(event);
    this.serverName = (<HTMLInputElement>event.target).value;
}
```

### 17 two-way binding

```html
[()]
<input
        type="text"
        class="form-control"
        [(ngModel)]="serverName">
    <p>{{ serverName }}</p>
```

### 18 combine all forms of data binding

