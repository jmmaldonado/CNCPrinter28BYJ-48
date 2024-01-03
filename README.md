#GRBL 28byj-48

This is a modified fork from ruizivo/GRBL-28byj-48-Servo.  This modification implements all 3-axises XYZ to a 28BYJ-48 stepper motor.

The motors (28byj-48) are connected to a controller card (Arduino UNO) that uses the chip ULN2003. This board is connected to pins A0, A1, A2, A3 for the Y-Axis(IN4->IN1), D5, D4, D3, D2 pins to the X-Axis(IN4->IN1), and 8,9,12,13 to the Z-Axis(IN4->IN1).


## 3D Printed parts for the CNC body
https://www.thingiverse.com/thing:4796222
Provides a maximum printing area of 12.7 x 12.7cm


## GRBL Settings
- $0=10          (Sets time length per step. Minimum 3usec.)
- $1=25          (Sets a short hold delay when stopping to let dynamics settle before disabling steppers. Value 255 keeps motors enabled with no delay.)
- $2=0           (Inverts the step signal. Set axis bit to invert (00000ZYX).)
- $3=0           (Inverts the direction signal. Set axis bit to invert (00000ZYX).)
- $4=0           (Inverts the stepper driver enable pin signal.)
- $5=0           (Inverts the all of the limit input pins.)
- $6=0           (Inverts the probe input pin signal.)
- $10=2          (Alters data included in status reports.)
- $11=0.010      (Sets how fast Grbl travels through consecutive motions. Lower value slows it down.)
- $12=0.002      (Sets the G2 and G3 arc tracing accuracy based on radial error. Beware: A very small value may effect performance.)
- $13=0          (Enables inch units when returning any position and rate value that is not a settings value.)
- $20=0          (Enables soft limits checks within machine travel and sets alarm when exceeded. Requires homing.)
- $21=0          (Enables hard limits. Immediately halts motion and throws an alarm when switch is triggered.)
- $22=0          (Enables homing cycle. Requires limit switches on all axes.)
- $23=0          (Homing searches for a switch in the positive direction. Set axis bit (00000ZYX) to search in negative direction.)
- $24=25.000     (Feed rate to slowly engage limit switch to determine its location accurately.)
- $25=300.000    (Seek rate to quickly find the limit switch before the slower locating phase.)
- $26=250        (Sets a short delay between phases of homing cycle to let a switch debounce.)
- $27=1.000      (Retract distance after triggering switch to disengage it. Homing will fail if switch isn't cleared.)
- $30=1000       (Maximum spindle speed. Sets PWM to 100% duty cycle.)
- $31=0          (Minimum spindle speed. Sets PWM to 0.4% or lowest duty cycle.)
- $32=0          (Enables laser mode. Consecutive G1/2/3 commands will not halt when spindle speed is changed.)
- $100=80.000    (X-axis travel resolution in steps per millimeter.)
- $101=80.000    (Y-axis travel resolution in steps per millimeter.)
- $102=50.000    (Z-axis travel resolution in steps per millimeter.)
- $110=300.000   (X-axis maximum rate. Used as G0 rapid rate.)
- $111=300.000   (Y-axis maximum rate. Used as G0 rapid rate.)
- $112=300.000   (Z-axis maximum rate. Used as G0 rapid rate.)
- $120=10.000    (X-axis acceleration. Used for motion planning to not exceed motor torque and lose steps.)
- $121=10.000    (Y-axis acceleration. Used for motion planning to not exceed motor torque and lose steps.)
- $122=10.000    (Z-axis acceleration. Used for motion planning to not exceed motor torque and lose steps.)
- $130=120.000   (Maximum X-axis travel distance from homing switch. Determines valid machine space for soft-limits and homing search distances.)
- $131=120.000   (Maximum Y-axis travel distance from homing switch. Determines valid machine space for soft-limits and homing search distances.)
- $132=200.000   (Maximum Z-axis travel distance from homing switch. Determines valid machine space for soft-limits and homing search distances.)

#GRBL 28byj-48 + Servo Motor

This GRBL uses an ugly hack to control two motors unipolar steps as 28byj-48 and also supports a servo motor on pin 11

The motors (28byj-48) are connected to a controller card that uses the chip ULN2003. This board is connected to pins A0, A1, A2, A3 for the Y axis and 2,3,4,5 digital pins to the axis X. The servomotor connected to pin 11 h.

Credits to robottini who did support the servo motor ... link to git https://github.com/robottini/grbl-servo

I tested the code very well with 328p (Arduino Uno, Duemilanove etv), not with 2560 (Arduino Mega) because I did not do the alterations in the file cpu_map_atmega2560.h



