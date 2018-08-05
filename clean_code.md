# Clean Code

_SUMMARY 1-3 paragraphs_

## Key Terms

* code-sense:
  * The ability to see bad code and know how to fix it by writing good code.
* refactoring:
  * objects: breakout into 2 or more objects
  * the extract method: one method that says more clearly what it does, and some sub-methods saying how it does it.
* meaningful naming:
  * use clear context and distinctions

## Chapter 1: Clean Code

Goes over in general what the issue with bad code is, and makes the case for writing good code as a matter of professionalism. TDD is the professional way to write good code. Continuous refactoring and tidying up any checked-out code, making it better than it was before you started working on it is key to keeping the system full of healthy and clean code.

### Key Rules of Clean Code

* Runs all the tests.
* Contains no duplicates.
* Expresses all the design ideas that are in the system.
* Minimizes the number of entities such as classes, methods, functions, and the like.

---

## Chapter 2: Meaningful Names

Naming can be hard, but will save time in the long run through readability and searching. Using naming conventions is handy if they are done right but needs to be updated along the way when names become more clear. Don't be afraid to rename something as an improvement to the code base.

### Strategies

* Use intention-revealing names: The name of a variable, function, or class, should answer all the big questions. Why it exists, what it does, and how it is used.

```ruby
# BAD
def d # elapsed time in days

# GOOD
def elapsed_time_in_days
```

* Avoid using misleading names

```rb
# BAD
accounts_list = [acct_1, acct_2]
# not a list but rather an array
# best not to use any object type in the name

# GOOD
accounts = [acct_1, acct_2]
```

* Make meaningful distinctions

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

* Use pronounceable names
* Use searchable names
* Avoid encodings
* Avoid mental mapping
  * ex. i, j, k for small loops only
* Class names: noun or noun phrase names
  * ex. account or account_parser
* Method names: verb or verb phrase names
  * ex. post_payment or set_name
* Pick one word per concept
  * ex. fetch, retrieve, get are all the same
* Don't pun
  * ex. add used to increment or concat some values but then used to insert into a collection. Same word, different intent.
* Add meaningful context
  * long if blocks can be broken out into methods with clear names
  * Wrap in classes to help with context and readability

## Chapter 3: Functions

_summary_

shorter and clearer
dont use multiple flags and nested if's when possible
function and intent

### Strategies

* Small!
  * 20 lines is the upper bounds
  * 80-100 char is max
  * if / else / while statements should only have single line or single method calls
    *  keeps them self documenting
* Do only one thing
  * Requires skill in articulating the abstraction layers and if you are adhearing to only 1 of them
  * [abstraction](https://en.wikipedia.org/wiki/Abstraction_(computer_science))
