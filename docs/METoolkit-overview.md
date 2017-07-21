### METoolkit Overview

METoolkit is an ME-DataMix (MeshExpert: DataMix - MR Data Integration Platform) client development toolkit that provides a growing range of functional modules and SDK to help developers develop AR apps based on HoloLens and ME-HoloServer.

METoolkit is also a development engine based on Unity 3D platform. Relying on powerful features of Unity3D, METoolkit is able to run on different devices or platforms, including HoloLens, Surface, iOS, Android, and PC.

> **Note:** Platform related features, such as spatial anchors, gesture recognition, may be unavailable on some platforms. Please read the [METoolkit Features](#metoolkit-features) for details.

### METoolkit Features

1. **MEHoloSDK**: providing a set of APIs used to work with ME-HoloServer, check out [MEHoloSDK documentation][MEHoloSDK_Docs].

2. **ARModule**: a collection of functional modules for AR development, including:

   - **_MultiInput_**: Giving you the ability to not only use keyboard, mouse and touch screen as input device, but also take advantages of spatial gesture recognition.

   - **_Speech_**: Speech perception. (`HoloLens only`)

   - **_UI_**: Indicating 3 part: cursor, menu, and List.

     - **_Cursor_**: showing the cursor in AR/VR application.
     - **_Block Menu_**: build a metro style Menu Control that provides a set of useful methods.
     - **_Block List_**: Build a metro style List Control with functions such as page up, page down, click, and so on.

   - **_Anchor_**：Spatial positioning module that can be used to set up one or more spatial anchors and sharing these location information using ME-HoloServer. It will work on HoloLens, and can simulate anchor on PC.

   - **_Capture&Share_**: Taking a picture or recording a video, which can be shared via ME-HoloServer. (`HoloLens only`)

   - **_Collaboration_**: Sending/receiving messages via ME-HoloServer.

     > **Note:** Basically, you will create and initialize what are called `Rooms` in which  user can collaborate with others. 

   - **_Storage_**: Make specific asset by Unity, upload by Website, and download from Cloud in Runtime.

   - **_Live!_**: Providing a control panel and relevant functions so that you can easily migrate other AR application to Live!.

   - **_Utility_**: Providing a set of utilities, such as Configuration file.

### METoolkit Structure

<img src="https://user-images.githubusercontent.com/7381020/28001974-8bb2103c-6563-11e7-972e-1a81842cf746.jpg" width="600">
<p align="center"><em>METoolkit Structure</em></p>


### METoolkit Manual

- [Configure your project][Configure_your_project]
- [Integrated with your project][Integrated_with_your_project]
- [Write your first App][Write_your_first_App]
- [World Anchor Module][World_Anchor_Module]
- [Multi-Input Module][Multi-Input_Module]
- [Speech Module][Speech_Module]
- [UI Module][UI_Module]
- [Collaboration Module][Collaboration_Module]
- [Storage Module][Storage_Module]
- [Live Controller Module][Live_Controller_Module]
- [Utility: Config Files][Utility_Config_Files]

### MEHoloSDK Docs

- [MEHoloSDK Docs][MEHoloSDK_Docs]

### METoolkit Reference

- DataMesh.AR
  - MEHoloEntrance
- DataMesh.AR.Anchor
  - SceneAnchorController
  - AnchorDefinition
- DataMesh.AR.Interactive
  - MultiInputManager
  - XBoxControllerInputManager
  - SpeechManager
- DataMesh.AR.UI
  - UIManager
  - BlockMenuManager
    - BlockMenu
  - BlockListManager
    - BlockList
    - BlockListData
  - CursorController
- DataMesh.AR.Network
  - CollaborationManager
- DataMesh.AR.Storage
  - StorageManager
- DataMesh.AR.MRC
  - MixedRealityCapture
  - PhotoCapture
  - VideoCapture
- DataMesh.AR.spectatorView
  - LiveController
  - ILiveListener
  - IRecordNamerGenerator
- DataMesh.AR.Log
  - LogManager
- DataMesh.AR.Utility
  - AppConfig
  - TimeManager





[Configure_your_project]: toolkit/toolkit-man-configure-your-project.md
[Integrated_with_your_project]: toolkit/toolkit-man-integrated-METoolkit.md
[Write_your_first_App]: toolkit/toolkit-man-write-your-first-app.md
[World_Anchor_Module]: toolkit/toolkit-man-world-anchor-module.md
[Multi-Input_Module]: toolkit/toolkit-man-multi-input-module.md
[Speech_Module]: toolkit/toolkit-man-speech-module.md
[UI_Module]: toolkit/toolkit-man-ui-module.md
[Collaboration_Module]: toolkit/toolkit-man-collaboration-module.md
[Storage_Module]: toolkit/toolkit-man-storage-module.md
[Live_Controller_Module]: toolkit/toolkit-man-live-module.md
[Utility_Config_Files]: toolkit/toolkit-man-utility-config-file.md
[MEHoloSDK_Docs]: me-holo-sdk.md