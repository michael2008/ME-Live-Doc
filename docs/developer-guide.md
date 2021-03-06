## Overview

This guide walks you through the process of building your one-stop app using MeshExpert Live!, which is composed of two main products, MeshExpert Center and METoolkit.
MeshExpert Center provides you with a way to use the following amazing features of MeshExpert Live!:

+ Uploading resources synchronously
+ Collaboration between multi-user and multi-device
+ Simplified application installation and management

METoolkit provides not only multiple APIs which could be used to communicate with MeshExpert, but also common modules. METoolkit will give you an idea of how things are working internally, which helps you to design and develop your own collaborated applications.

## Development Environment

The MeshExpert Live! development environment, which can be installed on a single computer (recommended), provides you a set of processes and tools used to help you create the product. Following are the prerequisites for installing MeshExpert Live! development environment.

### Hardware Requirement

|        Device         |     Quantity     |                 Purpose                  | Required |
| :-------------------: | :--------------: | :--------------------------------------: | :------: |
| Live Workstation host |     One set      | Install MeshExpert suite and establish Live Workstation |   Yes    |
|       Live Rig        |     One set      |        Synthesize the 3D holograms        |   Yes    |
|       HoloLens        | At least one set | Debug and release your mix-reality apps  |   Yes    |
|        Surface        |     Optional     |        Debug and release UWP apps        |    No    |
|      IPhone/IPad      |     Optional     | Debug and release iOS virtual-reality apps |    No    |
|        Android        |     Optional     |      Debug and release Android apps      |    No    |

Live Workstation can directly, without MeshExpert Center, serve as the development environment for the host. It’s recommended to use high-performance desktop host and the basic hardware requirements are as follows:

|      Item       | Requirements                             |
| :-------------: | :--------------------------------------- |
|       CPU       | Quad-core Intel i5/i7, AMD Ryzen 1600 or higher |
|     Memory      | 8GB+                                     |
| Hard disk space | 100GB+, SSD recommended                  |

The complete documentation for Live RIG hardware configuration and installation configuration is available at [RIG Installation in Usage Guide for MeshExpert Live!](user-guide.md#rig-installation)

> **Note:** The devices (Surface, iPhone/iPad and Android) and its quantity are determined by your needs.

### Software Requirement

MeshExpert Live! development environment can be directly set up on Live Workstation host so that you can easily debug your applications using MeshExpert Center.

#### Supported operating systems

MeshExpert Live! only supports Windows 10 now. The detailed requirement is as follows:

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

> **Note:** Make sure you have the latest Windows 10 SDK installed, otherwise you cannot use the HoloLens to debug your applications.



#### App development with METoolkit 

The METoolkit is a Unity plugin that provides a growing range of MeshExpert APIs and functional modules. It can help you develop MeshExpert-based HoloLens application easily and quickly.

You will find the METoolkit package, which can be imported into your Unity project, in MeshExpert Center.

For more information, please refer to [METoolkit Overview](METoolkit/METoolkit-overview.md)

