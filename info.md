#About the project:
What I wanted to achieve is a simple security system which I can turn on and off from my phone, my laptop and I can authenticate myself so nobody can shut down the system while I am away from home.
If the system detects an intruder than it can take photos and notify me. And a really important thing: it not just takes photos, but it uploads the photos to a server so if the intruder would notice the camera and destroys the Pi than I still would have his/her face.

#- Modules I use:

Flask – As I said I wanted something simple where I can login than start or stop the system. I think the best way to do this is a html site, and Flask is a simple choice (on this level…)
Firebase – I just love it….Super easy authentication and I have a storage where I can upload my photos
OpenCV – For the computer vision tasks. We detect the motion with this library
So these are the main libraries I use for this cool project

#Computer Vision
This is not magic! We can say that the theory behind it is pretty simple.

Motion detection is what I use to identify if there is somebody in my home or not. I know that there are curtains which can move, and maybe pets, but a pet is (almost) always smaller than a human so we can create an algorithm which can only detect humans and big changes on the webcam feed frames. An interesting approach would be with Deep Learning but because I did not have a big dataset I can rely only on the Classic Image Processing methods.

When the detection starts, it stores the first image that the camera captures. Than I convert it to a grayscale picture, apply Histogram Equalization and Gaussian Blur. Than the camera always captures new images and I create a difference image between the current image and the stored one. Of course I apply the same gaussian blur and grayscale conversion to the new images too.
