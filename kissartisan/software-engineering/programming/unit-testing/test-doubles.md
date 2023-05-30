## Types of test doubles:
1. Dummy - nothing will return but needs to fill the parameter list
2. Mock - includes expectations on what method needs to be called
3. Stub - includes expectations on what needs to be returned


## Two types of approaches when testing test doubles:
1. Classical approach (Detroit approach)
* Try to use real object wherever you can.
* Only use test doubles if it's incredibly incovenient to use the real object.
* Only focused on the response.
* Keep it loose as possible to encourage refactoring
& If refactoring breaks the test, it was seen as downside

Good read about classical approach: [Testing on the Toilet: Test Behavior, Not Implementation](https://testing.googleblog.com/2013/08/testing-on-toilet-test-behavior-not.html)

2. Mockist approach (London approach)
* For any dependencies that is a simple value object, always mock out the dependency
* Test is aware of the API implementation
* Implementation of the testing is the core part of the test itself
* Expectations are assertions that this API behaves and sends the messages that you expect
