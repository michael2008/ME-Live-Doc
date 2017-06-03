## Overview

ME-Live! includes a complete set of hardwares, supporting softwares and apps. This guide will firstly give you the detailed specifications of hardware devices and their installation instructions; then it will introduce you how to use the system, including license installation and management, management of HoloLens device and app installation and management; lastly it will show some built-in demo apps.

## System Structure

ME-Live! is made up of two parts:

* **Live Rig**: a set of movable video device with a function of getting  video and location information of the real world.
* **Live WorkStation**: a high performance graphic workstation used for running holographic program and synthesizing real-time holographic video.

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/17921380/26622840/4dfc5ee6-461e-11e7-9ee2-215810049b79.png" width="500">
<p align="center"><em>System Structure</em></p>
</p>

## How It Works

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/17921380/26623110/4165487c-461f-11e7-8182-a06471b19726.png" width="500">
</p>

ME-Live! contains two mains parts, collaboration and live streaming. The collaboration within multiple devices which is achieved by delivering messages between these devices through HoloServer, makes real-time synchronization of scenes on these devices a reality.  Through camera shooting and collecting real-life scenes as well as getting the mapping of spatial position by HoloLens on the tripod at the same time, live streaming of scenes can be achieved as long as scenes and mapping are input to Live Controller in Workstation to carry out real-time 3D synthesis and then output onto screens through HDMI interface.

## RIG Installation

### Function

Rig is used for obtaining the real-world images and location information and further delivering them to Workstation in order to carry out real-time synthesis.

### Composition

ME-Live! Rig is constituted of the following main components:
* Digital camera/vidicon
* HoloLens
* Tripod
* Accessories for fixing

> Note: HoloLens here is responsible for providing site position information. You can replace it with other devices which also can provide position information if you want. Besides, If you don't need real-time synchronization of site position information, such as fixing the camera stand, you can completely leave HoloLens alone.

### Assembly

Assembly is aimed to fixing the complete set of device firmly, so as to reduce unstable factors during usage, such as shaking.
Ways of assembly and connection depend on the site requirements and devices you choose. If you want to choose some non-recommended devices, you should know how to connect them together.

|         item          | Function                                 | specification                       |
| :-------------------: | :--------------------------------------- | :---------------------------------- |
|  **HoloLens stand**   | Fix HoloLens firmly                      | Aluminium stand offered by DataMesh |
|  **Digital camera**   | Hot shoe interface for the the convenience of connecting HoloLens | Sony ICLE-6500 + EPZ 16-50          |
|    **Tripod/head**    | Support camera and HoloLens firmly       |                                     |
| **Other accessories** | Camera can connect to HoloLens through hot shoe interface | Screws for hot shoe switch          |


The assembly process of Rig Suite is depicted in the picture below and steps are as follows:
1. Fix HoloLens on the stand which is specifically designed for HoloLens.
2. Install fixed module of hot shoe at the bottom of the stand.
3. Place tripod and fix digital camera on the head of tripod.
4. Fix hot shoe connector on the hot shoe of the camera.
5. Connect fixed module of hot shoe to the connector and screw it up.

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/17921380/26623976/0ef5370a-4622-11e7-8cdd-0e59c8ceebee.png" width="160">
<p align="center"><em>RIG Assembly Diagram</em></p>
</p>


### Installation of Relevant Rig Software

A special app need to be installed on HoloLens in order to send necessary messages to Workstation. This program is generally used as it can be a match for any ME-Live! Workstation app developed by METoolkit. You can find the app from MeshExpert suite or download the corresponding version from our website.

You can install the app by using MeshExpert manager.

> Note: Please confirm whether the app version is a match for the version of METoolkit in use.

## Workstation Installation

### Hardware Requirements

To meet the need of 3D synthesis and recording of ME-Live!, Workstation is required to be capable of certain demanding calculations. The MeshExpert Suite offered by DataMesh is preferred.

If you need to assemble Workstation by yourselves, please refer to the following recommended hardware specifications.

|         item         | specification                            |                  remark                  |
| :------------------: | :--------------------------------------- | :--------------------------------------: |
|       **CPU**        | Intel Skylake 6700k or above AMD Ryzen 1700X or above |                                          |
|       **GPU**        | Nvidia GeForce GTX 1070 or above         | 1. GPU is required to have x264API code in support of NVENC. Visit https://developer.nvidia.com/video-encode-decode-gpu-support-matrix#Encoder and check the GPU list supported. 2. GTX1070 single cassette is in support of 1080P video transcoding with eight-time rate. 3. AMD video card is not supported at present. |
|    **Mainboard**     | M.2 SSD or PCI-E SSD supported           |                                          |
|      **Memory**      | 16GB two-channel  DDR4 or above          |                                          |
|    **Hard disk**     | 500GB M.2 SSD or PCIE SSD                | SAMSUNG 850 EVO 500G M.2 SSD **recommended**. |
| **Operating system** | Windows 10 64bit                         | 1. only 64-digit system installation supported. 2. Early Windows versions, such as Windows 7/8 and Server, are not supported at present. |

### Assembly Steps

Workstation access steps are as follows:

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/17921380/26624534/bf87b4ac-4623-11e7-9001-07d93508f5bf.png" width="500">
<p align="center"><em>Workstation Connection Diagram</em></p>
</p>

1. Connect output interface of HDMI of the camera to input interface of HDMI of Workstation's video card by using the HDMI connecting wire (Micro HDMI - HDMI).
2. Connect Micro USB interface to USB3.0 interface of Workstation (optional for the convenience of USB debugging and charging) by using USB wire（Micro USB - USB）.
3. Connect Lan interface of Workstation to that of Router by using netting wire.
4. Connect output interface of HDMI of Workstation's video card to screen on which pictures are required to be displayed by using HDMI connecting wire.（HDMI - HDMI）
5. Add Router's Wi-Fi to HoloLens.

### Usage Guide for MeshExpert Installer

Installation steps are as follows:
1. Open MeshExpert Installer.exe and install according to guide.  If an old version has ever been installed, please unload it.
2. Restart the system or open Start MeshExpert in DataMesh Catalog on Start Menu to restart service.

After installation, DataMesh Catalog will be produced on Start Menu, including relevant operations on Re start and Stop service as well as some demo programs. Click Start Service of MeshExpert, wait for a while and open the browser, input localhost, then click Enter.  If there is a log-in page, you succeed to start service.

Stop and Restart service can be achieved by respectively clicking Stop MeshExpert and Restart MeshExpert in DataMesh Catalog.

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/17921380/26624704/45838afe-4624-11e7-8132-aa1a492c7060.png" </p>

The GPU compression is preferred when performing video compression operation in the program. If the machine does not have video card or cannot use GPU for certain reasons, we can conduct CPU video compression by changing configuration. You can change it by following following instructions: enter Installation directory (`"C:\Program Files\MeshExpert"` by default), and then enter `"HoloServer\hlstrans\configs"`,

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/17921380/26624857/cecb141c-4624-11e7-8d3d-9d6562d508c1.png" width="500">
</p>

Open config.toml Document, find `use_gpu` option, and change its value to be false.

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/17921380/26624884/e4f40b9a-4624-11e7-8880-a1d926487f33.png" width="500">
</p>


## License Management

### Adding

Visit `http://localhost/admin` and you will enter the interface of Adding License as follows. Choose your license document and upload it so as to activate. If you don't have a valid license right now, please contact `service@datamesh.com`.

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/17921380/26624939/1bf7ebde-4625-11e7-9041-33c7c065e4bc.png" width="500">
</p>

After adding, click License in the left column after the page forwarded, then you will see your License information as depicted in the following picture, and you can manage your License here, such as update, delete and renewal online.

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/17921380/26624973/3ff8609a-4625-11e7-82ac-d4742a526059.png" width="500">
</p>

### Managing

You can manage your License on License interface, including update, delete and online subscription renewal.

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/17921380/26625004/5c8f8526-4625-11e7-84bc-8b5eb88b5e47.png" width="500">
</p>

If your original License has been expired or you have already bought a new License, you can update it through License Update. You can delete your current License through delete.

## Device Management

You can manage HoloLens, app release and installation and License functions through Management which is comprised of some Windows Device Portal API

### Adding
Device management part provides operations of add, delete and management on HoloLens and other devices. Specific operations are as follows:

On the condition that legal License is acquired and added, you shall visit `http://<YOUR_SERVER_IP>/admin` and you will see a page similar to the following one:

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/17921380/26625097/aa48be18-4625-11e7-80fb-490162210a9a.png" width="500">
</p>

Click Add device Button, you will see the following page:

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/17921380/26625128/c4b2f174-4625-11e7-8bd3-f4af560e5bff.png" width="500">
</p>

On the condition that your HoloLens and Server are in the same network segment (usually connected to the same Router) and can communicate with each other, you shall fill in IP address of your HoloLens and click Next Button. If it is your first time to add the device, you will see the following page and PIN code in HoloLens at the same time.

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/17921380/26625182/e5c488fa-4625-11e7-854e-64383e5d8137.png" width="500">
</p>

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/17921380/26625232/108c82fe-4626-11e7-9e56-6d46cddd3e4a.png" width="500">
</p>

Input PIN and user name and password to be set up as well as confirm the password. Then click Pair.

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/17921380/26625333/6250a142-4626-11e7-8ee0-79099789c836.png" width="500">
</p>

And conduct relevant operations on it.

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/17921380/26625405/9006a488-4626-11e7-8c8b-f8e9d73f3b6f.png" width="500">
</p>

If the device is not paired at first time, just input user name and password.

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/17921380/26625462/bfccb2ca-4626-11e7-825c-e431ea089f03.png" width="500">
</p>

If you forget the password, you can reset it by clicking Forget your account.

### Status Checking

Visit `http://localhost/admin`, click Device in the left and check the current status of device connected to Holo-Server. Possible status values are Online and Offline.

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/17921380/26625625/4a950c7c-4627-11e7-888c-03b4cb11c6b7.png" width="500">
</p>

### Removal

Click Delete to strip the device of occupation of license.

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/17921380/26625694/79e99eca-4627-11e7-9e85-877711462243.png" width="500">
</p>


## App Management

### Release
Visit `http://localhost/admin` and choose Application. Release apps that have been packaged in App Center for the convenience of managing and installing them in HoloLens.

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/17921380/26625837/ece6545e-4627-11e7-8299-d80eb9b3b4bc.png" width="500">
</p>

Click Add Application Button

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/17921380/26625902/1ace8724-4628-11e7-93bb-5c6a64709648.png" width="500">
</p>

Choose installation package and click Add Dependency to add attachment (if necessary), then click Go to release apps. After that, you can manage them, including deletion, installation, update to the specified devices.

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/17921380/26625932/3008d2f2-4628-11e7-911d-f59160d5896d.png" width="500">
</p>

Click Go to upload with the speed on display. Then wait for the status of return to upload and installation.

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/17921380/26626301/6402794a-4629-11e7-8c8d-78eff7451595.png" width="500">
</p>

After installation, uploaded apps can be displayed in Application

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/17921380/26626329/803147e0-4629-11e7-8d09-b8939ca356e7.png" width="500">
</p>

### Upgrade

On Application page, click Update which calls for uploading apps with the same name but not of the same version. The program will check it and change the version in Application.

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/17921380/26626578/3ba82c82-462a-11e7-93b9-c9e3cb67ac04.png" width="500"><
</p>

Update is in support of replacing apps with the same name.

### Delete

Click Delete to remove apps.

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/17921380/26627450/1d5bc4c0-462d-11e7-9465-2833590a4673.png" width="500">
</p>

### Install and uninstall

Click More to start, stop, restart, install, uninstall, upgrade sand change configuration.

* Start
  <p align="center">
  <img src="https://cloud.githubusercontent.com/assets/17921380/26627563/77ef3778-462d-11e7-9c27-b881caa7fddd.png" width="500">
  </p>

* Stop
  <p align="center">
  <img src="https://cloud.githubusercontent.com/assets/17921380/26627577/89a66f7c-462d-11e7-879d-e8d73ada8df6.png" width="500">
  </p>

* Restart
  <p align="center">
  <img src="https://cloud.githubusercontent.com/assets/17921380/26627658/c74de0f8-462d-11e7-8374-15d7f9c778d5.png" width="500">
  </p>

* Install
  When users choose app programs to be installed, the system will change parameters of configuration documents in installation packages after installation, such as `Rout\LocalAppData\ChengDu_1.2.1.0_x86__pzq3xp76mxafg\LocalState\config.ini`. Namely field values of `Server_Url`, `Share_Anchor_Url` are Ip numbers of the current Server.
  <p align="center">
  <img src="https://cloud.githubusercontent.com/assets/17921380/26627737/05251cac-462e-11e7-946d-a464e8f59816.png" width="500">
  </p>

* Uninstall
  <p align="center">
  <img src="https://cloud.githubusercontent.com/assets/17921380/26627737/05251cac-462e-11e7-946d-a464e8f59816.png" width="500">
  </p>

* Upgrade
  When the installed apps in holoLens calls for update, we shall click Update and update them to the latest versions in Application.
  <p align="center">
  <img src="https://cloud.githubusercontent.com/assets/17921380/26658751/d1a45e3a-469e-11e7-80c8-4da0764c278e.png" width="500">
  </p>

* Configuration
  If  the current Server Ip of users  changes, we shall click Configure to change the field value of Server_Url, Share_Anchor_Url.
  <p align="center">
  <img src="https://cloud.githubusercontent.com/assets/17921380/26658793/02051f24-469f-11e7-868f-d77ccb526029.png" width="500">
  </p>

## Uninstall

Find Uninstall in DataMesh Catalog on Start menu and click it to uninstall it. If you cannot find Uninstall on Start menu, please enter installation directory to find Uninstall.exe, and uninstall it by double click the Uninstall.exe.

> Note: Uninstall MeshExpert will result in removal of all data, including app data and License.  If these data are very important to you, please make sure that you already backed it up.


## Built-in Apps

### SolarSystemExplorer

We have installed a built-in app as an example for your reference.  In this example, we have achieved the most fundamental sharing and scene synchronization of spatial anchors.
We will introduce you the details about how to use this app in the following part:
Open SolarSystemExplorer App, you will see the whole solar system in front of your eyes:

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/17921380/26658886/9908243e-469f-11e7-9bc8-d9673bd59f0b.png" width="500">
</p>

Click a certain planet and you will be able to exclusively observe it:

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/17921380/26658907/b1ee84fc-469f-11e7-8574-3e7826376a77.png" width="500">
</p>


<p align="center">
<img src="https://cloud.githubusercontent.com/assets/17921380/26658925/c3ef140a-469f-11e7-872f-9f8266e83238.png" width="500">
</p>

You can revolve and scale the whole scene at any time. As long as you click and carry out Horizon (revolving) and Squareness (scaling), the most fundamental interaction will be achieved.

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/17921380/26658941/e06c5930-469f-11e7-901d-6177ec15f10a.png" width="500">
</p>

You can speak "Open Menu" to find the concealed menu so as to adjust and share World Anchor. The operation is divided into three parts "move WorldAnchor", "upload WorldAnchor" and "downloads WorldAnchor".  which is to acquire and synchronize information from Server; "upload WorldAnchor" is to upload to Server with world anchors in the current HoloLens as criteria. "Move WorldAnchor" is to carry out upload to synchronize adjusted scenes to Server after adjusting the position of scenes at present.

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/17921380/26658969/f8634742-469f-11e7-88d9-2a8726b6d73b.png" width="500">
</p>

Steps of moving spatial anchors are as follows:

* Enter Anchor adjustment model by "Change Anchor" in the concealed menu. Then you will see the whole galaxy with an enclosed box outside and a blue crystalline is displayed on the benchmark position to demonstrate  position of the galaxy Anchor.

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/17921380/26658986/12510950-46a0-11e7-8ec7-9a0d7127d59f.png" width="500">
</p>

* Fix your eyes on enclosed box and Air Tap, The object's enclosed box will turn color and glitter and three Square Buttons will be displayed above the core crystalline at the same time.

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/17921380/26658996/2cc15f38-46a0-11e7-85e3-bc526203e40e.png" width="500">
</p>

* Fix your eyes on "Gaze" Button and Air Tap, you will enter the eyesight movement model and the surrounding environmental net will be displayed in HoloLens. The whole object will move as users move their eyes and stay in the environmental net position currently gazed at.

    - If there is no environmental net in the currently-gazed position, then the object will float in the direction of eyes three meters away.
    - Air Tap again and you will exit the eyesight movement model. Then re-choose the status of the object.

* Gaze at "Move" Button in the left and Air Tap, you will enter the manual movement model and movement sign will be displayed on crystalline.
  > Note: When using HoloLens, please operate the object in a manner of clicking and moving together and adjust the position of the object in the direction of three axis.

* Gaze at Rotate"Button and Air Tap, you will enter the manual revolve model and the revolve sign will be displayed above the crystalline.
  > Note: When using HoloLens, please operate the object in a manner of clicking and moving together and revolve the object in the direction of three axis.

After adjusting WorldAnchor, Air Tap at the blank area outside the enclosed box, you will exit the Anchor edit model and enclosed box and crystalline will disappear. At the same time, the position of the galaxy will be stored and the galaxy will return to the position if spatial recognition is commensurate after starting HoloLens.