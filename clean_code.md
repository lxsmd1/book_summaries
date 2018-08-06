# Clean Code

_SUMMARY 1-3 paragraphs_

## Key Terms

- code-sense:
  - The ability to see bad code and know how to fix it by writing good code.
- refactoring:
  - objects: breakout into 2 or more objects
  - the extract method: one method that says more clearly what it does, and some sub-methods saying how it does it.
- meaningful naming:
  - use clear context and distinctions

## Chapter 1: Clean Code

Goes over in general what the issue with bad code is, and makes the case for writing good code as a matter of professionalism. TDD is the professional way to write good code. Continuous refactoring and tidying up any checked-out code, making it better than it was before you started working on it is key to keeping the system full of healthy and clean code.

### Key Rules of Clean Code

- Runs all the tests.
- Contains no duplicates.
- Expresses all the design ideas that are in the system.
- Minimizes the number of entities such as classes, methods, functions, and the like.

---

## Chapter 2: Meaningful Names

Naming can be hard, but will save time in the long run through readability and searching. Using naming conventions is handy if they are done right but needs to be updated along the way when names become more clear. Don't be afraid to rename something as an improvement to the code base.

### Strategies

- Use intention-revealing names: The name of a variable, function, or class, should answer all the big questions. Why it exists, what it does, and how it is used.

```ruby
# BAD
def d # elapsed time in days

# GOOD
def elapsed_time_in_days
```

- Avoid using misleading names

```rb
# BAD
accounts_list = [acct_1, acct_2]
# not a list but rather an array
# best not to use any object type in the name

# GOOD
accounts = [acct_1, acct_2]
```

- Make meaningful distinctions

```ruby
# BAD
def get_active_account
def get_active_account_info
def customer_info
def klass # this should not be used to get around naming collisions

# GOOD
# Pick a clear naming convention
def get_active_account
def get_customer
```

- Use pronounceable names
- Use searchable names
- Avoid encodings
- Avoid mental mapping
  - ex. i, j, k for small loops only
- Class names: noun or noun phrase names
  - ex. account or account_parser
- Method names: verb or verb phrase names
  - ex. post_payment or set_name
- Pick one word per concept
  - ex. fetch, retrieve, get are all the same
- Don't pun
  - ex. add used to increment or concat some values but then used to insert into a collection. Same word, different intent.
- Add meaningful context
  - long if blocks can be broken out into methods with clear names
  - Wrap in classes to help with context and readability

## Chapter 3: Functions

Functions should be short and single responsibility. Error handling is something so it should be handled in its own function. Functions should tell the story of the program and expose the intent with clear names and limited thoughtful arguments. Levels of abstraction is the key to keeping the functions separate and `srp`

### Strategies

- Small!:
  - 20 lines is the upper bounds
  - 80-100 char is max
  - if / else / while statements should only have single line or single method calls
    -  keeps them self documenting
- Do only one thing:
  - [abstraction](https://en.wikipedia.org/wiki/Abstraction_(computer_science))
  - Requires skill in articulating the abstraction layers and if you are adhering to only 1 of them
  - functions that are properly scoped can not be broken down into smaller sections

Levels of abstraction:
```js
  // high level
  getHtml()
  // intermediate level
  filePathName = File.open('../some_path', 'a+')
  // low level
  .append('\n')
```

- Step Down Rule:
  - The function should be read like a set of TO paragraphs
    - To include the setups and teardown, we include setups, then we include the test page content, and then we include the teardown's.
    - To include the setups we include the suite setup if this is a suite, then we include the regular setup.
    - To include the suite setup, we search the parent hierarchy for the "SuiteSetUp" page and add an include statement with the path of that page.
    - To search the parent ...
- Switch Statements:
  - Use sparingly and bury them in lower level classes
```ruby
  class Employee
    @is_payday = True
    @calculated_pay = 100
    @deliver_pay = (pay(@calculate_pay)
    @type = 'HOURLY'

    def calculate_pay
    def pay
        @calculate_pay
    def is_payday
    def deliver_pay

  class EmployeeFactory
    case Employee.type
    when 'HOURLY'
      HourlyEmployee.new(employee)
    when 'COMMISSIONED'
      CommissionedEmployee.new(employee)
    when 'SALARIED'
      SalariedEmployee.new(employee)
    else
      raise exception(InvalidEmployeeRecordType(employee.type))
    end
  end
```
- Use descriptive names
  - Longer and consistent names like `includeSetup-AndTeardownPages` or `includeSetupPages` help to tell the story when you read the code.
- Function Arguments
  - Preferred to be 0 but 1, 2, and 3 accepted.
  - Over 3 is not great and would need special consideration.
  - When passing a variable number of arguments, use an object as the values are likely related and deserve a separate class or at the least their own object.
```ruby
  def monad(count)
  def dyad(name, count)
  def triad(name, count, args)
```
  - Prefer return values over output argument.
  - When the arguments are events, make that clear.
  - Flag Arguments
```ruby
  render(true)
```
  - This declares that there is more than 1 thing happening in this function as there can be a false case that would be acted upon.
- Verbs and Keywords
```ruby
  # GOOD
  def write(name)
  # BETTER
  def write_field(name)
  # DYAD
  def assert_expected_equals_actual(expected, actual)
```
- Have no side effects
  - If a function does something then something else that is not in the name of the function, that is a side effect.
- Output Arguments
```js
  // BAD
  append_footer(d);
  // GOOD
  document.append_footer();
```
- Command Query Separation
  - Functions should do only 1 of these
    - do something, change the state of an object
    - answer something, return the held value of the object
```ruby
  # BAD
  if (set_attribute('username', 'unclebob'))
    do something...
  end

  # GOOD
  if attribute_exists('username')
    set_attribute('username', 'unclebob')
  end
```
- Prefer exceptions over return codes
  - Try and Catch blocks should be extracted from functions and called in an error handling function, leaving the function to do its one thing.
  - New exceptions are derivatives of the exception class and do not need recompilation.
- DRY

## Chapter 4: Comments

_summary_

### Strategies

- Explain yourself with code
```ruby
  # BAD
  # check to see if employee is eligible for benefits
  if (employee.flags && HOURLY_FLAG) && (employee.age > 65)

  # GOOD
  if employee.isEligibleForBenefits?
```
