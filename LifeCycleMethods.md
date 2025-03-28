# Angular Lifecycle Hooks

## 1. ngOnChanges
**Trigger:** Called whenever one or more of the component's input properties (`@Input`) change value. It is also called on the first change check, even if no input property has changed.

**Purpose:** Detect and respond to changes to input properties, making updates within the component before the view is updated.

**Example:** Reacting to changes passed from a parent component to update the child component's state.

```typescript
import { Component, Input, OnChanges, SimpleChanges } from '@angular/core';

@Component({
  selector: 'app-child',
  template: `<p>Value: {{ value }}</p>`
})
export class ChildComponent implements OnChanges {
  @Input() value: number;

  ngOnChanges(changes: SimpleChanges) {
    console.log('Value changed:', changes.value.currentValue);
  }
}
```

---

## 2. ngOnInit
**Trigger:** Called only once, after the first `ngOnChanges` during a component's lifecycle.

**Purpose:** Ideal for initialization logic that needs to be performed after the input properties are available. This is a good place to fetch data from a service or perform initial setup.

**Example:** Calling an HTTP service to retrieve and initialize data for the component's display.

```typescript
import { Component, OnInit } from '@angular/core';
import { DataService } from './data.service';

@Component({
  selector: 'app-example',
  template: `<p>Data: {{ data }}</p>`
})
export class ExampleComponent implements OnInit {
  data: string;

  constructor(private dataService: DataService) {}

  ngOnInit() {
    this.data = this.dataService.getData();
  }
}
```

---

## 3. ngDoCheck
**Trigger:** Called for change detection during every cycle, right after `ngOnChanges` and `ngOnInit`.

**Purpose:** Implement custom change-detection logic.

**Example:** Manually tracking changes in an object.

```typescript
import { Component, DoCheck } from '@angular/core';

@Component({
  selector: 'app-check',
  template: `<p>Check called</p>`
})
export class CheckComponent implements DoCheck {
  ngDoCheck() {
    console.log('Change detection running');
  }
}
```

---

## 4. ngAfterContentInit
**Trigger:** Called only once, after the first `ngDoCheck` and after Angular has projected external content into the component's view (`<ng-content>`).

**Example:** Accessing projected content.

```typescript
import { Component, AfterContentInit, ContentChild, ElementRef } from '@angular/core';

@Component({
  selector: 'app-content',
  template: `<ng-content></ng-content>`
})
export class ContentComponent implements AfterContentInit {
  @ContentChild('contentRef') content: ElementRef;

  ngAfterContentInit() {
    console.log('Projected content:', this.content.nativeElement.innerText);
  }
}
```

---

## 5. ngAfterContentChecked
**Trigger:** Called after `ngAfterContentInit` and after every subsequent `ngDoCheck`.

**Purpose:** Respond to changes within projected content.

**Example:** Checking if projected content has changed.

```typescript
import { Component, AfterContentChecked } from '@angular/core';

@Component({
  selector: 'app-content-check',
  template: `<ng-content></ng-content>`
})
export class ContentCheckComponent implements AfterContentChecked {
  ngAfterContentChecked() {
    console.log('Projected content checked');
  }
}
```

---

## 6. ngAfterViewInit
**Trigger:** Called once after `ngAfterContentChecked` when Angular has fully initialized the component's view.

**Example:** Accessing a view element using `@ViewChild`.

```typescript
import { Component, AfterViewInit, ViewChild, ElementRef } from '@angular/core';

@Component({
  selector: 'app-view',
  template: `<p #textElement>Hello, World!</p>`
})
export class ViewComponent implements AfterViewInit {
  @ViewChild('textElement') text: ElementRef;

  ngAfterViewInit() {
    console.log('Text content:', this.text.nativeElement.innerText);
  }
}
```

---

## 7. ngAfterViewChecked
**Trigger:** Called after `ngAfterViewInit` and subsequent `ngDoCheck` checks.

**Purpose:** Respond to changes in the component's view.

```typescript
import { Component, AfterViewChecked } from '@angular/core';

@Component({
  selector: 'app-view-check',
  template: `<p>View Checked</p>`
})
export class ViewCheckComponent implements AfterViewChecked {
  ngAfterViewChecked() {
    console.log('View checked');
  }
}
```

---

## 8. ngOnDestroy
**Trigger:** Called just before Angular destroys the component/directive.

**Purpose:** Unsubscribe from observables, detach event listeners, and perform necessary cleanup to prevent memory leaks.

**Example:** Cleaning up an observable subscription.

```typescript
import { Component, OnDestroy } from '@angular/core';
import { Subscription } from 'rxjs';

@Component({
  selector: 'app-destroy',
  template: `<p>Destroy Example</p>`
})
export class DestroyComponent implements OnDestroy {
  subscription: Subscription;

  constructor() {
    this.subscription = new Subscription();
  }

  ngOnDestroy() {
    this.subscription.unsubscribe();
    console.log('Component destroyed');
  }
}
```

---

## **Important Notes:**
- You **don’t need** to implement all lifecycle hooks in a component. Use them only as needed.
- Be mindful of **performance implications**, especially when using `ngDoCheck`.
- Use `ngOnDestroy` to **clean up subscriptions, timers, and event handlers** to avoid memory leaks.

---

### 🚀 Happy Coding with Angular Lifecycle Hooks!

