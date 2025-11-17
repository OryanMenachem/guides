# Jest Functions Guide

Jest is a testing framework for JavaScript. Here are the most common functions:

## Test Functions

**describe(name, callback)**
Groups related tests together. Helps organize your test suite.
```javascript
describe('Math functions', () => {
  // tests go here
});
```

**test(name, callback)** or **it(name, callback)**
Defines a single test. Both `test` and `it` do the same thing.
```javascript
test('2 + 2 equals 4', () => {
  expect(2 + 2).toBe(4);
});
```

## Assertion Functions

**expect(value)**
Starts an assertion. You chain matchers after it to check if something is true.

**toBe(value)**
Checks if the value equals the expected value (uses ===).
```javascript
expect(5).toBe(5);
```

**toEqual(value)**
Checks if objects or arrays have the same content (deep comparison).
```javascript
expect({name: 'John'}).toEqual({name: 'John'});
```

**toContain(item)**
Checks if an array or string contains a specific item.
```javascript
expect([1, 2, 3]).toContain(2);
```

**toThrow()**
Checks if a function throws an error.
```javascript
expect(() => { throw new Error('Oops'); }).toThrow();
```

**toBeNull(), toBeUndefined(), toBeDefined()**
Checks for null, undefined, or defined values.

**toBeTruthy(), toBeFalsy()**
Checks if a value is truthy or falsy.

**toBeGreaterThan(value)** and **toBeLessThan(value)**
Compares numbers.
```javascript
expect(10).toBeGreaterThan(5);
```

## Setup and Teardown

**beforeEach(callback)**
Runs before each test in the describe block.
```javascript
beforeEach(() => {
  // setup code
});
```

**afterEach(callback)**
Runs after each test in the describe block.

**beforeAll(callback)**
Runs once before all tests in the describe block.

**afterAll(callback)**
Runs once after all tests in the describe block.

## Mocking Functions

**jest.fn()**
Creates a fake function you can track and control.
```javascript
const mockFunc = jest.fn();
mockFunc(5);
expect(mockFunc).toHaveBeenCalledWith(5);
```

**jest.spyOn(object, methodName)**
Watches a function on an object without changing it.

**jest.mock(moduleName)**
Replaces an entire module with a fake version for testing.

## Common Assertions with Mocks

**toHaveBeenCalled()**
Checks if a mock function was called.

**toHaveBeenCalledWith(arguments)**
Checks if a mock was called with specific arguments.

**toHaveBeenCalledTimes(number)**
Checks how many times a function was called.