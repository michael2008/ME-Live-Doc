## Overview

This guide walks you through the process of building your one-stop app using ME-Live! which is composed of two main products, MeshExpert Suite and [METoolkit](#metoolkit-overview).

MeshExpert Suite provides you with a way to use the following amazing features of ME-Live!.

+ Uploading resources synchronously
+ Multi-user, multi-device collaborative work experience is provided
+ Easy installer and smart app management

METoolkit provides not only multiple APIs could be used to communicate with MeshExpert, but also common modules. METoolkit will give you an idea of how things are working internally, which helps you to design and develop your own collaborated application.

## Development Environment

The ME-Live! development environment, which can be installed on a single computer (recommended), provides you a set of processes and tools used to help you create the product. Following are the prerequisites for installing ME-Live! development environment.

### Hardware Requirement

|        Device         |     Quantity     |                 Purpose                  | Required |
| :-------------------: | :--------------: | :--------------------------------------: | :------: |
| Live Workstation host |     One set      | Install MeshExpert suite and establish Live Workstation |   Yes    |
|       Live Rig        |     One set      |        Synthesize the 3D hologrms        |   Yes    |
|       HoloLens        | At least one set | Debug and release your mix-reality apps  |   Yes    |
|        Surface        |     Optional     |        Debug and release UWP apps        |    No    |
|      IPhone/IPad      |     Optional     | Debug and release iOS virtual-reality apps |    No    |
|        Android        |     Optional     |      Debug and release Android apps      |    No    |

Live Workstation can directly, without MeshExpert Suite, serve as the development environment for the host. It’s recommended to use high-performance desktop host and the basic hardware requirements are as follows:

|      Item       | Requirements                             |
| :-------------: | :--------------------------------------- |
|       CPU       | Quad-core Intel i5/i7, AMD Ryzen 1600 or higher |
|     Memory      | 8GB+                                     |
| Hard disk space | 100GB+, SSD recommended                  |

The complete documentation for Live RIG hardware configuration and installation configuration is available at [RIG Installation in Usage Guide for ME Live!](user-guide.md#rig-installation)

> **Note:** The devices (Surface, IPhone/IPad and Android Phone) and its quantity are determined by your needs.

### Software Requirement

ME-Live! Development environment can be directly set up on Live Workstation host so that you can easily debug your app using MeshExpert suite.

#### Supported operating systems

ME-Live! only supports Windows 10 now. The detailed requirement is as follows:

|    Operating system     |            Version            |
| :---------------------: | :---------------------------: |
| Windows 10 Professional | 64-bit, version 1607 or later |
|  Windows 10 Enterprise  | 64-bit, version 1607 or later |
|  Windows 10 Education   | 64-bit, version 1607 or later |

#### Unity

Please use Unity 5.5 or later to develop your apps. (Unity 5.5.1 recommended).

> **Note:** You can download the Unity [here](https://unity3d.com/get-unity/download/archive). For detailed installation and usage of Unity, check out the [Unity Documentation](https://docs.unity3d.com/Manual/index.html).

You also need to install the "UnitySetup-Metro-Support-for-Edito". Download the 5.5.1 version [UnitySetup-Metro-Support-for-Editor-5.5.1f1.exe](https://meshexpert-us.s3.amazonaws.com/UnitySetup-Metro-Support-for-Editor-5.5.1f1.exe). For other versions, you may download it yourself from the Unity website.

#### Visual Studio 2015 V3

What you'll need is Visual Studio 2015 Community V3 or later. Check out [Windows Dev Center](https://developer.microsoft.com/en-us/windows/mixed-reality/install_the_tools#immersive_headset_development_.28minimum.29) for details.

> **Note:** Making sure you have the latest Windows 10 SDK installed. Otherwise you cannot use the HoloLens to debug your app.

#### METoolkit

The METoolkit is a Unity plug-in that provides a growing range of MeshExpert APIs and  functional modules. It can help you easily develop MeshExpert-based HoloLens application.

You will find the METoolkit package, which can be imported into your Unity project, in MeshExpert suite.

## App Development with METoolkit

### METoolkit Overview

METoolkit is an ME-DataMix (MeshExpert: DataMix - MR Data Integration Platform) client development toolkit that provides a growing range of functional modules and SDK to help developers develop AR apps based on HoloLens and ME-HoloServer.

METoolkit is also a development engine based on Unity 3D platform. Relying on powerful features of Unity3D, METoolkit is able to run on different devices or platforms, including HoloLens, Surface, iOS, Android, and PC.

> **Note:** Platform related features, such as spatial anchors, gesture recognition, may be unavailable on some platforms. Please read the [METoolkit Features](#metoolkit-features) for details.

### METoolkit Features

1. **MEHoloSDK**: providing a set of APIs used to work with ME-HoloServer, check out [MEHoloSDK documentation](metoolkit-manual.md#meholosdk-docs).
2. **ARModule**: a collection of functional modules for AR development, including:
    + **_MultiInput_**: Giving you the ability to not only use keyboard, mouse and touch screen as input device, but also take advantages of spatial gesture recognition.

    + **_Speech_**: Speech perception. (`HoloLens only`)

    + **_Cursor_**: Indicating and showing the cursor in AR/VR application.

    + **_BlockMenu_**: Menu builder that provides a set of useful methods.

    + **_Anchor_**：Spatial positioning module that can be used to set up one or more spatial anchors and sharing these location information using ME-HoloServer. (`HoloLens only`)

    + **_Capture&Share_**: Taking a picture or recording a video, which can be shared via ME-HoloServer. (`HoloLens only`)

    + **_Collaboration_**: Sending/receiving messages via ME-HoloServer.

      > **Note:** Basically, you will create and initialize what are called `Rooms` in which  user can collaborate with others. 

    + **_Live!_**: Providing a control panel and relevant functions so that you can easily migrate other AR application to Live!.

    + **_Utility_**: Providing a set of utilities.

### METoolkit Structure

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/4099195/26622530/4e16db64-461d-11e7-8203-f25b5b631179.png" width="500">
<p align="center"><em>METoolkit Structure</em></p>
</p>

### Development Project Setting

#### General Setting

1. Set Camera to Solid Color and background color to 0,0,0
2. Set the position of Camera to 0,0,0
3. Open `Edit` -> `Project Setting` -> `Quality`, subsequently check all Levels and close `V Sync Count` of each level.

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/4099195/26622678/c8717432-461d-11e7-81a0-1d61b2f61c51.png" width="300">

<img src="https://cloud.githubusercontent.com/assets/4099195/26622679/cbbffb2c-461d-11e7-92cb-e9d145c5ed43.png"width="500">
<p align="center"><em>General Settings</em></p>
</p>

#### PC Standalone Setting

1. Open `File` -> `Build Settings` -> `Player Settings` and then choose `PC, Mac & Linux`.

2. Open `Other Setting` and change `API Compatibility level` to `.Net 2.0` in `Optimization`.

   > **Note:** Do not choose .Net 2.0 Subset.

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/4099195/26622845/55ac8e2c-461e-11e7-922f-51a7effea618.png" width="500">
<p align="center"><em>PC Standalone Setting</em></p>
</p>

#### Windows Stroe Setting

1. Switch to `Windows Store` in `Build Settings`
    + Choose `Universal 10` in `SDK`

    + Choose `HoloLens` in `Target` 

      > **Note:** Choose the proper device if your application is targeted to other platform.

    + Choose `D3D` in `UWP Build Type`

    + Making sure that you have ``Unity C# Projects` checked.

    + Click `Build And Run`

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/4099195/26623025/e7518f08-461e-11e7-8a83-1bc7a6ecb436.png" width="500">
<p align="center"><em>Windows Store Setting</em></p>
</p>

2. Open `Other Setting` and check `Virtual Reality Supported`
3. Choose `Windows Holographic`

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/4099195/26623099/346c882e-461f-11e7-9a13-a2966c2f6c5f.png" width="500">
<p align="center"><em>Windows Store Setting</em></p>
</p>

4. Check options in `Capabilities` in `Publishing Settings` according to your needs

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/4099195/26623115/45686fd0-461f-11e7-854d-fe1b04b67ce4.png" width="500">
<p align="center"><em>Windows Store Setting</em></p>
</p>

### Start Using METoolkit

We will use METoolkit to build a simple app so that you can preliminarily know about the core function of Mesh Expert.

#### Prepare

+ Making sure that **_MeshExpert_** has been installed in the host and its relevant services have been started.
+ Set up Unity Project and set the scenes according to the requirements of HoloLens (refer to "[Holograms 101E Document](https://developer.microsoft.com/en-us/windows/mixed-reality/holograms_101e)" by Microsoft)
+ Create an object in the scene and set its position as (0, 0, 5)
+ Import METoolkit into this Unity Project
+ Enter `DataMesh/ARModule/Entrance` and drag `MEHoloEntrance` that has been made in advance into the scene.
+ Choose `MEHoloEntrance` in the scene and click `Create All MEHolo Module` on Inspector Panel.

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/4099195/26623711/28df32c0-4621-11e7-9c58-41c132bb1ca7.png" width="500">
<p align="center"><em>Create all MEHolo Module</em></p>
</p>

#### Coding

+ Add an object in the scene and name it as `App`
+ Add a script on the object and name it as `GettingStartedSample.cs`
+ Copy and paste the following codes to the script.

```c#
using System.Collections;
using UnityEngine;
using DataMesh.AR.Network;
using DataMesh.AR;
using MEHoloClient.Entities;

public class GettingStartedSample : MonoBehaviour, IMessageHandler
{
    public GameObject cube;
    private CollaborationManager collaborationManager;

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

        collaborationManager = CollaborationManager.Instance;
        collaborationManager.appId = 9999;
        collaborationManager.roomId = "Room1";
        //replace with the IP of the machine on wihch MeshExpert has been installed.
        collaborationManager.serverHost = "192.168.2.50";

        collaborationManager.AddMessageHandler(this);

        SceneObjects roomInitData = new SceneObjects();
        ShowObject obj = new ShowObject(
            "Test",
            true,
            GetTransformFloat(cube.transform),
            null
        );
        roomInitData.ShowObjectDic.Add(obj.show_id, obj);
        collaborationManager.roomInitData = roomInitData;

        collaborationManager.TurnOn();
    }

    private float[] GetTransformFloat(Transform trans)
    {
        float[] rs = new float[6];
        rs[0] = trans.position.x;
        rs[1] = trans.position.y;
        rs[2] = trans.position.z;
        rs[3] = trans.eulerAngles.x;
        rs[4] = trans.eulerAngles.y;
        rs[5] = trans.eulerAngles.z;
        return rs;
    }

    public void DealMessage(SyncProto proto)
    {
        MsgEntry[] messages = proto.sync_msg.msg_entry;
        if (messages == null)
            return;

        for (int i = 0; i < messages.Length; i++)
        {
            MsgEntry msg = messages[i];
            cube.transform.position = new Vector3(msg.pr[0], msg.pr[1], msg.pr[2]);
            cube.transform.eulerAngles = new Vector3(msg.pr[3], msg.pr[4], msg.pr[5]);
        }
    }

    void Update()
    {
        if (collaborationManager != null && collaborationManager.hasEnterRoom)
        {
            MsgEntry entry = new MsgEntry(
                OP_TYPE.UPD,
                "Test",
                true,
                GetTransformFloat(cube.transform),
                null,
                null
            );
            collaborationManager.SendMessage(new MsgEntry[1] { entry });
        }
    }
}
```

#### Object Property

+ Click object `App` in the scene and check its `Inspector Panel`
+ Drag object `Cube` in the scene to property `Cube` on the Panel

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/4099195/26623909/d198c5f2-4621-11e7-92c8-6594245976af.png" width="500">
<p align="center"><em>Object Property Setting</em></p>
</p>

#### Runtime Tests

+ Deploy the app to HoloLens (check out [Microsoft Doc](https://docs.microsoft.com/en-us/hololens/hololens-install-apps))
+ Check if the HoloLens and the machine on which **_MeshExpert_** has been installed are in the same LAN environment.
+ Check if **_MeshExpert Server_** is running.
+ Launch the app on HoloLens. You will see a cube in front of your eyes.
+ Launch the app in Unity and then **_move_** or **_revolve_** the cube in `Scene`.

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/4099195/26624011/29ee5596-4622-11e7-95dc-afedabdd64fc.png" width="300">
<p align="center"><em>Cube</em></p>
</p>

+ Check the cube in HoloLens and you will see the cube, in Unity, is moving synchronously.
