## Collaboration Module


### Overview

CollaborationManager provides the following functions:

* Group players by rooms to let them collaborate with each other.
* Let a wide range of devices to communicate through the Workstation.
* Wrap a generic message format and communication channels to facilitate collaborations.

### Prepare Your Project

* Create a Unity project and set it up accordingly for HoloLens apps (refer to doc "[Configure Your Project](0-configure-your-project.md)" ).
* Set up METoolkit modules (refer to doc "[Integrated METoolkit](1-integrated-METoolkit.md)" ).
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

Server_Host = 192.168.2.31
```
You can change the host to your own server IP.

> ****Important: ** If your app is **NOT** running on _Unity Editor_ or _PC Standalone_ (e.g. HoloLens, iOS, Android),  app will load config file at **PersistentDataPath**, not from **StreamingAssets**. For more information, please refer to [Utility: Config Files](9-utility-config-file.md)



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

