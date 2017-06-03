## Overview

This guide walks you through the process of building your one-stop app using ME-Live!. The ME-Live! is composed of two main products: MeshExpert Suite and [METoolkit](https://github.com/DataMesh-OpenSource/MeshExpert-Live/wiki/Developer-Guide/_edit#app-development-with-metoolkit).

MeshExpert Suite provides you with a way to use amazing features of ME-Live!.

+ Uploading resources synchronously
+ Multi-device graphic collaboration
+ App installation and management

METoolkit provides not only multiple APIs could be used to communicate with MeshExpert, but also common modules. METoolkit will give you an idea of how things are working internally, which helps you to design and develop your own collaborated application.

## Development Environment

The ME-Live! development environment, which can be installed on a single node (recommended), provides you a set of processes and tools used to help you create the product. Following are the prerequisites for installing ME-Live! development environment.

### Hardware Requirement

| Device | Quantity | Purpose | Remark |
|:---:|:---:|:---:|:---:|
| Live Workstation host | One set | Install MeshExpert suite and establish Live Workstation | Required |
| Live Rig | One set | Synthesize the 3D hologrms| Required |
| HoloLens | At least one set | Debug and release your mix-reality apps | Required |
| Surface | Optional | Debug and release UWP apps | Optional |
| IPhone/IPad | Optional | Debug and release iOS virtual-reality apps | Optional |
| Android | Optional | Debug and release Android apps | Optional |

Live Workstation can directly, without MeshExpert Suite, serve as the development environment for the host. It’s recommended to use high-performance desktop host and the basic hardware requirements are as follows:

| Item | Requirements |
|:---:|:---|
| Cpu | Intel i5/i7 Quad, AMD Ryzen 1600 or higher |
| Memory | 8GB+ |
| Hard disk space | 100GB+; SSD recommended |

As for Live RIG hardware configuration and installation configuration, please refer to [RIG Installation in Usage Guide for ME Live!](https://github.com/DataMesh-OpenSource/MeshExpert-Live/wiki/Getting-Started#install-the-rig)

The required devices (HoloLens, Surface, IPhone/IPad and Android Phone) and its quantity are determined by your needs, but it is recommended to prepare a Hololens for the purpose of debugging.

### Software Requirement

ME-Live! Development environment can be directly set up on Live Workstation host so that you can easily debug your app using MeshExpert suite.

#### Supported operating systems

ME-Live! supports only Windows 10 now. The detailed requirement is as follows:

| Operating system | Version |
|:---:|:---:|
| Windows 10 Professional | 64-bit, version 1607 or later |
| Windows 10 Enterprise | 64-bit, version 1607 or later |
| Windows 10 Education | 64-bit, version 1607 or later |

#### Unity

Please use Unity 5.5 or later to develop your apps. (Unity 5.5.1 recommended).

> You can download the Unity [here](https://unity3d.com/get-unity/download/archive). For detailed installation and usage of Unity, check out [Unity Documentation](https://docs.unity3d.com/Manual/index.html).

#### Visual Studio 2015 V3

What you'll need is Visual Studio 2015 Community V3 or later. Check out [Windows Dev Center](https://developer.microsoft.com/en-us/windows/mixed-reality/install_the_tools#immersive_headset_development_.28minimum.29) for details.

> Making sure you have the latest Windows 10 SDK installed. Otherwise you cannot use the HoloLens to debug your app.

#### METoolkit

The METoolkit is a Unity plug-in that integrates the MeshExpert API and various functional modules. It can help you easily develop MeshExpert-based HoloLens application.

You will find the METoolkit package, which can be imported into your Unity project, in MeshExpert suite.

## App Development with METoolkit

### METoolkit Overview

METoolkit is an ME-DataMix (MeshExpert: DataMix - MR Data Integration Platform) client development toolkit. It provides a growing range of function modules and SDK to help developers develop AR apps based on Hololens and integrate with ME-HoloServer.

METoolkit is also a development engine based on Unity 3D platform. Relying on powerful features of Unity3D, METoolkit is able to run on different devices or platforms such as HoloLens, Surface, iOS device, Android device, and PC.

> Platform related features, such as spatial anchors, gesture recognition, may be unavailable on some platforms. Please read the [METoolkit Features](https://github.com/DataMesh-OpenSource/MeshExpert-Live/wiki/Developer-Guide#metoolkit-features) for details.

### METoolkit Features

1. MEHoloSDK: providing a set of APIs used to work with ME-HoloServer, check out [MEHoloSDK documentation](https://github.com/DataMesh-OpenSource/MeshExpert-Live/wiki/METoolkit-Developer-Manual#meholosdk-documentation).
2. ARModule: various function modules for AR development, including:
    + MultiInput: MultiInput module provides a set of input methods, such as a keyboard, mouse, touch screen and spatial gesture.
    + Speech: Speech input module (HoloLens only).
    + Cursor: AR/VR cursor.
    + BlockMenu: Block menu module can be used to make various menus, especially suitable for AR/VR environment.
    + Anchor：Space location module can be used to set up one or more spatial anchors and sharing its location using ME-HoloServer (HoloLens only).
    + Capture&Share: Take a picture or make a video and share through ME-HoloServer (HoloLens only).
    + Collaboration: Collaboration module uses ME-HoloServer for sending/receiving messages.
    + Live!: Provides a control panel and relevant functions so that developers can easily migrate the older AR application to Live！.
    + Utility: Provides a series of utilities.

### METoolkit Structure

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/4099195/26622530/4e16db64-461d-11e7-8203-f25b5b631179.png" width="500">
<p align="center"><em>METoolkit Structure</em></p>
</p>

### Development Project Setting

#### General Setting

1. Camera is set as Solid Color with its color 0,0,0
2. Camera position is set to be 0,0,0
3. Open `Edit` -> `Project Setting` -> `Quality Panel`, subsequently choose all Levels and close `V Sync Count` of each level.

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/4099195/26622678/c8717432-461d-11e7-81a0-1d61b2f61c51.png" width="333">
<img src="https://cloud.githubusercontent.com/assets/4099195/26622679/cbbffb2c-461d-11e7-92cb-e9d145c5ed43.png"
width="500">
<p align="center"><em>General Setting</em></p>
</p>

#### PC Standalone Setting

1. Choose `Player Setting` in `Build Settings` and open PC Mac & Linux Standalone.
2. Open `Other Setting` and change `API Compatibility level` to `.Net 2.0` under Optimization(do not choose Net 2.0 Subset!)

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/4099195/26622845/55ac8e2c-461e-11e7-922f-51a7effea618.png" width="500">
<p align="center"><em>PC Standalone Setting</em></p>
</p>

#### Windows Stroe Setting

1. Switch to WindowsStore in `Build Settings`
    + Choose Universal 10 in `SDK`
    + Choose Hololens in `Target` (for different platforms)
    + Choose D3D in `UWP Build Type`
    + Choose Build And Run on
    + Make "Unity C# Projects" option checked. (Be sure to check Unity C# Projects)

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/4099195/26623025/e7518f08-461e-11e7-8a83-1bc7a6ecb436.png" width="500">
<p align="center"><em>Windows Store Setting</em></p>
</p>

2. Open `Player Setting` and choose Windows Store.
3. Choose VR Support in `Other Setting` and have HoloLens checked.

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/4099195/26623099/346c882e-461f-11e7-9a13-a2966c2f6c5f.png" width="500">
<p align="center"><em>Windows Store Setting</em></p>
</p>

4. Choose Capabilities in `Publishing Settings` (according to need)

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/4099195/26623115/45686fd0-461f-11e7-854d-fe1b04b67ce4.png" width="500">
<p align="center"><em>Windows Store Setting</em></p>
</p>

### Start Using METoolkit

We will use METoolkit to build a simple app so that you can preliminarily know about the core function of Mesh Expert.

#### Prepare

+ Ensure Mesh Expert has been installed in the host and its relevant services have been started.
+ Set up Unity Project and set the scenes according to the requirements of HoloLens (refer to Holograms 101E Document)
+ Create an object in the scene and set its position as (0, 0, 5)
+ Import METoolkit into this Unity Project
+ Enter DataMesh/ARModule/Entrence/ Catalog and drag MEHoloEntrance that has been made in advance into Unity Scene.
+ Choose MEHoloEntrance in the scene and click “Create All MEHolo Module” Button on Inspector Panel.

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/4099195/26623711/28df32c0-4621-11e7-9c58-41c132bb1ca7.png" width="500">
<p align="center"><em>Create all MEHolo Module</em></p>
</p>

#### Coding

+ Add an object in the scene and name it as “App”
+ Add a script on the object and name it as “GettingStartedSample.cs”
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

+ Click object `App' in the scene and check its Inspector Panel.
+ Drag object 'Cube' in the scene to Cube Property on Panel as demonstrated in the following picture:

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/4099195/26623909/d198c5f2-4621-11e7-92c8-6594245976af.png" width="500">
<p align="center"><em>Object Property Setting</em></p>
</p>

#### Runtime Tests

+ Deploy the app to Hololens (check out [Microsoft Doc](https://docs.microsoft.com/en-us/hololens/hololens-install-apps))
+ Check if the HoloLens and the machine on which MeshExpert has been installed are in the same LAN environment.
+ Check if MeshExpert Server is running.
+ Launch the app on HoloLens. You will see a cube in front of your eyes.
+ Launch the app in Unity and then move or revolve the cube in Scene.

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/4099195/26624011/29ee5596-4622-11e7-95dc-afedabdd64fc.png" width="300">
<p align="center"><em>Cube</em></p>
</p>

+ Check the cube in Hololens and you will see the cube, in Unity, is moving synchronously.
