🔫 Gun Detection Using OpenCV
This is a simple Python project that detects the presence of a gun in front of a webcam using a pre-trained Haar Cascade classifier.

📷 How It Works
Uses OpenCV to access your webcam and process video frames in real-time.
Loads a Haar Cascade XML file (cascade.xml) trained to detect guns.
Detects and highlights any gun-like objects in the video feed.
Prints a message to the console if a gun is detected.

🛠️ Requirements
* Python 3.x
* OpenCV
* NumPy
* imutils

Install dependencies using pip:

pip install opencv-python numpy imutils
▶️ How to Run
1)Make sure you have the cascade.xml file in the same directory.

2)Run the script:
python gun_detection.py
3)A webcam window will open showing the video feed.
4)Press q to quit the feed.

5)The terminal will display whether a gun was detected.

📁 Files
$ gun_detection.py – Main Python script.

$ cascade.xml – Haar Cascade file used for gun detection.

