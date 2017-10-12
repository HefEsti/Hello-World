#ROCO222

## Lab journal
### 25th of September

#### First markdown document

Markdown - formating language
Used as it is easy to convert to HTML and other languages.

#### Command-line 101

![image-title-here](file:///home/student/Pictures/codeHELLO.png){:class="img-responsive"}

$ ls  
$ cd /tmp  
$ cd $HOME # what are those things starting with '$'?  
$ mkdir  
$ echo "Hello" > hello.md  
$ cat hello.md  
$ cp hello.md hello-again.md  
$ mv hello-again.md hello-hello.md  
$ rm hello.md  
$ rm -rf # be careful with that one!  
$ cat /proc/cpuinfo # is 'cpuinfo' a file??  

When we entered the code above startig with $, a message saying command not found was displayed. 
$ is automatically placed infront code
 no need to enter it again 

Remove the $ code- worked 

>echo - write arguments to outputs  
>cat - read files  
rm - remove  
>mv - move  
cp - copy   

#### Making a git repository

typing git init to create a repository 

$ git config user.name "Firstname Surname"  
$ git config user.email "<email>"  

Then added the journal to the repositorry by typing git add journal.md
  new commit using git commit

The logs you make of adds to your git repository can be seen by typing git log.

#### Adding the journal to Github

Github - remote internet server 
  upload (push) and retrieve (pull) your commits 

To do this you have to create an empty repository on your github account, then using the commands:

> git remote add origin https://github.com/<username>/<repositoryname>.git  
> git push -u origin master  

Then we logged into the github account through the terminal, and the journal was uploaded to my github.

To upload - git add journal.md, git commit, then git push
Using git pull you can retreive the file.


### Hacking into the robot


To hack into the robot enter the following commands:  
ping chapman  
ctrl c  
ssh nao@192.168.0.184 (ip)  
Enter password: nao  
Then you're in  

Type nano to edit a code to send  
type in the code  
mine:  
from naoqi import ALProxy  
tts = ALProxy("ALTextToSpeech", "localhost", 9559)  
tts.say("Hey now you're an all star, get your game on, go play!")  

then ctrl x  
yes  
enter name mine was shrek.py  
then enter  
  
then to send to the robot type python shrek.py  




### Building a DC motor

#### Commutator:
Cork and electric tape on two sides

#### Armature
Copper wire: 80 turn (minimum of 60)
Sandpaper ends and solder it 

#### Shaft
Built shaft with paperclips
  magnets opposite each other
  
#### Brushes
Electric tape
  -we had a couple of problems as it made the rotation uneven, the cork got stuck
  
  






