# Facedetection_from_image
we are detecting face in an image using opencv 

img = cv2.imread("C:\\Users\\Siddhant Sharma\\Desktop\\abc.png",1)

This code line takes the path where the image is stored as the input using imread() method 
and here 1 represent that the image is in RGB. 
If we write 0 in place of 1 then it means that the image is in black and white format.
Python stores the image as numpy array/matrix of number.


face_cascade = cv2.CascadeClassifier('C:\\Users\\Siddhant Sharma\\Downloads\\opencv\\build\\etc\\haarcascades\\haarcascade_frontalface_default.xml')

In this line we are creating face_cascade object of CascadeClassifier method.
It contains the path of the xml file of haarcascade_frontalface_default.
A Haar Cascade is basically a classifier which is used to detect particular objects from the source.
The haarcascade_frontalface_default.xml is a haar cascade designed by OpenCV to detect the frontal face

gray_img = cv2.cvtColor(img,cv2.COLOR_BGR2GRAY)

cvtColor is an OpenCV function to convert images to different color spaces
This line convert image from RGB to GRAY scale

faces = face_cascade.detectMultiScale(gray_img,1.06,5)

#detectMultiScale(image, scaleFactor, minNeighbors):
This line uses face_cascade object for detectMultiScale()method which is a general function to detect objects, in this case, it'll detect faces since we called in the face cascade. 
If it finds a face, it returns a list of positions of said face in the form “Rect(x,y,w,h).”, if not, then returns “None”.
image:- the grayscale image
ScaleFactor:- This function compensates a false perception in size that occurs when one face appears to be bigger than the other simply because it is closer to the camera.
minNeighbors:-This is a detection algorithm that uses a moving window to detect objects, 
it does so by defining how many objects are found near the current one before it can declare the face found.

for x,y,w,h in faces:

    img=cv2.rectangle(img,(x,y),(x+w,y+h),(0,255,0),3)

loop over the list of faces (rectangles) it returned and drew those rectangles using yet another built-in OpenCV rectangle function on our original colored image to see if it found the right faces:

resized = cv2.resize(img,(int(img.shape[1]),int(img.shape[0])))
image is resized

cv2.imshow("gray",resized)

This is a cv2 function used to display the image.
It also takes two arguments: the first one is the name of the window that will pop-up to show the picture and the second one is the image you want to display.

cv2.waitKey(0)

This is a keyboard binding function, which takes one argument: (x) time in milliseconds.
The function delays for (x) milliseconds any keyboard event.
If (0) is pressed, it waits indefinitely for a keystroke, if any other key is pressed the program continues.

cv2.destroyAllWindows()

This simply destroys all the windows we created using cv2.imshow(window_name, image)
