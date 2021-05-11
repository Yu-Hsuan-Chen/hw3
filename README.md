# hw3

(1) How I build my program
 - I use 5 threads to control the whole program:
    + mqtt_thread(osPriorityAboveNormal)
    + mqtt_send_thread(osPriorityHigh)
    + gesture_thread(osPriorityNormal)
    + detect_thread(osPriorityNormal)
    + uLCD_thread(osPriorityNormal)
 - Use 3 LEDs to show the mode and initialization 
    + LED1 : gestureUI mode (mode 1)
    + LED2 : tilt angle detection mode (mode 2)
    + LED3 : show the mbed board on table is initialized. (At the beginning in mode 2)
 - The flow in mode 1 and mode 2:
    + Python -> RPC function -> Thread function -> Some subfunctions
(2) how to setup and run my program 
     1. git clone my repo
     2. git clone some libraries likes mbed_rpc ...
     3. compile and open the screen 
     4. run the wifi_mqtt/mqtt_client.py after see the mqtt setup sucessful.
     ![ ](https://imgur.com/fD3Wafj.jpg)
     5. Then you will see the Screen enter Mode 1, and you can lift up the mbed board to select the threshold angle.
     6.After pressing the USER_BUTTON, you will enter the mode 2.
     7.At the beginnig, you need to place the mbed board on table to initialize (To make sure the direction align with gravity)
     8. Tile your board to see the tilt angle.
     ![](https://imgur.com/o92jhen.jpg)
     9. If the tilt angle is lager than the threshold angle, then you can see the event showed on PC/python.
     ![](https://imgur.com/YlDXp4P.jpg)
     10. After PC/python receive ten events, the mode 2 will be closed.
     11. Call the "closeAll" RPC function to close all threads.
