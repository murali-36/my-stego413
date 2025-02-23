Project Overview:

Conceal and retrieve secret messages within images using Python’s OpenCV library.
Uses the Least Significant Bit (LSB) technique to hide text within the image’s pixels, maintaining visual integrity.

Features:

Message Embedding:
Hide secret messages within image pixels.
Password Protection:
Secure the hidden message with a passcode.
Message Extraction:
Retrieve the hidden message by providing the correct passcode.

Prerequisites:
Python Version: 3.13.2 or higher
Required Libraries:
OpenCV (opencv-python)

Setup Instructions:
Clone the Repository:
git clone " https://github.com/murali-36/my-stego413.git "

Install Dependencies:
pip install opencv-python 

Usage Instructions:
Prepare Your Image:
Place your image ("image413.png") in the same directory as the script.
Run the Script:
Encode the Message:

Enter the secret message and a passcode.
The image with the hidden message is saved as encryptedImage.jpg.

Decode the Message:

Enter the correct passcode to retrieve and display the hidden message.




code:

import cv2

import os

import string


img = cv2.imread("image413.png") # Replace with the correct image path#image

msg = input("Enter secret message:")

password = input("Enter a passcode:")

d = {}

c = {}

for i in range(255):

    d[chr(i)] = i
    
    c[i] = chr(i)

m = 0

n = 0

z = 0

for i in range(len(msg)):

    img[n, m, z] = d[msg[i]]
    
    n = n + 1
    
    m = m + 1
    
    z = (z + 1) % 3

cv2.imwrite("encryptedImage.jpg", img)

os.system("start encryptedImage.jpg")  # Use 'start' to open the image on Windows

message = ""

n = 0

m = 0

z = 0


pas = input("Enter passcode for Decryption")

if password == pas:

    for i in range(len(msg)):
    
        message = message + c[img[n, m, z]]
        
        n = n + 1
        
        m = m + 1
        
        z = (z + 1) % 3
        
    print("Decryption message:", message)
    
else:

    print("YOU ARE NOT auth")

