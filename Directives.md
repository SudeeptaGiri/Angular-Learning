# Angular Directives

Directives are used to **create, update, and manipulate** the DOM dynamically in Angular.

## Types of Directives
There are three types of directives in Angular:

### 1. Structural Directives
Structural directives work with conditions and dynamically update the DOM elements based on the specified condition.

#### i. `*ngIf`
- The `ngIf` directive is used to conditionally render elements in the DOM.
- It removes or adds elements based on the truthy or falsy value of the condition.

```html
<div *ngIf="isVisible">This text is visible only if isVisible is true.</div>
```

#### ii. `*ngSwitch`
- The `ngSwitch` directive allows you to conditionally display elements based on a matching value.

```html
<div [ngSwitch]="color">
  <p *ngSwitchCase="'red'">The color is Red</p>
  <p *ngSwitchCase="'blue'">The color is Blue</p>
  <p *ngSwitchDefault>Unknown Color</p>
</div>
```

#### iii. `*ngFor`
- The `ngFor` directive is used to loop through an array and display each element dynamically in the template.

##### Example:
**HTML:**
```html
<div *ngFor="let p of products" class="product">
  <img src="{{p.url}}" alt="{{p.title}}">
  <h2>{{p.title}}</h2>
  <p>{{p.price}}</p>
</div>
```

**TypeScript:**
```typescript
products = [
  {
    title: 'Samsung S23',
    price: 250,
    url: 'https://images.samsung.com/is/image/samsung/levant-galaxy-note10-plus-n975-sm-n975fzsdmid-backauraglow-thumb-182079707?$344_344_PNG',
  }
];
```

#### Task:
Create an array of **food or movie objects** and display them using `*ngFor` in the template.

---

### 2. Property Directives
Property directives are used to **define and modify** properties such as **class, styles, and other attributes** dynamically based on conditions.

##### Example:
```html
<p [class.red-text]="isError">This text will be red if isError is true.</p>
<p [style.color]="isError ? 'red' : 'green'">Conditional styling based on isError.</p>
```

##### TypeScript:
```typescript
isError = true;
```

---

### 3. Custom Directives
Custom directives allow you to define your own behavior for manipulating the DOM dynamically.

##### Example:
**Creating a simple custom directive to change background color:**

**TypeScript (Custom Directive):**
```typescript
import { Directive, ElementRef, Renderer2 } from '@angular/core';

@Directive({
  selector: '[appHighlight]'
})
export class HighlightDirective {
  constructor(el: ElementRef, renderer: Renderer2) {
    renderer.setStyle(el.nativeElement, 'backgroundColor', 'yellow');
  }
}
```

**Usage in Template:**
```html
<p appHighlight>This text has a highlighted background.</p>
```

---

### Summary:
1. **Structural Directives:** `*ngIf`, `*ngSwitch`, `*ngFor` modify the DOM structure based on conditions.
2. **Property Directives:** Modify attributes like class and style dynamically.
3. **Custom Directives:** Define your own behavior for DOM manipulation.



