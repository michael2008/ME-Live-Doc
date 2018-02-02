
## World Anchor Module

### Overview

SceneAnchorController provides the following functionalities:

+ Manage the spatial scenes scanned by HoloLens.
+ Manage the spatial anchor, including creation, modification, deletion and storage.
+ Include a set of user interfaces to operate spatial anchors where users can adjust the position and angle of each Anchor by gesture.
+ Anchor upload and download (through the workstation).
+ All functions can simulate on PC, include save & load anchor. It's very useful in Live! application, that you can locate holographic without HoloLens.

> Note that HoloLens can use the raw WorldAnchor.

Next, let us create a demo app following the procedures below.



### Prepare Your Project

* Create a Unity project and set it up accordingly for HoloLens apps (refer to doc "[Configure Your Project][Configure_your_project]" ).
* Set up METoolkit modules (refer to doc "[Integrated METoolkit][Integrated_with_your_project]" ).
* Create three objects: Cube, Sphere, Cylinder, and place them in a position where the camera can capture.
* Confirm to check **Anchor**, **Input** and **Cursor** Modules in HoloEntrance.

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/7636848/26660808/039b6628-46ad-11e7-926d-03080e78ebd7.png" width="250">
</p>



### Prameters

In the Hierachy View, find **MEHolo/AnchorManager** object and choose it, and you will see the following panel in the Inspector View. Leave the parameters as defaults, later in this section you will get to know their meanings and then adjust them accordingly.

<p align="center">
<img src="https://user-images.githubusercontent.com/26785911/35388638-8cc781a2-020f-11e8-84e0-4fdb8da1a7ea.png" width="400">
</p>



### Setting up Anchor

* Choose an Anchor Object (such as Cube) you want to add, and then add "**AnchorDefinition**" in the Inspector Panel.

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/7636848/26661436/4855bf40-46b0-11e7-8b58-ab70794a3307.png" width="250">
</p>

* Enter a name for the Anchor.

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/7636848/26661439/4abcac26-46b0-11e7-89a4-c9edbd670cb5.png" width="320">
</p>

* Choose the object in the scene and you will see a blue **bounds** which indicates the Anchor scope. By dragging the ball handles, you can change the size of the bounds.
<p align="center">
<img src="https://cloud.githubusercontent.com/assets/7636848/26661440/4beae40a-46b0-11e7-90c8-e0cbb1e0f52e.png" width="320">
</p>

> Note: the size of the bounds is only used for showing the Anchor when it is moved. It has no practical significance and can be set according to your preferences.

* Now the Anchor of one object is set, please set the Anchors of the other two objects yourself with the same procedures.



### Limit Rotate Axis

- In some case you may want some axis not to rotate, you can lock specific axis by switching the option of specific axis to 'Lock'.

  <p align="center">
  <img src="https://user-images.githubusercontent.com/13318047/35616118-407c332a-06af-11e8-95f3-6903a6faba54.png" width="500">
  </p>

### Write a Test Demo

+ Create an object of name "**App**" in Hierarchy view.
+ Add a new module with name "**SceneAnchorSample**" and save.
+ Open the "**SceneAnchorSample**" module to add the following codes:
```C#
using System.Collections;
using UnityEngine;
using DataMesh.AR;
using DataMesh.AR.Anchor;
using DataMesh.AR.Interactive;

public class SceneAnchorSample : MonoBehaviour
{
    private MultiInputManager inputManager;

    void Start ()
    {
        StartCoroutine(WaitForInit());
    }

    private IEnumerator WaitForInit()
    {
        MEHoloEntrance entrance = MEHoloEntrance.Instance;
        while (!entrance.HasInit)
        {
            yield return null;
        }

        // Todo: Begin your logic
        inputManager = MultiInputManager.Instance;
        inputManager.cbTap += OnTap;
    }

    private void OnTap(int count)
    {
        inputManager.cbTap -= OnTap;

        SceneAnchorController.Instance.cbAnchorControlFinish = ModifyAnchorFinish;
        SceneAnchorController.Instance.TurnOn();
    }

    private void ModifyAnchorFinish()
    {
        SceneAnchorController.Instance.TurnOff();
        inputManager.cbTap += OnTap;
    }
}
```

Now you can build and install the app to HoloLens to see the results.



### Change Anchor

* After starting the app in HoloLens, you shall see three objects in front of you.
* Air-tap at any place to enter the Anchor adjustment mode. Now every anchor you created would show up with bounds and with a blue crystalline at the base position indicating the position of the Anchor.

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/7636848/26663242/fb0911cc-46bb-11e7-918d-e88e1368d0f9.png" width="500">
</p>

* Gaze at the bounds box of an object, and then air-tap it. The box would change color and glitter indicating a selection of the object. Upon selection, three square buttons would show up above the crystalline.

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/7636848/26663244/fd39a7fe-46bb-11e7-86f3-bc637b64c3e4.png" width="320">
</p>

* Fix your eyes with the cursor on the middle "**Gaze**" button and air-tap. You will enter the "**Eye Move Mode**" where the spatial grid would appear. In this mode, the object would move alone with the focal point (the cursor) and when stops it would land on the spatial grid.
> Note: if there is no spatial grid covering the focal point, the object would float at 3 meters away from the currently gazed position. To exit the "**Eye Move Mode**", do another air-tap.
* When the choose buttons appear, gaze at the left "**Move**" button and air-tap, then you will enter the "**Manual Move Mode**" and three moving axes would show up under the crystalline.
  * when using HoloLens, you can "Tap your finger down and Move" to move the object in the space.
  * when used on a computer, a keyboard hint would show up alone with the axes (as demonstrated in the following picture). Following the hint, you can move the object around using the "**UIOJKL**" keys on your keyboard.

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/7636848/26663246/fee543b0-46bb-11e7-84e2-f0e5f6707172.png" width="320">
</p>

* When gaze at the right "**Rotate**" Button and air-tap, you will enter the "**Manual Rotate Mode**" where the a rotating sign would surround the the crystalline.
  * when using HoloLens, you can **"Tap your finger down and Move"** to rotate the object in the space.
  * when used on a computer, you can follow the hint to use the "**UIOJKL**" keys to help you rotate the object.
<p align="center">
<img src="https://cloud.githubusercontent.com/assets/7636848/26663278/2f2a45a2-46bc-11e7-8227-b152450779ed.png" width="320">
</p>

> Note:
> * when an object is selected, you can air-tap at a blank area to unselect the object.
> * when no object is selected, you can air-tap at a blank area to exit the **Anchor Editing Mode**, where the surrounding boxes and crystalline would all disappear, and the positions of objects will be saved so that on next boot all the positions would be automatically restored if the space matches.



[Configure_your_project]: toolkit-man-configure-your-project.md
[Integrated_with_your_project]: toolkit-man-integrated-METoolkit.md
[Utility_Config_Files]: toolkit-man-utility-config-file.md
[User_Guide_for_workstation]: ../user-guide.md#workstation-installation
