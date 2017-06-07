## Unity-related
### Unity Application Release
Q: **Released application didn't work properly**

The Scene selected at the time of publication may not right.

Q: **There are no compilation errors in Unity, but there are compilation errors when publishing it as an application which can run on HoloLens.**

It is usually because the codes or libraries used are not supported by UWP. Please remove these kind of things and then recompile it.

Q: **Application debugging fails when installing it from Visual Studio to HoloLens.**

The possible solutions:

Check build parameters of Visual Studio. Platform must be and Target must be x86 and Device respectively.

Check whether HoloLens is closed or in hiberation state. If yes, please open it or wake it up.

Try to delete Application on HoloLens.

Try to start it again. If there are still some problems, try to delete Visual Studio Project and release it again from Unity.

## METoolkit-related
### Anchor Module
Q: **When the SceneAnchorController module is enabled, the border and the crystal appear two sets of ghosting**

Check whether MEHolo/AnchorManager/AnchorCamera Object in the scene is active. Other cameras which need to follow the main camera must remain active at startup and can not be hidden, otherwise the cameras' position will never be synchronized to the position of the main camera.

Q: **Fail to upload Anchor**

Check whether IP setting of Share Anchor Serve is right.

If space information is too big, it will result in failure when you upload it. Please remove space information in HoloLens, rescan it, and re-upload.

Q: **Anchor position is not right after you download it successfully.**

It usually because of downloaded space information and space information currently recognized by HoloLens are not commensurate. So WorldAnchor cannot be located (if downloading Anchor on Live, no special hint will appear in such a state). Please try to move HoloLens in all directions. When space information is recognized to be commensurate, Anchor object will return to the right position.

### Input Module
Q: **Gaze to click the object but Air Tap fails.**

Confirm MultiInputManager has been started.

Check whether layer setting in MultiInputManager covers layer used for clicking the object.

If callback method of MultiInputManage is used, check the corresponding callback function is right or not. Confirm all positions use “+=” to add callback, instead of using “=” to cover callback.

If operational method of response function of clicking object is used, please check whether Collider used for clicking objects and modules with response function are on the same object.

Test in Unity. Open “Simulate Gaze” on InputManager module. Then adjust the camera, fix the sight on the target object and click Enter to simulate Air Tap

Q: **Manipulation or Navigation is invalid.**

Confirm MultiInputManager has been started.

Confirm whether MultiInputManager has been switched to the corresponding recognition model. Use ChangeToManipulationRecognizer() and ChangeToNavigationRecognizer() to conduct switch.

### Collaboration Module
Q: **Collaboration Module fails to work.**

Check all devices in the same network or not.

Check the setting of all devices to ensure they have right server IP.

Q: **There is some delay in collaboration**

Delivery interval of Collaboration Server is 100ms. Thus delay within about 100ms is reasonable.

If time for delay is too long. Please check whether the network is stable and the loading situation of Server Host.

### Live Module
Q: **Jam occurs soon after starting**

Please check Quality setting and vertical synchronization in all running models has been closed. In the condition of opening vertical synchronization, jam when starting Live may occur, including Editor Environment and Standalone Environment.

Q: **Live Workstation cannot be connected to HoloLens SpectatorView**

Check HoloLens and Live Workstation are in the same network.

Check SpectatorView app on HoloLens has been started. If necessary, repeat starting the app.

Check whether SpectatorView Listen Port Setting in Live Workstation and setting of SpectatorView in HoloLens are commensurate.

## Project Environment
Q: **Stuck in starting program inside Unity**

If it is Windows 10, please check whether you have opened “Developer Mode”. If it is not “Developer Mode”, also the project includes HoloLensInputModule, it will result in getting stuck when starting it in Editor Environment.

Q: **The position of the object in HoloLens and the preliminarily set one are not commensurate after starting.**

Check whether the main camera's position is (0,0,0). If its initial position is not (0,0,0), it will result in shewing of the object’s position inside HoloLens.



