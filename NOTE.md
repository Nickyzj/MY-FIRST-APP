# Study notes for Angular 4 

`[sudo] npm install -g @angular/cli`

`ng new my-first-app`

`ng serve`

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

`npm install --save bootstrap`

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
`selector: 'app-servers',`
* select by class
`selector: '.app-server',`

### string-interpolation
```html
    <p>Server with ID {{ serverId }} is {{ serverStatus }}</p>
    <p>Call serverStatus(): {{ getServerStatus() }}</p>
```

### property binding
```html
()
    <button class="btn btn-primary" [disabled]="!allowNewServer" (click)="onCreateServer()">Add Server</button>

    <input
        type="text"
        class="form-control"
        (input)="onUpdateServerName($event)">
    <p>{{ serverName }}</p>
```
```javacript    
    onUpdateServerName(event: Event) {
        this.serverName = (<HTMLInputElement>event.target).value;
    }
    
```

### two-way binding

```html
<input
        type="text"
        class="form-control"
        [(ngModel)]="serverName">
    <p>{{ serverName }}</p>
```