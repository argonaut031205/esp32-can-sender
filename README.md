# esp32-can-sender
## updateencoder() ->
![Screenshot 2024-07-19 215820](https://github.com/user-attachments/assets/371ba128-f90a-43e2-9eb3-ef61f2b87489)
the interrupt monitors the A channel of encoder and recors value whenever its value transitions to HIGH. If both are HIGH at that time then it add in CCW direction.if B is LOW during that time, then it adds in CW direction.
## movearmcomands() ->
in the rosmessageCb() function we recieve the pwm values for each of the 5 motors and process it in this function and then send it to CAN bus using pushtoCAN().
* if you take any value in the arm_buf list, depending on the sign of the value, the direction if motor is decided(making it HIGH or LOW) and speed is the absolute value.
* and for the first 2 motors LED's are connected which glows based on the direction of those 2 motors.
* then the pwm and direction values of other 3 motors are sent to the can transceiver.
## pinmodeinit() ->
here all pins are being defined.
* for 1st 2 motors to identify their direction an LED is connected which glows based on their direction (arm_dir[0],arm_dir[1]).
* the speed of these 1st 2 motors are controlled using pwm signals which come from pins: pwm[0],pwm[1] ; which are setup using ledC with specific freq and resolution which controls duty cycle.
## pushtocan() ->
This function is obvious as it gets data from the movearmcommands() using buffsendtocan variable, but here the last to indices of the array is always kept as 0.
