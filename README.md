import time
import os
import pyautogui
import jetson.inference
import jetson.utils
print("it's on!")
time.sleep(10)
count = 0
for i in range(5):
     pyautogui.press("i")
     time.sleep(1)
     filename = "/home/e104/my_photo-1.jpg"
     img = jetson.utils.loadImage(filename)
     network = "googlenet"
     net = jetson.inference.imageNet(network)
     class_idx, confidence = net.Classify(img)
     class_desc = net.GetClassDesc(class_idx)
     gave = "image is recognized as '{:s}' (class #{:d}) with {:f}% confidence">
     if "cat" in gave.lower():
         print("That's a cat!! A cat is present!")
     else:
         print("No cat present!")
     time.sleep(2)
     count += 1
     print(count)
     os.remove("/home/e104/my_photo-1.jpg")

