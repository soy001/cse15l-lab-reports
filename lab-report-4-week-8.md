# **Lab Report 4** 
## Reviewing Code
By: Sophia Yu

<br>

**Links**

1. [My Repo](https://github.com/soy001/markdown-parse)
2. [Reviewed Repo](https://github.com/soy001/markdown-parse-main-1-)

<br> 

## **Snippet 1**
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
My Implementation - FAILED
```
1) testSnippet1(MarkdownParseTest)
java.lang.AssertionError: expected:<[url.com, `google.com, google.com, ucsd.edu]> but was:<[google.com, google.com, ucsd.edu]>
        at org.junit.Assert.fail(Assert.java:89)
        at org.junit.Assert.failNotEquals(Assert.java:835)
        at org.junit.Assert.assertEquals(Assert.java:120)
        at org.junit.Assert.assertEquals(Assert.java:146)
        at MarkdownParseTest.testSnippet1(MarkdownParseTest.java:42)
```

Reviewed Implementation - FAILED
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
My Implementation - FAILED
```
There was 1 failure:
1) testSnippet2(MarkdownParseTest)
java.lang.AssertionError: expected:<[a.com, a.com((, example.com]> but was:<[a.com, a.com, example.com]>
        at org.junit.Assert.fail(Assert.java:89)
        at org.junit.Assert.failNotEquals(Assert.java:835)
        at org.junit.Assert.assertEquals(Assert.java:120)
        at org.junit.Assert.assertEquals(Assert.java:146)
        at MarkdownParseTest.testSnippet2(MarkdownParseTest.java:50)
```

Reviewed Implementation - FAILED
```
1) testSnippet2(MarkdownParseTest)
java.lang.AssertionError: expected:<[a.com, a.com((, example.com]> but was:<[a.com, a.com, example.com]>
        at org.junit.Assert.fail(Assert.java:89)
        at org.junit.Assert.failNotEquals(Assert.java:835)
        at org.junit.Assert.assertEquals(Assert.java:120)
        at org.junit.Assert.assertEquals(Assert.java:146)
        at MarkdownParseTest.testSnippet2(MarkdownParseTest.java:36)
```

<br>

## **Snippet 3**
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
My Implementation - FAILED
```
1) testSnippet3(MarkdownParseTest)
java.lang.AssertionError: expected:<[]> but was:<[https://www.twitter.com, https://ucsd-cse15l-w22.github.io/, https://cse.ucsd.edu/]>
        at org.junit.Assert.fail(Assert.java:89)
        at org.junit.Assert.failNotEquals(Assert.java:835)
        at org.junit.Assert.assertEquals(Assert.java:120)
        at org.junit.Assert.assertEquals(Assert.java:146)
        at MarkdownParseTest.testSnippet3(MarkdownParseTest.java:58)
```

Reviewed Implementation - FAILED
```
1) testSnippet3(MarkdownParseTest)
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
``