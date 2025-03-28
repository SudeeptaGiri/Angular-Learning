# Angular Components and Communication

## Component
A **Component** is the logical division of the User Interface in Angular. Each component consists of four main files:

1. `component.ts` - Logic and functionality (Component class)
2. `component.html` - UI structure (Template)
3. `component.css` - Styling (Stylesheet)
4. `component.spec.ts` - Testing (Unit tests)

Every component has a unique **selector** that determines where the component appears in the application.

### Nesting Components
One component inside another is called **nesting of components**:
- **Container components** are called **parent components**.
- **Inner components** are called **child components**.

### Creating a Component
Use the Angular CLI command to generate a new component:
```sh
ng generate component component-name
```

---

## Component Communication
Components communicate with each other in three ways:
1. **Parent to Child**
2. **Child to Parent**
3. **Component to Component** (using services)

### 1. Parent to Child Communication
The **parent** component sends data to the **child** component using `@Input()`.

#### Example:
**Parent Component (`parent.component.html`)**
```html
<app-child [title]="'Hello Child'" ></app-child>
```

**Child Component (`child.component.ts`)**
```typescript
import { Component, Input } from '@angular/core';

@Component({
  selector: 'app-child',
  template: `<p>{{ title }}</p>`
})
export class ChildComponent {
  @Input() title: string;
}
```

### 2. Child to Parent Communication
The **child** component sends data to the **parent** using `@Output()` and `EventEmitter`.

#### Example:
**Child Component (`child.component.ts`)**
```typescript
import { Component, Output, EventEmitter } from '@angular/core';

@Component({
  selector: 'app-child',
  template: `<button (click)="sendMessage()">Send Message</button>`
})
export class ChildComponent {
  @Output() messageEvent = new EventEmitter<string>();

  sendMessage() {
    this.messageEvent.emit('Hello from Child!');
  }
}
```

**Parent Component (`parent.component.ts`)**
```typescript
import { Component } from '@angular/core';

@Component({
  selector: 'app-parent',
  template: `
    <app-child (messageEvent)="receiveMessage($event)"></app-child>
    <p>Received Message: {{ receivedMessage }}</p>
  `
})
export class ParentComponent {
  receivedMessage: string;

  receiveMessage(message: string) {
    this.receivedMessage = message;
  }
}
```

### 3. Component to Component Communication
To communicate between sibling components, we use **services**.

#### Example:
1. **Create a Service (`message.service.ts`)**
```typescript
import { Injectable } from '@angular/core';
import { BehaviorSubject } from 'rxjs';

@Injectable({ providedIn: 'root' })
export class MessageService {
  private messageSource = new BehaviorSubject<string>('');
  currentMessage = this.messageSource.asObservable();

  changeMessage(message: string) {
    this.messageSource.next(message);
  }
}
```

2. **Component 1 (`sender.component.ts`)**
```typescript
import { Component } from '@angular/core';
import { MessageService } from '../message.service';

@Component({
  selector: 'app-sender',
  template: `<button (click)="sendMessage()">Send</button>`
})
export class SenderComponent {
  constructor(private messageService: MessageService) {}

  sendMessage() {
    this.messageService.changeMessage('Hello from Sender!');
  }
}
```

3. **Component 2 (`receiver.component.ts`)**
```typescript
import { Component, OnInit } from '@angular/core';
import { MessageService } from '../message.service';

@Component({
  selector: 'app-receiver',
  template: `<p>Message: {{ message }}</p>`
})
export class ReceiverComponent implements OnInit {
  message: string;

  constructor(private messageService: MessageService) {}

  ngOnInit() {
    this.messageService.currentMessage.subscribe(message => this.message = message);
  }
}
```

---

## Using `@ViewChild`
The `@ViewChild()` decorator allows a parent component to access a child component’s properties and methods.

### Example:
**Parent Component (`parent.component.ts`)**
```typescript
import { Component, ViewChild, AfterViewInit } from '@angular/core';
import { ChildComponent } from './child.component';

@Component({
  selector: 'app-parent',
  template: `<app-child></app-child>`
})
export class ParentComponent implements AfterViewInit {
  @ViewChild(ChildComponent) child: ChildComponent;

  ngAfterViewInit() {
    this.child.childMethod();
  }
}
```

**Child Component (`child.component.ts`)**
```typescript
import { Component } from '@angular/core';

@Component({
  selector: 'app-child',
  template: `<p>Child Component</p>`
})
export class ChildComponent {
  childMethod() {
    console.log('Child component method called.');
  }
}
```

---

## Summary
- **Components** are UI building blocks in Angular.
- **Communication between components** is done using:
  - `@Input()` for **Parent to Child**
  - `@Output()` for **Child to Parent**
  - **Services** for **Component to Component**
  - `@ViewChild()` to access a **Child Component** from a **Parent Component**.
- Use **Angular CLI** to generate components:
  ```sh
  ng generate component component-name
  ```

