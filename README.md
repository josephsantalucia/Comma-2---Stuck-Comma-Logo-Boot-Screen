# Comma-2---Stuck-Comma-Logo-Boot-Screen
If your Comma 2 will not boot and not boot past the comma logo - here are some instructions to get back to the 'Getting Started' screen


<img width="848" height="1124" alt="Stuck Comma Logo - C2 - Boot" src="https://github.com/user-attachments/assets/27f08017-8e6d-40c2-b745-93ab62903486" />



How I got here
  1. I was stuck on the "Connect to WiFi" screen. A common issue with the fix found here https://github.com/jyoung8607/neos-manual-install
  2. There is an issue with the instructions above and that is what caused my C2 to not boot past the Comma.ai logo
  3. The last step from jyoung8607 instructs to download a Custom Fork
  4. After I downloaded the Custom Fork - the C2 wouldn't boot past the comma logo

I recommend not downloading a Custom Fork once you follow jyoung8607 instructions and gain adb access to your C2. 


How to re-flash your C2
  0. These steps will take you back to the "Getting Started" screen adn the "Connect to WiFi" problem
  1. 	https://github.com/commaai/eon-neos/releases/tag/neos20
    	a. ota-signed-e5aa34ebb279777…. (818 MB - Oct 11, 2023)
    	b. recovery-cf752ceb79.......	(14.5 MB - Oct 11, 2023)
    	c. Source code (zip)  - Apr 18, 2022
  2. Extract the two .zip files
  3. Extract all files/directories to the same directory as the recovery.img
  4. Your directory should look something like:
     	download.py
    	files (folder)
    	flash.ps1
    	flash.sh
    	META-INF (folder)
    	ota-signed-e5aa34….. (folder)
    	README.md
    	recovery.img
  5. Modify the flash.sh file to skip the downloading part. I chose to comment out the original code
  6. Run flash.sh - in mac terminal ./flash.sh
  7. Here is what my output looked like in my Mac Terminal:
     
@Josephs-M2-MacBook-Pro eon-neos % sudo ./flash.sh
Password:
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
 58 11.2M   58 6672k    0     0   531k      0  0:00:21  0:00:12  0:00:09  958k^Z
zsh: suspended  sudo ./flash.sh
josephsantalucia@Josephs-M2-MacBook-Pro eon-neos % sudo ./flash.sh
FAILED (remote: 'unknown command')
fastboot: error: Command failed
fastboot: error: cannot load 'recovery.img': No such file or directory
josephsantalucia@Josephs-M2-MacBook-Pro eon-neos % sudo ./flash.sh
FAILED (remote: 'unknown command')
fastboot: error: Command failed
Warning: skip copying recovery image avb footer (recovery partition size: 0, recovery image size: 15222060).
Sending 'recovery' (14865 KB)                      OKAY [  0.390s]
Writing 'recovery'                                 OKAY [  0.116s]
Finished. Total time: 0.612s
Warning: skip copying boot image avb footer (boot partition size: 0, boot image size: 11969832).
Sending 'boot' (11689 KB)                          OKAY [  0.310s]
Writing 'boot'                                     OKAY [  0.096s]
Finished. Total time: 0.514s
Sending sparse 'system' 1/5 (506934 KB)            OKAY [ 12.238s]
Writing 'system'                                   OKAY [  5.244s]
Sending sparse 'system' 2/5 (516459 KB)            OKAY [ 12.466s]
Writing 'system'                                   OKAY [  6.792s]
Sending sparse 'system' 3/5 (502802 KB)            OKAY [ 12.197s]
Writing 'system'                                   OKAY [  5.468s]
Sending sparse 'system' 4/5 (514182 KB)            OKAY [ 12.343s]
Writing 'system'                                   OKAY [ 17.597s]
Sending sparse 'system' 5/5 (191168 KB)            OKAY [  4.608s]
Writing 'system'                                   OKAY [ 47.979s]
Finished. Total time: 137.752s
******** Did you mean to fastboot format this ext4 partition?
Erasing 'userdata'                                 OKAY [  0.066s]
Finished. Total time: 0.096s
mke2fs 1.46.6 (1-Feb-2023)
Creating filesystem with 65536 4k blocks and 65536 inodes
Filesystem UUID: 8ff178c0-bf5f-4128-aad1-94e805e4745a
Superblock backups stored on blocks: 
	32768

Allocating group tables: done                            
Writing inode tables: done                            
Creating journal (4096 blocks): done
Writing superblocks and filesystem accounting information: done

Warning: skip copying cache image avb footer due to sparse image.
Sending 'cache' (184 KB)                           OKAY [  0.039s]
Writing 'cache'                                    OKAY [  0.025s]
Finished. Total time: 1.004s
Rebooting                                          OKAY [  0.000s]
Finished. Total time: 0.001s


  9. As you can see there were some errors - but the C2 rebooted after the code ran and now back to the "Getting Started" screeen.
