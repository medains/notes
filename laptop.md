
Details for making it work as a tablet automatically.


Disable/Reenable trackpad

xinput --set-prop 10 "Device Enabled" 0; sleep 10s; xinput --set-prop 10 "Device Enabled" 1

Disable/Reenable keyboard

xinput --set-prop 11 "Device Enabled" 0; sleep 10s; xinput --set-prop 11 "Device Enabled" 1

Onscreen keyboard

Onboard


Detect Screen orientation (for changing)

monitor-sensor

See https://askubuntu.com/questions/799727/ubuntu-with-tablet-mode-for-lenovo-yoga

