# Summary Linux and The CLI

## Linux

- What you will learn
        
	 The objective of this course is teach you two principle concepts: what is Linux and why you'd use it, and how to use a command line. This two concepts I found were big barriers for developers getting started in their careers and I wanted to help demystify that. Throughout my career I've worked with developers who purposefully avoid the command line and I think that's a shame, you can do a lot of things quickly with just a bit of know-how.

    So today we'll cover the following:

    - What is Linux
    - What problems Linux solves for you
    - How Linux is generally laid out
    - What the command line is
    - Basic navigation in the command line
    - Common tasks with the command line
    - Some basic customizations

    I hope you'll come out the other side of this excited about what the command line and Linux can do for you!

- What is Linux

    Linux is an operating system. In fact, one of the most popular platforms on the planet, Android, is powered by the Linux operating system. An operating system is software that manages all of the hardware resources associated with your desktop or laptop. To put it simply, the operating system manages the communication between your software and your hardware. Without the operating system (OS), the software wouldn?t function.
 - why linux
    - it's free.
    - It's very well maintained.
    - It runs just about anywhere.
    - Most of the the things you need already exist for it.
    - The knowledge base for Linux is enormous.

##  The CLI
- Anatomy of a CLI Command
    
    CLI is often called a REPL, a Read Evaluate Print Loop. It's basically an interactive way of programming where you're writing one line of code at a time, feeding data in and out of little programs. Using commands here, you can navigate around you computer, read and write data, make network calls, and all sorts of other stuff. Basically most anything you can do with a desktop you can do with a command line, just a little less obvious how to do it.

    The way a REPL works is that you send one command at a time and the shell runs the command and returns to you a result. During the course of running that one command, it may print some things out. And you can, using some rudimentary programming syntax, write a line that runs multiple times (or, another way of saying "runs multiple times" is looping.) That's it! That's whole concept of what we're going to learning today.

## Editors
- nano
    
    nano is an old open source text editor that itself was an evolution from a previous text editor called pico. Pico was the text editor of the command-line email client Pine that people grew to love so much that they used it for everything. Because Pine was licensed in such a way that Debian wouldn't include it with its distro, Chris Allegretta re-implemented under the name TIP (Tip Isn't Pico, computer scientists love recursive acronyms) it eventually was renamed to nano.

    Due its tiny size, light weight, and permissive license, nano is included on just about every Linux/Unix-like OS and is frequently the default text editor, even on tiny little embedded devices where even vim is too much. As such, it's a good tool to have your tool belt if you need to do some light text editing.

- vim
   
     The genesis of the ideas that went into vim started with an editor called ed (said ee-dee) which itself was inspired by a previous editor called qed. ed was developed by Ken Thompson at Bell Labs in 1969. It is a line-oriented editor and I have no clue how to use it. It's actually rather well known for being pretty user unfriendly. In spite of this, it's still available on most Unix-like systems including Ubuntu and macOS. If you do start it, just know it's CTRL+D a few times to quit it. It's important to note that ed was created in a time where memory was precious, screens were tiny and sometimes just one line at a time, and modems were measured in bits, not even kilobits. It arose at a time when it fit its constraints.

## Files, Pipes, and Permissions
- Interacting with Files
    A core concept of computing in general is files but in particular when it comes to navigating a command line. In this section we're going to go over some of the core programs you'll want to know so you can interact with files in Linux :

    - `less`. `less` is a program for reading files.
    - `man`. it will show manual for a command. If you run `man less` it will show you the manual for `less`.
    - `cat`. `cat` is short for concatenate because it concatenates the file to the standard output. Similar to less but all `cat` does is read the entire file and output it.
    - `head` / `tail`. Head will read the first lines of a file and out put them and tail will read the last lines of a file and output them.
    - `mkdir`. mkdir makes a new directory/folder.
    - `touch`. `touch` create a new, empty file.
    - `rm`. Remove a file.
    - `cp`. `cp` is short for copy.
    - `mv`. `mv` stands for move. This how you move a file from one place to another, or how you rename a file.
    - `tar`. `tar` is short for tape archive and it initially used to prepare files to be backed up to a magnetic tape archive but it became useful to just group together files in single files as a tarball (like a zip file).
- Wildcards and Replacements
    ### Wilcards
    
    A wildcard is a symbol that takes the place of an unknown character or set of characters. Commonly used wildcards are the asterisk (*) and the question mark (?). Depending on the software or the search engine you are using, other wildcard characters may be defined.

- Streams and Pipes
    
    ### Streams
    Linux has an interesting concept where basically all input and output (which are text) are actually streams of data/text. Like plumbing pipes where you can connect and disconnect sections to redirect water to different places, so too can you connect and disconnect streams of data. There are three standard streams :
    
    - stdout (said standard output or standard out).
    - stdin (said standard input or standard in).
    - stderr (said standard error or standard err).
   
    ###  Pipes
    One of the most powerful shell operators is the pipe (|). The pipe takes output from one command and uses it as input for another. And, you're not limited to a single piped command—you can stack them as many times as you like, or until you run out of output or file descriptors.
    
    

- Users, Groups, and Permissions

    - User: the owner of the file (person who created the file).
    - Group: the group can contain multiple users. Therefore, all users in that group will have the same permissions. It makes things easier than assign permission for every user you want.
    
    ### Permissions
    Every file and directory in your UNIX/Linux system has following 3 permissions defined for all the 3 owners discussed above.
    
    Read: This permission give you the authority to open and read a file. Read permission on a directory gives you the ability to lists its content.
    Write: The write permission gives you the authority to modify the contents of a file. The write permission on a directory gives you the authority to add, remove and rename files stored in the directory. Consider a scenario where you have to write permission on file but do not have write permission on the directory where the file is stored. You will be able to modify the file contents. But you will not be able to rename, move or remove the file from the directory.
    Execute: In Windows, an executable program usually has an extension “.exe” and which you can easily run. In Unix/Linux, you cannot run a program unless the execute permission is set. If the execute permission is not set, you might still be able to see/modify the program code(provided read & write permissions are set), but not run it.


## Environments and Processes
- Environments
    In Linux and Unix based systems environment variables are a set of dynamic named values, stored within the system that are used by applications launched in shells or subshells. In simple words, an environment variable is a variable with a name and an associated value.
- Processes
    At all times with Linux a certain amount of processes will be running. A process is any sort of command that's currently running. Go ahead and run ps and see what it outputs. For me the list is pretty short because it's showing just what me, ubuntu, is running which isn't much. ps stands for processes snaphshot. To prove my point, try the following.

- Exit Codes, Process Operators, and Subcommands
   
     Before we jump too far into how to run commands in sequences, let's chat one second about exit codes. Whenever a process exits, it exits with an exit code. This exit code corresponds to if a process successfully completed whatever you told it to do. Sometimes this is a bit misleading because sometime programs are meant to be stopped before they complete (as some like yes will never actually complete by themselves).

    A program that successfully runs and exits by itself will have an exit code of 0. Try this:

        date # show current date, runs successfully
        echo $? # $? corresponds to the last exit code, in this case 0
        yes # hit CTRL+C to stop it
        echo $? # you stopped it so it exited with a non-zero code, 130

    So what do all the codes mean? Well, it depends on the program and it's not super consistent. It can be any number from 0 to 256. But here are a few good ones that are common

    - 0: means it was successful. Anything other than 0 means it failed
    - 1: a good general catch-all "there was an error"
    - 2: a bash internal error, meaning you or the program tried to use bash in an incorrect way
    - 126: Either you don't have permission or the file isn't executable
    - 127: Command not found
    - 128: The exit command itself had a problem, usually that you provided a non-integer exit code to it
    - 130: You ended the program with CTRL+C
    - 137: You ended the program with SIGKILL
    - 255: Out-of-bounds, you tried to exit with a code larger than 255
    
    There are a few others but these are the most common ones you'll see. You'll see some programs use numbers like 5 to 100 to signify different ways the program ended but you can pretty safely ignore that. It's usually just important if it's 0 or not-0.
    
    Okay, so why is this important? It can be useful to see if a previous command succeeded or not, but it's also useful for running programs in a sequence using operations.
    
    So what if you need to run two processes in a row, one right after the other? Well, you have a few options.
    
    ### Run if first one succeeds
    
    You'll probably see this the most. Let's say I wanted to create a file, add the date to it, and then add my current uptime to it. (try runnning uptime, it just tells you how long your computer has been running.)

        touch status.txt && date >> status.txt && uptime >> status.txt
        cat status.txt
    
    You can see it does all three commands right in a row. That's what the && operator does. It runs from left to right (touch, date, then uptime). The && operator will bail if any of those commands fails. Try this:

        date && cat not-real-file.txt && echo hi # the date will display but hi won't
    
    Since not-real-file.txt doesn't exit, it bails and hi is never echoed.

    ### Run if first one fails

    There's also a || command that will run if the first one fails.

        false || echo hi # you'll see hi
        false && echo hi # you won't see hi
    
    false is a command that just returns 1 (there is a true that always returns 0) In this case, you'll see hi the first time and not the second time.

    ### Always Run
    
    If you need always run the second command, use a ; instead of either && or ||.

        false ; true ; echo hey # you'll see hey

    ### Subcommands
    
    Sometimes you need to invoke a command within a command. Luckily bash has you covered here with the ability to run subcommands.

        echo I think $(whoami) is a very cool user # I think ubuntu is very cool
    
    The $() allows you to put bash commands inside of it that then you can use that output as part of an input to another command. In this case, we're using whoami to get your username to echo that affirming message out. Let's a more practical one. Let's say you wanted to make a job that you could run every day to output what your current uptime was. You could run this command

        echo $(date +%x) – $(uptime) >> log.txt

    The +%x part is just saying what date of format you want, and I got that from reading date --help. So end printing something like

        06/17/20 – 21:38:34 up 8:51, 1 user, load average: 0.00, 0.00, 0.00
    
    There are far more useful logs to write but you can see here the power of subcommands. Note you can also use backticks like ` instead of $() but it's preferred to use the $() notation. Notably, you nest infinitely with $(). For more reasons

## Networking and the Internet
- SSH
    One of the most key things you need to take away from this workshop is how to remotely connect to a server and run commands on it. This is one of the times you absolutely must know your way around bash or you'll be out of look because there's no other way how to do it.

    ### When would you do this
    
    One of the easiest things to do is to get a VM (virtual machine) up and running in the cloud. So many companies offer this like Azure, DigitalOcean, AWS, Linode, etc. A VM is literally just a Linux machine running somewhere in the cloud. Many times the only real way to administrate and run code on these servers is just to connect into a remote CLI session and run the code yourself. It's also very easy with your newly learned skills! Let's see how to do that.
- SFTP

    Sometimes you need to transfer files between two computers. This can take the form of either transferring files from you local computer to your remote server or from your remote computer back to your local computer. Before we had more mature continuous deployment tools like Azure Pipelines, Travis CI, or GitHub Actions, we often used a tool called ftp (file transfer protocol). While it worked and it was a relatively simple and straightforward of doing things, we moved onto to more reliable tools. However ftp evolved into secure ftp which we still use today.

    ### How to set up sftp
    Okay, buckle up. This is your biggest challenge yet.

    Just kidding, you're already done. One of the best things about sftp is that it works 100% over the same ways that ssh does so if you've set up ssh you've inherently set up sftp too (it possible to set up one and not the other but you have change some options.) This was a welcome departure from ftp which has its own setup process and ports that had to be managed.

    Okay so using the VMs we set up in the previous section, let's sftp into secondary from primary. The sftp interactive shell is similar to a less friendly and stripped down version of bash. The thing to keep in mind is you're in two directories at the same time as opposed to normal bash when you're just in one. With sftp, you have a local context and a remote context. In order to run a local command, tack an l to the start of whatever command you're running, like lls, lpwd, or lcd. When you want to do it on the remote machine, just run the commands like normal, like ls, pwd, or cd.
- wget

	Frequently you will want to send requests to the Internet and/or network. The two most common tools to do that are wget and curl. Both of these are common to find in use so I'll take the time to show you both but they do relatively do the same thing. In general I'd suggest you stick to using curl; it's a more powerful tool that can do (almost) everything wget can.

	example :
	    `wget https://raw.githubusercontent.com/btholt/bash2048/master/bash2048.sh
	    chmod 700 bash2048.sh
	    .bash2048.sh`
	
	That wget gets the file, the chmod 700 makes the file executable, readable, and writable for the current user (and no one else) and the  `. bash2048.sh`  executes the game. Pretty cool, right? Very cool project. Feel free to play for a second. When you're done, hit CTRL+C to exit. It does exit the shell entirely so may need to open a new shell after via Multipass.

	wget can do a lot more than this, including be able to post and various other ways of shaping requests. Just say  `wget --help`  to see the myriad options available to you.

	So why learn a bit about wget? wget is a GNU project and it's available  _everywhere_. Frequently you'll find tutorials that use it so I wanted you to have a bit of familiarity with it. Now let's get into curl which is the one I recommend you invest more into that wget. Know and be aware of wget but learn curl.

	The one case you'll want to use wget is if you want recursive downloads of site. wget has a peculiar ability that it will read the incoming document and download all the links it finds within it, crawling all the documents until it downloads all the files it founds. That can occasionally be useful and not something curl does by itself.

- curl
    
    curl is used in command lines or scripts to transfer data. curl is also used in cars, television sets, routers, printers, audio equipment, mobile phones, tablets, settop boxes, media players and is the Internet transfer engine for thousands of software applications in over ten billion installations.
## Package Management
- What is Package Management
   
     Ubuntu by itself is a very useful system but we begin to see its infinite possibilites when we dive into the packages that are available to it. Ubuntu comes with its own lovely package manager tools and I'm going to show you how to use some of them to get more tools so you can do more cool stuff.

     We'll be going over specifically what Ubuntu has for package management but just be aware that each Linux distro has its own package management tools.

    - Debian has dpkg. Because Ubuntu is based on Debian it also has dpkg installed and available to use.
    - APT (advanced packaging tool) is based on dpkg and available to all in the Debian family of distros
    - Red Hat had RPM, Red Hat Package Manager
    - Similar to how APT is on top of dpkg, YUM is on top of RPM to make it easier to use. DNF is the next generation of YUM
    - Arch has Pacman
    - Alpine has APK
    
    Even macOS has one with Homebrew and Windows with its new winget system. Again, we'll be focusing on APT and Snap today.
    
- APT
  
     The first tool of interest is APT, advanced packaging tool. This tool has been around for a while and uses dpkg under the hood. There have been several iterations of it so let's make sure you get what APT is going to do for you and how to use it.

    This will go out and fetch the package lolcat from the apt registry and install. After a second it should download and be immediately be available for use. Now try this: ls -lsah | lolcat.
    
- Snaps
    Okay, so a bit of history here is necessary and I don't want to delve too much into it. It has to do with how Linux programs are packaged and there's a decent amount of controversy and disagreement around the best way to do it is.

    Canonical a few years announced a new way of packaging app called snaps. Snaps are advantageous over what was there before (apt typically deals with debs) for a few reasons:

    - They're totally self contained. They package all their dependencies with them
    - They're sandboxed. They can't mess with your system
    - They can update by just downloading the difference between ther versions

    
## Shell Scripts
- Writing Your Own Scripts
    
    Let's make our first bash script. Let's make make a directory called temp, generate ten files, and exit. Basically we want to make a bashscript that does this:

        mkdir -p ~/temp # -p mean don't error if it exists in this case, it does other things too
        cd ~/temp
        touch file{1..10}.txt
        echo done

    So let's do that. You can use either vi or nano, both work. So run vi gen_files.sh or nano gen_files.sh. From there, put the above code in it and save.

    Also, you can cd freely within a script: it only changes the working directory for that shell script, not for the user. The user in their interactive shell won't

    Now, to run it, do `. gen_files.sh` or `source gen_files.sh` or `bash gen_files.sh` Any of those work the same way.

- Variables
    
    As you write more complicated scripts you need to use variables to make it more flexible. The way to do this is to use variables. Can you imagine writing code without use variables? It's possible, I suppose, but certainly not fun. And let's not do it!

    ### Setting a Variable
    
    This is a short section! It's very easy to set a variable. and you've already done it. Modify `~/bin/gen_files` to be as follow:

        #! /bin/bash
    
        DESTINATION=~/temp
        FILE_PREFIX=file
        
        mkdir -p $DESTINATION
        cd $DESTINATION
        touch ${FILE_PREFIX}{1..10}.txt
        echo done

    
    As you can see above, setting a variable is as easy as saying `NAME=value.` You can use quotes too, optionally. You do not have to make them uppercase though I suggest you do as that's what's normal for bash scripts.

    Below we're using them like we used environmental variables before (hint: those are really just variables too.)

    Let's talk about touch `${FILE_PREFIX}{1..10}.txt.` Whereas we don't need the `{}` the first two times we refer to a variable, we do on this one. That's because we're inserting it in the middle of something. The `{}` let bash know where the variable names stops. The first two you can totally use them too e.g. `cd ${DESTINATION}` but it's optional. As a reminder, if you use `$()` it means a subcommand like `touch $(whoami).txt.`

    ### User Input
    
    So what if we want users to be able to define the file prefix? Easy! There's a program called read that will get user input and define a variable based on it. Try it by running read name && echo hello $name

    So let's stick that in there

        #! /bin/bash
        
        DESTINATION=~/temp
        read -p "enter a file prefix: " FILE_PREFIX
        
        mkdir -p $DESTINATION
        cd $DESTINATION
        touch ${FILE_PREFIX}{1..10}.txt
        echo done

    The -p flag allows us to prompt the user with a string, letting them know what we're expecting

    ### Arguments
    
    What if we want the user to be able to pass in the path to where we want to create the directory? We can do that via arguments (sometimes called parameters too.) We want the user to be able say `gen_files ~/different_directory` and use that input as $DESTINATION. Easy!

        #! /bin/bash
        
        DESTINATION=$1
        read -p "enter a file prefix: " FILE_PREFIX
        
        mkdir -p $DESTINATION
        cd $DESTINATION
        touch ${FILE_PREFIX}{1..10}.txt
        echo done
        
    Here we just replaced what went into DESTINATION with $1. We totally could have replaced everywhere there was DESTINATION with $1, but it was easier (and made the script clearer) by replacing the contents of DESTINATION with $1.

    $0 is available here too. It'll be gen_files. And if you gave two arguments, the second one will be $2 and so on and so forth.
- Conditionals
   
     In order to write useful bash scripts you need if statements. Let's go over how to make more complicated scripts using these control structures.
    
    Conditionals
    A conditional is a statement that only runs if a condition is true. Let's say we want to use the path ~/temp if the user don't provide an argument.
    
    for example code
    
        #! /bin/bash
    
        DESTINATION=$1
        read -p "enter a file prefix: " FILE_PREFIX
        
        if [ -z $DESTINATION ]; then
          echo "no path provided, defaulting to ~/temp"
          DESTINATION=~/temp
        fi
        
        mkdir -p $DESTINATION
        cd $DESTINATION
        touch ${FILE_PREFIX}{1..10}.txt
        echo done


- Loops and Arrays
    Any programming language needs a way to do repetitive tasks and bash is no different. It has several flavors of loops that should look familiar to anyone who has done programming before.

    You frequently also need groups of variables. Bash has this is as well with arrays and we'll go over how to use those.
    
    ### Arrays and For Loops
    Arrays can do a lot and are very flexible. For now we're just going to go over how to declare them and how to read from them. Make a new array.sh and put this in there:
    
        #!/bin/bash
    
        friends=(Kyle Marc Jem "Brian Holt" Sarah)
        
        echo My second friend is ${friends[1]}
        
        for friend in ${friends[*]}
        do
            echo friend: $friend
        done
        
        echo "I have ${#friends[*]} friends"

    ### While
    
    What if we wanted to make a program that wouldn't exit until you guessed the correct number? We can use a while loop together with read to make such a wonderfully annoying game.

        # let "NUM_TO_GUESS = ${RANDOM} % 10 + 1"
        NUM_TO_GUESS=$(( $RANDOM % 10 + 1 ))
        GUESSED_NUM=0
        
        echo "guess a number between 1 and 10"
        
        while [ $NUM_TO_GUESS -ne $GUESSED_NUM ]
        do
          read -p "your guess: " GUESSED_NUM
        done
        
        echo "you got it!"


## Last Thoughts
- cron
   
    Ever had a task that needs to be done every day? Linux has a feature called cron that will run tasks on a schedule.

    There are two ways to accomplish this, an easy way to remember and a slightly less easy way.
    
    ### cron folders
  
    Any script you put in any of the following will be run on a schedule:
    
    `/etc/cron.daily`
    `/etc/cron.hourly`
    `/etc/cron.monthly`
    `/etc/cron.weekly`
    
    Just make sure they have executable privileges. sudo chmod +x <file> will do what you need it to do. Anything in here will be run as root.
