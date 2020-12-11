# linux-serial-config
If you get error */dev/ttyANY Permision denied* 
### Add serial port permsion to user

First thinks first depending on your configuration **ttyANY** may be replace by **ttyACM** or **ttyUSB**, the same for **groupname** can be **uucp** or **dialout** and **#** by the number of your device.

##### Step 1 type *ls -l /dev/ttyANY*. Example in my case:
```
ls -l /dev/ttyUSB*
```
you will get a line like this *crw-rw---- l root groupname 188, 0 10 dec 12:20 /dev/ttyANY#*, in my case **groupname** was **uucp** and **ttyANY#** was **ttyUSB0**.

##### Step 2 type (remember, replace the corresponding fields):

```
sudo chmod a+rw /dev/ttyANY#
```
it will request your password.

##### Step 3 type:
```
sudo chmod a+rw /dev/ttyANY#
```
it will change the permision on your serial device, and that's it.

### Read serial port from console

To get serial readings, choose according your device port number and baudrate configuration, for example *ttyUSB0 115200* 
```
stty -F /dev/ttyANY# baudrate
stty -F /dev/ttyANY# raw
cat < /dev/ttyANY#
```
