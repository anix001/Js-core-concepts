currying is a functional programming technique that involves breaking down a function that takes multiple arguments into a series of functions that take one argument each. This creates a chain of functions, where each function returns another function until the final result is achieved.

Now here are some important things to understand.

1. A curried function that has only had some of its arguments passed, is incomplete and called a partial application.

2. Each step in the curried function has access to the closure scope of the function. This means when you pass the second argument, it has access to the previous argument and the current internal state of the curried function.

```
// when we only pass some of the args, we get a partial application
const partialApplication = curried(1)(2);
// we can finish our curried function by passing remaining args
const finalResult = partialApplication(3);
// this is also the equivalent of
const alsoFinalResult = curried(1)(2)(3);
```


Currying allows us to create new functions with some pre-defined data in their closure scope.


**WITHOUT CURRYING**
```

const createURL = (baseURL, path) => {
  const protocol = "https";
  return `${protocol}://${baseURL}/${path}`;
};

// create URLs for our main site
const homeURL = createURL("mysite.com", "");
const loginURL = createURL("mysite.com", "login");
const productsURL = createURL("mysite.com", "products");
const contactURL = createURL("mysite.com", "contact-us");

// create URLs for our careers site
const careersHomeURL = createURL("mysite-careers.com", "");
const careersLoginURL = createURL("mysite-careers.com", "login");
```

**WITH CURRYING**
```

const createURL = baseURL => {
  const protocol = "https";

  // we now return a function, that accepts a 'path' as an argument
  return path => {
    return `${protocol}://${baseURL}/${path}`;
  };
};

// we create a new functions with the baseURL value in it's closure scope
const createSiteURL = createURL("mysite.com");
const createCareersURL = createURL("mysite-careers.com");

// create URLs for our main site
const homeURL = createSiteURL("");
const loginURL = createSiteURL("login");
const productsURL = createSiteURL("products");
const contactURL = createSiteURL("contact-us");

// create URLs for our career site
const careersHomeURL = createCareersURL("");
const careersLoginURL = createCareersURL("login");
```