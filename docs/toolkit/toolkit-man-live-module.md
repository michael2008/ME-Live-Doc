## Live! module


### Overview

LiveController provides the following functions:

* Communicate with the  [**DataMesh Live Agent**][DataMesh_Live_Agent]  of the HoloLens on the Rig to synchronize spacial anchors in real-time.
* Use of keyboards to adjust the position and angle of the Anchor, if the automatical synchronization failed.
* Control the upload and download WorldAnchor from Live Agent via the Workstation.
* Compose the images captured by the camera on the Rig with virtual scenes, and cast it out.
* Record the composed video stream as MPEG-4 file with a maximum resolution of 4K.

Please follow the instructions below to create a demo app.



### How to integrate Live! function to a project

It's very easy to integrate Live! function to any project which made by METookit. 

* Open any project which made by METoolkit.
* Open **Player Settings**, and open **Other Settings** panel.
* Add a compilation parameter "**ME_LIVE_ACTIVE;CROSS_PLATFORM_INPUT**" into Scripting Define Symbols field.

<p align="center">

<img src="https://user-images.githubusercontent.com/26785911/35388942-c575e7fe-0210-11e8-9420-311e371e4cd3.png" width="400">

</p>

* Now your project will became a Live! project.




### Config for Live!

Live! will load a config file when program start. You can create or modify this file.

- Find **Asset/StreamingAssets** folder, and create a file named **MEConfigLive.ini**
- The content of this configuration file like this:

```
###############################################
# config for Live
###############################################

#### Live Workstation Server Port (For SpectatorView) ####
Live_Port = 8099
Live_Port_UDP = 8098
Use_UDP = TRUE

#### HologramCapture Config
Out_Put_Path = C:/HologramCapture/
```

> Usually, you don't need to change **Live Port**. 
>
> If you don't want use UDP mode, you can set **Use_UDP=FALSE**, so program will use TCP to transfer location data.
>
> You can set a path to save Span and Record file. Ensure the program has write permissions to this folder.
>
> **Important: ** If your app is **NOT** running on _Unity Editor_ or _PC Standalone_ (e.g. HoloLens, iOS, Android),  app will load config file at **PersistentDataPath**, not from **StreamingAssets**. For more information, please refer to [Utility: Config Files][Utility_Config_Files]



### Build Live! program

Build a **PC Standalone** program, and select Architecture to **x86_64**.

<p align="center">

<img src="https://user-images.githubusercontent.com/13318047/35611287-89530d90-069f-11e8-9c90-4de7ce8d6677.png" width="500">

</p>

It will create a **exe** file and some folders. You can deploy them to your Workstation.



### Start to use

- Start [**DataMesh Live Agent**][DataMesh_Live_Agent] App on the HoloLens of the Rig.
- Start "**.exe**" program on the Workstation.
- There will be some buttons on the screen:

<p align="center">
<img src="https://user-images.githubusercontent.com/26785911/35389668-8f0d8d72-0213-11e8-8935-f16da3a1915b.png" width="800">
</p>

There will be four functional areas:

- The top left is the panel's functional area, which provides application configuration, anchor adjustment and HoloLens connectivity.
- The middle is the media operation area, taking pictures and video recording, and you can open the automatic upload function at the same time.
- The upper right corner is a preview window, you can preview the mixed reality screen.
- The lower left corner is the information window, it will print the program running information.




### Functional area

<p align="center">
<img src="https://user-images.githubusercontent.com/26785911/35390701-4bc255f8-0217-11e8-83a2-b2711dbc4fd1.png" width="100">
</p>

Here are three buttons:

- Settings panel
- Move anchor
- Connect with HoloLens




#### Settings panel

<p align="center">
<img src="https://user-images.githubusercontent.com/26785911/35390861-c682fc3e-0217-11e8-95c2-f08c25d684bc.png" width="400">
</p>

Click the Settings panel button to open the Settings panel:

- The first area is the Holographic settings area, you can adjust the content as follows:

  - Video delay
  - Software anti-shake time
  - Mixed reality transparency
  - Black Filter
  - Apply the overall volume size

- The second area is the advanced configuration content:

  - Set the default photo, video save address (click address to change)
  - Open the program's configuration file path, modify the configuration file
  - Open the program log file
  - Clear the anchor information and camera information saved by the program (that is, reset camera and space anchor data)

- The third area is the Social Settings area, you can set the content as follows

  - Album used
  - Recording time limit (15s, 30s, 60s, unlimited, etc.)

- The fourth area is the HoloLens advanced settings, they will change to a clickable state  when connected to the HoloLens , you can download the anchor spatial data on the HoloLens

  - If you want to synchronize with another HoloLens, you need to:

    - First click "Stop Follow" to stop synchronization.
    - Then Click "Download Anchor".
    - Upon success, the position of the Holographics would change and the synchronization would start automatically.
    - If an alert of anchor not positioned appears, it means the spacial information scanned by the two HoloLens is different. You need to move the HoloLens to do a rescan until the alert disappears.
  - You can download the spatial mapping information (Meshes) from HoloLens, so you can simulate spatial mapping on your workstation.

    - Click button Download Spatial, and when download finished, you can see tips on right-top
    - Spatial mapping meshes will only appear in Anchor Move mode. Start to move anchor, click an anchor, and select Gaze button in the middle, so you can see the meshes


<p align="center">
<img src="https://user-images.githubusercontent.com/7381020/28115007-c433e9fc-6735-11e7-8ed1-8db0bcb75843.png" width="400">
</p>



#### Move anchor

<p align="center">
<img src="https://user-images.githubusercontent.com/26785911/35391404-91b1fb2a-0219-11e8-83b0-6a4a7f96a213.png" width="800">
</p>

Click the button to open the anchor adjustment panel, click the anchor you want to move while the virtual object change to the anchor adjustment status:

<p align="center">
<img src="https://user-images.githubusercontent.com/26785911/35391560-07852020-021a-11e8-895b-7245020a00db.png" width="400">
</p>

- When the virtual object can not be seen, an arrow appears to direct the position of the virtual object
- Use the six buttons below "Move" or the corresponding location of the keyboard button to move the virtual object
- Use the six buttons below "Rotate" or the corresponding location of the keyboard button to rotate the virtual object
- You can reset the anchor to the pre-adjustment state by click "Anchor Reset" button
- You can reset the main camera to the pre-adjustment state by click "Camera Reset" button
- You can adjust the speed of movement and rotation by using  speed slider




#### Connect with HoloLens

<p align="center">
<img src="https://user-images.githubusercontent.com/26785911/35391826-c79a26d0-021a-11e8-9eae-2d111aae13ee.png" width="300">
</p>

There are three states for this button:

- Connecting
- Connected
- Disconnected



When doing the first follow-up:

- The application will first establish a connection with HoloLens (button status becomes connecting)
- Start the synchronization of the location information after connected (button status changes to connected)
- You can then click the button to disconnect the follow state (do not disconnect with the HoloLens)



### Media operation area

<p align="center">
<img src="https://user-images.githubusercontent.com/26785911/35392487-0660969a-021d-11e8-901b-d2f205dd6e38.png" width="300">
</p>



There are three buttons in the media operation area:

- Automatic upload switch button
- Shooting button
- Recording button




#### Shooting button

Click the shooting button will take a picture of the current mixed reality scene and saved in the media resource path

PS:

- When auto upload is on, photos will be automatically uploaded to "Social" server
- When the recording status is activated, this button can not be clicked



#### Recording button

Click the recording button will start recording for the current mixed reality scene and saved in the media resource path

PS:

- When auto upload is on, photos will be automatically uploaded to "Social" server
- The button has two states, start and stop



### Preview window

<p align="center">
<img src="https://user-images.githubusercontent.com/26785911/35392633-7e419f92-021d-11e8-9727-22e85ce1ff8c.png" width="400">
</p>



The preview window will display the mixed reality scene in the current state. Click the button in the upper right corner to switch the size of the preview window, and then switch to:

- Default state (small window mode)
- Full screen mode
- Hidden mode




#### Full screen mode

<p align="center">
<img src="https://user-images.githubusercontent.com/26785911/35392674-98a83e18-021d-11e8-8485-47c1fea0b923.png" width="800">
</p>



- When the preview window is in full screen mode, the upper left corner of the ribbon and the lower left corner of the information areas will be hidden
- At this time, the panel only displays the media operation area and the preview window size switching button in the upper right corner



### Information window

<p align="center">
<img src="https://user-images.githubusercontent.com/26785911/35393391-cbb86ae2-021f-11e8-8116-5489a9b189f5.png" width="300">
</p>

This window will show the status of the program running tips, you can close it in the settings panel



[Configure_your_project]: toolkit-man-configure-your-project.md
[Integrated_with_your_project]: toolkit-man-integrated-METoolkit.md
[Utility_Config_Files]: toolkit-man-utility-config-file.md
[DataMesh_Live_Agent]: ../user-guide.md#datamesh-live-agent
