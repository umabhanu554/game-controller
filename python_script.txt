import subprocess   
import time
import pyautogui
import serial
subprocess.call([r'C:\Program Files (x86)\Google\Chrome\Application\chrome.exe',  
    '-new-tab', 'https://chromedino.com/'])  
								#Add google chrome application path to open
								#open Dino game 
          						
time.sleep(6)                 	                        #wait short time to open the game
print("Let the game begins")

ser = serial.Serial('COM3', 9600, timeout=.1)		#board is connected to COM3 baud rate 9600

while True:					        #loop for the game
  Serial_Data=ser.readline() 			                #read serial button state from the board
  if Serial_Data:
   buttonState = int(Serial_Data.decode('utf-8'))                #convert button value from string to int
   if buttonState== 1:				        #if button is pressed
   	print("Dino jumps")		
   	pyautogui.press('up') 		                #Send (Space) on keyboard to jump

