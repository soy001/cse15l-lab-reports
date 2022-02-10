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

![Image](/screenshots/Pt3_cc.PNG)

> Note: we only need the .java, .md, junit imports, and makefile files. So, we add specific filters to our command to get those files.

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

* Command: ``` scp -r *.java *.md lib\ ieng6:~/markdown-parse; ssh ieng6 "cd markdown-parse/; make test"```

    ![Image](/screenshots/Pt3_e.PNG)