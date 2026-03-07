# General Learnings from Backend Developments

1. Python is a _dynamically typed_ programming language. That means type of variables are determined during run time and not during complile time. Ex: a = 1 + "2", during compile time will not give error, but during run time would.
2. For FastAPI backend, to implement system level environment configuration, use _pydantic-settings_ for environment variables.
3. In pydantic_settings, use BaseSettings class, and SettingsConfigDict class. Below is a sample code:

   ```
   from pydantic_settings import BaseSettings, SettingsConfigDict
   class Settings(BaseSettings):

                   project_name: str
                   database_url: str

                   model_config = SettingsConfigDict(
                       env_file=".env",
                       env_file_encoding="utf-8"
                   )

                   def __init__(self, **data):
                       super().__init__(**data)

               settings = Settings()
   ```

## Asymptotic Analysis - Time Complexity Analysis

4. It is a mathematical framework used to define the eficiency of an algorithm as a function of input size.
5. Generally Represented by Captiol Letter O -> **O(_n_)**.
6. This is used typically as the **worst case** scenario analysis.
7. Common notaions:
   - **_O(1)_**: **Constant Time** - This is the **fastest**, where the number of steps in the algorithm remains the same irrespective of the size of the input.
     <span style="color:red">Ex: Fetching an array element with index.</span>
   - **_O(logn)_**: **Logrithmic Time** - Considered very **efficient**, The problem size (input size) is halved at every step.
     <span style="color:red">Ex: Finding a word in dictionary, or doing Binary Search on a sorted list.</span>
   - **_O(n)_**: **Linear Time** - Number of operations increase in direct proportion to the input size. <span style="color:red">Ex: a simple For Loop</span>
   - **_O(n logn)_**: **Linearithmic Time** - Considered **Fast but slower than Linear search**. You divide input into smaller inputs, sort, merge and then do Log search.
     <span style="color:red">Ex: Merge Sort algorithm</span>
   - **_O(n^2)_**: **Quadratic Time** - Considered slow and number of operations in the algorithm is proprotional to the power of 2 of the input size. If size doubles, number of steps quadruples.<span style="color:red">Ex: Nested for loop</span>
   - **_O(2^n)_**: **Exponential Time** - **Extremely Slow algorithm time**, Number of operations double with every single new piece of data. <span style="color:red">Ex: Recursive algorithms - Fibonacci sequence</span>
   - **_O(n!)_**: **Factorial Time** - **Slowest Algorithm time**, grows extremely fast even with smaller data sets.<span style="color:red">Ex: Brute force solutions to `Travelling Salesman` problem</span>
     - *Travelling Salesman problem*np-hard problem: Find the most optimum route for a salesman to travel specific series of location. With each new city added to the list, the number of options increases drastically.
