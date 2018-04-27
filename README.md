### Show Canary Release

This package provides a function that allows for gradually shifting assignments from one to another, without changing the assignments for those users that have already been shifted. It is deterministic.

This functionality is achieved by hashing a given salt, such as `${userId}.${salt}` onto an index of 0 - 100. This assures that users will always hash to the same number, allowing for the gradual shifting of more and more users to the canary.

#### Usage

`npm install --save show-canary`

```js
import showCanary from "show-canary";

const userId = "user-1";
const salt = "some-salt";

// percent of users to see canary. increasing this will continue
// to show previously assigned users the canary, so they will not "jump"
// between versions
const weight = 10;

if (showCanary(`${userId}.${salt}`, weight)) {
    // canary stuff
} else {
    // default stuff
}
```
