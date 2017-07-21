## Live! module


### Overview

LiveController provides the following functions:

* Communicate with the [**SpectatorView**](https://github.com/Microsoft/HoloLensCompanionKit/tree/master/SpectatorView "SpectatorView GitHub") of the HoloLens on the Rig to synchronize spacial anchors in real-time.
* Use of keyboards to adjust the position and angle of the Anchor, if the automatical synchronization failed.
* Control the upload and download of SpectatorView WorldAnchor via the Workstation.
* Compose the images captured by the camera on the Rig with virtual scenes, and cast it out.
* Record the composed video stream as MPEG-4 file with a maximum resolution of 4K.

Please follow the instructions below to create a demo app.



### How to integrate Live! function to a project

It's very easy to integrate Live! function to any project which made by METookit. 

* Open any project which made by METoolkit.

* Open **Player Settings**, and open **Other Settings** panel.

* Add a compilation parameter "**ME_LIVE_ACTIVE**" into Scripting Define Symbols field.

<img src="https://user-images.githubusercontent.com/7381020/28108773-3ee73c4c-671f-11e7-8aed-4c602ec366b4.png" width="500">

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
Out_Put_Path = C:\\HologramCapture\\
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

<img src="https://user-images.githubusercontent.com/7381020/28109547-027fd90a-6722-11e7-89a9-baa47c714576.png" width="500">

It will create a **exe** file and some folders. You can deploy them to your Workstation.



### Start to Use

* Start SpectatorView App on the Hololens of the Rig.

* Start "**.exe**" program on the Workstation.

* There will be an operation panel on the screen:
   <p align="center">
   <img src="https://user-images.githubusercontent.com/7381020/28112129-81c9bd2c-672a-11e7-97bc-4cb0e5e30333.png" width="700">
   </p>

### Connect to HoloLens Spectator View

* Click the "**Connect HoloLens Spectator View**" button on the right-side panel. Then the program would try to connect to the HoloLens on the Rig.
   <p align="center">
   <img src="https://cloud.githubusercontent.com/assets/7636848/26675735/9e7cf0fe-46f7-11e7-85cf-b5425560f28d.png" width="120">
   </p>

* If the connection succeeded, an echo text "**HoloLens connected**" would show up. Otherwise, "**HoloLens offline**" would appear. When connection failed, retry from the first step.
   <p align="center">
   <img src="https://user-images.githubusercontent.com/7381020/28112383-687b5a1e-672b-11e7-867d-f415b107e1e0.png" width="300">
   </p>



* With a successful connection, the program will try to synchronize automatically, and the "**Start Follow**" button would turn blue. You will see from the monitor screen that the real-time Holographics are captured.


<img src="https://user-images.githubusercontent.com/7381020/28114294-cc64a0d8-6732-11e7-9f9d-c4f04681b7aa.png" width="550">

* If you want to synchronize with another HoloLens, you need to:
    - First click "**Stop Follow**" to stop synchronization.
    - Then Click "**Download Anchor**".
    - Upon success, the position of the Holographics would change and the synchronization would start automatically.
    - If an alert of anchor not positioned appears, it means the spacial information scanned by the two HoloLens is different. You need to move the HoloLens to do a rescan until the alert disappears.
* You can download the spatial mapping information (Meshes) from HoloLens, so you can simulate spatial mapping on your workstation.
    * Click button **Download Spatial**, and when download finished, you can see tips on right-top
    * Spatial mapping meshes will only appear in **_Anchor Move_** mode. Start to move anchor, click an anchor, and select **Gaze** button in the middle, so you can see the meshes


<img src="https://user-images.githubusercontent.com/7381020/28115007-c433e9fc-6735-11e7-8ed1-8db0bcb75843.png" width="400">



### HoloLens Status Panel

- If **Config holoLens** Button shows blue, you can see the HoloLens Status Panel. If you connected HoloLens with USB line, there will show the information of HoloLens. You can check following information here.
  - IP of this HoloLens 
  - Which wifi network this HoloLens joined
  - Spectator View App version
  - If the spectator view App is running
  - Remaining battery capacity

<img src="https://user-images.githubusercontent.com/7381020/28114218-6100b886-6732-11e7-9eda-2f4e82993135.png" width="300">

> Note:
>
> - You need input your account and password of HoloLens when you login first time.
> - Some information you may need to keep the HoloLens turn on.
> - These information based on Windows Device Portal by USB, so you need to install Visual Studio in your computer.

 

### Snap and Record

- There is a MR preview window in the upper right corner. You can click the "**Full Screen**" button to make it display in Full-Screen Mode, and to exit press the "**Esc**" key on the keyboard. You can also click "**hide/show Preview**" to hide or show the Preview window.

- To record a MR video, click "**Begin Capture**". And a red "**REC**" sign would appear on the window as an indication. To finish recording, click "**Stop Capture**", and you can see the video file at the path you configured previously.

- To capture a screenshot, click "**Take Snap**" to save the captured picture to the same path for video recordings.




[Configure_your_project]: toolkit-man-configure-your-project.md
[Integrated_with_your_project]: toolkit-man-integrated-METoolkit.md
[Utility_Config_Files]: toolkit-man-utility-config-file.md
