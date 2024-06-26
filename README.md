# Blender-Motion-Capture-Addon
A Blender Addon that uses Mediapipe in Blender to capture a person's movements, and apply them to a character in real time.

Here is a demo of what the addon can do:

https://www.loom.com/share/b89c79e10396484681948b2ccf612ebf

The initial code was taken from the "BlendyPose" python script by ZonkSoft, and adapted to apply the motion onto a character in Blender. Mediapipe is a pose-estimation library authored by Google, that estimates the pose of a person in an image (using open-cv in Python), and predicts the 3d coordinates of each landmark. In Blender, the addon applies the location of each landmark onto plain axes in the 3d space, and adds bone constraints to some of the bones in the Blender Rigify Addon (only with the rig, not the armature), so that the bone follows the axes in the space.

The drivers (plain axes) are the objects that move the bones, meaning that the keyframes are not actually applied to the rig. This is important to know when using this addon for more advanced scenes in Blender. In order to move the rig around after the drivers are connected (after "Transfer Animation" is clicked), the "Select System" button must be pressed, so that the drivers move with the rig, and the motion is properly conserved. However, if you are going to re-capture the motion after moving the rig to a different location/rotation, this button does not need to be pressed.

The motion capture in the addon will not run if there is no armature chosen in the "Select an Armature" dropdown. If it is not chosen, Blender will present an error, and you must then choose an armature before proceeding.

Another thing to note is to not change the name/designation of the drivers, as the addon relies on that information.

If an error appears, stating that mediapipe isn't defined, try installing the addon on elevated privelages for Blender.

And for the final part of this addon, the smooth animation button smooths the animation to make it look more realistic. Above this button is a section where you can decide the degree to how much you want the animation smoothed. For example, setting this value to "10" would smooth the animation the most.

In future versions, this addon will hopefully run more on deep learning algorithms, which will allow things like multi-person motion capture, as well as more accurate motion capture in general.



# How To Install:

First, download the zip file from github, and then extract the python script titled "Blender Mocap (Newest Version)" from the folder. Then, open Blender **WITH** **ADMINISTRATOR** **PRIVILEGES**.

Click on the "Scripting" tab:

![image](https://github.com/Daniel-W-Blender-Python/Blender-Motion-Capture-Addon/assets/142774885/ee35af04-7e91-44cd-9b60-7e21831b6e30)

Click "Open", and navigate to the "Install Dependencies.py" script from the zip file:

![image](https://github.com/Daniel-W-Blender-Python/Blender-Motion-Capture-Addon/assets/142774885/7356a715-0330-4853-9d1d-e65142ae7566)

Then, click the "Run Script" button:

![image](https://github.com/Daniel-W-Blender-Python/Blender-Motion-Capture-Addon/assets/142774885/2fbd2085-5228-4b7f-824b-3b57346ffeb4)

Click (Edit >> Preferences >> Add-ons >> Install >> Blender Mocap.py)

![image](https://github.com/Daniel-W-Blender-Python/Blender-Motion-Capture-Addon/assets/142774885/402f7c6c-0338-415b-ad79-09208cda66fa)

Double-Click "Blender Mocap V3.py":

![image](https://github.com/Daniel-W-Blender-Python/Blender-Motion-Capture-Addon/assets/142774885/d5083034-4d73-4c1c-9379-0bc2798ca9db)

Then select the box next to the addon:

![image](https://github.com/Daniel-W-Blender-Python/Blender-Motion-Capture-Addon/assets/142774885/2b85fb17-ac42-451c-b1b1-9f63dc69654f)

The addon should appear in the side panel:

![image](https://github.com/Daniel-W-Blender-Python/Blender-Motion-Capture-Addon/assets/142774885/2331ab57-136c-4112-aa12-fa8304c70c6f)



# How to Use:

Click "Add Rig", or import your own rig from the Rigify addon. This must be the rig though, not the actual armature.

![image](https://github.com/Daniel-W-Blender-Python/Blender-Motion-Capture-Addon/assets/142774885/5272a9e2-7486-44bf-bc85-1a613c4f6a13)

Then, you can delete the armature beneath the rig. To show more parts of the rig, click "data", and check all of the layers.

![image](https://github.com/Daniel-W-Blender-Python/Blender-Motion-Capture-Addon/assets/142774885/176ac437-ea9d-45bd-83d1-43d29944b649)

You have to input the rig you want to track the motion to in the "Armature" box.

![image](https://github.com/Daniel-W-Blender-Python/Blender-Motion-Capture-Addon/assets/142774885/2e4ca3ba-2b93-4a6a-9b56-4680209b3643)

Then, you can either capture motion from a webcam, or you could import a file. This may take a while the first time you click it. Then hit "Transfer Animation" to transfer the animation to your rig.

![image](https://github.com/Daniel-W-Blender-Python/Blender-Motion-Capture-Addon/assets/142774885/060a6084-ab0f-4b1b-9baf-acdf279f3516)

To smooth the animation, set the degree to which you want it smoothed in the "Smooth Value" box, then click the "Smooth Animation" button. To save the animation to your rig, click "Save Animation". This ensures that if you want to track motion for a different character in your scene, the motion you tracked for your original character will stay with that rig.

The "Select System" button, selects the rig and the drivers, so that you can move the rig around the scene without your motion being changed.

In Version 3, there is a new Rokoko Retargeting feature. Rokoko is a popular free motion capture resource, but it uses a different rig than the standard one from Rigify. In the addon, you would first import the Rokoko rig (with animation) as an FBX, making sure to click "Automatic Bone Orientation" before importing:

![image](https://github.com/Daniel-W-Blender-Python/Blender-Motion-Capture-Addon/assets/142774885/2e576c2b-e1bf-4bd5-a919-637ba0cbbc0f)

This orients the bones in the standard format, rather than rotating them all vertically in the 3d space. Then, select "Root" as the object under "Source" in the addon. After that, select the Rigify rig you are using as the object under "Target".

![image](https://github.com/Daniel-W-Blender-Python/Blender-Motion-Capture-Addon/assets/142774885/5c8463e5-6b90-4d07-bbc0-8e0d4a338234)

Then, to link the rig to the Rokoko armature's motion, click "Link Armatures". This will add bone constraints to the bones on the rig, so that whatever you change to the Rokoko armature in terms of motion, it will be mimicked by the rig.

![image](https://github.com/Daniel-W-Blender-Python/Blender-Motion-Capture-Addon/assets/142774885/4cbeb298-193e-4599-a666-65aafa7fea1c)

If you want to transfer the Rokoko armature's motion to the rig, click the "Retarget Animation" button.



# TroubleShooting

If you are getting an error when adding a rig, try first enabling the "Rigify" addon.

![image](https://github.com/Daniel-W-Blender-Python/Blender-Motion-Capture-Addon/assets/142774885/749dbf6a-9db2-44e8-8503-23d18329d34a)

If you are getting an error stating that there is no module named cv2, or that there is no module named mediapipe, try opening the scripting tab in blender, adding a new python script, and running this code:

import subprocess

import sys

import os

python_exe = os.path.join(sys.prefix, 'bin', 'python.exe')

py_lib = os.path.join(sys.prefix, 'lib', 'site-packages','pip')

subprocess.check_call([sys.executable, "-m", "ensurepip"])

subprocess.check_call([sys.executable, "-m", "pip", "install", "--upgrade", "pip"])

subprocess.check_call([sys.executable, "-m", "pip", "install", "mediapipe"])

subprocess.check_call([sys.executable, "-m", "pip", "install", "opencv-python"])

![image](https://github.com/Daniel-W-Blender-Python/Blender-Motion-Capture-Addon/assets/142774885/2fbd2085-5228-4b7f-824b-3b57346ffeb4)

This will download the OpenCV and Mediapipe libraries, which are required to run this addon.

If your computer is crashing while checking the addon box, try importing and running both scripts (Blender Mocap V (Latest Version) and the code above), then checking the box:

![image](https://github.com/Daniel-W-Blender-Python/Blender-Motion-Capture-Addon/assets/142774885/664018bc-86be-46b1-9c04-b13cece1b2df)

If you are getting an error when clicking "Smooth Animation", make sure that the drivers aren't hidden in the scene.

If you are getting an error when clicking "Save Animation", or the button simply doesn't work, try showing all the layers of the rig. Then try saving the animation.

![image](https://github.com/Daniel-W-Blender-Python/Blender-Motion-Capture-Addon/assets/142774885/641b108a-2a4e-46a5-b95c-22ee053fee17)

If the "Smooth Animation" button still doesn't work, try selecting all of the drivers, and then clicking the button:

![image](https://github.com/Daniel-W-Blender-Python/Blender-Motion-Capture-Addon/assets/142774885/9774681f-dcc7-41b3-b4a1-7871e22a93f6)











