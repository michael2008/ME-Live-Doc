## Speech Manager Module

### Overview

SpeechManager offers voice control of Hololens. Developers could add keywords as control commands alone with corresponding callback methods. If the speech manager is enabled, it will constantly monitor the voice input of HoloLens. And when a voice command is detected, the bound action will take place.



### Use of SpeechManager

* Create a Unity project and set it up accordingly for HoloLens apps (refer to doc "[Configure Your Project][Configure_your_project]" ).
* Set up METoolkit modules (refer to doc "[Integrated METoolkit][Integrated_with_your_project]" ).
* Do not check the "**Auto Turn On**" box, and we need to enable or disable voice control manually.

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/7636848/26667234/beab6a98-46d6-11e7-8b32-44c49ef880ea.png" width="320">
</p>

* Call **AddKeywords()** method of SpeechManager to add keywords and associated action method for voice commands.
```C#
void Start ()
{
    SpeechManager.Instance.Init(); // manually initialize since we do not check the AutoTurnOn box
    SpeechManager.Instance.AddKeywords("Open Menu", OpenMenuAction);
    SpeechManager.Instance.TurnOn(); // now enable voice commands recognition
}

public void OpenMenuAction ()
{
    Debug.Log("Recognize command: Open Menu");
}
```

> Note: The codes above add a voice command "**Open Menu**", and in its action part, we print a log message. 




[Configure_your_project]: toolkit-man-configure-your-project.md
[Integrated_with_your_project]: toolkit-man-integrated-METoolkit.md
[Utility_Config_Files]: toolkit-man-utility-config-file.md