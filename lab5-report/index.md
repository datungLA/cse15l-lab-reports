# Part 1 – Debugging Scenario
## 1) The original post from a student
<img width="629" alt="image" src="https://github.com/datungLA/cse15l-lab-reports/assets/97591324/f2b91f08-0174-4781-9f22-4ed7e9a5f7ab"> \
Hello instructors, \
I have a problem passing the JUnit tests because my Merge function from the ListExamples class is probably not implemented correctly. I do not know exactly where the bug is but I want to guess, based on the output from the JUnitTest, that the condition of a loop in the function was never met. This causes an infinite loop which making the test terminated after 500s. This is unusual if the function performs correctly. \
The failure-inducing input is 
```
    List<String> left = Arrays.asList("a", "b", "c");
    List<String> right = Arrays.asList("a", "d");
    List<String> merged = ListExamples.merge(left, right);
```
## 2) A response from the TA 
Hello student,
I think you have the correct guess about what the bug could be. This is impor 
# Part 2 – Reflection
