### Development Project Setting

#### General Setting

1. Set Camera to Solid Color and background color to 0,0,0
2. Set the position of Camera to 0,0,0
3. Open `Edit` -> `Project Setting` -> `Quality`, subsequently check all Levels and close `V Sync Count` of each level.

<p align="center">
<img src="https://user-images.githubusercontent.com/13318047/35611131-12a1f382-069f-11e8-8aa0-4adfa86f0175.png" width="240">

<img src="https://cloud.githubusercontent.com/assets/4099195/26622679/cbbffb2c-461d-11e7-92cb-e9d145c5ed43.png" width="400">
<p align="center"><em>General Settings</em></p>
</p>

#### PC Standalone Setting

1. Open `File` -> `Build Settings` -> `Player Settings` and then choose `PC, Mac & Linux`.

   + Set **Architecture** to **x86-64**

   <p align="center">

   <img src="https://user-images.githubusercontent.com/13318047/35611287-89530d90-069f-11e8-9c90-4de7ce8d6677.png" width="400">

   <p align="center"><em>PC Standalone Setting</em></p>
   </p>

2. Open `Other Setting` and change `Scripting Runtime Version` to `Experimental(.Net 4.6 Equivalent)` in `Optimization`. The Unity application may require a restart after this change.


<p align="center">
<img src="https://user-images.githubusercontent.com/13318047/35611491-1f904034-06a0-11e8-93d0-fdc4bb711e0f.png" width="500">
<p align="center"><em>PC Standalone Setting</em></p>
</p>

#### Windows Store Setting

1. Switch to `Universal Windows Platform` in `Build Settings`
    + Choose `HoloLens` in `Target Device` 

      > **Note:** Choose the proper device if your application is targeted to other platform.

    + Choose `D3D` in `Build Type`

    + Making sure that you have ``Unity C# Projects` checked.

    + Click `Build And Run`

<p align="center">
<img src="https://user-images.githubusercontent.com/13318047/35612069-5cc0d9d0-06a2-11e8-96f3-ca16774246ca.png" width="550">
<p align="center"><em>Windows Store Setting</em></p>
</p>

2. Open `XR Settings` and check `Virtual Reality Supported`
3. Choose `Windows Holographic`

<p align="center">
<img src="https://user-images.githubusercontent.com/13318047/35612193-d08c12c6-06a2-11e8-9644-05bc7e717fa8.png" width="500">
<p align="center"><em>Windows Store Setting</em></p>
</p>

4. Check options in `Capabilities` in `Publishing Settings` according to your needs

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/4099195/26623115/45686fd0-461f-11e7-854d-fe1b04b67ce4.png" width="300">
<p align="center"><em>Windows Store Setting</em></p>
</p>


