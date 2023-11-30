# Part 1 – Debugging Scenario
## 1) The original post from a student
<img width="629" alt="image" src="https://github.com/datungLA/cse15l-lab-reports/assets/97591324/f2b91f08-0174-4781-9f22-4ed7e9a5f7ab"> \
Hello instructors, \
I'm encountering an issue with the JUnit tests for my ListExamples class, specifically with the Merge function. It appears there might be an implementation error, though I'm not entirely certain of the precise location of the bug. Based on the results from the JUnit tests, I suspect that a loop condition within the function is not being met, leading to an infinite loop. This is causing the test to terminate after 500 seconds, which is an unexpected behavior if the function were functioning correctly. \
The failure-inducing input is 
```
    List<String> left = Arrays.asList("a", "b", "c");
    List<String> right = Arrays.asList("a", "d");
    List<String> merged = ListExamples.merge(left, right);
```
## 2) A response from the TA 
Hello student, \
Your guess about the potential bug seems accurate. Identifying the exact location of any bugs in your program is crucial. I recommend using a debugger to further investigate this issue. A valuable tool for debugging in Java, which we have discussed in our class, is jdb. I suggest using jdb to pinpoint the bug in your code. Start by setting a breakpoint at the first line of your ListExamples class and then step through each line carefully. This approach should help you detect the point where the infinite loop occurs.

## 3) Student implements TA's suggestion
<img width="1099" alt="image" src="https://github.com/datungLA/cse15l-lab-reports/assets/97591324/5c6537c8-21a0-4216-8c6d-9147cedbdb1c"> \
Hello instructors, \
Thank you for your advice. It turns out I overlooked the use of jdb and resorted to inserting numerous print statements in my code. Utilizing jdb is indeed highly effective in such scenarios, as it allows for halting the loop and methodically examining each line of code along with the local variables. After a thorough inspection of the class with jdb, I successfully identified the exact location of the bug. The issue was on line 43. The error occurred because I was incrementing the wrong variable, index1, while the loop condition was actually dependent on index2. As a result, the loop condition was never fulfilled, leading to an endless loop. 

## 4) All the information needed about the setup
The file & directory structure needed)

<img width="207" alt="image" src="https://github.com/datungLA/cse15l-lab-reports/assets/97591324/251e5b33-cbd0-4311-8836-631b6bab790a"> 

The contents of each file before fixing the bug)
TestListExamples.java
```
import static org.junit.Assert.*;
import org.junit.*;
import java.util.Arrays;
import java.util.List;

class IsMoon implements StringChecker {
  public boolean checkString(String s) {
    return s.equalsIgnoreCase("moon");
  }
}

public class TestListExamples {
  @Test(timeout = 500)
  public void testMergeRightEnd() {
    List<String> left = Arrays.asList("a", "b", "c");
    List<String> right = Arrays.asList("a", "d");
    List<String> merged = ListExamples.merge(left, right);
    List<String> expected = Arrays.asList("a", "a", "b", "c", "d");
    assertEquals(expected, merged);
  }
}
```
ListExamples.java
```
import java.util.ArrayList;
import java.util.List;

interface StringChecker {
  boolean checkString(String s);
}

class ListExamples {

  // Returns a new list that has all the elements of the input list for which
  // the StringChecker returns true, and not the elements that return false, in
  // the same order they appeared in the input list;
  static List<String> filter(List<String> list, StringChecker sc) {
    List<String> result = new ArrayList<>();
    for (String s : list) {
      if (sc.checkString(s)) {
        result.add(0, s);
      }
    }
    return result;
  }

  // Takes two sorted list of strings (so "a" appears before "b" and so on),
  // and return a new list that has all the strings in both list in sorted order.
  static List<String> merge(List<String> list1, List<String> list2) {
    List<String> result = new ArrayList<>();
    int index1 = 0, index2 = 0;
    while (index1 < list1.size() && index2 < list2.size()) {
      if (list1.get(index1).compareTo(list2.get(index2)) < 0) {
        result.add(list1.get(index1));
        index1 += 1;
      } else {
        result.add(list2.get(index2));
        index2 += 1;
      }
    }
    while (index1 < list1.size()) {
      result.add(list1.get(index1));
      index1 += 1;
    }
    while (index2 < list2.size()) {
      result.add(list2.get(index2));
      index1 += 1;
    }
    return result;
  }
}
```
The full command line (or lines) you ran to trigger the bug)
```
javac -g -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar TestListExamples.java ListExamples.java 
java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore TestListExamples 
```
A description of what to edit to fix the bug) \
Acknowledging the issue identified on line 43, as previously discussed, I returned to the ListExamples.java file to make the necessary correction. By changing the variable from index1 to index2, I ensured that the correct variable, which the loop condition relies on, is incremented. This adjustment effectively allows the loop to reach its termination condition, resolving the issue of the infinite loop. \
Fixed code: \
<img width="647" alt="image" src="https://github.com/datungLA/cse15l-lab-reports/assets/97591324/e22f9aad-a310-4b3c-8afc-7ec6b51fc812">

# Part 2 – Reflection
Throughout this course, I've gained substantial knowledge about UNIX and its myriad of powerful applications. Although a wide array of topics was covered, I recognize the need for additional practice to attain fluency in skills such as using vim, writing bash scripts, and mastering command-line operations. I recall an early lab session where I worked alongside a classmate who demonstrated remarkable proficiency in vim. Her enthusiasm for coding and dedication to learning had clearly paid off. Initially, her skill level was both impressive and a bit intimidating, but she reassured me that all these skills would be covered in the course. True to her word, as the course progressed and we delved into vim, I began to understand and replicate the techniques she used. This journey has been a testament to the importance of patience and practice in mastering new skills.
