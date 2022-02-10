# **Lab Report 3** 
## Copy whole directories with ```scp -r```
By: Sophia Yu

<br>

## **Copying markdown-parse directory to ieng6 account**

* ieng6 ```ls``` before copying directory:

    ![Image](/screenshots/Pt3_b.PNG)

* ieng6 ```ls``` after copying directory:   

    ![Image](/screenshots/Pt3_a.PNG)

* copied files: 

    ![Image](/screenshots/Pt3_c.PNG)

<br><br>

---

<br>

## **Logging and testing in ieng6**

* Logging into ```ieng6``` account and running makefile to run tests:

    ![Image](/screenshots/Pt3_d.PNG)

<br><br>

---

<br>

## **Running tests in one line**
[link to branch](https://github.com/soy001/markdown-parse/tree/Fix-3)

1. Screenshot of change diff in Github: [[view on Github]](https://github.com/soy001/markdown-parse/commit/12d18c61fafd536eae1df6592d62d1ded632f1b3)
    >**Note:** both breaks were able to be fixed with the same code change


    ![Image](/screenshots/Pt2_c.PNG)

2. Link to test files with failure-inducing input: [test-file6.md](https://github.com/soy001/markdown-parse/blob/Fix-3/test-file6.md?plain=1), [test-file7.md](https://github.com/soy001/markdown-parse/blob/Fix-3/test-file7.md?plain=1)

3. Running the program:

    | input | output | expected |
    | ----- | ------ | -------- |
    | ```javac MarkdownParse.java```<br>```java MarkdownParse test-file6.md``` | ```[page.com]```| ```[]``` |
    | ```javac MarkdownParse.java```<br>```java MarkdownParse test-file7.md``` | ```Exception in thread "main" java.langStringIndexOutOfBoundsException: begin 1, end 0, length 2``` <br> ```at java.base/java.lang.String.checkBoundsBeginEnd(String.java:4601)``` <br> ```at java.base/java.lang.String.substring(String.java:2704)``` <br> ```at MarkdownParse.getLinks(MarkdownParse.java:31)``` <br> ```at MarkdownParse.main(MarkdownParse.java:44)``` | ```[]``` |

4. Analysis:

    The first file (test-file6.md) provides an image, not a link. However, the program still picks up the command as a link because it found []'s and ()'s. As a result, page.com was still listed as a link. 
    
    The second file (test-file7.md) provided this: )[. Because our program keeps track of the index of both open and closed brackets/parenthesis, there was an index-out-bounds exception because the "link" that we provided was missing some information. 