# i2c0-rtc.dtbo
RTC overlay for second i2c bus on Raspberry Pi

RTCs supported:

bcm2708, 
ds1307, 
ds1339, 
ds3231, 
mcp7940, 
mcp7941, 
pcf2127, 
pcf8523, 
pcf8563, 
m41t62


Copy this file to /boot/overlays to run a RTC on i2c bus 0 on the raspbery pi.

Add this to /boot/config.txt with whichever model of RTC you are using:

`dtoverlay=i2c0-rtc,ds3231`

do these:

```
sudo apt-get remove fake-hwclock
sudk update-rc.d -f fake-hwclock remove
sudo systemctl disable fake-hwclock
```

reboot the pi

verify it's working by:

`i2cdetect -y 0`

UU should be at 0x68

if it's not idk

make sure your time is synced eith to GPS or internet.
Verify by running:

`date`

If that's correct do this:
```
sudo hwclock -w
sudo hwclock -r
```
the right time should print.

Das it!

Checkout this how-to to get the i2c bus 0 going:

https://woodgears.ca/tech/i2c.html

73, Jake KF0ARE
