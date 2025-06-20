# Model-Based PID Ball Balancing System

This project implements a real-time PID control system to balance a ball at a fixed position on a tiltable platform. Developed using MATLAB Simulink for modeling and deployed on an Arduino Uno, the system demonstrates feedback control in embedded systems using sensors, actuators, and manual gain tuning.

 <p align="center">
   <img src="https://github.com/user-attachments/assets/6a10623e-d4cb-403d-ba40-79fec56f3216" alt="Model" width=60%>
 </p>
 
### Hardware Components & Software Tools 

Hardware components include Ardunio Uno for deployment, Servo Motor for platform tilting, Ultrasonic Distance Sensor for ball distance reading, Potentionmeters for Kp, Ki, Kd tuning. MATLAB Simulink for the design and simultaion, Serial Communication for data monitoring and External Model for dynamic parameter tuning.

### Simulink Ball Balancing System 

An ultrasonic sensor reads the distance of the ball, and the signal is first scaled, filtered using a median filter, and limited to valid ranges. The processed value is then compared to a reference (25 cm) to compute the error. 
 <p align="center">
   <img src="https://github.com/user-attachments/assets/ab423b1b-a043-4120-8aeb-390dc51928e6" alt="Receiver" width=65%>
 </p>
This error feeds into a PID controller, where the proportional, integral, and derivative gains are dynamically set using potentiometers connected to the Arduino's analog pins. 
The resulting control output adjusts a servo motor via Arduino pin 11 to maintain the ball at the desired central position. Display blocks are used throughout to monitor the system’s behavior in real time.

### Functionality Verification 

Various figures of the PID control response were plotted, namely the immediate distance obtained from the ultrasonic sensor readings.
By placing the scope at the ultrasonic sensor’s output after filtering, the plot showcases the motion of the ball on the track. 

 <p align="center">
   <img src="https://github.com/user-attachments/assets/9ae4ee93-b7c5-4258-a42b-f0482183707d" alt="Distance Graph" width=50%>
 </p>
 
 The oscillations in the distance graph are due to a stopping edge placed near the ultrasonic sensor, which causes the ball to bounce slightly upon contact, preventing it from hitting the sensor directly.

  <p align="center">
   <img src="https://github.com/user-attachments/assets/28a284b5-8167-4633-9da1-e99716ef82db" alt="Controller Response" width=50%>
 </p>
 
 The PID controller generates an output ranging from -90 to 90 degrees, which is used to set the position of the servo motor and adjust the platform accordingly.
