To write a [[jest]] test case we need to import the [[jest-runner]] using [[Require()]].

usually [[jest]] test case follows the [[expect modifiers matchers pattern]] and [[Asymmentric Matchers]], [[Assertion Count]], [[Extend Utilities]].

The extension for the [[jest]] is commonly uses as {file_name}.test.js;

[[test()]] has two params one is the output when that particular test case passed and another one is a [[callback function]] which executed the test case.

inside the [[callback function]] we need to specify the [[expect()]] and [[toBe()]] method.

```
//addFive.test.js

const {default: TestRunner} = require("jest-runner")
const addFive = require('./addFive');

test('returns the number plus 5', () => {
	expect(addFive(1)).toBe(6);
})
```