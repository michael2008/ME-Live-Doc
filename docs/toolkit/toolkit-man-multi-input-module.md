## Multi-Input Manager Module

### Overview

MultiInputManager provides the following functions:

* Manage input events on multiple platforms
* Provide a unified callback interface for basic input events on multiple platforms, for instance, gestures on HoloLens and keyboard/mouse operations on PC.
* Set callback methods for **Navigation** gesture and **Manipulation** gesture respectively on HoloLens and switch they if necessary.
* Integrate XBOX game controller input, and mapping some control to common input. (Button A as Air Tap, left stick as manipulation, and right stick as navigation)

Please refer to the following procedure to create a demo app



### Prepare Your Project

* Create a Unity project and set it up accordingly for HoloLens apps (refer to doc "[Configure Your Project][Configure_your_project]" ).

* Set up METoolkit modules (refer to doc "[Integrated METoolkit][Integrated_with_your_project]").

* Confirm to check **Input** module in HoloEntrance.

* Create a **Cube** object and place it in a position where the camera can capture.

  ​

###Set Layer Mask

  You can use layer mask to tell InputManager which layers should interactive. 

<p align="center">

<img src="https://user-images.githubusercontent.com/7381020/28011297-6bb0c2d4-6594-11e7-96c3-ee379da167d2.png" width=300>

</p>

You can also set layer mask with code.

```C#
inputManager.layerMask = LayerMask.GetMask("Default") | LayerMask.GetMask("UI");
```



### Bind the Callback

Now we test the the binding of callback function, using Click and Navigation as an example.

* Create an object in Hierarchy view named "**App**"
* Add a new module named "**InputSample**" to the "**App**" object, and save.
* Open the "**InputSample**" module to add the following codes:
```C#
using System.Collections;
using UnityEngine;
using DataMesh.AR;
using DataMesh.AR.Anchor;
using DataMesh.AR.Interactive;
public class InputSample : MonoBehaviour
{
    public Transform targetObject;
    private MultiInputManager inputManager;
    void Start()
    {
        inputManager = MultiInputManager.Instance;
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
        BindinputManager(true);
    }
    private void OnNavigationEnd(Vector3 delta)
    {
        Debug.Log("Navigation End");
    }
    private void OnNavigationStart(Vector3 delta)
    {
        Debug.Log("Navigation Start");
    }
    private void OnNavigationUpdate(Vector3 delta)
    {
        Debug.Log("Navigation Update");
        targetObject.Rotate(new Vector3(0, 1, 0), -delta.x);
    }
    void OnTapped(int tapCount)
    {
        Debug.Log("Tapped Event");
        targetObject.GetComponent<MeshRenderer>().material.color = new Color(1, 0, 0);
    }
    public void BindinputManager(bool bind)
    {
        inputManager.ChangeToNavigationRecognizer();
        if (!bind)
        {
            Debug.Log("unbind gesture");
            inputManager.cbTap -= OnTapped;
            inputManager.cbNavigationStart -= OnNavigationStart;
            inputManager.cbNavigationUpdate -= OnNavigationUpdate;
            inputManager.cbNavigationEnd -= OnNavigationEnd;
            return;
        }
        else
        {
            Debug.Log("bind gesture");
            inputManager.cbTap += OnTapped;
            inputManager.cbNavigationStart += OnNavigationStart;
            inputManager.cbNavigationUpdate += OnNavigationUpdate;
            inputManager.cbNavigationEnd += OnNavigationEnd;
        }
    }
}
```
* Drag the "**Cube**" in the scene to the "**Target Object**" Column of "**InputSample**" of "**App**" in the Hierarchy View.
   <p align="center">
   <img src="https://cloud.githubusercontent.com/assets/7636848/26666376/2005d95e-46d2-11e7-85f3-9dfce47fe2b2.png" width="320">
   </p>
* Release the Project to HoloLens or start it directly in Unity.
> Note: If you run the app in Unity on PC, the **Alt+J/K/L/I/U/O** keys on PC would be mapped to the Navigation gesture on HoloLens. And if you have bound the **Manipulation** gesture, the corresponding keys on PC would be **Shift+J/K/L/I/U/O**.
>
> Note: if you uncheck **Need Assist Key** option in **_MultiInputManager_**, you can use **J/K/L/I/U/O** as Manipulation or Navigation , without Alt and Shift Key.



### Switch between Navigation and Manipulation

The use of **Manipulation** is the same as that of **Navigation**. The difference is that the input parameters of **Manipulation** are the absolute displacement of user's hand in the real world.

Add the following codes in the "**InputSample**" script to options to switch to the **Manipulation** gesture.
```C#
public void BindinputManager(bool bind, bool isManipulation)
{
    if (!bind)
    {
        Debug.Log("unbind gesture");
        inputManager.cbTap -= OnTapped;
        inputManager.cbNavigationStart -= OnNavigationStart;
        inputManager.cbNavigationUpdate -= OnNavigationUpdate;
        inputManager.cbNavigationEnd -= OnNavigationEnd;
        inputManager.cbManipulationEnd -= OnManipulationEnd;
        inputManager.cbManipulationStart -= OnManipulationStart;
        inputManager.cbManipulationUpdate -= OnManipulationUpdate;
        return;
    }
    else
    {
        Debug.Log("bind gesture");
        inputManager.cbTap += OnTapped;
        if (!isManipulation)
        {
            inputManager.ChangeToNavigationRecognizer();
            inputManager.cbNavigationStart += OnNavigationStart;
            inputManager.cbNavigationUpdate += OnNavigationUpdate;
            inputManager.cbNavigationEnd += OnNavigationEnd;
        }
        else
        {
            inputManager.ChangeToManipulationRecognizer();
            inputManager.cbManipulationEnd += OnManipulationEnd;
            inputManager.cbManipulationStart += OnManipulationStart;
            inputManager.cbManipulationUpdate += OnManipulationUpdate;
        }
    }
}
private void OnManipulationEnd(Vector3 delta)
{
    Debug.Log("Manipulation End");
}
private void OnManipulationStart(Vector3 delta)
{
    Debug.Log("Manipulation End");
}
private void OnManipulationUpdate(Vector3 delta)
{
    targetObject.Translate(delta);
}
```



## Use XBOX Game Controller

### Prepare

+ To use XBOX Game Controller, you need to add key mapping to Unity config **Input** 

  <p align="center">

  <img src="https://user-images.githubusercontent.com/7381020/28008234-4be3b7b4-6589-11e7-9ace-834630e21cb4.png" width="300">

</p>

+ For convenience, we provide a complete Input set file, and you can copy it to you Unity project simply. 

  + This file is located in this folder: `%Unity_Project%/Assets/DataMesh/ARModule/Interactive/Config/InputManager.asset`
  + you can copy it to this folder: `%Unity_Project%/ProjectSettings/`  , and overwrite the file with same name.
  + Note: if you have defined your own input key mapping, don't overwrite it directly, otherwise you will lose your configuration. Please merge them manually.

+ Connect your XBOX Game Controller to your HoloLens (or PC / other device) with Bluetooth.

  + if you want to use controller on PC, you can also use USB line to connect directly.

  ​

### Use XBOX controller to simulate Air Tap and hand move

You don't need any code work.  Once your connect the XBOX Controller to HoloLens, you can:

+ use **Button A** as Air Tap.
+ use **left stick** as Manipulation. (When you push left stick, Input system will switch to manipulation mode automatically).
+ use **right stick** as Navigation. (When you push left stick, Input system will switch to navigation mode automatically).



### Use other key on XBOX controller 

if you wan't to use other key and stick on XBOX controller, you can get all button and stick status in **Update** function of MonoBehaviour.

It's very similar as **Input** in UnityEngine.

```C#
 private void Update()
    {
        if (inputManager == null)
            return;

        float ltaxis = inputManager.controllerInput.GetAxisLeftTrigger();
        float rtaxis = inputManager.controllerInput.GetAxisRightTrigger();

        float hAxis = inputManager.controllerInput.GetAxisLeftThumbstickX();
        float vAxis = inputManager.controllerInput.GetAxisLeftThumbstickY();

        float htAxis = inputManager.controllerInput.GetAxisRightThumbstickX();
        float vtAxis = inputManager.controllerInput.GetAxisRightThumbstickY();

        bool a = inputManager.controllerInput.GetButton(ControllerButton.A);
        bool b = inputManager.controllerInput.GetButton(ControllerButton.B);
        bool x = inputManager.controllerInput.GetButton(ControllerButton.X);
        bool y = inputManager.controllerInput.GetButton(ControllerButton.Y);
        bool lb = inputManager.controllerInput.GetButton(ControllerButton.LeftShoulder);
        bool rb = inputManager.controllerInput.GetButton(ControllerButton.RightShoulder);
        bool ls = inputManager.controllerInput.GetButton(ControllerButton.LeftThumbstick);
        bool rs = inputManager.controllerInput.GetButton(ControllerButton.RightThumbstick);
        bool view = inputManager.controllerInput.GetButton(ControllerButton.View);
        bool menu = inputManager.controllerInput.GetButton(ControllerButton.Menu);

        DebugText.text =
            string.Format(
                "LeftStickX: {12:0.000} LeftStickY: {13:0.000}\n" +
                "RightStickX: {14:0.000} RightStickY: {15:0.000}\n" +
                "LTrigger: {0:0.000} RTrigger: {1:0.000}\n" +
                "A: {2} B: {3} X: {4} Y:{5}\n" +
                "LB: {6} RB: {7} LStick: {8} RStick:{9}\n" +
                "View: {10} Menu: {11}\n"
                ,
                ltaxis, rtaxis,
                a, b, x, y,
                lb, rb, ls, rs,
                view, menu,
                hAxis, vAxis,
                htAxis, vtAxis
                );
    }
```




[Configure_your_project]: toolkit-man-configure-your-project.md
[Integrated_with_your_project]: toolkit-man-integrated-METoolkit.md
[Utility_Config_Files]: toolkit-man-utility-config-file.md
