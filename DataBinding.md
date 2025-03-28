# Angular Data Binding: One-Way & Two-Way

Data binding in Angular allows communication between a component and its template. Angular supports:
- **One-Way Data Binding** (Component → Template or Template → Component)
- **Two-Way Data Binding** (Component ⇌ Template)

## 1. One-Way Data Binding
One-way data binding can be from **Component to Template** or **Template to Component**.

### A. Component → Template
1. **String Interpolation (`{{}}`)**  
   - Transfers component data to the template as a string.
   - Example:
     ```html
     <h1>Welcome, {{ userName }}</h1>
     ```

2. **Property Binding (`[]`)**  
   - Transfers data without converting it to a string.
   - Example:
     ```html
     <input [value]="userName">
     ```

### B. Template → Component (Event Binding)
- Sends data from the template back to the component using `()`.
- Example:
  ```html
  <button (click)="increaseCount()">Increase</button>
  ```

---

## Task 1: Counter with Event Binding
**Requirements:**  
✅ Display a `count` value from the component in the template.  
✅ Clicking a button should increase the count.

**Hint:** Use `{{ count }}` for displaying and `(click)="increaseCount()"` for updating.

---

## Task 2: Show Even/Odd Status
**Requirements:**  
✅ Display whether the count is even or odd.  
✅ Use a flag in the top-right corner.

**Hint:** Use a ternary operator in the template:  
```html
<p>Count is: {{ count }} ({{ count % 2 === 0 ? 'Even' : 'Odd' }})</p>
```

---

## 2. Two-Way Data Binding
- Allows data transfer in both directions (Component ⇌ Template).
- Achieved using `[(ngModel)]`.

### Syntax:
```html
<input [(ngModel)]="email">
```

### Setup Steps:
✅ Import `FormsModule` in `app.module.ts`.  
✅ Add `FormsModule` to the `imports` array.

---

## Task 3: Login Form with Two-Way Data Binding
**Requirements:**  
✅ Create a form with `email` and `password` fields.  
✅ Display entered email and password immediately.  
✅ Show an alert **"Successfully Logged In"** when the button is clicked.

**Hint:**  
- Bind input fields using `[(ngModel)]`.  
- Use a button with `(click)` to show the alert.

---

### Need Help?
Would you like a complete Angular component code for these tasks? 😊

