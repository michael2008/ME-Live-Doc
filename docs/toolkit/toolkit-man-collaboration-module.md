## Collaboration Module


### Overview

CollaborationManager provides the following functions:

* Group players by rooms to let them collaborate with each other.
* Let a wide range of devices to communicate through the Workstation.
* Wrap a generic message format and communication channels to facilitate collaborations.



### Prepare Your Project

* Create a Unity project and set it up accordingly for HoloLens apps (refer to doc "[Configure Your Project][Configure_your_project]" ).
* Set up METoolkit modules (refer to doc "[Integrated METoolkit][Integrated_with_your_project]").
* Create a **Cube** object, and place it in a position where the camera can capture.
* Confirm to check **Collaboration** Module in HoloEntrance.

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/7636848/26671865/9f2de05c-46e9-11e7-9a90-0ada5fc492ae.png" width="250">
</p>



### Set up Collaboration

* In order to setup the host of collaboration server, you need to create a configuration file.

* Find **Asset/StreamingAssets** folder, and create a file named **MEConfigNetwork.ini**

* The content of this configuration file like this:

```
###############################################
# config for network
###############################################

Server_Host = 192.168.8.250
Server_Port = 8848
```
You can change the host to your own server IP.

> ****Important: ** If your app is **NOT** running on _Unity Editor_ or _PC Standalone_ (e.g. HoloLens, iOS, Android),  app will load config file at **PersistentDataPath**, not from **StreamingAssets**. For more information, please refer to [Utility: Config Files][Utility_Config_Files]



### Try Collaboration

* Create an object named "**MainApp**" in Hierarchy view.
* Add a new module "**CollaborationSample**" and then save.
* Open the "**CollaborationSample**" to add the following codes:
```C#
using System.Collections;
using UnityEngine;
using DataMesh.AR.Interactive;
using DataMesh.AR.Network;
using MEHoloClient.Entities;

namespace DataMesh.AR.Samples.Collaboration
{
    public enum ColorType
    {
        red = 0,
        blue = 1,
        green = 2,
    }
    public class CollaborationSample : MonoBehaviour, IMessageHandler
    {
        private MultiInputManager inputManager;
        CollaborationManager cm;

        int appId;
        string roomId;
        string serverHost;
        int serverPort;
        ColorType CurrentColor;
        ShowObject showObject;
        SceneObjects roomData;
        void Start()
        {
            StartCoroutine(WaitForInit());
        }

        private IEnumerator WaitForInit()
        {
            MEHoloEntrance entrance = MEHoloEntrance.Instance;

            while (!entrance.HasInit)
            {
                yield return null;
            }


            // Todo: Begin your logic
            inputManager = MultiInputManager.Instance;
            inputManager.cbTap += OnTap;

            cm = CollaborationManager.Instance;
            cm.AddMessageHandler(this);
            cm.cbEnterRoom = cbEnterRoom;

            roomData = new SceneObjects();
            string showId = "showId001";
            bool enabled = false;
            string obj_type = "ColorType";
            float[] pr = new float[7];
            float[] prInit = new float[7];
            showObject = new ShowObject(showId, enabled, pr, prInit);
            showObject.obj_type = obj_type;
            roomData.ShowObjectDic.Add(showObject.show_id, showObject);
            cm.roomInitData = roomData;
            cm.TurnOn();

        }

        private void OnTap(int count)
        {
            ClickCube();
        }
        
      	private void cbEnterRoom()
        {
            Debug.Log("Enter Room Sucessfully");
        }

        [ContextMenu("ClickCube")]
        private void ClickCube()
        {
            CurrentColor += 1;
            if ((int)CurrentColor > 2)
            {
                CurrentColor = 0;
            }
            
            showObject.pr[0] = (float)CurrentColor;
            roomData.ShowObjectDic[showObject.show_id] = showObject;
            MsgEntry entry = new MsgEntry(OP_TYPE.UPD, showObject.show_id, true, showObject.pr, null, null);
            entry.obj_type = showObject.obj_type;
            cm.SendMessage(new MsgEntry[1] { entry });
        }

        void ChangeCubeColor(ColorType CurrentColor)
        {
            GameObject cube = GameObject.Find("Cube");

            switch (CurrentColor)
            {
                case ColorType.red:
                    cube.GetComponent<Renderer>().material.color = Color.red;
                    break;
                case ColorType.blue:
                    cube.GetComponent<Renderer>().material.color = Color.blue;
                    break;
                case ColorType.green:
                    cube.GetComponent<Renderer>().material.color = Color.green;
                    break;
            }
        }
        void Update()
        {
            if (Input.GetMouseButtonDown(0))
            {
                Ray ray = Camera.main.ScreenPointToRay(Input.mousePosition);
                RaycastHit hit;
                if (Physics.Raycast(ray, out hit))
                {
                    if (hit.collider.name == "Cube")
                    {
                        ClickCube();
                    }

                }
            }
        }
        void IMessageHandler.DealMessage(SyncProto proto)
        {

            this.DealMessage(proto);
        }
        void DealMessage(SyncProto proto)
        {
            MsgEntry[] messages = proto.sync_msg.msg_entry;
            if (messages == null)
                return;
            for (int i = 0; i < messages.Length; i++)
            {
                MsgEntry msgEntry = messages[i];
                if (msgEntry.show_id == showObject.show_id)
                {
                    ChangeCubeColor((ColorType)((int)msgEntry.pr[0]));
                }

            }
        }
    }

}
```
* Now you can build and install the app on HoloLens to see the results.
* After the app started, you will see a cube. air-tap the cube to change its color, and the color would be synchronized to other connected devices through the Workstation. For instance, you can view the synchronized change of color in Unity editor if the app is running.

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/7636848/26671872/a1c319c2-46e9-11e7-97d8-5005701a4877.png" width="250">
</p>



### Further explanation

The SyncProto type parameter of **DealMessage** method contains two types of message from server:

- **Broadcast Message **(SyncProto.BrdMsg):

  When one client send broadcast message to server , server will automatically transmit it to everyone in the 'room'. It can be used to inform some one-time event such as 'playing a sound effect', in case missing such a message doesn't lead to a bad result and you don't want it to execute after it misses the correct moment.

  The server won't save anything about broadcast message, which is different from Synchronize Message.

  **Send Broadcast**

```c#
private void SendBroadcastMessage(int[] data,string msgContent)
{
    BroadcastMsg msg = new BroadcastMsg();
    msg.Sender = selfUserId;
    msg.Content = msgContent;
        
    ComplexContent content = new ComplexContent();  	
    for (int i = 0; i < data.Length; i++)
    {
      //of course you can use datas in other format like: 
      //ontent.MsgFloat64
      //content.MsgString
      //content.MsgBytes
        content.MsgInt64.Add(data[i]);
    }
    msg.ComplexContent = content;
    collaborationManager.SendCommand(msg);
}
```

- **Synchronization Message** (SyncProto.SyncMsg):

  The synchronization message is based on 'objects' data maintained by server. When recieving object status data from clients, the server will rapidly update the data on server and send a **final** status data to clients after it reaches the synchronization interval. Such synchronization **may not** reserve all the small changes during a synchronization interval, which means it cannot ensure that every change sent by client during a synchronization interval will be trasmit to others. So it is not fit to informs events which need to be counted. 

  It can be used to synchronize status based on object which you want clients to get the latest status, such as object transformation;

  **Send Synchronization**

```c#
private void SendSyncMessage(string sid, float[] data)
{
    SyncMsg msg = new SyncMsg();
    msg.Sender = selfUserId;
    MsgEntry msgEntry = new MsgEntry();
    //set msgEntry data
    msgEntry.ShowId = sid;
    for (int i = 0; i < data.Length; i++)
    {
        msgEntry.Pr.Add(data[i]);
    }
    //......
    msg.MsgEntry.Add(msgEntry);
    collaborationManager.SendMessage(msg);
}
```

Both type of message would be sent to everyone in the 'room', which means the client which sends the message (or raise the status update) will get update message from server. In some case it may lead to an infinite loop, so it is recommended that functions which really change local object status be called after the application get 'confirmation' from server, **or** check whether the sender of message is itself.




[Configure_your_project]: toolkit-man-configure-your-project.md
[Integrated_with_your_project]: toolkit-man-integrated-METoolkit.md
[Utility_Config_Files]: toolkit-man-utility-config-file.md