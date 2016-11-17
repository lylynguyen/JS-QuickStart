# JS-QuickStart
> Set up the required tools and frameworks for Full-Stack JavaScript Development

<em> Welcome to the JS QuickStart Instructions! </em>

[Windows Setup](#windows) | [Mac OS Setup](#mac-os)

## Windows

This document aims to provide a guide for setting up the developer's workstation on Windows operating system using chocolatey package manager.

REQUIREMENTS
* Processor: Intel Core i3 or higher (ideally Core i5 or i7) 2GHz or more recommended
* Memory: 4GB (8 to 16GB recommended) DDR3
* Hard Drive: 250GB recommended
* Operating System: Windows 7 or higher

Overview:
1. SET UP CHOCOLATEY
 * Chocolatey is the package manager for Windows. You'll use it to install various software componets on your workstation.

2. INSTALL THE SOFTWARE

<em> If you encounter any issues during the installation process check whether you are running cmd as administrator. Entering the chocolatey installation command in any kind of Unix shell will result in a failure. Be sure to use plain cmd.exe program for the installation. </em> <br>

3. DOWNLOAD ARCHANIST <br>
4. POST-INSTALLATION CONFIGURATION<br>
5. INSTALL OPTIONAL SOFTWARE<br>

* Select the In the Windows and start menu, start typing cmd.exe. 
* Right click it and select "Run as administrator". 

This will fire up a plain windows command line (cmd.exe) as administrator
<em> Now you're ready to copy the following command into the command line.</em>

| Command       | Result       |
|:------------- |:-------------|
| SET UP CHOCOLATEY | |
| `@powershell -NoProfile -ExecutionPolicy unrestricted -Command "iex ((new-object net.webclient).DownloadString('https://chocolatey.org/install.ps1'))" && SET PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin` | This should download and setup chocolatey using powershell. |
| `choco --version` | Checks whether everything is working. You should see the current version of Chocolatey if the installation process finished successfully. |
| INSTALL THE SOFTWARE| |
| `cinst -y git & refreshenv` | Installs GIT |
| `cinst -y php --ignore-checksums & refreshenv` | Installs PHP (ignore-checksum flag required since feature was only left in configuration because previous choco had it according to "https://github.com/chocolatey/choco/issues/112".) | 
| `cinst -y nodejs.install & refreshenv` | Installs nodejs |
| `cinst -y vcredist2015 & refreshenv` | Installs vcredist2015 |
| `git --version` | Ensures that the git command is recognized. You may want to restart the command prompt. Ensure you have access to your project's repository|
| `cd %USERPROFILE%\AppData\Local\Temp & git clone https://[github].[business].com/chocolatey-repo/arcanist.git && move arcanist\php.ini C:\tools\php\ && cinst -y arcanist.portable -source %USERPROFILE%\AppData\Local\Temp\arcanist & rmdir /S /Q arcanist` | This command adds arcanist binary and npm to the PATH environment variable so we can use it. (You may be prompted to enter your credentials). |
| SETX PATH "%PATH%;C:\tools\php;C:\ProgramData\chocolatey\lib\arcanist.portable\tools\arcanist\bin; & refreshenv" | |
| arc set-config editor "C:\Program Files(x86)\Git\share\vim\vim74\vim.exe" | Arcanist requires you to set up an editor. This editor will be used to present you with differential forms. This example uses vim installed with git. |

| To work with [github] need to generate rsa keys and set public key (id_rsa.pub) in [github] (Dashboard -> Manage SSH keys). |  To run ssh-keygen command, you might have to run git-bash first (right clink on 'desktop' and select 'Git Bash Here' option).|

Note: If GitHub usage is blocked via git protocol, you will need to set it up to use https instead. Following command will do the trick:

git config --global url."https://".insteadOf git://
TESTING OUR INSTALLATION
The software installed includes:

NodeJS,
Git,
Arcanist (+ php & vcredist2012 as dependencies)
Now restarting the command line allows this change to the environment variable to take effect.

You can test whether nodejs/npm is working fine by installing grunt and bower globally npm install bower grunt-cli -g and running grunt.

To test arcanist package run arc help and you should see the arcanist command reference.

OPTIONAL SOFTWARE
You can install additional (optional) software (caution, will download full size installers)

cinst -y google-chrome-x64 Firefox vagrant virtualbox phantomjs atom boot2docker
Additional software includes:

Google Chrome
Firefox,
Vagrant,
VirtualBox
PhantomJS
Atom
boot2docker
To install specific packages (due to low connection or failed attempt) modify the command to include only desired packages (i.e. cinst -y nodejs).


## Mac OS
<em> Have you got your Apple OS X Macbook ready to go? Let's do it! </em>

<<< UNDER CONSTRUCTION >>>

#### Navigate to the Terminal (Command + SPACEBAR)
*Once prompted, copy the commands below:*

| Command        | Result           |
|:------------- |:-------------|
| `ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"` | Installs Homebrew, the MAC OS package manager |
| `brew update`       | Checks for latest version of Homebrew |
| `brew install node` | Installs Node.js                      |
| `npm update npm -g` | Installs npm, the major package manager for JavaScript (Learn about it [here]()) |                                      |

#### Click the links below:

* [Learn about JavaScript](http://bdcampbell.net/javascript/book/javascript_the_good_parts.pdf)
  * [Download "JavaScript: The Good Parts" by Douglas Crockford] (http://bdcampbell.net/javascript/book/javascript_the_good_parts.pdf) <br>
    <em> Especially recommended for individuals coming from the <b>Java</b> language </em>
* Learn about Node.js <br>
> <em> Node.js is a platform built on Chrome's JavaScript runtime for easily building fast, scalable network applications. </em>
* [Learn about NPM](https://www.npmjs.com/)
> <em> NPM is the most widely used package manager for JavaScript </em>
* [Learn about Express](http://expressjs.com/)
<em>Express is a minimal and flexible node.js web application framework, providing a robust set of features for building single and multi-page, and hybrid web</em> applications.
* Optional: Get an overview of Angular
> <em> AngularJS lets you extend HTML vocabulary for your application. The resulting environment is extraordinarily expressive, readable, and quick to develop. </em>
