import numpy as np
import cv2
import imutils
import datetime

# Load Haar Cascade XML file
gun_cascade = cv2.CascadeClassifier('cascade.xml')
if gun_cascade.empty():
    print("Error loading cascade.xml")
    exit()

# Start webcam
camera = cv2.VideoCapture(0)

firstFrame = None
gun_exist = False

while True:
    ret, frame = camera.read()
    if not ret:
        break

    frame = imutils.resize(frame, width=500)
    gray = cv2.cvtColor(frame, cv2.COLOR_BGR2GRAY)

    # Detect gun in the frame
    guns = gun_cascade.detectMultiScale(gray, 1.3, 5, minSize=(100, 100))

    if len(guns) > 0:
        gun_exist = True

    for (x, y, w, h) in guns:
        cv2.rectangle(frame, (x, y), (x + w, y + h), (255, 0, 0), 2)
        roi_gray = gray[y:y + h, x:x + w]
        roi_color = frame[y:y + h, x:x + w]

    if firstFrame is None:
        firstFrame = gray
        continue

    # Show the frame
    cv2.imshow("Security Feed", frame)
    key = cv2.waitKey(1) & 0xFF

    if key == ord('q'):
        break

# Final message
if gun_exist:
    print("Gun Is Detected")
else:
    print("Gun is Not Detected")

camera.release()
cv2.destroyAllWindows()
