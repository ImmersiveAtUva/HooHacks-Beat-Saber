# Beat Saber Unity Tutorial

Welcome to HooHacks 2019!
We are Immersive @ UVA, and this is a tutorial on how to create Beat Saber in VR with unity. This tutorial is based on the Youtuber Valem's video where he created this game in 10 minutes as an online challenge. His original video is here: https://www.youtube.com/watch?v=gh4k0Q1Pl7E

Here is a short video if you are not familiar with beat saber: https://www.youtube.com/watch?v=vL39Sg2AqWg 
Today we are going to be walking you through how to make your very own Beat Saber game. We will be using the Oculus Integration kit, which means this tutorial will work for the HTC Vive and the Oculus Rift, and will also work for mobile VR development with some modifications on the controller setup.

The song that we will be using can be downloaded here: click.dj/thefatrat/thefatrat-unity-1
You can also feel free to pick your own song!

If you would like to be put in the raffle for the VR equipment, enter your information here:
https://docs.google.com/spreadsheets/d/1SNAjRNmHE3fxmBmc_KoKs1sZJMbbR6DuRPkwdcASTfw/edit?usp=sharing

We will be distributing 2 HTC Vive backpacks (with laptop), 5 Oculus Gos, and access to three VR Stations at Clemons library from 6pm to 12am tonight. (2 Vives and 1 Oculus Rift)
The Vive backpacks must be returned to us at 10am tommorow so that VR teams can perform their demos.

### Download Unity Hub

* Download Unity version 2018.3.6f1

### Create New Project

* 3D Project

### Create Materials

* Create Folder call Materials in Assets folder, and switch to it
* Right click in folder→Create→Material
* In the inspector, select Particles→Standard Surface for its Shader
* Click the HDR box for Albedo, and select black
* Select two-sided
* Copy this material by clicking CTRL+D
* Create a blue and red material as well
    * Give the blue and red materials intensity of 1
    * Select emission, and then give them the same colors as Albedo

### Setup VR Camera Rig

* Delete Main Camera and Directional Light from the Scene
* From Asset Store, get the Oculus Integration, and import it into the project
* From Assets→Oculus→VR→Prefabs, drag the OVRCameraRig into the scene

### Create World

* Create cube, of scale 5,1,5, and drag it below the camera rig, and move the black material onto it
* Duplicate the cube, set scale to 5,1,12, and drag it in front of the first cube (in front of camera)
* Duplicate it again, and set scale to 30, 30, 100

### Add Accents Inside Box

* Duplicate a cube, set scale to 0.2, 0.2, 100, and drag it to the inside of the wall
* Drag the blue material onto this cube
* Duplicate the cube, and drag the new one up
* Duplicate both cubes and drag it to the other side of the box
* Drag the red material to these two cubes

### Add Saber to Hands

* In OVRCameraRig→TrackingSpace→LeftHandAncor, add a cube of scale 0.05, 0.05, 1
* Set the Z position to 0.424
* Duplicate this cube, and add it to the RightHandAncor as well

### Create Beat Saber Cube

* Create cube with scale 0.4, 0.4, 0.4
* Duplicate this cube, and then make a smaller cube which protrudes slightly from the top of the original cube
* Drag this smaller cube into the first one from the Hierarchy tab to join them
* Drag the red material onto the smaller of these cubes
* Duplicate the parent cube. Rename one "Red Cube" and the other "Blue Cube"
* Select both Cubes from the scene at the same time and select "Add Component"→"New Script", and name it "Movement"
* Edit this script so that it is the same as Movement.cs (Provided)
* Create a blue layer for the blue cube and a red layer for the red cube, apply to all children
* Drag these cubes into the Asset Folder

### Create Spawner

* In the Scene, right click and select "Create Empty", and rename this to Spawner
* Move this to the end of the other platform
* Add a new script, and call it "Spawner", edit this script so that the code is the same as Spawner.cs (Provided)
* Drag the two cubes from the Assets folder into the Cubes array in the Spawner script
* In the Spawner, create 4 empty objects, and set their positions so that they form a  square
    * X,Y 0.4, 0
    * X,Y -0.4, 0
    * X,Y 0, 0.4
    * X,Y -0.4, 0.4
* Drag these 4 objects into the list for Points array in the Spawner script
* Enter 60/105 for the Beat, or change this according the the beat of your song

### Add Saber Script

* Select both LeftHandAnchor and RightHandAnchor from OVRCameraRig→TrackingSpace and add a new script named Saber, and edit this script so that it is the same as Spawner.cs (Provided)
* Drag the Blue material to the cube in the RighHandAnchor
* Drag the Red material to the cube in the LeftHandAnchor
* Select the blue layer for the LeftHandAnchor within the script, and the red layer for the RightHandAnchor

### Add Music

* Download your song, and add it to the assets folder
* Enable auto play by clicking the song and then clicking the auto play button (A little speaker icon)

### Add Post Processing [OPTIONAL]
* From Asset store, download and import the Post Processing Stack from Unity Technologies
* Add the PostProcessingBehaviour Script to OVRCameraRig→TrackingSpace→CenterEyeAnchor
* Right click in Assets and select Create→Post-Processing Profile
* Drag this profile into the CenterEyeAnchor script
* Add bloom of intensity 1.7 to the post-processing profile
* Add ColorGrading, Select the Filmic Tonemapper, and set Post Exposure to 2
* From Window→Rendering→LightSettings, add a blue fog