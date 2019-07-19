
# Redux Musings

- _**Middleware** is some code you can put between the `framework receiving a request`, and the `framework generating a response`_**
- _The best feature of `middleware` is that `it's composable in a chain`. You can use multiple independent third-party middleware in a single project._
- _Redux provides a `third-party extension point` between dispatching an action, and the moment it reaches the reducer_

> ### How can we do it on our own ?

- _How to `dispatch` action and fix `monkey patching`_

> . 
```javascript
    function logger(store) {
          const next = store.dispatch //~ trap `dispatch` as ref
          return function dispatchAndLog(action) {
            /*
             * once done with the action dispatch ref
            **/
            console.log('dispatching', action)
            let result = next(action)
            console.log('next state', store.getState())
            return result
          }
    }
  
  ```

  > .

#### AND

  > **Note** : spend more time here to understand why reversed the middleware array!

  ```javascript
    function applyMiddlewareByMonkeypatching(store, middlewares) 
    {
    middlewares = middlewares.slice();
    middlewares.reverse() // Reversed to get the right order.
    //Transform dispatch function with each middleware.
    middlewares.forEach(middleware => (store.dispatch = middleware(store))) }

```

# Still It is Monkey-patching...!

- **_Why do we even overwrite `dispatch`?_**
        - To be able to call it later
        - Also every middleware can access the previously wrapped `store.dispatch`
        - Otherwise chaining would break
        - Here we are wrapping `function` over a `function` in series to get the desired chaining

# But there is Another way :)

- _The middleware could accept the `next()` dispatch function as a parameter **instead of reading it from the `store` instance**_

> ### inception moment :/'

```javascript
function logger(store) { 
    // created closure to get access to the `store`
  return function wrapDispatchToAddLogging(next) {
      // wrapping dispatch but are we creating the same Onion again
    return function dispatchAndLog(action) {
                console.log('dispatching', action)
                let result = next(action)
                console.log('next state', store.getState())
                return result
    }
  }
}
```

> ### Throwing ES6 to the mix !!

```javascript
	const logger = store =>  next =>  action => { 
			console.log('dispatching', action) 
			let result = next(action) 
			console.log('next state', store.getState()) 
			return result 
	} 
	const crashReporter = store =>  next =>  action => { 
			try { 
					return next(action)
			} catch (err) { 
					console.error('Caught an exception!', err) 
					Raven.captureException(err, 
					{ extra: { 
								action, 
								state: store.getState() 
							  } 
					}) 
					throw err 
				} 
	}
```

> ###  In the new arrangement

- _The middleware accepts the `next()` dispatch function_
- _Returns a **dispatch** function, which in turn serves as `next()` to the middleware to the left_

> ### Approach

- The new `applyMiddleware()` first obtains the fully wrapped dispatch function
- Then returns a copy of the `store` , which would use the fully wrapped dispatch function

> ### Similar to what Redux does internally
```javascript
// *not* Redux API.  
function applyMiddleware(store, middlewares) { 
	middlewares = middlewares.slice() 
	middlewares.reverse() 
	let dispatch = store.dispatch 
	middlewares.forEach(middleware => (dispatch = middleware(store)(dispatch))) 
	return  Object.assign({}, store, { dispatch }) 
}
```

- _Redux `applyMiddleware()` is similar, but **different in three important aspects**:_

    - It only **exposes a subset** of the [`store API`](https://redux.js.org/api/store) to the middleware: [`dispatch(action)`](https://redux.js.org/api/store#dispatch) and [`getState`](https://redux.js.org/api/store#getState)
    - It does a **bit of smart work** to make sure that if you call `store.dispatch(action)` from your middleware instead of `next(action)`, the action will actually travel the whole middleware chain again, including the current middleware.
    
    - _**This is useful for asynchronous middleware**_
    - To ensure that you may only **apply middleware once**, it operates on `createStore()` rather than on `store` itself. Which means whenever you are creating the `store` you have to pass in the `middlewares` , **which assumes the probability of you creating the same `store` again in the same application is from little to none ;)**
    - Instead of `(store, middlewares) => store`, its signature is `(...middlewares) => (createStore) => createStore`
