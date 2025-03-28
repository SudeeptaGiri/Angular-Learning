# Angular Basics

## What is Angular?

Angular is a popular open-source web application framework developed by Google. It is used to build dynamic, modern, and scalable web applications. Angular is a complete rewrite of AngularJS and follows a component-based architecture.

---

## Key Features of Angular

### 1️⃣ Component-Based Architecture
- Applications are organized into reusable and self-contained components.
- Each component consists of a **template, logic, and styles**.

### 2️⃣ Two-Way Data Binding
- Automatically synchronizes data between the **model** (data) and the **view** (UI).

### 3️⃣ Dependency Injection
- Manages application dependencies efficiently, promoting **modularity** and **testability**.

### 4️⃣ Directives & Templates
- Extends HTML with custom directives like `*ngFor`, `*ngIf`, and `ngClass`.

### 5️⃣ Routing & Navigation
- Built-in **Angular Router** for handling navigation in single-page applications (SPAs).

### 6️⃣ HTTP Client
- Simplifies making HTTP requests to communicate with a backend server.

### 7️⃣ Forms & Validation
- Supports **template-driven** and **reactive** forms with built-in validation mechanisms.

### 8️⃣ State Management
- Manages application state using **services**, **observables**, or libraries like **NgRx**.

### 9️⃣ Testing Support
- Built-in support for **unit testing** and **end-to-end testing** with Jasmine and Karma.

### 🔟 Cross-Platform Development
- Supports **PWA (Progressive Web Apps)**, **Mobile Apps (Ionic)**, and **Desktop Apps (Electron)**.

---

## How Angular Works

1️⃣ **Modules (`@NgModule`)** – Defines the structure of the application.
2️⃣ **Components (`@Component`)** – UI building blocks of the application.
3️⃣ **Templates & Directives** – Defines the view and behavior of components.
4️⃣ **Services & Dependency Injection (`@Injectable`)** – Manages business logic.
5️⃣ **Routing (`RouterModule`)** – Handles navigation and multiple views.
6️⃣ **Forms & HTTP Client** – Manages user input and API communication.

---

## Angular CLI (Command Line Interface)

The Angular CLI is a powerful tool for scaffolding, building, and managing Angular projects.

### 🛠 Install Angular CLI:
```bash
npm install -g @angular/cli
```

### 🚀 Create a New Angular Project:
```bash
ng new my-angular-app
cd my-angular-app
```

### ▶ Run the Application:
```bash
ng serve
```
Open `http://localhost:4200/` in your browser.

---

## Angular Project Structure

📂 `src/`
- 📁 `app/` → Contains components, services, and modules.
- 📄 `main.ts` → Entry point of the application.
- 📄 `index.html` → Main HTML file.
- 📁 `assets/` → Stores images and other static files.

📄 `angular.json` → Configuration for Angular CLI.
📄 `package.json` → Lists project dependencies.
📄 `tsconfig.json` → TypeScript configuration.

---

## Bootstrapping Angular Applications

Bootstrapping in Angular initializes the application and renders the root component.

- The **root module** (`app.module.ts`) is defined with `@NgModule`.
- The **root component** (`app.component.ts`) is declared and loaded.

Example:
```typescript
import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
import { AppComponent } from './app.component';

@NgModule({
  declarations: [AppComponent],
  imports: [BrowserModule],
  bootstrap: [AppComponent]
})
export class AppModule {}
```

---

## Summary 📝

✔ **Angular** is a frontend framework developed by Google.
✔ Uses **TypeScript** instead of JavaScript.
✔ Supports **SPA and PWA** development.
✔ Implements **Component-based architecture**.
✔ Provides **Powerful CLI tools** for development.
✔ **Bootstraps with `appModule`**.
✔ Follows **MVC principles** with built-in features like routing, HTTP requests, and state management.

🔗 **Further Learning**: [Angular Official Documentation](https://angular.io/docs) 🚀

