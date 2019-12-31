# The Basics

- Started with repo "poc-react-react-boostrap"
- That one started with "npx create-react-app poc-react-react-bootstrap"
- Then applied basics of react-router-dom and react-boostrap
- Starting from here, I want to apply a basic Auth0 configuration for login
- In the beginning, App.js looks like this:

```jsx
import React from "react";
import { BrowserRouter as Router, Switch, Route, Link } from "react-router-dom";
import "bootstrap/dist/css/bootstrap.min.css";

import Nav from "react-bootstrap/Nav";
import Navbar from "react-bootstrap/Navbar";

export default function App() {
  return (
    <Router>
      <div>
        <Navbar bg="light">
          {/* 1st Nav item, mr-auto pushes the 2nd Nav item to the right */}
          <Nav className="mr-auto">
            <Nav.Item>
              <Nav.Link href="/">Home</Nav.Link>
            </Nav.Item>
            <Nav.Item>
              <Nav.Link href="/about">About</Nav.Link>
            </Nav.Item>
            <Nav.Item>
              <Nav.Link href="/users">Users</Nav.Link>
            </Nav.Item>
          </Nav>
          {/* 2nd Nav item, gets pushed to right because of mr-auto on first item */}
          <Nav>Status: Connected</Nav>
        </Navbar>

        {/* A <Switch> looks through its children <Route>s and
            renders the first one that matches the current URL. */}
        <Switch>
          <Route path="/about">
            <About />
          </Route>
          <Route path="/users">
            <Users />
          </Route>
          <Route path="/">
            <Home />
          </Route>
        </Switch>
      </div>
    </Router>
  );
}

function Home() {
  return <h2>Home</h2>;
}

function About() {
  return <h2>About</h2>;
}

function Users() {
  return <h2>Users</h2>;
}
```

# Adding Auth0

Here's my guess at what needs to happen

- Copy my streamlined react-auth-spa.js
- Create auth_config.json
- App.js: Add a "Profile" page that is protected
- App.js: Implement "PrivateRoute"
- Switch from Router to HashRouter
- index.js: Create onRedirectCallback
- index.js: Wrap <app> in <Auth0Provider>
