### Development Project Setting

#### General Setting

1. Set Camera to Solid Color and background color to 0,0,0
2. Set the position of Camera to 0,0,0
3. Open `Edit` -> `Project Setting` -> `Quality`, subsequently check all Levels and close `V Sync Count` of each level.

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/4099195/26622678/c8717432-461d-11e7-81a0-1d61b2f61c51.png" width="300">

<img src="https://cloud.githubusercontent.com/assets/4099195/26622679/cbbffb2c-461d-11e7-92cb-e9d145c5ed43.png" width="400">
<p align="center"><em>General Settings</em></p>
</p>

#### PC Standalone Setting

1. Open `File` -> `Build Settings` -> `Player Settings` and then choose `PC, Mac & Linux`.

   + Set **Architecture** to **x86-64**

   <p align="center">

   <img src="https://user-images.githubusercontent.com/7381020/28236077-e7aa7156-694e-11e7-8923-cf1502c8be27.png" width="400">

   <p align="center"><em>PC Standalone Setting</em></p>
   </p>

2. Open `Other Setting` and change `API Compatibility level` to `.Net 4.6` in `Optimization`.


<p align="center">
<img src="https://user-images.githubusercontent.com/26785911/35387876-8248162c-020c-11e8-9ce8-29c858cd289e.jpg" width="400">
<p align="center"><em>PC Standalone Setting</em></p>
</p>

#### Windows Store Setting

1. Switch to `Windows Store` in `Build Settings`
    + Choose `Universal 10` in `SDK`

    + Choose `HoloLens` in `Target` 

      > **Note:** Choose the proper device if your application is targeted to other platform.

    + Choose `D3D` in `UWP Build Type`

    + Making sure that you have ``Unity C# Projects` checked.

    + Click `Build And Run`

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/4099195/26623025/e7518f08-461e-11e7-8a83-1bc7a6ecb436.png" width="400">
<p align="center"><em>Windows Store Setting</em></p>
</p>

2. Open `Other Setting` and check `Virtual Reality Supported`
3. Choose `Windows Holographic`

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/4099195/26623099/346c882e-461f-11e7-9a13-a2966c2f6c5f.png" width="600">
<p align="center"><em>Windows Store Setting</em></p>
</p>

4. Check options in `Capabilities` in `Publishing Settings` according to your needs

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/4099195/26623115/45686fd0-461f-11e7-854d-fe1b04b67ce4.png" width="300">
<p align="center"><em>Windows Store Setting</em></p>
</p>


