# **Lab Report 5** 
## Commonmark-Spec Tests
By: Sophia Yu

<br>

## **How I compared the results**
For all the test files, I used ```diff``` to compare the results. First, I stored each of the outputs (from the two implementations) into text files. Then, I used ```diff``` to compare, using this command:
```
[cs15lwi22ane@ieng6-202]:~:499$ diff your-markdown-parse/results.txt cse15l-markdown-parse/results.txt
```

Then, this was the output I got: 
```
212c212
< []
---
> [url]
230c230
< []
---
> [baz]
866,867c866
< [foo
< bar]
---
> []
871,872c870
< [<foo
< bar>]
---
> []
880c878
< [\(foo\]
---
> [\(foo\)]
882c880
< [foo(and(bar]
---
> [foo(and(bar))]
884c882
< [foo(and(bar]
---
> []
886c884
< [foo\(and\(bar\]
---
> []
888c886
< [<foo(and(bar]
---
> []
918c916
< []
---
> [/uri]
936c934
< []
---
> [uri1]
1056c1054
< []
---
> [/url]
1058c1056
< []
---
> [/url]
1064c1062
< []
---
> [train.jpg]
1068c1066
< []
---
> [<url>]
1072c1070
< []
---
> [/url]
```

From here, I had to manually check the lines using this command:
```
[cs15lwi22ane@ieng6-202]:~:500$ sed -n '883p' results.txt
```
> the number that goes inside the single-quotes is the code line number (based off of my results from above)

<br>

## **Comparison 1**
**File: 194.md** 
```
[Foo*bar\]]:my_(url) 'title (with parens)'
[Foo*bar\]]
```
**My output:** [] vs. **CSE15L output:** [url]

**Which implementation is correct?**
Using the VSCode preview, I was able to see that my implementation is correct. 

**What's the bug?** 
As we can see, the CSE15L implementation is incorrect. And this is because it recognized "url" as the link. What should be fixed here is that the code needs to look for and keep track of when there is a complete pair of parenthesis or brackets. 
> Note: there is another thing that is needed to solve this, but this will be explained in Test 2 (here, I will focus on the pairs)

**This is where we should add more code:**
![Image](/screenshots/Pt5_c.png)
Instead of getting the next close bracket, we should be getting the close bracket that matches the pair (for the open bracket we have). So, before we store the index of the nextCloseBracket, we should have an if-condition that checks to see how many open brackets we have. If this close bracket matches our first open bracket that we stored, then we have the right index. Otherwise, we have to get the index of the correct close bracket that matches our open bracket.

<br>

## **Comparison 2**
**File: 201.md** 
```
[foo]: <bar>(baz)
[foo]
```
**My output:** [] vs. **CSE15L output:** [baz]

**Which implementation is correct?**
Using the VSCode preview, I was able to see that my implementation is correct. 

**What's the bug?** 
As we can see, the CSE15L implementation is incorrect. And this is because it recognized "baz" as the link. What should be fixed here is that the code needs to check that the ] is right before the (.

**This is where we should add more code:**
![Image](/screenshots/Pt5_b.png)
Before we create the potentialLink String, we should check to make sure that the close bracket is right before the open parenthesis. That's why the CSE15L implementation recognized the foo as a real link, because it overlooked the space.
