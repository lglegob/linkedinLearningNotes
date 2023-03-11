# React: Creating and Hosting a Full-Stack Site

- Shaun Wassell
- [GitHub Repo](https://github.com/LinkedInLearning/react-creating-and-hosting-a-full-stack-site-3209140)

## 1. Creating a React Front End

```npm
npx create-react-app sudokuSolverReact
```

```npm
npm start
```

### Creating the app component

- Customizing the install
  - app.js
    - delete header
    - add one header to see something
  - src folder
    - delete logo.svg

### Creating your blog pages

- src folder

  - create pages folder
  - in React, pages are usually just regular components, there is not a special type of component

- Basic structure for a page component

  ```js
  const HomePage = () => {
    return <h1>This is the Home Page</h1>;
  };

  export default HomePage;
  ```

- Then import all the components in App.js

- Routing

  - To be able to route, install the react Route Package by stopping the app and installing

    ```npm
    npm install react-router-dom
    ```

  - import some components

    ```js
    import { BrowserRouter, Routes, Route } from "react-router-dom";
    ```

  - Wrap all the App component withinthe <BrowserRouter>
  - And Wrap all the Pages components within <Routes>
  - And define for each Page a Route component

    ```js
    function App() {
      return (
        <BrowserRouter>
          <div className="App">
            <h1>My Awesome React App</h1>
            <div id="page-body">
              <Routes>
                <Route path="/" element={<HomePage />} />
                <Route path="/contact" element={<ContactPage />} />
                <Route path="/menu" element={<MenuCategoriesPage />} />
                <Route path="/legend" element={<TheLegendPage />} />
                <Route path="/whoweare" element={<WhoWeArePage />} />
                <Route path="/menu/:menuId" element={<MenuCategoriePage />} />
              </Routes>
            </div>
          </div>
        </BrowserRouter>
      );
    }
    ```

  ```

  ```
