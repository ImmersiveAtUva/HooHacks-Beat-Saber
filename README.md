# Beat Saber Unity Tutorial

### Download Unity Hub

* Download version 2018.3.6f1

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
* Change the beats if you like by taking 60 and dividing it by the BMP of your song. Multiply by 2 to get faster block generation

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