
--- 
tags: 
date: 2024-07-12

---
```js
function onSuccess(callback, order) {
    return callback(order);
}

function notify(order) {
    return { message: 'SUCCESS' };
}

function onError(order) {
    return { message: 'ERROR' };
}

// Grocery store API function 
function order(query, callbackSuccess, callbackError) {

    if (query.quantity > 0) {
        callbackSuccess();
    } else {
        callbackError();
    }
}

function orderFromGrocer(query, callbackSuccess, callbackError) {
    return order(query, callbackSuccess, callbackError);
}

function exampleSuccessCallback() {
    console.log('Order successful!');
}

function exampleErrorCallback() {
    console.log('Error placing the order.');
}

function postOrder(variety, quantity) {
    const query = { variety, quantity };
    const callbackSuccess = () => console.log(`Order placed for ${quantity} pieces of ${variety}`);
    const callbackError = () => console.log('Error placing the order.');
    return orderFromGrocer(query, callbackSuccess, callbackError);
}

module.exports = {
    onSuccess,
    notify,
    onError,
    orderFromGrocer,
    postOrder
}
```

```js
const { onSuccess, notify, onError, orderFromGrocer, postOrder } = require('./fruitPicker');

test('Notify your customer when their order was successful test', () => {
    const order = 'SUCCESS';
    const mockCallback = jest.fn(notify);

    onSuccess(mockCallback, order);
    expect(mockCallback).toHaveBeenCalledTimes(1);
    expect(mockCallback).toHaveBeenCalledWith(order);
    expect(mockCallback(order)).toEqual({ message: 'SUCCESS' });
});

test('Notify your customer when their order was unsuccessful test', () => {
    const order = 'ERROR';
    const mockCallback = jest.fn(onError);

    onSuccess(mockCallback, order);
    expect(mockCallback).toHaveBeenCalledTimes(1);
    expect(mockCallback).toHaveBeenCalledWith(order);
    expect(mockCallback(order)).toEqual({ message: 'ERROR' });
});

test('Order from grocer with successful order', () => {
    const query = { variety: 'pear', quantity: 12 };
    const mockSuccessCallback = jest.fn();
    const mockErrorCallback = jest.fn();

    orderFromGrocer(query, mockSuccessCallback, mockErrorCallback);
    expect(mockSuccessCallback).toHaveBeenCalledTimes(1);
    expect(mockErrorCallback).not.toHaveBeenCalled();
});

test('Order from grocer with unsuccessful order', () => {
    const query = { variety: 'pear', quantity: 0 };
    const mockSuccessCallback = jest.fn();
    const mockErrorCallback = jest.fn();

    orderFromGrocer(query, mockSuccessCallback, mockErrorCallback);
    expect(mockSuccessCallback).not.toHaveBeenCalled();
    expect(mockErrorCallback).toHaveBeenCalledTimes(1);
});

test('Post order with successful order', () => {
    const consoleSpy = jest.spyOn(console, 'log');
    postOrder('peach', 100);
    expect(consoleSpy).toHaveBeenCalledWith('Order placed for 100 pieces of peach');
    consoleSpy.mockRestore();
});

test('Post order with unsuccessful order', () => {
    const consoleSpy = jest.spyOn(console, 'log');
    postOrder('peach', 0);
    expect(consoleSpy).toHaveBeenCalledWith('Error placing the order.');
    consoleSpy.mockRestore();
});
```


NEW not working

```js
function notify(message) {
    console.log(message.message);
}

function order(query, onSuccess, onError) {
    setTimeout(() => {
        if (query.variety && query.quantity > 0) {
          onSuccess();
        } else {
          onError();
        }
      }, 1000);
}

function onSuccess() {
    notify({ message: 'SUCCESS' });
}

function onError() {

    notify({ message: 'ERROR' });
}


function orderFromGrocer(query, onSuccessCallback, onErrorCallback) {
    order(query, onSuccessCallback, onErrorCallback);
}
function postOrder(variety, quantity) {
    const query = { variety, quantity };
    orderFromGrocer(query, onSuccess, onError);
}

module.exports = {
    notify,
    order,
    onSuccess,
    onError,
    orderFromGrocer,
    postOrder
}
```

```js
const { notify, order, onSuccess, onError, orderFromGrocer, postOrder } = require('./fruitPicker'); // Replace 'fruitPicker' with the actual file name

jest.mock('./fruitPicker', () => {
  const originalModule = jest.requireActual('./fruitPicker');
  return {
    ...originalModule,
    notify: jest.fn(),
    order: jest.fn()
  };
});

describe('Order Tests', () => {
  beforeEach(() => {
    jest.clearAllMocks();
  });

  test('onSuccess should call notify with a success message', () => {
    onSuccess();
    expect(notify).toHaveBeenCalledTimes(1);
    expect(notify).toHaveBeenCalledWith({ message: 'SUCCESS' });
  });

  test('onError should call notify with an error message', () => {
    onError();
    expect(notify).toHaveBeenCalledTimes(1);
    expect(notify).toHaveBeenCalledWith({ message: 'ERROR' });
  });

  test('orderFromGrocer passes query and callback function arguments forward', () => {
    const query = { variety: 'apple', quantity: 10 };
    orderFromGrocer(query, onSuccess, onError);
    expect(order).toHaveBeenCalledTimes(1);
    expect(order).toHaveBeenCalledWith(query, onSuccess, onError);
  });

  test('postOrder composes a request to the grocer using the defined callbacks', () => {
    const variety = 'banana';
    const quantity = 5;
    postOrder(variety, quantity);
    expect(order).toHaveBeenCalledTimes(1);
    expect(order).toHaveBeenCalledWith(
      { variety, quantity },
      onSuccess,
      onError
    );
  });
});

```


### References:


---



