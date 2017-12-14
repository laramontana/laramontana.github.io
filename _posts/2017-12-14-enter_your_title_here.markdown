---
layout: post
title:      "Enter your title here"
date:       2017-12-14 23:45:27 +0000
permalink:  enter_your_title_here
---


‘Props’ (short for properties) is one of the main concepts in React. Every component has props and they are accessible via `this.props`. A parent component can pass data or functionality to it’s child via props: 

```
var value1 = {name: «Sergey», surname: «Brin»};
<MyComponent data={value1} oneMoreValue={[1,2,3,4,5]} />
```

`this.props` is used for reading only, so you cannot change props, which were already passed from the outside of the component. However you can still manipulate over this data in order to render it. 

Let us look at the differences between `props` and `state` as it is important to decided what use for which purposes.  
Unlike `props`, you can change the `state` of the current component. To do so there is a function `this.setState()` where you pass in an object. This object will get merged with the current `state`. When updating `state`, we do not have to pass in the entire state, just the property we want to update. When the `state` has been updated, the component re-renders automatically.  Another important thing to keep in mind is that `state` changes happen asynchronously. If you need the access to your new `state` after it has been updated, you have to add a callback as a second argument to the `this.setState()` function. In this case callback function will get invoked once the `state` has been updated, ensuring that `this.state` is now the new updated state. 

```
handleOnClick = () => {
  this.setState(
    {
      hasBeenClicked: true,
    },
    () => console.log(this.state.hasBeenClicked)
  ); // prints true
};
```



