# Obstacle-Avoiding-Robot
Learn how to make your own Basic Obstacle Avoiding Robot

1)Time Needed: 3-4 Hours(if you are solo)

2)Parts/Components Needed: 

    ->Ultrasonic Sensor-HC SR04
    ->Arduino Uno
    ->Motor Driver Module- L293D
    ->Breadboard
    ->Chassis
    ->2x Geared Motors with wheels
    ->Jumper Wires: Male-Male, Male-Female
    ->And x2 9V Batteries / 9-12V DC power supply.

 3)Code:
 
    const int trigPin = 11;  //Defines the Trig pin from Ultrasonic Sensor to Arduino pin 11
    const int echoPin = 10;  //Defines the Echo pin from Ultrasonic Sensor to Arduino pin 10
    const int in1 = 9;       //Defines the Input 1 pin from Motor Driver Module to Arduino 9
    const int in2 = 8;       //Defines the Input 2 pin from Motor Driver Module to Arduino 8
    const int in3 = 4;       //Defines the Input 3 pin from Motor Driver Module to Arduino 4
    const int in4 = 3;      //Defines the Input 4 pin from Motor Driver Module to Arduino 3


    void setup() 
    {
    pinMode(trigPin, OUTPUT);  //Sound sent from Ultrasonic Sensor To detect Obstacle 
    pinMode(echoPin, INPUT);   //Information of the obstacle sent from Ultrasonic Sensor back To Arduino
    pinMode (in1, OUTPUT);     //Instruction from Arduino To Motor Driver for wheels(Precise Motion)
    pinMode (in2, OUTPUT);     //Instruction from Arduino To Motor Driver for wheels(Precise Motion)
    pinMode (in3, OUTPUT);     //Instruction from Arduino To Motor Driver for wheels(Precise Motion)
    pinMode (in4, OUTPUT);    //Instruction from Arduino To Motor Driver for wheels(Precise Motion)
    }
    long duration, distance;

    void loop()
    {     
    digitalWrite(trigPin, LOW);
    delayMicroseconds(2);
    digitalWrite(trigPin, HIGH);
    delayMicroseconds(10);
    digitalWrite(trigPin, LOW);  
    duration = pulseIn(echoPin, HIGH);
    distance = duration/58.2;
    if(distance<15)       //Distance of object [greater than 15cm]
    {
      digitalWrite(in1, LOW); 
      digitalWrite(in2, HIGH); 
      digitalWrite(in3, HIGH); 
      digitalWrite(in4, LOW);
     }
    else
    {
      digitalWrite(in1, HIGH); 
      digitalWrite(in2, LOW); 
      digitalWrite(in3, HIGH); 
      digitalWrite(in4, LOW);
    }  
    delay(50);
    }
 
    ->Arduino IDE Software necesssary for uploading the code to arduino
