# esp32-can-sender
## updateencoder() ->
<img width="262" alt="image" src="https://github.com/user-attachments/assets/6487d651-ca56-44f6-847e-a00f9a07a727">
the interrupt monitors the A channel of encoder and recors value whenever its value transitions to HIGH. If both are HIGH at that time then it add in CCW direction.if B is LOW during that time, then it adds in CW direction.
## movearmcomands() ->
in the rosmessageCb() function we recieve the pwm values for each of the 5 motors and process it in this function and then send it to CAN bus using pushtoCAN().
if you take any value in the arm_buf list, depending on the sign of the value, the direction if motor is decided and speed is the absolute value.
