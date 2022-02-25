# **Lab Report 4** 
## Reviewing Code
By: Sophia Yu

<br>

**Links**

1. [My Repo](https://github.com/soy001/markdown-parse)
2. [Reviewed Repo](https://github.com/soy001/markdown-parse-main-1-)

<br> 

## **Snippet 1**
**Expected Output:** 

![Image](/screenshots/Pt4_a.PNG)

Test Method:
```
@Test
    public void testSnippet1() throws IOException{
        String path = "snippet1.md";
        String contents= Files.readString(Path.of(path));
        List<String> expect = List.of("google.com", 
            "google.com", "ucsd.edu");
        assertEquals(MarkdownParse.getLinks(contents), expect);
    }
```
My Implementation - ***FAILED***
```
1) testSnippet1(MarkdownParseTest)
java.lang.AssertionError: expected:<[url.com, `google.com, google.com, ucsd.edu]> but was:<[google.com, google.com, ucsd.edu]>
        at org.junit.Assert.fail(Assert.java:89)
        at org.junit.Assert.failNotEquals(Assert.java:835)
        at org.junit.Assert.assertEquals(Assert.java:120)
        at org.junit.Assert.assertEquals(Assert.java:146)
        at MarkdownParseTest.testSnippet1(MarkdownParseTest.java:42)
```

Reviewed Implementation - ***FAILED***
```
1) testSnippet1(MarkdownParseTest)
java.lang.AssertionError: expected:<[url.com, `google.com, google.com, ucsd.edu]> but was:<[google.com, google.com, ucsd.edu]>
        at org.junit.Assert.fail(Assert.java:89)
        at org.junit.Assert.failNotEquals(Assert.java:835)
        at org.junit.Assert.assertEquals(Assert.java:120)
        at org.junit.Assert.assertEquals(Assert.java:146)
        at MarkdownParseTest.testSnippet1(MarkdownParseTest.java:28)
```

<br>

## **Snippet 2**
**Expected Output:** 

![Image](/screenshots/Pt4_b.PNG)

Test Method: 
```
 @Test 
    public void testSnippet2() throws IOException{
        String path = "snippet2.md";
        String contents= Files.readString(Path.of(path));
        List<String> expect = List.of("a.com", "a.com", 
            "example.com");
        assertEquals(MarkdownParse.getLinks(contents), expect);
    }
```
My Implementation - ***FAILED***
```
2) testSnippet2(MarkdownParseTest)
java.lang.AssertionError: expected:<[a.com, a.com((, example.com]> but was:<[a.com, a.com, example.com]>
        at org.junit.Assert.fail(Assert.java:89)
        at org.junit.Assert.failNotEquals(Assert.java:835)
        at org.junit.Assert.assertEquals(Assert.java:120)
        at org.junit.Assert.assertEquals(Assert.java:146)
        at MarkdownParseTest.testSnippet2(MarkdownParseTest.java:50)
```

Reviewed Implementation - ***FAILED***
```
2) testSnippet2(MarkdownParseTest)
java.lang.AssertionError: expected:<[a.com, a.com((, example.com]> but was:<[a.com, a.com, example.com]>
        at org.junit.Assert.fail(Assert.java:89)
        at org.junit.Assert.failNotEquals(Assert.java:835)
        at org.junit.Assert.assertEquals(Assert.java:120)
        at org.junit.Assert.assertEquals(Assert.java:146)
        at MarkdownParseTest.testSnippet2(MarkdownParseTest.java:36)
```

<br>

## **Snippet 3**
**Expected Output:**

![Image](/screenshots/Pt4_c.PNG)

Test Method: 
```
 @Test 
    public void testSnippet3() throws IOException{
        String path = "snippet3.md";
        String contents= Files.readString(Path.of(path));
        List<String> expect = List.of("https://www.twitter.com", 
            "https://ucsd-cse15l-w22.github.io/", 
            "https://cse.ucsd.edu/");
        assertEquals(MarkdownParse.getLinks(contents), expect);
    }
```
My Implementation - ***FAILED***
```
3) testSnippet3(MarkdownParseTest)
java.lang.AssertionError: expected:<[]> but was:<[https://www.twitter.com, https://ucsd-cse15l-w22.github.io/, https://cse.ucsd.edu/]>
        at org.junit.Assert.fail(Assert.java:89)
        at org.junit.Assert.failNotEquals(Assert.java:835)
        at org.junit.Assert.assertEquals(Assert.java:120)
        at org.junit.Assert.assertEquals(Assert.java:146)
        at MarkdownParseTest.testSnippet3(MarkdownParseTest.java:58)
```

Reviewed Implementation - ***FAILED***
```
3) testSnippet3(MarkdownParseTest)
java.lang.AssertionError: expected:<[
    https://www.twitter.com
,
    https://ucsd-cse15l-w22.github.io/
, github.com

And there's still some more text after that.

[this link doesn't have a closing parenthesis for a while](https://cse.ucsd.edu/


]> but was:<[https://www.twitter.com, https://ucsd-cse15l-w22.github.io/, https://cse.ucsd.edu/]>
        at org.junit.Assert.fail(Assert.java:89)
        at org.junit.Assert.failNotEquals(Assert.java:835)
        at org.junit.Assert.assertEquals(Assert.java:120)
        at org.junit.Assert.assertEquals(Assert.java:146)
        at MarkdownParseTest.testSnippet3(MarkdownParseTest.java:44)
```

<br>

## **Questions**
1. As seen in the output, my MarkdownParse gave extra outputs because it didn't recognize the backticks. This issue should be able to be fixed in less than 10 lines. All I should have to do is keep track of beginning and end backticks and have a condition that breaks out of the loop when it finds a section quoted by backticks if complete pairs of parentheses/brackets are not found.

2. Here, similar to the first case, we are checking for open and closed elements. So, what I would need to do is check for when the parentheses and brackets close off, which should take less than 10 lines.

3. I don't think the fix for this will be a small change because we're going to have to keep track of all newlines and where the open/close brackets are. As concluded from the preview that VSCode provides, there are multiple cases that it'll consider to be a link, so I would have to write conditions for each of the ways newlines and parentheses/brackets are used. Furthermore, I will also need to keep track of open/close elements.