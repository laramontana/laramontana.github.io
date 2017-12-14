---
layout: post
title:      "Understanding fetch request in asynchronous actions "
date:       2017-12-14 22:54:00 +0000
permalink:  understanding_fetch_request_in_asynchronous_actions
---

Working on my travia app helped me at better understanding of fetch requests, specifically when you need to dispatch asynchronous actions in the react-redux project. First of all, you need to dispatch “useless” `action.type`, so after it is dispatched, reducer does not do much and returns the default or current state. In the example below the line `dispatch({type: 'LOADING'}) `would take care of this. Or if you know that your next request will properly take a while, you can set some behaviour while data is loading, such as animation or message for a user. 

 ```
fetchCategories() {
  return function(dispatch){
    dispatch({type: 'LOADING'})
    return fetch('http://www.jservice.io/api/categories?count=48')
      .then(res => {
        return res.json()
      }).then(categories => {
        dispatch({type: 'FETCH_CATEGORIES', payload: categories})
    })
  }
}
```

Secondly, you make a fetch request to url, which returns a promise, which needs to be handled by a function like` .then()`. Inside this function you call a callback in order to tell the promise what you want to do with this data next. As you can see, you can chain multiple `.then()` functions after each other, having a return value of previous function as an argument for the next one.   
It is also useful to handle errors for cases, when promise does not have ok status. 

 ```
fetch('http://www.jservice.io/api/categories?count=48')
      .then(res => {
        return res.json()
      }).catch(error => {
//handle error
)}
```

 

