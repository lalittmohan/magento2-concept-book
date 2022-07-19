**Main interface:** This interface contains the main methods that you must extend.

**Concrete class:** This is the main class the implements the main interface and contains the initial functionality.

**Abstract decorator:** This is the most important class, this class must implement the main interface and also dependency inject the main interface in the constructor.

**Decorator classes:** These classes must extend from the abstract decorator and provides the extra functionality to the main concrete class.
