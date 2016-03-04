# Core-concepts in buidling JavaScript Frameworks

Structure

+ MVC (Model-View-Controller)
+ MVP (Model-View-Presenter)
+ MVVM (Model-View-ViewModel)
+ MV* (Model-View-*)
+ HMVC (Hierachical Model-View-Controller)

Case studies

+ [dirty-checking](#user-content-dirty-checking)
+ automatic event registration
+ delegate events
+ observable models
+ two-way data binding
+ proxy
+ observer
+ mediator
+ facade
+ central data dispatcher
+ router
+ dom tranversing
+ components
+ mixins
+ session 

# Dirty Checking

Dirty checking can be done by checking each key-value pairs for changes or by listening to model changes in setters and getters.

# Automatic Event Registration (AER)

+ Register all components that might listen to something.
+ Register all events they might listen to.
+ For each listener method among the components, automatically bind the event to it.


# Super-patterns

A combination of different design patterns are called super-patterns

# Session 

Similar to Meteor's implementation of getting/setting the model across pages. Using the window.sessionStorage allows changes to be reflected on other tabs when a user carry out actions. The problem is how to remove the data that is no longer in used.

# Boilerplate MVC

```javascript

function MVCInterface () {
  return {
    Model: {},
    View: {},
    Controller: {}
  }
}

var SomeComponent = new MVCInterface();
```
