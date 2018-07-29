## Installation Instructions

These are notes on installation for the various tools and packages we'll use throughout the course.

## Before you arrive

Before you arrive, you should install three things: a command-line terminal, R, and RStudio.

### Command-line terminal
If you are bringing a Mac or Linux computer to work on, this is already taken care of for you. If you are bringing a Windows computer, you will need to set up a working command-line environment. 

* If your operating system is Windows 10 or later, the operating system includes a way to run a command-line environment. You can follow the helpful steps outlined [here](https://www.howtogeek.com/249966/how-to-install-and-use-the-linux-bash-shell-on-windows-10/) to get set up.

* If you have an older Windows operating system, you can set up a command-line working environment relatively easily through [Git for Windows](https://gitforwindows.org/) by following these steps.  
  * Download the "Git-2.18.0-32-bit.exe" file from the Git for Windows [download page](https://github.com/git-for-windows/git/releases/tag/v2.18.0.windows.1)  
  * After it is finished downloading, run the installer by opening the file and proceed through the installation:  
    * installing in the default folder location is fine
    * for "Which components should be installed?", make sure the following boxes are checked: "On the Desktop"; "Git Bash Here"; "Git GUI Here"; "Associate .git* configuration files with the default text editor"; and "Associate .sh files to be run with Bash"
    * the shortcuts default location is fine
    * change the default Git editor to "Nano"
    * on the "Adjusting your PATH environment" screen, select "Use Git from Git Bash only"
    * just click "Next" on the remaining configuration windows, and "Install" at the final one
  * When the installation is finished, you should be able to open a terminal window by launching Git Bash from your desktop. 


### R 
R is a programming language that is extremely useful for statistical analysis and generating figures. Follow the instructions at the following pages to download and install the appropriate version for your operating system:  
Mac – https://cran.r-project.org/bin/macosx/ (download the latest release "R-3.5.1.pkg")  
Windows – https://cran.r-project.org/bin/windows/base/  
Linux – https://cran.r-project.org/bin/linux/  

### RStudio
Rstudio is an interface for R that not only makes everything you will do in R easier and more organized, but it’s also invaluable for reproducibility of your analyses as it makes it second-nature to generate and save log files (R scripts) of everything you’re doing.

Download and install the appropriate version of RStudio for your system from here: https://www.rstudio.com/products/rstudio/download/#download


## Connecting to the MBL Servers

On your badge, you have a username and password. That will be your account for the course. 

To connect, we'll use **ssh**, a command that let's us establish a secure connnection. At the command line type the following, but replace "\<USERNAME\>" with your username:

`ssh <USERNAME>@class.mbl.edu`

Don't include the brackets. For example, if your username was "bsmith", the command would look like `ssh bsmith@class.mbl.edu`. 

The first time you log in you will get a message about security. Type "yes", and press `enter`. 

Then it will ask you for your password. Type the password listed on your badge and press `enter`; the cursor will not respond, but it is still be entered as you type.

This will take you to a prompt that might look like this "-bash-4.2$ ". This is called the 'gateway'. We won't be doing our work here though, we're going to take one more step and log into specific servers so we don't overload the computing resources. 

On your badge you also have something that says a class and a number, e.g. "class-03". Now we want to `ssh` into that specific server, so enter the following, but change the "\<??>\" to your specific class number:

`ssh class-<??>` 

Again, don't include the brackets. For example, if your class number is "class-03", the command would look like: `ssh class-03`.

Then if it asks for you password again, enter it the same way as above and press `enter`.

Now you're at the command line prompt that you'll use for much of the course.

## Other tools used in the course
