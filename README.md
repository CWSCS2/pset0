# Problem Set 0: An Explosion of Bits
In Chapter 1 of *Blown to Bits*, the authors write:

> Almost everything is stored in a computer somewhere: court records, grocery purchases, precious family photos, pointless radio programs... Computers contain a lot of stuff that isn't useful today but somebody thinks might someday come in handy. It is all being reduced to zeroes and ones – "bits." The bits are stashed on disks of home computers and in the data centers of big corporations and government agencies. The disks can hold so many bits that there is no need to pick and choose what gets remembered.

In this assignment, you will begin to investigate those bits, and get a sense for how your computer sees the world.

### 1. The Command Line

To do that, we need to strip away a lot of the magic that your Operating System provides you and go back to basics. Throughout this course, you'll be using the **command line** to interact with your computer textually, rather than graphically.

Open up a Terminal window, and you should see a command prompt. I see this:

	MacBook-Pro:~ alexlew$ 

Almost anything you can do with programs like Finder and Microsoft Word, you can do on the command line. It's another way to interact with your computer. Try typing in a simple command, like `date`, and pressing enter. You should see something like this:

	$ date
	Sun Mar 13 23:17:58 EDT 2016
    
Another command, `whoami`, will tell you the username of the user who is currently logged in to the terminal:

	$ whoami
    alexlew

There are many, many commands like `date` and `whoami` (many of them significantly more interesting) already built in to your computer. You'll learn some of the most useful ones soon. You'll also see that it's possible for you to use a programming language – like Racket or C or Go – to teach the computer your *own* commands.

### 2. Directories and Files

In order to make good use of the command line, you need to understand that the information on your computer is, conceptually, all organized into "Directories" and "Files."

Let's take a step back. Where do "bits" (zeroes and ones) actually live? When you say that a photo is "on your computer," what do you mean, exactly? Everything that you see on your screen (and lots that you don't see) is represented in zeroes and ones *somewhere* – but where? If you look at a website in Safari, is it "on your computer" in the same sense that your photos are?

In fact, zeroes and ones are stored in *two* places on your computer. Some are in *memory* ("RAM"), and some are in *storage* (the "hard drive"). Both your computer's memory and its storage are physical things, inside your laptop's casing. They both contain millions of *transistors*, the physical properties of which allow them to carry "on/off" state. Some of those transistors are on and some are off, at any given moment, and so we can read the states of those transistors as patterns of zeroes and ones (`off, off, on, off` becomes `0010`, for example).

The major difference between memory and storage is this: When you turn off your computer, whatever patterns of zeroes and ones were stored in memory are lost. Storage, on the other hand, persists. When you reboot your computer, everything on your hard drive stays where it was. You can even take out your hard drive and put in another computer, and access all your files there. Memory is for information your computer needs *temporary* access to, like an image you're looking at in your browser, or the current location (on your screen) of your Microsoft Word window. Storage is for the things you want *permanent* access to, like apps and photos and documents and system settings.

For now, let's focus on storage (we'll talk much more about memory later in the course). When you get down to it, your hard drive contains a long, long string of zeroes and ones, and that's it. Conceptually, though, we don't think of things that way. We think of those zeroes and ones as being grouped together into *files*: a set of bits to represent that photo from spring break, another set to represent your Modern East Asia essay, yet another to represent *I Knew You Were Trouble (When You Walked In)* in MP3 format. 

Each of those files (groups of bits that represent something) has some *metadata* associated with it, too: the name of the file, the date it was created, the date it was last modified, and so on. This information is not actually part of the file itself; it just describes certain properties of the file. 

Files live inside *directories*, or folders. Every computer has at least one folder, called *the root folder*. On a Mac, you can visit your root folder by going into Finder, selecting `Go to Folder...` from the `Go` menu, and typing `/` (a single slash) when asked what folder you'd like to see. You'll likely see several directories (folders) inside the root directory, like `Applications` and `Users`. Directories, like files, live inside other directories.

Every single file on your computer lives inside some directory; every single directory lives inside another directory; except for the root directory, which is, in a sense, the "top of the tree." A *path* is a string of text that describes exactly where a file or directory is on your computer, in relation to the root directory. For example, I have a file called `notes.doc	` in a folder called `Notes` on my Desktop. It turns out that my Desktop is actually just a directory, called `Desktop`, which is inside of another directory, called `alexlew` (my username). That directory is inside of a directory called `Users	`, which is inside the root directory, otherwise known simply as `/`. The "path" to notes.doc, then, is:

	/Users/alexlew/Desktop/Notes/notes.doc

Starting at the root directory, we go into Users, then alexlew, then Desktop, then Notes, and finally, we find the file notes.doc. The slash character separates pieces of the path from one another.

### 3. Navigating Storage on the Command Line

Whenever you are on the command line, you are (conceptually) "inside" some directory, called your *working directory*. Which directory you are in will change the meaning of the commands you type. Your working directory is allowed to be any directory on your computer, and you can change it anytime. To see the path of your current working directory, you can type the command `pwd`, which stands for 'print working directory':

	$ pwd
    /Users/alexlew/Desktop/Notes

In this case, I am in my Notes directory. If I wanted to change my working directory, for example, to the root directory, I could use the `cd`, or 'change directory,' command, followed by the path of the directory I want to change to:

	$ cd /

You won't get a response here, but if you try `pwd` again, you'll see your directory has changed to the root directory. I can also go to my Documents folder:

	$ cd /Users/alexlew/Documents
    
Once you are in a directory, you may want to know what's in it. That's what the `ls`, or 'list,' command is for:

	$ ls
    Commonwealth		IMG_49321.jpg
    Personal			ScreenShot.png
    important.docx		taylorswift.mp3
    presentation.pptx	
    
This lists all the files and subdirectories in the working directory. You can see more of the metadata associated with those files if you type `ls -l` instead of plain `ls`:

	$ ls -l
	drwxr-xr-x@   4 alexlew  staff      136 Jan 27 17:33 Commonwealth
	drwxr-xr-x    3 alexlew  staff      102 Dec  2 18:53 Personal
	-rw-r--r--   38 alexlew  staff     1292 Mar 13 10:27 important.docx
    ... and so on

The number just before the date is the size of the output, in bytes. (A byte is 8 bits, or binary digits.)

### 4. Commands

1. mkdir
2. rmdir
3. rm
4. cp
5. touch
6. open
7. cd
8. pwd
9. xxd [-b]
10. cat
11. man

Create a new file, put some text in it using a text editor, and save. Then use output redirection to save the binary dump to a file.
