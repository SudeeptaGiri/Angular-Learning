# Angular Basics

## Introduction
Angular is a frontend framework and developer platform developed by **Google** in **2012**. It is built upon **TypeScript (TS)**, unlike its previous version, which was based on **JavaScript (JS)**.

### **Use Cases**
- **SPA (Single Page Application)**
- **PWA (Progressive Web Apps)**

---
## Framework vs. Library

### **Library**
A library is predefined code for a **specific purpose**. For example, **React** is a library designed for **UI development**.

### **Framework**
A framework provides a **complete development package** with built-in features and tools.

### **Note:**
**Scaffolding** refers to generating specific code using **terminal commands**.

---
## Steps to Install Angular

1. **Install npm (Node Package Manager) and check version:**
   ```sh
   npm -version
   ```
2. **Install Angular CLI globally:**
   ```sh
   npm install -g @angular/cli
   ```
3. **Check Angular version:**
   ```sh
   ng v
   ```

### **Creating a New Angular Application**
1. Open **Terminal (Command Prompt)**
2. Run:
   ```sh
   ng new app-name --standalone=false
   ```
3. Select **CSS**
4. **Server-Side Rendering?** → Select **No**
5. **Run the application:**
   ```sh
   ng serve
   ng serve --o  # Opens in browser automatically
   ```

### **Default Server**
- **localhost:4200**

---
## Folder Structure

### **TypeScript Configuration Files**
- **`tsconfig.json`** → Defines rules for TypeScript compiler when converting TS into JS.
- **`.spec.json`** → Testing configurations.
- **`.app.json`** → Application configuration.

### **Package Files**
- **`package.json`** → Contains metadata of the project.
- **`package-lock.json`** → Stores package dependency metadata for `package.json`.

### **Git Ignore**
- **`.gitignore`** → Specifies files to be ignored by **Git** when storing in GitHub.

---
## Bootstrapping in Angular
Converting **static DOM** into **dynamic DOM** is called **Bootstrapping**.
- Angular **only bootstraps `appModule`**.

### **Application Structure**
- The entire application is divided into **components**.
- Each component has:
  - **`.ts`** (Component logic)
  - **`.spec.ts`** (Testing)
  - **`.html`** (Template/UI)
  - **`.css`** (Styling)
- Each component has a **selector** (name).
- All components are registered inside a **module**.

### **Important Files**
- **`app/index.html`** → Main HTML file containing `<app-root>`
- **`main.ts`** → Bootstraps `appModule`
- **`style.css`** → Global CSS file

---
### **Happy Coding! 🚀**

