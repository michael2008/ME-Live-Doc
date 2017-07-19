## Overview

ME-Live! includes a complete set of hardware, support software, and application software. This guide will first provide you the detailed description of hardware specifications and their assembly methods; then it will introduce you how to use the system, including license installation and management, management of HoloLens device and app installation and management; lastly, it will show some built-in demo apps.

## System Structure

ME-Live! is made up of two parts:

* **Live Rig**: a set of movable video device with the function of getting video and location information of the real world.
* **Live WorkStation**: a high performance graphics workstation used for running holographic program and synthesizing real-time holographic video.

<p align="center">
<img src="https://user-images.githubusercontent.com/7636848/26872303-9d9425d0-4ba8-11e7-8e90-80e7389a41e2.png" width="500">
<p align="center"><em>System Structure</em></p>
</p>

## How It Works

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/17921380/26623110/4165487c-461f-11e7-8182-a06471b19726.png" width="500">
</p>

ME-Live! contains two main parts, collaboration, and live streaming. The collaboration within multiple devices which is achieved by delivering messages between these devices through HoloServer makes real-time synchronization of scenes on these devices a reality.  Through camera shooting and capturing real scenes, while getting the mapping of spatial position by HoloLens on the tripod, live streaming is achieved by putting them into Live Controller in Workstation to carry out real-time 3D synthesis and then output onto screens through HDMI interface.

## RIG Installation

The Rig is used for obtaining the real-world images and location information and further delivering them to the workstation in order to carry out real-time synthesis.

ME-Live! Rig consists of the following **main components**:

* Digital camera/video camera
* HoloLens
* Tripod
* Accessories for fixing

> Note: HoloLens here is responsible for providing location information. You can replace it with other devices which also can provide position information. Besides, HoloLens can be removed if you don't need real-time synchronization of location information, such as fixing the camera stand.

### Rig Assembly

The purpose of the assembly is to securely secure the complete set of equipment together to minimize the effects of unstable factors such as shaking.
Depending on the requirements of the working site and the choice of equipment, the ways of assembly and connection may vary. If you want to use non-recommended equipment, please make sure that you know how to connect them together.
Below is a typical example of the assembly.

|         item          | Function                                 | specification                       |
| :-------------------: | :--------------------------------------- | :---------------------------------- |
|  **HoloLens stand**   | Fix HoloLens firmly                      | Aluminium stand offered by DataMesh |
|  **Digital camera**   | Hot shoe interface for the the convenience of connecting HoloLens | Sony ICLE-6500 + EPZ 16-50          |
|    **Tripod/head**    | Support camera and HoloLens firmly       |                                     |
| **Other accessories** | Camera can connect to HoloLens through hot shoe interface | Screws for hot shoe switch          |


The assembly processes of Rig Suite depicted in the picture below, and the steps are as follows:

1. Fix HoloLens on the dedicated **Aluminum HoloLens Bracket**.
2. Add the **Hotshoe Adapter** to the HoloLens mount in Step 1 (to later in Step 5, connect the HoloLens mount to the camera).
3. Connect the **Camera** to the **Tripod**. 
4. Fix the **Hotshoe Fastener** to the **Camera**.
5. Finally, connect the **HoloLens Mount** and the **Camera** by connecting the **Hotshoe Adapter** and the  **Hotshoe Fastener**.

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/17921380/26623976/0ef5370a-4622-11e7-8cdd-0e59c8ceebee.png" width="160">
<p align="center"><em>RIG Assembly Diagram</em></p>
</p>


## Workstation Installation

### Hardware Requirements

The workstation requires a certain amount of computing power, which could be satisfied by hardware sets of the given specifications, to meet the demands of ME-Live!. There would also be some restrictions regarding the hardware and software choices.
Below is a list of recommended requirements for the workstation:

|         Item         |              Specification               | Remark                                   |
| :------------------: | :--------------------------------------: | :--------------------------------------- |
|       **CPU**        | Intel Skylake 6700K or above OR AMD Ryzen 1700X or above |                                          |
|       **GPU**        |     NVIDIA GeForce GTX 1070 or above     | <ul><li>GPU needs to support NVENC (Hardware-Accelerated Video Encoding) encoding APIs for H.264.</li><li>AMD GPUs currently are not supported.</li></ul> |
|    **Mainboard**     |       Support M.2 SSD or PCI-E SSD       |                                          |
|      **Memory**      |     16GB dual-channel DDR4 or above      |                                          |
|    **Hard disk**     |        500GB M.2 SSD or PCIE SSD         | <ul><li>Recommend SAMSUNG 850 EVO 500G M.2 SSD.</li></ul> |
| **Operating system** |        Windows 10 64bit or above         | <ul><li>Only 64bit system is supported.</li><li>Windows 7/8 and Windows Server editions are not supported.</li></ul> |

> Note 1: Visit [https://developer.nvidia.com/video-encode-decode-gpu-support-matrix#Encoder](https://developer.nvidia.com/video-encode-decode-gpu-support-matrix#Encoder) to see the NVIDIA GPU support matrix.

> Note 2: Single common GTX1070 card could accelerate the transcoding process up to 8x, which roughly means the system can process an 8-minutes recording in about 1 minute. The use of cards of lower GPU computation power is also possible but would result in slower video processing.

### Assembly Steps

Workstation access steps are as follows:

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/17921380/26624534/bf87b4ac-4623-11e7-9001-07d93508f5bf.png" width="500">
<p align="center"><em>Workstation Connection Diagram</em></p>
</p>

1. Connect the camera's **HDMI Output Port** to the **Input Port ** of the capture card of the workstation, with a **HDMI to Mini-HDMI cable**.
2. Connect the **Micro USB port** of HoloLens to one of the USB3.0 port on the workstation with a **Micro USB to USB cable**. (This is for the convenience of USB debugging and charging of HoloLens, and thus is optional) .
3. Connect the workstation to the **LAN Port** of the **Wireless Router** using a Lan cable.
4. Use an **HDMI to HDMI cable** to attach the **Output Port** of the capture card of the workstation to an external display or any other campatible screens.
5. Let the HoloLens join the local wireless network and make sure the HoloLens and the workstation are in the same vlan.


### Configurations

#### Network Configurations

1. Get the Rig and Workstation ready first.
2. Make sure a dedicated WIFI router, 802.11ac perferred, with wired connection has connected to the Rig. Router IP should be `192.168.8.1`, DHCP range set to `192.168.8.100~249`. Internet link is not necessary.
3. IP address of the Workstation should be set to `192.168.8.250`. We need to run both of the soft  Suite and the Demo app on it.

> Note: If you have other devices to collaborate, e.g. a Surface Pro as a controller, it needs to join the same WIFI network with wireless connnection, which would get an IP from pool `192.168.8.100~249` automatically. Besides, please make sure there's not a lot of WIFI devices around when you start to move the rig. WiFi latency impacts the performance.

#### Environment Preparation

1. Connect everything to the WIFI router. Make sure they all have `192.168.8.x` IP address, and the workstation has the fixed IP `192.168.8.250`. This is very important since we fixed the network settings to ensure there's no surprise.
2. Install the `SpectatorView Test App` onto your spectator view HoloLens on the Rig. You can download the `SpectatorView Test App` from [here]().

### MeshExpert Center

#### Dashboard Panel

<p align="center">
<img src="https://user-images.githubusercontent.com/17921380/28303167-37645852-6bc4-11e7-9781-a2a81ec1ad2e.png" width=500>
<p align="center"><em>Dashboard Panel</em></p>
</p>

Dashboard panel provides the following main functionalities:
1. Manage the MeshExpert Server, such as start, shutdown and restart
2. Check and display the status, the version and the connectivity of the MeshExpert Server
3. Alert error message when error occurs

> Note 1: You should make sure that the MeshExpert Server is started if you want to do anything further

> Note 2: You can manually check the MeshExpert Server's status by clicking the `Recheck` icon

> Note 3: You may need to restart or reinstall the MeshExpert Server when an error occurrs. Please follow the troubleshooting instructions or contact us if you any further question.

<p align="center">
<img src="https://user-images.githubusercontent.com/17921380/28305410-2621fb80-6bce-11e7-9c0b-1626cf8ede6f.png" width=500>
<p align="center"><em>Dashborad Error Alert</em></p>
</p>

#### Devices Panel
<p align="center">
<img src="https://user-images.githubusercontent.com/17921380/28309508-29776082-6bdc-11e7-88bd-79c3f458d764.png" width=500>
<p align="center"><em>Devices Panel</em></p>
</p>

Devices Panel provides the following main functionalities:
1. Add HoloLens
2. upload HoloLens applications to HoloLens
3. Install HoloLens applications on HoloLens
4. Manage the applications installed through this Device Panel, such as start, stop, restart and removal
5. Show basic infos of the applications which are installed through this Device Panel and also running currently

You can add HoloLens in the `Add HoloLens` section. Before you start the adding operation, you should make sure that the HoloLens the MeshExpert Server are in the same network segment (usually connected to same router) and can communicate with each other.

#### My Apps Panel
In My Apps Panel, you can upload your applications to HoloLens and view basic infos of the applications which are already uploaded.
<p align="center">
<img src="https://user-images.githubusercontent.com/17921380/28312356-7335e794-6be5-11e7-804e-de84d065976c.png" width=500>
<p align="center"><em>My Apps Panel</em></p>
</p>

#### Account Panel
In Account Panel, you can view and manage your account and license infos here.
<p align="center">
<img src="https://user-images.githubusercontent.com/17921380/28312295-3f546626-6be5-11e7-8278-f212d9272dae.png" width=500>
<p align="center"><em>Account Panel</em></p>
</p>

### Usage Guide for MeshExpert Suite

Installation steps are as follows:

1. Find the MeshExpert Installer.exe, double click it, and proceed according to the installation guide.  If you have installed an older version, please uninstall the old version first.

2. Restart the system or open Start MeshExpert under DataMesh entry on the Start Menu to start the service.

After the installation is complete, the DataMesh entry will be generated on the Start menu bar, which will include the service management operations, such as start and stop, and some demo programs. Click Start MeshExpert start the service, wait a moment, open the browser, enter localhost and then enter. If there is a sign-in page, the service starts successfully.

 You can click Stop MeshExpert and Restart MeshExpert under the DataMesh entry on the Start menu bar to stop or restart service, respectively.

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/17921380/26624704/45838afe-4624-11e7-8132-aa1a492c7060.png" </p>

The GPU compression is preferred when performing video compression operations in the program. If the machine does not have video card or cannot use GPU for some reasons, you can use CPU for video compression by changing configuration. Instructions: go to the installation directory (`"C:\Program Files\MeshExpert"` by default), and then enter `"HoloServer\hlstrans\configs"`,

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/17921380/26624857/cecb141c-4624-11e7-8d3d-9d6562d508c1.png" width="500">
</p>

Open config.toml file, find `use_gpu` option, and change its value to false.

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/17921380/26624884/e4f40b9a-4624-11e7-8880-a1d926487f33.png" width="500">
</p>

## Built-in Apps

### SolarSystemExplorer

We have installed a built-in app as a sample for your reference. In this example, we implemented the most basic space anchor sharing and scene synchronization.

Below we will give you a detailed description of how to use this application.

Open the SolarSystemExplorer application, you will see the whole solar system surfaced in front of you.

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/17921380/26658886/9908243e-469f-11e7-9bc8-d9673bd59f0b.png" width="500">
</p>

Click on a specific planet, and you will be able to explore it exclusively.

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/17921380/26658907/b1ee84fc-469f-11e7-8574-3e7826376a77.png" width="500">
</p>


<p align="center">
<img src="https://cloud.githubusercontent.com/assets/17921380/26658925/c3ef140a-469f-11e7-872f-9f8266e83238.png" width="500">
</p>

You can rotate and zoom in on the entire scene at any time, just use gestures to tap and level (rotate), vertical (zoom) drag to achieve the most basic interactions. All of these operations will be synced in ME-Live! in real-time to produce a consistent scene.

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/17921380/26658941/e06c5930-469f-11e7-901d-6177ec15f10a.png" width="500">
</p>

You can use the voice "Open Menu" to call out the hidden menu, to adjust and share the space anchor. The operation is divided into three categories: **Change Anchor**, **Upload Anchor** and **Download Anchor**. Download Anchor means obtaining latest space anchor information for the Server and synchronizing with it; Upload Anchor means uploading the current HoloLens's space anchor to the Server;  Change Anchor means adjusting the current scene's location and then uploading it to the Server to synchronize after the adjusting completes.

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/17921380/26658969/f8634742-469f-11e7-88d9-2a8726b6d73b.png" width="500">
</p>

Steps of Change Anchor are as follows:

* Through air-tapping the **Change Anchor** in the hidden menu, you'll enter the anchor adjustment mode, where you can see a bounding box outside the entire galaxy and a blue crystal at the reference position showing the anchor of the galaxy.

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/17921380/26658986/12510950-46a0-11e7-8ec7-9a0d7127d59f.png" width="500">
</p>

* Eyes stare at the box, air-tap, and the object of the bounding box will change and flash indicating that it's being selected, while the top of the core crystal will appear three square buttons.

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/17921380/26658996/2cc15f38-46a0-11e7-85e3-bc526203e40e.png" width="500">
</p>

* Watch the middle of the "Gaze" button and air-tap, you'll enter the sight movement mode, in which the HoloLens will display the surrounding environment's spatial mesh, and the entire object will move with the user's gaze and stay at the environment spatial mesh on which you gaze.

    - If there is not environmental spatial mesh in the currently-gazed position, then the object will float in the direction of eyes three meters away.
    - Air-tap again and you will exit the sight movement mode. Then re-choose the status of the object.

* Gaze at Move button in the left and air-tap, and you will enter the manual movement mode and the crystal will appear on the mobile logo.
  > Note: When using HoloLens, use the "press the finger and move" to manipulate the object, you can adjust the position of the object in three axes.

* Gaze at Rotate button and air-tap, and you'll enter the manual rotation mode and then the crystal appears back to the rotation mark.
  > Note: When using HoloLens, use the "press the finger and move" to manipulate the object and you can rotate object in three axes.

After completing the adjustment of the space anchor, air-tapping at the blank area outside of the bounding box will exit the anchor edit mode, the outer circumference and the crystal will disappear, and the location of the galaxy will be stored. When you open the program in HoloLens next time, the galaxy will return to this position.
