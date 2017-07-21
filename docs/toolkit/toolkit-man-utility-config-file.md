
## Config Files

### Functionalities

The use of configuration file adds dynamical aspects to the apps. We recommend you to use a configuration file to control the volatile properties in your apps.

> Note: You need to place your config file in "**StreamingAssets**" folder.  If your app is **NOT** running on _Unity Editor_ or _PC Standalone_ (e.g. HoloLens, iOS, Android), when the app starts at its first time the config file would be automatically copied to "**PersistentDataPath**" directory and later on the app would load the configs from the "**PersistentDataPath**".
>
> **Remember**: if you want to modify a config file of a App running on _Unity Editor_ or _PC Standalone_, you can modify it directly in "**StreamingAssets**" folder; But if your App running on other platforms, you need to find it in "**PersistentDataPath**", instead of "**StreamingAssets**" folder.
>
> For more information about **PersistentDataPath** , please refer to Unity document: [Application.persistentDataPath](https://docs.unity3d.com/ScriptReference/Application-persistentDataPath.html)

### Use Configuration File

Below is an example config file.

```
###############################################
# config for app
###############################################

#### Colaberation Server Config ####
Server_Url = 192.168.1.48
Server_Port = 8823

#### Storage Config
License = 3ACE54EFC4B267908AB5210EDFB16A3F

#### HologramCapture Config
 Out_Put_Path = C:\\HologramCapture\\HoloReady\\
```
Save this file and put it in "**StreamingAssets**" folder.

<img src="https://cloud.githubusercontent.com/assets/7636848/26676698/73aaa76e-46fb-11e7-8d4b-f4ce31389a03.png" width="500">

### Use AppConfig

* First, you need to load a config file. 
```C#
		AppConfig.Instance.LoadConfig("config.ini");
```
* To get the configured data, call the **GetConfigByFileName(string, string)** method of AppConfig in your scripts.
```C#
        string param =  AppConfig.Instance.GetConfigByFileName("config.ini", "ParamName");
    
```
* There is an overloaded method **GetConfig(string, string, string)**. The last parameter is the default value to return if the method is unable to locate the config value by the given key.
```C#
    void Start () {
        string param =  AppConfig.Instance.GetConfigByFileName("config.ini", "ParamName", "Default Value");
    }
```



