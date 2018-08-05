# Clean Code

_SUMMARY 1-3 paragraphs_

## Key Terms / Ideas

* code-sense: The ability to see bad code and know how to fix it by writing good code.
* refactoring:
  * objects: breakout into 2 or more objects
  * the extract method: one method that says more clearly what it does, and some sub-methods saying how it does it.
* intention-revealing names: The name of a variable, function, or class, should answer all the big questions. Why it exists, what it does, and how it is used.
  ```ruby
  # BAD
  # elapsed time in days
  def d
  
  # GOOD
  def elapsed_time_in_days
  ```

## Chapter 1: Clean Code

Goes over in general what the issue with bad code is, and makes the case for writing good code as a matter of professionalism. TDD is the professional way to write good code. Continuous refactoring and tidying up any checked-out code, making it better than it was before you started working on it is key to keeping the system full of healthy and clean code.

### Key Rules of Clean Code

* Runs all the tests.
* Contains no duplicates.
* Expresses all the design ideas that are in the system.
* Minimizes the number of entities such as classes, methods, functions, and the like.

---

## Chapter 2: Meaningful Names

### Strategies

* Use intention-revealing names:
