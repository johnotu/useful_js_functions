# Useful JS Functions
Some of the functions I find myself writing frequently when writing APIs. 

### Verify that a phone number is valid
This function takes a number (String) and checks if there are 11 digits, the first number should be 0 else if there are 10 digits, the first number should not be 0.

```
const isValidPhoneNumber = number => {
  return /^[0][1-9]\d{9}$|^[1-9]\d{9}$/.test(number);
}
```


### Verify that an amount is in the correct format
If you are receiving an amount as input, you'll want to make sure that it comprises of numbers and does not begin with a 0.

```
const isValidAmount = amount => {
  return /^(?!(0))[0-9]*$/.test(amount);
}
```


### Return missing parameters
When trying to ensure a user sends all required params in a request to an endpoint, it's good to let them know the ones that are missing if any. Assuming Express request Object **req**, this can be used for both body (`req.body`) and query (`req.query`) params.
_params_ is an array of string parameters.

```
const missingParameters = (params, req) => {
  return `Missing parameters: ${params.filter(param => req.body[param] === undefined || req.body[param] === null).join(, )}`;
}
```