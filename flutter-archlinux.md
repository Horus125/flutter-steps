```bash
# linux desktop
yay -S flutter-dev

sudo gpasswd -a <user> flutterusers
source /etc/profile
newgrp flutterusers
flutter config --enable-linux-desktop

# android
yay -S flutter android-sdk android-sdk-platform-tools android-sdk-build-tools android-platform android-emulator android-x86-64-system-image 

sudo gpasswd -a <user> flutterusers

sudo groupadd android-sdk
sudo gpasswd -a <user> android-sdk
sudo setfacl -R -m g:android-sdk:rwx /opt/android-sdk
sudo setfacl -d -m g:android-sdk:rwX /opt/android-sdk

source /etc/profile
newgrp flutterusers
newgrp android-sdk

avdmanager list device <--- get id of device you want to emulate (phone, tablet, tv etc)

avdmanager create avd -n "someName, i.e. tablet" -k "system-images;android-29;default;x86_64" -d <id, i.e 34>
emulator @someName

#available package names: system-images;android-<version>;default|google_apis|google_apis_playstore;x86|x86_64|armeabi-v7a

flutter doctor --android-licenses
flutter doctor -v

cd yourFlutterProject;
flutter run #<---- run in emulator
flutter build apk #<---- build apk
```

https://www.rockyourcode.com/how-to-get-flutter-and-android-working-on-arch-linux/
https://wiki.archlinux.org/index.php/Android
https://gist.github.com/mrk-han/66ac1a724456cadf1c93f4218c6060ae
