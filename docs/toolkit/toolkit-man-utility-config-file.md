
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
# config for network
###############################################

Server_Host = 192.168.8.250

Server_Port = 8848

```
Save this file and put it in "**StreamingAssets**" folder.

<p align="center">

<img src="https://cloud.githubusercontent.com/assets/7636848/26676698/73aaa76e-46fb-11e7-8d4b-f4ce31389a03.png" width="500">

</p>



### Use AppConfig

* First, you need to load a config file. 
```C#
		AppConfig.Instance.LoadConfig("config.ini");
```
* To get the configured data, call the **GetConfigByFileName(string configFileName, string keyName)** method of AppConfig in your scripts.
```C#
        string param =  AppConfig.Instance.GetConfigByFileName("config.ini", "ParamName");
    
```
* There is an overloaded method **GetConfig(string configFileName, string keyName, string defaultValue)**. The last parameter is the default value to return if the method is unable to locate the config value by the given key.
```C#
    void Start () {
        string param =  AppConfig.Instance.GetConfigByFileName("config.ini", "ParamName", "Default Value");
    }
```

- To update config file, call method:

   **bool UpdateConfigFile(string configFileName, Dictionary<string, string> data)**

  or the overloaded one:

   **bool UpdateConfigFile(string configFileName, string key, string value)** 

  The specific parameter value will be modified and the config file will be updated immediately. If the key does not exist in origin config, it will be automatically added as a new line.

  **Attention**:  Since streamingAssetsPath is not editable in UWP platform and we copy the config files to  persistentDataPath(See the above **Functionalities** Part). This function only modify the config files in persistentDataPath.

```c#
    public bool WriteAnchor(string anchorName, Vector3 pos, Vector3 eulerRotate)
    {
        string data = AnchorToString(pos, eulerRotate);
        return AppConfig.Instance.UpdateConfigFile("anchors.txt", anchorName, data);
    }
	public static string AnchorToString(Vector3 pos, Vector3 rot)
    {
      	return string.Format("{0:F},{1:F},{2:F},{3:F},{4:F},{5:F}", pos[0], pos[1], pos[2], rot[0], rot[1], rot[2]);
    }
```



