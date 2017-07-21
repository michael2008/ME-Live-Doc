## MEHoloSDK Docs

### Overview

The aim of MEHolo SDK is to provide methods and APIs that developers can use to build their own application. In addition, based on Xamarin's cross-platform solution, MEHolo SDK can be integrated with the different platforms such as iOS, Android, UWP and .Net Framework.

### Basic Usage

* Open Unity and import `MEHolo SDK Unity package` directly from `Assets` -> `Import Package` -> `Custom Package`.
* For MEHoloSDK-Plugins-Unity, change all DLL files to be in support of Editor and Standalone platform only.
   <p align="center">
   <img src="https://cloud.githubusercontent.com/assets/4099195/26666994/85def26c-46d5-11e7-93f4-48cb566ea468.png" width="500">
   </p>
* For MEHoloSDK-Plugins-UWP, change all DLL files to be in support of WSAPlayer only.
   <p align="center">
   <img src="https://cloud.githubusercontent.com/assets/4099195/26667023/aaaaa58c-46d5-11e7-9076-0006ff5181a1.png" width="500">
   </p>

### Function and API

#### Picture Uploading

---

This method is used to upload images to **_HoloCloud-Share_**.

**By using the given file path**

```c#
//UWP
public async Task<HoloServerResp<string>> UploadImage(string fileName, string filePath, int appId, string token, string tags)
{
}

//Unity
public HoloServerResp<string> UploadImage(string fileName, string filePath, int appId, string token, string tags)
{
}
```

_Parameters_

|   Name   |  Type  |       Description       |
| :------: | :----: | :---------------------: |
| filename | string | the name of the picture |
| filePath | string |      the file path      |
|  appId   |  int   |     the project id      |
|  token   | string |    the access token     |
|   tags   | string |          tags           |

_Demo code_

```c#
//UWP
var resultUWP = await api.UploadImage("name", path, 1111, "3ACE54EFC4B267908AB5210EDFB16A3F", "");
//Unity
var resultUnity = api.UploadImage("name", path, 1111, "3ACE54EFC4B267908AB5210EDFB16A3F", "");
```
**Upload directly**

```c#
//UWP
public async Task<HoloServerResp<string>> UploadImage(string fileName, byte[] fileBytes, int appId, string token, string tags)
{
}

//Unity
public HoloServerResp<string> UploadImage(string fileName, byte[] fileBytes, int appId, string token, string tags)
{
}
```

_Parameters_

|   Name    |    Type    |       Description        |
| :-------: | :--------: | :----------------------: |
| filename  |   string   | the name of the picture  |
| fileBytes | byte array | the content of the image |
|   appId   |    int     |      the project id      |
|   token   |   string   |     the access token     |
|   tags    |   string   |           tags           |

_Demo code_

```c#
var bytes = File.ReadAllBytes(filePath);
//UWP
var resultUWP = await api.UploadImage("name", bytes, 1111, "3ACE54EFC4B267908AB5210EDFB16A3F", "");
//Unity
var resultUnity = api.UploadImage("name", bytes, 1111, "3ACE54EFC4B267908AB5210EDFB16A3F", "");
```

#### Image Download

---

This method is used to download images from **_HoloCloud Share (Social)_**.

**Download to Local**

```c#
//UWP
public async Task DownloadImage(string imageId, string organizationId, string imageType, string xtoken, string downloadPath)
{
}

//Unity
public void DownloadImage(string imageId, string organizationId, string imageType, string xtoken, string downloadPath)
{
}
```

_Parameters_

|      Name      |  Type  |           Description           |
| :------------: | :----: | :-----------------------------: |
|    imageId     | string |          the image id           |
| organizationId | string |       the organization id       |
|   imageType    | string |     indicate the image type     |
|     xtoken     | string |        the access token         |
|  downloadPath  | string | the file path include file name |

_Demo code_

```c#
//UWP
await api.DownloadImage("05c4d859-8a42-46ae-b2d0-28e0f45aa633EWApUUPTI", "1003", "original", "token", localPath);

//Unity
api.DownloadImage("05c4d859-8a42-46ae-b2d0-28e0f45aa633EWApUUPTI", "1003", "original", "token", localPath);
```

**Get image contents**

```c#
//UWP
public async Task<byte[]> DownloadImage(string imageId, string organizationId, string imageType, string xtoken)
{
}

//Untiy
public byte[] DownloadImage(string imageId, string organizationId, string imageType, string xtoken)
{
}
```

_Parameters_

|      Name      |  Type  |       Description       |
| :------------: | :----: | :---------------------: |
|    imageId     | string |      the image id       |
| organizationId | string |   the organization id   |
|   imageType    | string | indicate the image type |
|     xtoken     | string |    the access token     |

_Demo code_

```c#
//UWP
var fileBytesUWP = await api.DownloadImage("05c4d859-8a42-46ae-b2d0-28e0f45aa633EWApUUPTI", "1003", "original", "token");

//Unity
var fileBytesUntity = api.DownloadImage("05c4d859-8a42-46ae-b2d0-28e0f45aa633EWApUUPTI", "1003", "original", "token");
```

#### File Upload

---

You can use this method to upload the local file to MEHolo Server.

```c#
//UWP
public async Task<HoloServerResp<string>> UploadFile(string fileName, string filePath, int blockIndex, int appId, string token)
{
}

//Unity
public HoloServerResp<string> UploadFile(string fileName, string filePath, int blockIndex, int appId, string token)
{
}
```

_Parameters_

|    Name    |  Type  |              Description              |
| :--------: | :----: | :-----------------------------------: |
|  fileName  | string |         the name of the file          |
|  filePath  | string |             the file path             |
| blockIndex |  int   | indicate the index of the file blocks |
|   appId    |  int   |              the app id               |
|   token    | string |           the access token            |

_Demo code_

```c#
//UWP
var responseUWP = await api.UploadFile("a.mp4", filePath, 0, 1, "token");

//Unity
var responseUnity = api.UploadFile("a.mp4", filePath, 0, 1, "token");

//Check progress
var progress = api.CheckProgress("a.mp4");
```

#### File Download

---

This method is used to download files from MEHolo Server

```c#
//UWP
public async Task DownloadFile(string fileId, string token, string downloadPath, int timeout)
{
}

//Unity
public void DownloadFile(string fileId, string token, string downloadPath, int timeout)
{
}
```

_Parameters_

|     Name     |  Type  |        Description         |
| :----------: | :----: | :------------------------: |
|    fileId    | string |        the file id         |
|    token     | string |      the access token      |
| downloadPath | string |       the file path        |
|   timeout    |  int   | indicate the timeout value |

_Demo code_

```c#
//UWP
await api.DownloadFile(fileId, token, downloadPath, 40);

//Unity
api.DownloadFile(fileId, token, downloadPath, 40);
```

#### Get Lecture List

---

This method is used for getting lecture list.

```c#
//UWP
public async Task<List<Lecture>> GetLectures(string token)
{
}

//Unity
public List<Lecture> GetLectures(string token)
{
}
```

_Parameters_

| Name  |  Type  |   Description    |
| :---: | :----: | :--------------: |
| token | string | the access token |

_Demo code_

```c#
//UWP
var lectures = await api.GetLectures(token);

//Unity
var lectures = api.GetLectures(token);
```



>  **Note:** Detailed lecture information is required for some method, which can be retrieved from the lecture list. Giving the following code as an example.

```c#
//get a certain lecture
var lecture = lectures[0];
//get a lecutre's content
var lectureContent = lecture.LectureContent[0];
//get the name of the video
var videoName = lectureContent.VideoName;
//get screenshot prefix
var screenshotPrefix = lectureContent.ScreenshotPrefix;
//get the name of the model
var modelName = lectureContent.ModelName;
//get hls url
var hlsUrl = lecture.HlsBaseUrl + "/" + lectureContent.HlsSubLocation + "/" + lectureContent.HlsName;
```

#### Video Download

---

This method is used to download a specific video.

```C#
//UWP
public async Task<byte[]> DownloadVideoLecture(string videoName, string token)
{
}

//Unity
public byte[] DownloadVideoLecture(string videoName, string token)
{
}
```

_Parameters_

|   Name    |  Type  |      Description      |
| :-------: | :----: | :-------------------: |
| videoName | string | the name of the video |
|   token   | string |   the access token    |

_Demo code_

```c#
//UWP
var videoBytes = await api.DownloadVideoLecture(videoName, token);

//Unity
var videoBytes = api.DownloadVideoLecture(videoName, token);
```

####  Get Thumbnail of Video

---

This method is used to get the thumbnail of a certain video.

```c#
//UWP
public async Task<byte[]> DownloadThumbnail(string screenshotPrefix, string token)
{
}

//Unity
public byte[] DownloadThumbnail(string screenshotPrefix, string token)
{
}
```

_Parameters_

| Name             | Type   | Description                          |
| ---------------- | ------ | ------------------------------------ |
| screenshotPrefix | string | you can get it from the lecture list |
| token            | string | the access token                     |

_Demo code_

```c#
//UWP
var thumbnail = await api.DownloadThumbnail(screenshotPrefix, token);

//Unity
var thumbnail = api.DownloadThumbnail(screenshotPrefix, token);
```

#### Model Download

---

This method is used to download a specific model.

```c#
//UWP
public async Task<byte[]> DownloadModel(string modelName, string token, int timeout)
{
}

//Unity
public byte[] DownloadModel(string modelName, string token, int timeout)
{
}
```

_Parameters_

| Name      | Type   | Description                      |
| --------- | ------ | -------------------------------- |
| modelName | string | you can get it from lecture list |
| token     | string | the access token                 |

_Demo code_

```c#
//UWP
var model = await api.DownloadModel(modelName, token, 40);

//Unity
var model = api.DownloadModel(modelName, token, 40);
```

#### Check If the Anchor Exists

---

This method is used to check if the given anchor file exists in the room managed by the MEHolo Server.

```c#
//UWP
public async Task<bool> Exists(int app, string room)
{
}

//Unity
public bool Exists(int app, string room)
{
}
```

_Parameters_

| Name | Type   | Description          |
| ---- | ------ | -------------------- |
| app  | int    | the project id       |
| room | string | the name of the room |

_Demo code_

```c#
//UWP
var result = await api.Exists(1, room);

//Unity
var result = api.Exists(1, room);
```

#### Anchor Upload

---

This method is used to upload an anchor file to MEHolo Server.

```c#
//UWP
public async Task<bool> UploadAnchor(int app, string room, string fileName, byte[] fileBytes)
{
}

//Unity
public bool UploadAnchor(int app, string room, string fileName, byte[] fileBytes)
{
}
```

_Parameters_

| Name      | Type   | Description                    |
| --------- | ------ | ------------------------------ |
| app       | int    | the project id                 |
| room      | string | the name of the room           |
| fileName  | string | the anchor file name           |
| fileBytes | byte[] | the content of the anchor file |

_Demo code_

```c#
byte[] bytes = DoGetBytesFromFile();

//UWP
var result = await api.UploadAnchor(1, room, "a.json", bytes);

//Unity
var result = api.UploadAnchor(1, room, "a.json", bytes);
```

#### Anchor Download

---

This method is used to download anchor file.

```c#
//UWP
public async Task<byte[]> DownloadAnchor(int app, string room)
{
}

//Unity
public byte[] DownloadAnchor(int app, string room)
{
}
```

_Parameters_

| Name | Type   | Description    |
| ---- | ------ | -------------- |
| app  | int    | the project id |
| room | string | the room name  |

_Demo code_

```c#
//UWP
var anchor = await api.DownloadAnchor(1, room);

//Unity
var anchor = api.DownloadAnchor(1, room);
```

#### Enter the room

---

If the local room is empty, it will initialize the room according to the given scene. You will get a server time if you entered a room.

```c#
//UWP
public async Task<bool> EnterAppRoom(int app, string room, SceneObjects initialScene)
{
}

//Unity
public bool EnterAppRoom(int app, string room, SceneObjects initialScene)
{
}
```

_Parameters_

| Name         | Type         | Description              |
| ------------ | ------------ | ------------------------ |
| app          | int          | the project id           |
| room         | string       | the room name            |
| initialScene | SceneObjects | the initial scene object |

_Demo code_

```c#
var scene = new SceneObjects();
scene.ShowObjectDic.Add("showid111", new ShowObject("showid111", true, new[] { 1.5f }, new[]{ 1.2f }) { obj_type = "type1" });

//UWP
var initTime = await api.EnterAppRoom(1, room, scene);
//Unity
var initTime = api.EnterAppRoom(1, room, scene);
```

#### Check If the Room Is Empty

---

This method is used to check if a certain room is empty.

```c#
//UWP
public async Task<bool> QueryAppRoom(int app, string room)
{
}

//Unity
public bool QueryAppRoom(int app, string room)
{
}
```

_Parameters_

| Name | Type   | Description    |
| ---- | ------ | -------------- |
| app  | int    | the project id |
| room | string | the room name  |

_Demo code_

```c#
//UWP
var isEmpty = await api.QueryAppRoom(1, room);

//Unity
var isEmpty = api.QueryAppRoom(1, room);
```


#### Initialize room

---

This method is used to initialize the scene of a certain room,

```c#
//UWP
public async Task InitRoom(SceneObjects scene, int app, string room)
{
}

//Unity
public void InitRoom(SceneObjects scene, int app, string room)
{
}
```

_Parameters_

| Name  | Type         | Description     |
| ----- | ------------ | --------------- |
| scene | SceneObjects | the local scene |
| app   | int          | the project id  |
| room  | string       | the room name   |

_Demo code_

```c#
//UWP
await InitRoom(scene, 1, room);

//Unity
InitRoom(scene, 1, room);
```

#### Sync Time

---

This method can be used to get the delay between local machine and the remote **_MEHolo Server_**. 

```c#
public void StartSyncTime()
{
}
```

_Demo code_

```c#
SyncTimeClient syncTimeClient = new SyncTimeClient("ws://192.168.1.142:8823/sync/time");
//UWP
try
{
    syncTimeClient.StartSyncTime();

    Task.Delay(3000).Wait();
    int i = 0;
    while (i < 8000)
    {
        Task.Delay(100).Wait();
        if (!syncTimeClient.SyncTimeRunning)
            continue;
        i++;
        Debug.WriteLine("deley = " + syncTimeClient.Delay);
    }
}
finally
{
    syncTimeClient.Terminate();
    Task.Delay(3000).Wait();
}

//Unity
try
{
    syncTimeClient.StartSyncTime();

    Thread.Sleep(3000);
    int i = 0;
    while (i < 8000)
    {
        Thread.Sleep(100);
        if (!syncTimeClient.SyncTimeRunning)
            continue;
        i++;
        Debug.WriteLine("deley = " + syncTimeClient.Delay);
    }
}
finally
{
    syncTimeClient.Terminate();
    Thread.Sleep(3000);
}
```
