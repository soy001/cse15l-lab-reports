# **Lab Report 2** 
## Code Fixes from Lab 3 and 4
By: Sophia Yu

<br>

>**Note:** in order to include everything asked in the lab report prompt, I had to create separate branches for my three fixes

>The three branches will remain open for future preference and will not be pulled into the main branch

<br>

## **Break 1 (Lab 3)**
[link to branch](https://github.com/soy001/markdown-parse/tree/Fix-1)

<br>

1. Screenshot of change diff in Github: [[view on Github]](https://github.com/soy001/markdown-parse/commit/17dd3c31c7901e54816ab6c160f028e567795592)


![Image](/screenshots/Pt2_a.PNG)

2. Link to test file with failure-inducing input: [click here](https://github.com/soy001/markdown-parse/blob/Fix-1/breaking-file.md?plain=1)

3. Running the program:

| input | output | expected |
| ----- | ------ | -------- |
|```javac MarkdownParse.java```<br>```java MarkdownParse breaking-file.md``` | ```[but not really, https://www.google.com]```| ```[https://www.google.com]```

4. Analysis:

