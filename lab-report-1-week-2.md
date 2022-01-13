# **How to use a course-specific account on ```ieng6```** 
By: Sophia Yu

<br>

## **Installing Visual Studio Code**

> Visit the VSCode website to download the software: [click here](https://code.visualstudio.com/download)
<br> 

![Image](screenshots\Pt1_a.PNG)
Depending on what computer you have, download the corresponding file

<br> 

>Once your file has downloaded, click on it to open, and follow the instructions prompted on your computer to finish setting up

<br>

![Image](screenshots\Pt1_c.PNG)


After you finishing downloading and you open VSCode, you will see this welcome screen

<br> 

---

<br>

## **Remotely Connecting**

>**NOTE: Before I started:** since I'm on **Windows**, I needed to install [OpenSSH](https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse)

<br>

<img src="screenshots\Pt1_h.PNG" width=200px>

>1. Find your course-specific account for CSE15L here: [https://sdacs.ucsd.edu/~icc/index.php](https://sdacs.ucsd.edu/~icc/index.php)
>2. Open a terminal in VSCode (Ctrl or Command + `, or use the Terminal → New Terminal menu option)
>3. Type in this command: ```ssh cs15lwi22zz@ieng6.ucsd.edu``` but replace ```zz``` with the three letter of your own course-specific account
>4. Follow the prompt
>>**NOTE:** if your password does not work, make sure to reset it [here](https://password.ucsd.edu/)

<br>

Once I logged in, my terminal output looked like this:
```
Hello cs15lwi22ane, you are currently logged into ieng6-203.ucsd.edu

You are using 0% CPU on this system

Cluster Status
Hostname     Time    #Users  Load  Averages
ieng6-201   21:00:01   11  2.19,  2.29,  2.28
ieng6-202   21:00:01   12  2.19,  1.97,  1.83
ieng6-203   21:00:01   15  0.20,  0.52,  0.55


Wed Jan 12, 2022  9:02pm - Prepping cs15lwi22
[cs15lwi22ane@ieng6-203]:~:19$
```

<br>

Yay! Now onto the next part!

<br> 

---

<br>

## **Running Some Commands**

<br>

Here's a list of cool commands I tried + the outputs and explanations

| Command | Description | Output |
| ------- | ----------- | ------ |
| cd      | changes directory (only if you specify a directory name) | ```blank```|
| ls      | lists files in the directory | ```Main.class  Main.java  WhereAmI.class  perl5``` |
| pwd     | prints the full name of the current directory | ```/home/linux/ieng6/cs15lwi22/cs15lwi22ane``` |
| mkdir report1 | creates a new directory with the name ```report1``` | ```blank``` |

<br>

Check out this command ```ls -a```:

![Image](screenshots\Pt1_d.PNG)

>Woah! Why are there so many items??

>>```ls``` lists directory contents and ```-a``` stands for all, so this command lists all the contents within the directory I'm in

<br>

Lastly, a cool and useful trick: press Ctrl/Cmd-D and type ```exit```
>Ctrl/Cmd-D logs you out of your school-specific account and ```exit``` closes the terminal

<br> 

---

<br>

## **Moving Files over SSH with scp**

<br>

>First, I need a file:

* Create a file in VSCode called ```whereAmI.java```
```
class WhereAmI{
        public static void main(String[] args){
            System.out.println("hello world!");
        }
}
```

>Open up the terminal in VSCode and run this command: ```scp whereAmI.java cs15lwi22zz@ieng6.ucsd.edu:~/``` (remember to replace the ```zz```)

>Next, login with ssh. Once successful, you can use ```ls``` to see if your new file is there!

<br> 

Here's my full process:

![Image](screenshots\Pt1_e.PNG)

<br> 

---

<br>

## **Setting an SSH Key**

<br>

>Follow the steps here to create an SSH key: [click here](https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_keymanagement#user-key-generation)

<br> Once it's a success, I am be able to login without having to type my password!

![Image](screenshots\Pt1_f.PNG)

<br> 

---

<br>

## **Optimizing Remote Running**

<br>

> These are the two things I considered: **time** and **code-length**

* With the key that we created in the previous section, it saves you a lot of time

* Moreover, we can even shorten the number of times we have to ```enter``` in the command prompt too:

<br>

![Image](screenshots\Pt1_g2.PNG)









