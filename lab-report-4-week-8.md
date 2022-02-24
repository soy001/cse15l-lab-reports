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
My Implementation


Reviewed Implementation

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
My Implementation


Reviewed Implementation

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
My Implementation


Reviewed Implementation