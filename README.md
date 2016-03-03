# Core-concepts in buidling JavaScript Frameworks

Case studies

+ [dirty-checking](#user-content-dirty-checking)
+ automatic event registration
+ observable models
+ delegate events
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


# Dirty Checking

```javascript

function MVCInterface () {
  return {
    Model: {},
    View: {},
    Controller: {}
  }
}

const TabComponent = (function () {


  
  // create a new mvc component
  let Tab = new MVCInterface();
  
  
  Tab.Model.defaults = {
    index: 0
  }
  
  Tab.Model.isDirty = function (index) {
    return this.model.defaults.index === index;
  }
  
  
  // targets a tab
  Tab.View.tabs = $('.tabs');
  Tab.Controller.initialize = function () {
    this.bindEvents();
  }
  Tab.Controller.bindEvents = function () {
    Tab.View.tabs.click(this.onClickTabs.bind(this));
  } 
  
  Tab.Controller.unbindEvents = function () {
    Tab.View.tabs.unbind();
  }
  
  Tab.Controller.onClickTabs = function (evt) {
    const index = $(evt.currentTarget).index();
    // compare the current index and the selected index
    // update only if they are different
    if (Tab.Model.isDirty()) return;
    // update if not dirty
    Tab.Model.defaults.index = index;
  }
  
  
  
  return {
    start: function () {
      // initialize the controller
      Tab.Controller.initialize();
    },
    end: function () {
      Tab.Controller.unbindEvents();
    }
  }
})();


TabComponent.start();

```
