### Lab Report 3 - Bugs and Commands (Week 5)

## Part 1 - Bugs

### Bug Description

**Chosen Bug: Week 4 - ArrayIndexOutOfBoundsException**

**Failure-Inducing Input:**

```java
import static org.junit.jupiter.api.Assertions.*;
import org.junit.jupiter.api.Test;

public class BuggyProgramTest {

    @Test
    public void testFailureInducingInput() {
        int[] input = {1, 2, 3};
        int index = 3; // Index out of bounds
        assertThrows(ArrayIndexOutOfBoundsException.class, () -> {
            int result = BuggyProgram.getElementAtIndex(input, index);
        });
    }
}
```

**Non-Failure-Inducing Input**:

```java
import static org.junit.jupiter.api.Assertions.*;
import org.junit.jupiter.api.Test;

public class BuggyProgramTest {

    @Test
    public void testNonFailureInducingInput() {
        int[] input = {1, 2, 3};
        int index = 2; // Valid index
        assertDoesNotThrow(() -> {
            int result = BuggyProgram.getElementAtIndex(input, index);
        });
    }
}
```

**Symptom:**


**Buggy Code (Before Fix):**
```java
public class BuggyProgram {
    public static int getElementAtIndex(int[] array, int index) {
        return array[index];
    }
}
```

**Fixed Code (After Fix):**
```java
public class BuggyProgram {
    public static int getElementAtIndex(int[] array, int index) {
        if (index < 0 || index >= array.length) {
            throw new ArrayIndexOutOfBoundsException("Index " + index + " is out of bounds");
        }
        return array[index];
    }
}
```
##  Part 2 - Researching Commands
**Command Chosen: grep**

## Option 1: -i (Ignore Case)

Description: The -i option makes grep case-insensitive, allowing it to match patterns regardless of case.

**Example 1:**

``` java

grep -i "error" ./technical/logs.txt

```

Output: This command searches for the term “error” in logs.txt, matching “Error”, “ERROR”, and other case variations.

**Example 2:**

``` java
grep -i "warning" ./technical/documents/report.txt

```

Output: This command searches for the term “warning” in report.txt, matching “Warning”, “WARNING”, and other case variations.

Source: GNU grep Manual

## Option 2: -r (Recursive)

Description: The -r option allows grep to search recursively through directories.

**Example 1:**

``` java

grep -r "TODO" ./technical/

``` 
Output: This command searches for the term “TODO” in all files within the technical directory and its subdirectories.

**Example 2:**

``` java

grep -r "fixme" ./technical/code/
```

Output: This command searches for the term “fixme” in all files within the code directory and its subdirectories.

Source: GNU grep Manual

## Option 3: -v (Invert Match)

Description: The -v option inverts the match, displaying lines that do not match the specified pattern.

**Example 1:**

``` java

grep -v "DEBUG" ./technical/logs.txt

``` 
Output: This command shows all lines in logs.txt that do not contain the term “DEBUG”.

**Example 2:**

``` java
grep -v "INFO" ./technical/logs.txt
``` 

Output: This command shows all lines in logs.txt that do not contain the term “INFO”.

Source: GNU grep Manual

## Option 4: -l (Files with Matches)

Description: The -l option lists the names of files with matching lines, rather than displaying the matching lines themselves.

**Example 1:**

``` java

grep -l "ERROR" ./technical/logs/*

``` 

Output: This command lists all files in the logs directory that contain the term “ERROR”.

**Example 2:**

``` java
grep -l "import" ./technical/code/*
``` 

Output: This command lists all files in the code directory that contain the term “import”.

Source: GNU grep Manual

These examples demonstrate the versatility of the grep command in various scenarios, making it a powerful tool for searching through text in files and directories.
