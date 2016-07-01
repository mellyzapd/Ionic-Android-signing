# Ionic-Android-signing
A tutorial to manually sign apk file for ionic

Free to use and share

This post will show you how to sign your apk manually, from ionic framework for release.
Recently I signed my first apk from ionic and ran into some issues that will be ironed out in this blog. 

1. You will need to have the sdk and jdk / jdr tools installed.
2. Have a ionic project with the Android platform installed.

LETS START

You need to build your app using below in the cmd line then move that project-release.apk file into this directory

 ionic build android --release

exampleApp\platforms\android


MAKING THE KEYSTORE

You then need to make the key store in that file and write in all the info. Do not lose the key file and keep a record of the information.
keytool -genkey -v -keystore my-release-key.keystore -alias alias_name -keyalg RSA -keysize 2048 -validity 10000

SIGN THE APK

Now we have to sign the apk
jarsigner -verbose -sigalg SHA1withRSA -digestalg SHA1 -keystore my-release-key.keystore HelloWorld-release-unsigned.apk alias_name
now it is signed.
ZIPPING UP

Now zip up the files to create a project.apk find Zip align tool found here(Program Files (x86)\Android\android-sdk\build-tools\21.1.2) might be different for you put it into exampleApp\platforms\android. Then write this in the cli

zipalign -v 4 HelloWorld-release-unsigned.apk HelloWorld.apk

You are finished and now should have a exampleApp.apk file in the platforms android folder


TROUBLE SHOOTING

Some of the cli cmds may not work and for this you need to change your path in
computer>advanced settings> environment variables
 and then find path and add a new and type in the directory path for your key-tool etc this tells the cmd line where to find the exc files etc.

