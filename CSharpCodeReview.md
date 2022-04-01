## C# coding and review guidelines
A code review can provide value towards your `design, techniques, patterns, approach` etc. There are numerous guidelines and best practices software development 
teams follow. However, I want to assure you that all the guidelines mentioned below will help any individual to practice and apply good coding principles and perform
a quality code review. Feel free to add any specific guidelines that you think is necessary. 

# Let's begin with `C#`  code review guidelines.
I have worked in various teams settings and work environments. Many times I have been invited to perform a code review for a friend who is not part of my team or rather
I am not part of their team. But what I admire and appreciate here is the fact that someone reached out to another dev/architect in case their team's developers is
either not available or busy with critical production issues. Such a mindset empowers the team to deliver the best written code. 
- Use of `SonarLint` (is an IDE extension) that helps you detect and fix quality issues as you write code. Lke a spell checker, SonarLint squiggles  flaws so that
  they can be fixed before committing code
  - Read more: [Sonar Lint addon Vs2019 ](https://marketplace.visualstudio.com/items?itemName=SonarSource.SonarLintforVisualStudio2019)
  - Sonar Analyzer: `C#` nuget package manager
- Try to code & review in terms of `Code Reusability, Code Consistency & Code Readability`.
- Write comments on top of all methods to describe their usage and expected input types and return type information.
- Avoid straight forward copy paste of code from other sources. 
- Mange sure there should not be any project warnings, treat warning as error. It will be much better if `Code Analysis(style cop & fx cop)` is performed on a project.
- Its not enough to deliver well written functional code. A well defined project and file name is equally important and brings a lot  of clarity. 
  	- Generally variables/parameters follow `camel casing` and methods /class names use `pascal casing`

- Unit testing: Write developer test cases and perform unit testing to make sure basic testing is done before it goes to QA.
    - Read More: [Get started with unit testing](https://docs.microsoft.com/en-us/visualstudio/test/getting-started-with-unit-testing?view=vs-2019&tabs=mstest)
    ```yaml
     public class Program
     {
        public static void Main()
        {
           Console.WriteLine("Hello World!");
        }
     }
     
     //Unit testing
     [TestClass]
     public class UnitTest1
       {
          private const string Expected = "Hello World!";
          [TestMethod]
          public void TestMethod1()
          {
             using (var sw = new StringWriter())
             {
                Console.SetOut(sw);
                HelloWorldCore.Program.Main();

                var result = sw.ToString().Trim();
                Assert.AreEqual(Expected, result);
             }
          }
       }
    ```
- `Disposing unmanaged resources` like File I/O, network resources.  e.g. Using block for unmanaged code
    - Use Organize using and sort using before compilation
    - Also verify code for memory leaks.
    ```yaml
    using System.IO; //organize and sort using statements
    using (Stream input = File.OpenRead(filename))
    {
        ...
    }
    ```
- Take necessary steps to avoid security issues. Follow all OWASP top 10 security rules.
    - read more : [OWASP top 10 rules](https://owasp.org/www-project-top-ten/)
- Implementation of exception handling and logging of exceptions. 
    - read more: [Best practices for exception](https://docs.microsoft.com/en-us/dotnet/standard/exceptions/best-practices-for-exceptions)
- Use latest `c#` version features for coding standards
    - read more: [What's new in C# 9.0](https://docs.microsoft.com/en-us/dotnet/csharp/whats-new/csharp-9)
    - e.g. `Null` has a catastrophic impact on your code functionality. Handle null conditions where ever possible
    ```yaml 
           string s1 = null;
          // for null value always return true
        bool b1 = String.IsNullOrWhiteSpace(s1);
          string s2 = " ";
        // for whitespace value always return true
        bool b2 = String.IsNullOrWhiteSpace(s2);
          string s4 = " \n ";
          // for new line value return true
        bool b4 = String.IsNullOrWhiteSpace(s4);
            string s5 = "\t";
          // for tab value return true
        bool b5 = String.IsNullOrWhiteSpace(s5);
          string s6 = "\r";
          // for carriage Return value return true
        bool b6 = String.IsNullOrWhiteSpace(s6);
          string s7 = "GFG";
          // for s7 it return False
        bool b7 = String.IsNullOrWhiteSpace(s7);
    ```
    - Avoid nested for/foreach loops and nested if conditions
    - Use anonymous types if code is going to be used for once
    - Use access specifier as per the scope need of method or class or variable
    - Save heap memory allocation e.g. uses `stringbuilder` in place of `string` if mutable concatenations required.
- Always `encrypt (by encryption algo)` secret/sensitive information like passwords to avoid manipulation by unauthorized users.
- Use asynchronous programming using `C# async await` where needed. As it tremendously improves the performance
    - read more: [asynchronous programming](https://docs.microsoft.com/en-us/dotnet/csharp/async#:~:text=C%23%20has%20a%20language-level%20asynchronous%20programming%20model%2C%20which,is%20known%20as%20the%20Task-based%20Asynchronous%20Pattern%20%28TAP%29.)
