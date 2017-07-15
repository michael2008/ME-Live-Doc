## Integrated METoolkit

Through an integrated entrypoint provided by METoolkit, users are able to import and integrate all the METoolkit modules to apps at once just by dragging them to the scene.

### Preparing for Use

* Import METoolkit to Unity Project.
* Go to folder **"DataMesh/ARModule/Entrance/"** and drag MEHoloEntrance bundle into Unity scenes.
* Choose MEHoloEntrance in the scene and click **"Create All MEHolo Module"** button on Inspector Panel.
  <p align="center">
  <img src="https://user-images.githubusercontent.com/7381020/28106606-0f5411ec-6717-11e7-9e5b-673c214bc4a7.png" width="400">
  </p>
* MEHolo objects will be automatically generated in the scene, which includes all the modules in Toolkit.
  <p align="center">
  <img src="https://user-images.githubusercontent.com/7381020/28006996-4c0f1198-6584-11e7-8d00-ecd895a13680.png" height="200">
  </p>


### Input your App Name

- Select MEHoloEntrance object again, input your App name in the text field, and then push the button "Set App Name". 

<img src="https://user-images.githubusercontent.com/7381020/28106778-ca7fab16-6717-11e7-8e75-567f39b026d3.png" width="400">



- Then app name will appear in inspector panel by Green.

<img src="https://user-images.githubusercontent.com/7381020/28106850-194d144a-6718-11e7-8dab-3abc4c451471.png" width="400">



> **Important:** You must set a **different App Name to every app**, because many of ME functions (such as collaboration, storage, and so on) will depend on this name.

### Choose Modules

* Select MEHoloEntrance object again to see the Inspector Panel, here you can choose what modules to use, and uncheck those you don't need.
* **NOTE:** there are module dependencies such that the use of some modules demands some other modules to be present. For instance, when Live module is checked, Anchor and Input modules will be checked automatically and can not be unchecked.
* As for the detailed usage of these modules, please refer to their corresponding instructions later in this section.

### Code Integration

MEHoloEntrance will automatically run and initialize after the app started. But before initialization, the system is not ready for use. Therefore, developers should check the **'HasInit'** property in code and wait until its value turned to 'true' before any other operations.

Demo codes are as follows:
```C#
using System.Collections;
using UnityEngine;
using DataMesh.AR;
public class MainApp : MonoBehaviour
{
    // Use this method to initialize
    void Start()
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
    }
}
```

