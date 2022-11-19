#IBM Watson IOT Platform
#pip install wiotp-sdk
import wiotp.sdk.device
import time
import random
myConfig = {
    "identity": {
        "orgId": "fytwic",
        "typeId": "gasleakage114",
        "deviceId":"device114"
    },
    "auth": {
        "token": "01234567"
    }
}
def myCommandCallback(cmd):
    print("Message received from IBM IoT Platform: %s" % cmd.data['command'])
    m=cmd.data['command']
client = wiotp.sdk.device.DeviceClient(config=myConfig, logHandlers=None)
client.connect()

while True:
    temp=random.randint(32,40)
    hum=random.randint(60,80)
    gas=random.randint(500,800)
    pres=random.randint(20,80)
    myData={'temperature':temp, 'humidity':hum, 'gasLevel':gas, 'pressure':pres, 'latitude':13.148760, 'longitude':80.229100}
    client.publishEvent(eventId="status", msgFormat="json", data=myData, qos=0, onPublish=None)
    print("Published data Successfully: %s", myData)
    client.commandCallback = myCommandCallback
    time.sleep(2)
client.disconnect()
