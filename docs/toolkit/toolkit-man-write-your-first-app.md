### Write your first App

Now let's make an app step by step. Through it's simple, it can show you some core functionalities of MeshExpert. 

#### Coding

- Add an object in the scene and name it as `App`
- Add a script on the object and name it as `GettingStartedSample.cs`
- Copy and paste the following codes to the script.

```c#
using System.Collections;
using UnityEngine;
using DataMesh.AR.Network;
using DataMesh.AR;
using MEHoloClient.Entities;
using MEHoloClient.Proto;

public class GettingStartedSample : MonoBehaviour, IMessageHandler
{
    public GameObject cube;
    private CollaborationManager collaborationManager;

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

        collaborationManager = CollaborationManager.Instance;

        collaborationManager.AddMessageHandler(this);

        MsgEntry entry = new MsgEntry();
        entry.ShowId = "Test";
        GetTransformFloat(cube.transform, entry);

        ShowObject showObject = new ShowObject(entry);
        SceneObject roomData = new SceneObject();
        roomData.ShowObjectDic.Add(showObject.ShowId, showObject);

        collaborationManager.roomInitData = roomData;

        collaborationManager.TurnOn();
    }

    private void GetTransformFloat(Transform trans, MsgEntry entry)
    {
        entry.Pr.Clear();

        float[] rs = new float[6];
        entry.Pr.Add(trans.position.x);
        entry.Pr.Add(trans.position.y);
        entry.Pr.Add(trans.position.z);
        entry.Pr.Add(trans.eulerAngles.x);
        entry.Pr.Add(trans.eulerAngles.y);
        entry.Pr.Add(trans.eulerAngles.z);
    }

    public void DealMessage(SyncProto proto)
    {
        Google.Protobuf.Collections.RepeatedField<MsgEntry> messages = proto.SyncMsg.MsgEntry;
        if (messages == null)
            return;

        for (int i = 0; i < messages.Count; i++)
        {
            MsgEntry msg = messages[i];
            cube.transform.position = new Vector3(msg.Pr[0], msg.Pr[1], msg.Pr[2]);
            cube.transform.eulerAngles = new Vector3(msg.Pr[3], msg.Pr[4], msg.Pr[5]);

            Debug.Log("Receive Message! " + msg.Pr);
        }
    }

    void Update()
    {
        if (collaborationManager != null)
        {
            if (collaborationManager.enterRoomResult == EnterRoomResult.EnterRoomSuccess)
            {
                MsgEntry entry = new MsgEntry();
                entry.OpType = MsgEntry.Types.OP_TYPE.Upd;
                entry.ShowId = "Test";
                GetTransformFloat(cube.transform, entry);

                SyncMsg msg = new SyncMsg();
                msg.MsgEntry.Add(entry);

                collaborationManager.SendMessage(msg);
            }
        }
    }

}

```

The **GettingStartedSample** inherits **DealMessage(SyncProto proto)** method from **IMessageHandler**. This Method will be called when application recieve message from server. 



#### Object Property

- Click object `App` in the scene and check its `Inspector Panel`
- Drag object `Cube` in the scene to property `Cube` on the Panel

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/4099195/26623909/d198c5f2-4621-11e7-92c8-6594245976af.png" width="500">
<p align="center"><em>Object Property Setting</em></p>
</p>



#### Runtime Tests

- Deploy the app to HoloLens (check out [Microsoft Doc](https://docs.microsoft.com/en-us/hololens/hololens-install-apps))
- Check if the HoloLens and the machine on which **_MeshExpert_** has been installed are in the same LAN environment.
- Ensure that **_MeshExpert Server_** is running.
- Launch the app on HoloLens. You will see a cube in front of your eyes.
- Launch the app in Unity and **_move_** or **_revolve_** the cube in `Scene`.

<p align="center">
<img src="https://cloud.githubusercontent.com/assets/4099195/26624011/29ee5596-4622-11e7-95dc-afedabdd64fc.png" width="300">
<p align="center"><em>Cube</em></p>
</p>

- Check the cube in HoloLens and you will see the cube transforms in the same way as in Unity.
