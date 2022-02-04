# Get Windows Product Key
For activation. Useful if computer becomes deactivated after upgrade as it finds the original key.

```cmd
wmic os get "serialnumber" # to get serial number if needed
wmic path softwarelicensingservice get OA3xOriginalProductKey
```
