## Storage Module


### Overview

Storage Module provides the following functions:

* Build asset data from Unity prefab. It can contain any asset which can be added to AssetBundle. You can build them with a Unity editor plugin.
* Upload asset data to Cloud with website.
* Download asset data in App runtime, and use it in App.
* Provide a list UI as default.

### Make Asset

MeshExpert has a asset file type, include Unity AssetBundle and some other information. METoolkit provide a tool to create this kind of asset file from Unity prefab. You can do it as follow:

- Find your prefab which you want to build in Unity **Project** panel.
- Select all prefabs you want to build.

<img src="https://user-images.githubusercontent.com/7381020/28152736-93f0b6f4-67d4-11e7-9053-cbdb1e89f87a.png" width="200">

- Right Click select item, select "**DataMesh/Build Storage Asset (PC and WSA)**" from Content Menu.

<img src="https://user-images.githubusercontent.com/7381020/28153300-4c766938-67d7-11e7-8812-99eab17fe391.png" width="500">

- Select a folder.

<img src="https://user-images.githubusercontent.com/7381020/28153321-5b95ce04-67d7-11e7-9f60-088c0b296169.png" width="400">

- Go to this folder, you can find the assets, with extension name "**.medb**" .


<img src="" width="300">


### Upload Asset to Cloud

You can upload assets (.medb file) to MeshExpert Cloud. 

For more information, please refer to MeshExpert Cloud Document.

> Note: Ensure the **AppID** you created in MeshExpert Cloud Storage and the **AppID** in your App built by METoolkit is **SAME**. Otherwise, your App can't get any Asset you uploaded.



### Use Asset in runtime

#### Preparing for use

First, you need to prepare your App by METoolkit.

* Create a Unity project and set it up accordingly for HoloLens apps (refer to doc "[Configure Your Project][Configure_your_project]" ).
* Set up METoolkit modules (refer to doc "[Integrated METoolkit][Integrated_with_your_project]" ).
* Confirm to check **Storage** Module in HoloEntrance.



#### Set up Storage

> Note: The configurations in this step is same as Collaboration. If you have created this config file, ignore this step.

* In order to setup the host of server, you need to create a configuration file.
* Find **Asset/StreamingAssets** folder, and create a file named **MEConfigNetwork.ini**
* The content of this configuration file like this:

```
###############################################
# config for network
###############################################

Server_Host = 192.168.2.31
```
You can change the host to your own server IP.

> ****Important: ** If your app is **NOT** running on _Unity Editor_ or _PC Standalone_ (e.g. HoloLens, iOS, Android),  app will load config file at **PersistentDataPath**, not from **StreamingAssets**. For more information, please refer to [Utility: Config Files][Utility_Config_Files]



#### Prepare StorageManager and StorageUI

```C#
        StorageManager storageManager = StorageManager.Instance;
        StorageUI storageUI = storageManager.GetUI();

        storageUI.ShowUI(OnChangePage, OnSelect);     // Show UI, with 2 callback function
        LoadAssetPages(1);                            // Load page 1
```

**OnChangePage** and **OnSelect** is 2 callback function which to be invoke in UI Event. 

We will write them later.

```C#


```



#### Get Asset list from Cloud

When you call **StorageManager.GetStorageResourceList** to retrieve Assets, the result will divided by page. You must get assets page by page, and you can set how many assets each page contains.  

```C#
    private void LoadAssetPages(int page)
    {
          storageManager.GetStorageResourceList(
                StorageManager.StorageResourceType.Asset,        // resoure type
                page,                                            // current page
                12,                                              // how many assets per page
                OnLoadPageFinish                                 // the Callback function when list is ready
                );
    }
```

>  note: For default UI, 12 assets per page is recommended.

In the callback function, you should tell UI to get new data from StorageManager.

```C#
    private void OnLoadPageFinish(bool succ, string error)
    {
        if (!succ)
        {
            Debug.Log("Error! " + error);
            return;
        }

        storageUI.ChangeUIData();
    }
```



#### Page Turning

If you want to get another page of assets, you must implement the callback function **OnChangePage** .

```C#
    private void OnChangePage(int page)
    {
        LoadAssetPages(page);
    }
```

When you click Page Up or Page Down button, this function will be invoked, and send the new page number.



#### Download Asset

After you have got the list of Assets, you can get the real Asset from MeshExpert Cloud. 

The callback **OnSelect** can do it well. When you click a item from UI, OnSelect will be invoked, and send you the Asset as parameter.

```C#
    private void OnSelect(BaseResource res)
    {
        Asset asset = res as Asset;
        storageManager.DownloadAsset(asset, OnDownloadAssetFinish);
    }
```

**OnDownloadAssetFinish** is another callback function, and it will be invoked when Asset download finish.

```C#
    private void OnDownloadAssetFinish(string filePath)
    { 
        Debug.Log("Asset at " + filePath);

        if (filePath == null)
        {
            Debug.LogWarning("Download file Failed!");
            return;
        }

        storageUI.HideUI();

        LoadAssetFromFile(filePath);    // load and show the asset
    }
```



#### Load and Show Asset

You can load AssetBundle from Asset by **StorageAssetData**.

```C#
    private void LoadAssetFromFile(string fileName)
    {
        StorageAssetData data = StorageAssetManager.Instance.LoadAsset(fileName);

        if (data.bundle == null)
        {
            Debug.LogError("Load Bundle " + fileName + " failed!");
            return;
        }

        try
        {
            GameObject prefab = data.bundle.LoadAsset<GameObject>(data.assetName);

            PrefabUtils.DestroyAllChild(currentSelectBooth.gameObject);

            GameObject obj = PrefabUtils.CreateGameObjectToParent(currentSelectBooth.gameObject, prefab);
        }
        catch (System.Exception e)
        {
            Debug.LogError("Exception! " + e);
        }
    }

```


[Configure_your_project]: toolkit-man-configure-your-project.md
[Integrated_with_your_project]: toolkit-man-integrated-METoolkit.md
[Utility_Config_Files]: toolkit-man-utility-config-file.md
