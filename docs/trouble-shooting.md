## METoolkit-related

## Unity-related
## Project Environment
* **Stuck in starting program inside Unity**

a) If it is Windows 10, please check whether you have opened “Developer Mode”. If it is not “Developer Mode”, also the project includes HoloLensInputModule, it will result in getting stuck when starting it in Editor Environment.
* **The position of the object in HoloLens and the preliminarily set one are not commensurate after starting.**

b) Check whether the main camera's position is (0,0,0). If its initial position is not (0,0,0), it will result in shewing of the object’s position inside HoloLens.
## Unity App Release
*  **What if the released app is terribly wrong?**

a) Check whether Scene which you chose when releasing is right.
* **What if compiling of app is displayed as wrong when it is released to HoloLens but right in Unity?**

b) It is usually caused by using classes or methods which is not supported by UWP. Please remove these kind of things and then recompile it.
* **App debugging fails when installing it from Visual Studio to HoloLens.**

c) Check builds parameter of VisualStudio. Platform must be x86 and Target Device

d) Check whether HoloLens is closed or in the sleep state. If yes, please open or wake it.

e) Try to delete App in holoLens

f) Repeat trying to start. If there is still any problem, try to delete VisualStudio Project and release it again from Unity.
## Anchor Module
* **When starting SceneAnchorController, you will see double groups of ghosting on frame and crystalline.**

a) Check whether MEHolo/AnchorManager/AnchorCamera Object in the scene is active. The main camera, which is required for following other cameras, must be kept active when starting it. It can not be covered, otherwise the position of other cameras will never be synchronized to the position of the main camera.

* **Fail to upload Anchor**

b) Check whether IP setting of Share Anchor Serve is right.

c) If space information is too big, it will result in failure when you upload it. Please remove space information in HoloLens, rescan it, and re-upload.

* **Anchor position is not right after you download it successfully.**

d)It usually because of downloaded space information and space information currently recognized by HoloLens are not commensurate. So WorldAnchor cannot be located (if downloading Anchor on Live, no special hint will appear in such a state). Please try to move HoloLens in all directions. When space information is recognized to be commensurate, Anchor object will return to the right position.

## Input Module
* **Gaze to click the object but Air Tap fails.**

a)Confirm MultiInputManager has been started.

b) Check whether layer setting in MultiInputManager covers layer used for clicking the object.

c) If callback method of MultiInputManage is used, check the corresponding callback function is right or not. Confirm all positions use “+=” to add callback, instead of using “=” to cover callback.

d) If operational method of response function of clicking object is used, please check whether Collider used for clicking objects and modules with response function are on the same object.

e) Test in Unity. Open “Simulate Gaze” on InputManager module. Then adjust the camera, fix the sight on the target object and click Enter to simulate Air Tap

* **Manipulation or Navigation is invalid.**

f) Confirm MultiInputManager has been started.

g) Confirm whether MultiInputManager has been switched to the corresponding recognition model. Use ChangeToManipulationRecognizer() and ChangeToNavigationRecognizer() to conduct switch.

## Collaboration Module
* **Collaboration Module fails to work.**

a) Check all devices in the same network or not.

b) Check the setting of all devices to ensure they have right server IP.

* **There is some delay in collaboration**

c) Delivery interval of Collaboration Server is 100ms. Thus delay within about 100ms is reasonable.

d) If time for delay is too long. Please check whether the network is stable and the loading situation of Server Host.

## Live Module
* **Jam occurs soon after starting**

a) Please check Quality setting and vertical synchronization in all running models has been closed. In the condition of opening vertical synchronization, jam when starting Live may occur, including Editor Environment and Standalone Environment.
* **Live Workstation cannot be connected to HoloLens SpectatorView**

b) Check HoloLens and Live Workstation are in the same network.

c) Check SpectatorView app on HoloLens has been started. If necessary, repeat starting the app.

d) Check whether SpectatorView Listen Port Setting in Live Workstation and setting of SpectatorView in HoloLens are commensurate.




