# Change mouse scroll direction

In Windows, mouse scroll direction is not an easily accessible option in the normal settings menu (although it is for trackpads!).
In order to change the mouse direction, you will need to locate the device in device manager, and check the details section for the hardware ID.
Once this is obtained, use the regestry editor to locate the following registry folder:

```
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Enum\HID
```

Within this folder, you should find a subfolder that matches the hardware ID obtained earlier. 
Under "Device Parameters", locate `FlipFlopWheel` and toggle this from `0` to `1` as desired to reverse the current direction.
For horizontal scroll direction, locate instead `FlipFlopHScroll` and toggle this value.
A restart is needed for this change to take affect.
