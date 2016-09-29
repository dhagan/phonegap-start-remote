Phonegap Build

Prerequisites

Create an account on build.phonegap.com - some organizations have adobe accounts so it can be free.  If the app is under 50 MB you may be able to use the free plan
Get the apple certificate from the developers.apple.com - upload the certifciate and provisioning files per http://docs.phonegap.com/phonegap-build/signing/ios/#windows-users -- Need the password as well
For apple ad-hoc builds, internal users will need to authorize the app from iPad/iPhone - 
app Settings > General > Profiles or Profiles & Device Management
Under the "Enterprise App" heading tap the <<Company Name>> profile to establish trust for this developer. You're then prompted to confirm your choice.


Getting jump started

Sanity check for build.phonegap.com - see that the following github build works - zip up the parrent $phonegap-zip/www and upload as an app to your build.phonegap.com https://github.com/phonegap/phonegap-start

Once this is working you are now free to use an iterative approach to get the config.xml settings

You can set the build to public under the applications -> settings -> make public (?)

Then a link similar to the following will be accessible to the public

https://build.phonegap.com/apps/2283197/share

Lesson learned

There is a tool configap http://configap.com/ which helps determine which icons to use.  The xml it creates often does not validate.  I use it as crutch, but edit the config.xml by hand.  The Win10 version is now working.  I have gone back and forth with the maintainer who does it as a hobby.
I set the following to get the remote URL app to work
<access origin="http://www.winecountry.com" subdomains="true"/>
<allow-navigation href="http://www.winecountry.com"/>
You can set the user agent header - place it inside your respective platform block
<preference name="OverrideUserAgent" value="MyCordovaApp/1.2.3" /> 
Config.xml can be at the $phone-gap root or the $phone-gap/www - I saw documentation where both are supported.  I follow the https://github.com/phonegap/phonegap-start sample


Code review

For the remote url packaged version, I used the boiler plate from  https://github.com/phonegap/phonegap-start 

I changed 

receivedEvent: function(id) {
   window.location =  "http://www.winecountry.com";
}

Just to get things working.  We should probably change this to only load the window.location if the user is determined to be online.

Also I took out the reference to <script> reference to cordova.js since we are not using any onboard phone services.

These are TBD tasks.


