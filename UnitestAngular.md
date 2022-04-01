# Unit testing Guidelines for Angular latest version
***
[Read more on Angular IO](https://angular.io/guide/testing)

## Code coverage enforcement
- The code coverage percentages let you estimate how much of your code is tested. If your team decides on a set minimum amount to be unit tested, you can enforce this minimum with the Angular CLI.

  - For example, suppose you want the code base to have a minimum of 80% code coverage. To enable this, open the Karma test platform configuration file, karma.conf.js, and add the check property in the coverageReporter: key.
- Read shallow documentation before you start writing unit test cases for your project [Shallow Documentation](https://getsaf.github.io/shallow-render/)
- Avoid calling `instance.SomeMethod()` directly. Use component based testing in place of creating all test cases at one place.
- All services & dependencies in a component testing need to be mocked. Never call real services.
- All external `e.g. Http` calls are also need to be mocked. Never call real services from external site also
- When writing unit test cases related to `date, moment` make sure unit test passes in every date/time they run.
- If your test has async methods, make sure they are resolved before ending the test.
- Also make sure private methods inside component gets covered under unit testing.
- Try to mock your data using `Mock.of()`. this way you do not need to define values for every required field. In case you have defined your objects in place of mock add them under unit unit test.

## Unit testing angular components
- Mocking components dependencies using Shallow- service, pipes etc.
- Component `init` code - loading data on init, showing busy indicator, hiding busy indicators, calling services etc.
- Testing Observables/Subscriptions
- Showing UI elements depending on state/data fetched- spinner, error, child components
- Testing components `@Input & Output`
- Html tags and properties inside component html
- Posting data to services on events from HTML

## Unit testing angular service
- Calling external http services
- Sffo authorization
- Private methods in services
- Post http call
- Rxjs operators like - pipe, catchError, map
