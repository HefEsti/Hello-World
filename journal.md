# ROCO222

## Lab journal
### 25th of September



#### First markdown document

Markdown - formating language
Used as it is easy to convert to HTML and other languages.

#### Command-line 101

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
We tried to build a DC motor from sratch. We used magnets, paper clips and electric tape. 
![alt text](https://github.com/HefEsti/ROCO222/blob/master/26134019_1933000850046889_34657071_o.jpg)


We used the design given in the labsheets: 

#### Commutator:
-Cork and electric tape on two sides

#### Armature
-Copper wire: 80 turn (minimum of 60)
-Sandpaper ends and solder it 
      We had problems with the wires, we didnt get any voltage.
          After rewireing 2 times, we found that we didnt sand the ends properly, so we re did them and after that it worked

#### Shaft
-Built shaft with paperclips
     we had problems with the paperclips, the nails holding the cork got stuck, and didnt let the cork turn 
        we re did the shaft, trying to get a perfect loop with the paperclips so the cork can turn - it did. 
  magnets opposite each other
  
#### Brushes
-Electric tape
  we had a couple of problems as it made the rotation uneven, the cork got stuck 
     we re did them with longer tapes, so it didnt get stuck in the end of it
    
[The video shows our DC motor and the problems wit the brushes](https://www.youtube.com/watch?v=N0y_D7YMK28 )

  
After this we added a second coil to our motor.
We rebuilt the shaft with LEGO and attached a wheel to the end of the cork to see its rotation and to help our next task, the encoder.
[Video shows the new shaft](https://www.youtube.com/watch?v=8WvBiNtY8GU  )

### Incremental Encoder
#### Understanding the basics
  First we took some time to understand how the encoder works
     We have 3 componets
        -LED light source
        -phototransistor detector
        -Paper with holes on it 
     
  As the paper turns, the light from the LED passes through the holes, reaching the detector. 
      because of the holes, the signal is not constant
         
#### Building the circuit and adding thr encoder
  We built the circuit provided in the labsheets
     using 1K and 10K ohm resistors
     
  It was working, we checked if we get any voltage and we did. 
     if the LED is blocked the voltage across will rise
      
 We tried adding the encoder, but it was to thick, and got stuck between the reciever and the light source.
   we used a different kind of paper and it worked
   
#### Arduino
  We connected our encoder to the arduino board and tested with the provided code
  
#### Motor Control with Arduino  
 We got the Arduino kit out of the store and put it together
      put the motor shield on the board
      
 We connected the motor to Chanel A on the motor shield and Set up the Arduino program
    We used the code provided, but the Pins needed to be changed
    
PinMode(12, OUTPUT); //  Controlls the direction of the motor (Forward or backwards)
pinMode(9, OUTPUT); //   Start or stops the motor

You can controll the speen in the analogWrite(X, Y); command
255 is full speed
 
Our code broke down to an easier form was:
  
 ```c
// ...
Set forward direction
start motors 
wait
stop motors
set backwards direction
start motors
....
// ...
```
     
Later when we experimented with the robot arm, we made the motor to move around one way completly then to the other. (code inserted there.)     
         

#### Stepper motors
 First we took some time to understand how the encoder works, using the lecture slides and some researh on the internet.
 

We did the following modes: 

Full-step 
Double-step mode 
Half-step mode 
Micro-step mode  (we couldnt do this one)

we wrote a truth table for each of them and acordint to it, wrote the code.


INSER CODE HERE AND TRUTH TABLES!!! (PICTURE)
 

#### Building a Robotic Arm
### Experimenting with the motors
We wanted to move the motor to one way completly than the other
 
   
 ```c
// ...
 #include 
Servo myservo; // create servo object to control a servo

int potpin = 0; // analog pin used to connect the potentiometer
int val=0; // variable to read the value from the analog pin
int val2=0;

void setup() {
myservo.attach(3,700,2000); // attaches the servo on pin 9 to the servo object
}

void loop() {

for (val==0; val<=180; val++)
{
myservo.write(val); // sets the servo position according to the scaled value
delay(15); //Waits for servo to get there
}

for (val==180; val>=0; val--)
{
myservo.write(val); // sets the servo position according to the scaled value
delay(15); //Waits for servo to get there
}
}
// ...
```
![alt text](https://github.com/HefEsti/ROCO222/blob/master/26772522_1947747018572272_1047964130_o.jpg)
Unfortunatelly I  had to miss a couple of labs after this so the speed of progressed slowed down. 
I designed a 3d model for our robotic arm. 
The idea was to have the motor's rotors fit into a hole exactly the shape and size as the rotors and then as it cannot move out of the whole it moves the whole arm.

[ the final design](https://www.youtube.com/watch?v=f7zUKXsmWtg )


we printed it and assembled it.

we then loaded the code and tested the robotic arm.
IT WORKS! KINDA. BUT IT WORKS.
we connected the two motor to one power pin (soldered them together)
and then to the same output pin as well. (no, its not on fire... SUCCES)
[Robotic arm in motion, using both motor](https://youtu.be/cOelTML7cZ )

