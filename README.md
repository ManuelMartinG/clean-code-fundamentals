# Clean Code Fundamentals
This repository is intended to showcase the different
Clean Code fundamentals rules outline by "Uncle Bob"
in his book "Clean Code" and from his talks like:
[Youtube Link](#https://www.youtube.com/watch?v=7EmboKQH8lM)

---

## Notes from the book "Clean Code"

### Chapter 2. Meaningful Names

#### Use Intention-Revealing Names

- The name of a function should tell you why it exists, what it does and how it is used.

    ```python
        d = 1  # Elapsed time in days
    ```

    This does not tell us anything. If it needs a compliment, it is not well named. Instead:

    ```python
        elapsed_days = 1
    ```

#### Avoid disinformation

- Do not use words for variables such as `account_list` if the structure of that variable is not a `List`. It may lead to false conclusiones.

- Do not use variables that vary only in a small way.

    ```python
    ClassThatHandlesALotOfThings()
    ClassThatHandlesABunchOfThings()
    ```

    They are difficult to differentiate.

#### Make Meaningful Distinctions

- Don't use number-series naming sucha as: `(a1, a2, a2, an)`. They are Non Informative.

- Don't use noise words to distinguish elements. See the example of a class named `Product`, and 2 other ones called respectively `ProductInfo` and `ProductData`. In this context, `Info` and `Data` do not make any difference.

- Never use the word `variable` for a variable, nor even prefixing or suffixing it. Don't use the word `table` in a table. 'NameString' is not better than 'Name'.

#### Use pronunciable names

- `genymdhms` to name a function that generates year, month, day, hour, minute and second is not a good idea.

#### Use Searchable Names

- Don't use single-letter names and numeric constants because they are very difficul to search.

- *"The length of a name should correspond to the size of its scope"*

#### Interfaces and Implementations

- Don't preface interfaces as `IShapeFactory`.

#### Avoid Mental Mapping

- Code readers shouldn't have to mentally translate your names into other names they already know. They shouldn't have to know that `r` is the variable that contains the lowercase version of the url with the host and scheme removed.

- *Clarity is King*

#### Class Names

- They should be named as nouns or noun phrase names like `Customer`, `WikiPage`, `Account`. Avoid words like `Manager`, `Processor`, `Data` or `Info` in the name of a class. A class name should not be a verb.

#### Method Names

- They should have verb or verb phrase names like `post_payment`, `delete_page` or `save`.

- Mutators, Accessors and predicates should be name for their value and prefixed with `get`, `set` and `is`.

#### Don't be cute

- Don't use names as jokes. `HolyHandGrenade`is clearly worse than `DeleteItems`.

- *Say what you mean. Mean what you say*

#### Pick one word per concept

- Pick one word for one abstract concept and stick with it. For exmaple, it's confusing to have `fetch`, `retrieve` and `get`as equivalents methods of different classes.

- Likewise, it's confusing to have a `controller`, a `manager` and a `driver` in the same codebase. The name may lead you to expect two objects that have very different type as well as having different classes.

- *A consistent lexicon is a great boon to the programmers who must use your code*

#### Don't Pun

- Avoid using the same word for 2 purposes. This is the opposite of the "one word per concept rule". For example, don't use the word `add` for methods in different classes that do things very differently.

- *Out goal is to make our code as easy as possible to understand*

#### Use Solution Domain Names

- The people reading your code are programmers, so go ahead and use Computer Science terms for algorithms, patterns, math, etc.

#### Use Problem Domain Names

- At least the programmer who maintains your code can ask a domain expert what it means.

#### Add Meaningful Context

- You need to place names in context for your reader by enclosing them in well-named classes, functions or namespaces.

- Shorter names are generally better than longer ones, so long as they are clear. Add no more context to a name that is necessary.


### Chapter 3. Functions

#### Small!

- The first rule is that functions should be small.

- The second rule is that functions should be samller than that.

- Functions should hardly ever be 20 lines long.

#### Blocks and Indenting

- This implies that the blocks within `if`, `else` and `while` statements should be one line long. Probably that line should be a function call. The functions should have also a nicely descriptive name.

#### Do One Thing

- *Functions should don one thing. They should do it well. They should do it only*

- Another way to know that a function is doing more than "one thing" if if you can extract another function from it with a name that is not merely a restatement of its implementation.

#### Section within Functions

- Functions sometimes have the following sections *declarations*, *initilizations*, and *sieve*. If a function does only one thing, it cannot be reasonably divided into sections.

#### One Level of Abstraction per Function

- The statements withing our function are all at the same level of abastraction. Sometimes, we see functions with statements that correspond to very high-level of abstraction and also contain others that are very low level.

- Mixing levels of abstraction within a function is always confusing. Readers may not be able to tell wether a particular expression is an essential concepto or a detail.

#### Reading Code From the Top to Bottom: The Stepdown Rule

- We want the code to read like a top-down narrative. We want every function to be followed by those at the next level of abstraction so that we can read the program, descending one level of abstraction a t a time as we read down the list of functions.

> In Python we cannot do this.

#### Use Descriptive Names

- Don't be afraid to make a name long. It's better than a shor enigmatic name. A long descriptive name is better than a long descriptive comment. Use a naming convention that allows multiple words to be easily read in the function names, and then make use of those multiple words to give the function a name that says what it does.

- Choosing descriptive names will clarify the design of the module in your mind and hekp you to improve it. It is not uncommon that while hunting for a good name, you end up restructuring the code.

- Be consistent in your names. Use the same prhases, nouns and verbs in the function names you choose for your modules.

#### Function Arguments

- The ideal number of arguments i s 0 - *Nyladic*

- The next less ideal is 1 - *Monadic*

- The next less ideal is 2 - *Dyadic*

- 3 or more should be avoided if possible.

- Arguments are hard. They take a lot of conceptual power. They are even harder from a testing point of view. Imagine writing all the tests to tackle all the possible combinations of arguments properly.

- Output arguments are harder to understand than input arguments. When we read a function, we are used to the idea of information going in to the function through parguments and out through the return value. We don't ussually expect information to be going out through the arguments. So outpu arguments often cause us to do a double-take.

#### Common Monadic Forms

- For example, if you are asking a question about an argument `file_exists("my_file.txt")`.

- Transforming the argument into something else: `open_file("my_file.txt")`.

- Or dealing with events. The program has no output argument becuase its goal is to alter the state of the system. `password_attempt_failed_n_times(attemps=4)`.

- Try to avoid monadic functions that do not follow this forms.


#### Flag Arguments

- They are ugly. Passing a boolean argument to a function is a terrible practice. It immediately complicates the signature of the method, loudly procaliming that this function does more than one thing. If the flag is true, it does 1 thing, and if it is false, it does another.

#### Dyadic Functions

- It easier to see `write_field(name)` than `write_field(output_stream, name)`. The second requires a shor pause intul we learn to ignore the first parameters. And that, of course, eventually results in problems because we should never ignore any part of code. The parts we ignore are where the bugs will hide.

- Even obvious dyadic functions such as `assert_equals(expected, actual)`. How many times you've confused both variables order?-

#### Triad Functions

- Think very carefully before creating a triad.

#### Argument Objects

- When a function seems to need more than two or three arguments, it is likely that some of those arguments ought to be wrapped into a class of their own. For example:

    ```java
    Circle makeCircle(double x, double y, double radius);
    Circle makeCircle(Point center, double radius);
    ```

- It may seem that passing arguments as objects is cheating, but it is not. A group of arguments tend to represent a higher level of abstraction representation.

#### No Side Effects

- Side effects are lies. Your function promises to do one thing but it also does other hidden things. Sometimes it will make unexpected changes to the variables of its own class. They often result in strange temporal couplings and order dependencies.


#### Command Query Separation

- Functions should either do something or answer somethings. But not both. Or your function changes the state of an object or it should return some informaition of that object. Doing both often leads ot confusion.

#### Extract Try/Catch Blocks

- They are ugly in the own right. They confuse the structure of the code and mix error processing with normal processing. It is better to extract the bodies of the try and catch blocks out into functions of their own.

#### Error handling is one thing

- Functions should do one thing. Error handling is one thing. Thus, a function that handles errors should do nothing else. This implies, that if the keyword `try` exists in a function, it should be the very first word in the function and that there should be nothing after the catch/finally blocks.

#### Don't Repeat Yourself

- Duplication may be the root of all evil in software.

#### Structure Programming

- Every function and every block within a function should have one entry and one exit only.

There should be only one return statement in a function, no break or continue statements in a loop. But this is bring benefits to large functions. If you keep them small, no need to apply this rule.


### Chapter 4. Comments

Nothing can be quite so helpful as a well-placed comment. Nothing can be so damaging as an old crufty comment that propagates lies and misinformation.

- The use of comments is to compensate for our failure to express ourself in code. Comments are always failures. We must have them becuase we cannot always figure out how to express ourselves without them, but theis use is not a cause for celebration.

- It's better to express ideas with descriptive code.

- Comments don't always follow code changes, so they remain there to intoxicate the codebase.

- Truth is only in one place, the code.


### Chapter 5. Formatting

#### Newspaper Metaphor.

- The name of the source file should be self explanatory as the title of a news article.

- The topmost part of the source file should provide the high-level concepts and algorithms.

- Detail should increase as we move downward, until at the end we find the lowest level functions and details in the source file.

#### Dependent Functions

- If one function calls another, the should be vertically close, and the caller should be above the callee, if at all possible. This gives the program a natural flow. If the convention is followed realiably, readers will be able to trust that function definitions will follow shortly after their use.

#### Conceptual Affinity

- Certain bits of code want ot be near other bits. They have a certain conceptual affinity. The stronger the affinity, the less vertical distance there should be between them. Affinity might me based on a caller-callee relationship, of even if the functions perform similar operations.