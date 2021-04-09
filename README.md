# Reaction-game

import RPi.GPIO as GPIO
import time
import random

GPIO.setmode(GPIO.BCM)

GPIO.setup(13, GPIO.OUT)
GPIO.setup(20, GPIO.IN)
GPIO.setup(21, GPIO.IN)

wait = (5)
time.sleep(wait)

GPIO.output(13,GPIO.HIGH)
timestart = time.time()

winner = "no"

while winner == "no":
    if GPIO.input(20) == True:
        winner = "Emma"
    
    if GPIO.input(21) == True:
        winner = "Cameron"
        
time_total = time.time() - timestart

time_total = "%.3f" % time_total
    
        
print(winner + " wins!")

print("your reaction time was " + time_total + " seconds")

GPIO.output(13, GPIO.LOW)



GPIO.cleanup()

