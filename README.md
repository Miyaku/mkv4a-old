#ViPER4Android
This a stock ViPER4Android on MoKee ROM, Based android Lollipop and Marshmallow are supported.
In this ViPER Panel you can't install drivers automatically, he NOT will ask you to install drivers.

##Informations
This a file include on master branches, you can clone or download manual a <a href="https://github.com/Miyaku/mkv4a/archive/master.zip">master.zip</a><br />
<pre>/
|- system
|`- etc
|   |- <a href="https://github.com/Miyaku/mkv4a/tree/master/system/etc">audio_effects.*.conf</a>
|`- lib
|   |- soundfx
|   `-- <a href="https://github.com/Miyaku/mkv4a/blob/master/system/lib/soundfx/libv4a.so">libv4a.so</a>
|    -- <a href="https://github.com/Miyaku/mkv4a/blob/master/system/lib/soundfx/libv4a_fx.so">libv4a_fx.so</a>
|`- priv-app
|   |- ViPER4Android
     `- <a href="https://github.com/Miyaku/mkv4a/blob/master/system/priv-app/ViPER4Android/ViPER4Android.apk">ViPER4Android.apk</a></pre>
</pre>

##Getting Start & Test Manually
1). Copy all file in your storage<br />
2). Copy <b><a href="https://github.com/Miyaku/mkv4a/blob/master/system/lib/soundfx/libv4a.so">libv4a.so</a></b> to <code>/root/system/etc/lib</code> and set permission are 644<br />
3). Copy dir <b>ViPER4Android</b> to <code>/root/system/priv-app/</code> an set permission for dir 755 and .apk 644<br />
4). Open up <code>/root/system/build.prop</code> in text editor using any file explorer with root access.<br />
	Change the line (If you can’t find these lines, skip this step.)
	<pre>
	Ipa.decode=true to lpa.decode=false
	tunnel.decode=true to tunnel.decode=false
	lpa.use-stagefright=true to lpa.use-stagefright=false</pre>
	
5). Now you must make modification in <code>/root/system/etc/audio_effect.conf</code> <br />
	Under “libraries {“, add:
	<pre>
	v4a_fx {
          path /system/lib/soundfx/libv4a.so
        }
    </pre>
    Under “effects {“ add:
     <pre>
     v4a_standard_fx {
          library v4a_fx
          uuid 41d3c987-e6cf-11e3-a88a-11aba5d5c51b
        }
    </pre>
Note: If your rom running Dolby Atmos, maybe you must edit <i>audio_effect.conf</i> too on <code>/root/system/vendor/etc/</code><br /><br />
Save, and reboot your device
6). After booting, open stock music app and play your song, keep play now open ViPER4Android FX app and swipe to right > drivers status
If working, the popup will be show like this<br />
<blockquote>Driver version: xxxx<br />
Status: Normal<br />
Format audio: Supported<br />
Proccess: Yes</blockquote>

If the status is Abnormal maybe your device selinux is not permissive, you can find out here http://miya.cf/merim

Alright, i'm NOT promise it's can work to your rom on your devices, but if you want know, trying will give you best answers :)

##Pull Request to here
If your hard work is perfecly working, you can share and pull new branch here, this a simple guide to push via local<br />
1). Clone this repository
<pre>git clone https://github.com/Miyaku/mkv4a.git</pre>
2). Edit for your devices and make work and include flashble zip on root dir and lets check out
<pre>git checkout -b your_device_info
git add *
git commit -m "rom[info]-devices"
git push -u origin your_device_info
</pre>
Create Pull Request

##Credits
ViPER4Android <a href="http://www.vipersaudio.com/blog">vipersaudio.com</a><br />
MoKee Open Source <a href="http://mokeedev.com/">rom.mk</a><br />
Guide Petaling Jaya, Bradl79 <a href="http://forum.xda-developers.com/showthread.php?t=2191223">@xda</a><br />
