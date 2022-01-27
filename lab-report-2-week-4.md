# **Lab Report 2** 
## Code Fixes from Lab 3 and 4
By: Sophia Yu

<br>

>**Note:** in order to include everything asked in the lab report prompt, I had to create separate branches for my three fixes

>The three branches will remain open for future preference and will not be pulled into the main branch

<br>

## **Break 1 (Lab 3)**
[link to branch](https://github.com/soy001/markdown-parse/tree/Fix-1)

1. Screenshot of change diff in Github: [[view on Github]](https://github.com/soy001/markdown-parse/commit/17dd3c31c7901e54816ab6c160f028e567795592)


![Image](/screenshots/Pt2_a.PNG)

2. Link to test file with failure-inducing input: [breaking-file.md](https://github.com/soy001/markdown-parse/blob/Fix-1/breaking-file.md?plain=1)

3. Running the program:

| input | output | expected |
| ----- | ------ | -------- |
| ```javac MarkdownParse.java```<br>```java MarkdownParse breaking-file.md``` | ```[but not really, https://www.google.com]```| ```[https://www.google.com]``` |

4. Analysis:

<br><br>

---

<br>

## **Break 2 (Lab 3)**
[link to branch](https://github.com/soy001/markdown-parse/tree/Fix-2)

1. Screenshot of change diff in Github: [[view on Github]](https://github.com/soy001/markdown-parse/commit/3ea64ac085c186d1f467f55b82aeda013248fdfe)


![Image](/screenshots/Pt2_b.PNG)

2. Link to test file with failure-inducing input: [another-file.md](https://github.com/soy001/markdown-parse/blob/Fix-2/another-file.md?plain=1)

3. Running the program:

| input | output | expected |
| ----- | ------ | -------- |
| ```javac MarkdownParse.java```<br>```java MarkdownParse another-file.md``` | ```infinite loop (terminal never closes)```| ```[thislinkwont(work).html]``` |

4. Analysis:

<br><br>

---

<br>

## **Break 3 (Lab 4)**
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

