---
layout: post
title: Raspberry Pico Motor Controller
---
*****
This project form part of the section of myself projects that I have in mind.  
In this post I'm going to explain one component that form part of a huge project that maybe or not I will upload here. 
I design a DC motor controller and I carry out. I received the new raspberry Pico few days ago and to learn how it works
and the differences between it and arduino I decided implement an idea that I keep in mind.  
To do it I have needed the following components:
- Raspberry Pico (Link to Datasheet: [Raspberry_Pico_Datasheet](https://datasheets.raspberrypi.org/pico/pico-datasheet.pdf)).
- Integrated Circuit L293D (Link to Datasheet: [L293D_Datasheet](https://www.ti.com/lit/ds/symlink/l293.pdf)).
- Green Led.
- 220 Ohms Resistance.
- Potentiometer (1K).
- A DC Motor
- Wires (It's recomendable different colours).
- A feed source, I have use two: a battery of 9V with a transformer to 5V, and a 5V feed through a usb wire connected to
the computer and splice with the board.
- A PCB board with 30x18 dots.
- A USB serial wire to connect the raspberry to the computer and run the program in it.
- Tin and a Tin solder

If you are new in the micropython world, I would recommend you install Thonny IDE to run the programs of micropython. 
I have tried to use other IDEs, like my favourite python IDE, Pycharm, but sometimes Pycharm can't find some microPython 
libraries (for example PWM) despite to install the pluggins and change preferences to work with microPython.


The following image explain how elements are disposed:  
<div class="img-contenedor">
<img src="/images/projectsImages/RaspArdu/ControladorMotor_bb.png" alt="Protonboard" title="protonboard" width="100%" style="
    display: block;
    margin-left: auto;
    margin-right: auto;
    margin-top: 10px;
    border-radius: 7px;
">
</div>

The following image explain how elements are disposed schematized:  
<div class="img-contenedor">
<img src="/images/projectsImages/RaspArdu/ControladorMotor_esquemático.png" alt="Esquematico" title="Esquematico" width="100%" style="
    display: block;
    margin-left: auto;
    margin-right: auto;
    margin-top: 10px;
    border-radius: 7px;
">
</div>  

Below we can find the main code in matlab:
````python
from machine import Pin, PWM
from time import sleep

pwmPIN=16
a_Pin=11 
b_Pin=15

def motorMove(speed,direction,speed_pwm,a_P,b_P):
  if speed > 100: 
      speed=100
  if speed < 0: 
      speed=0
  Speed = PWM(Pin(speed_pwm))
  Speed.freq(50)
  a = Pin(a_P, Pin.OUT)
  b = Pin(b_P, Pin.OUT)
  Speed.duty_u16(int(speed/100*65536))
  if direction < 0:
      a.value(0)
      b.value(1)
  if direction == 0:
      a.value(0)
      b.value(0)
  if direction > 0:
      a.value(1)
      b.value(0)
      
def led_blink():
    #We are going to blink the led to know that the program is runnning in the Rasp
    led=Pin(25, Pin.OUT)
    led.on()
    sleep(2)
    led.off()
    sleep(2)

# main program
while True:
    led_blink()
    motorMove(100,1,pwmPIN,a_Pin,b_Pin)
#bermejo4

````

The next image shows the final result: 
<div class="img-contenedor">
<img src="/images/projectsImages/RaspArdu/ImagenTodoEnsamblado.jpg" alt="ResultadoFinal" title="Resultado Final" width="100%" style="
    width: 75%;
    display: block;
    margin-left: auto;
    margin-right: auto;
    margin-top: 10px;
    border-radius: 7px;
">
</div> 