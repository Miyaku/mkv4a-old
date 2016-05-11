#ViPER4Android
This a stock ViPER4Android on MoKee ROM, Based android Lollipop and Marshmallow are supported.


##Informations
This a file include on master branches, you can clone or download manual zip<br />
<pre>/
|- system
|
|`- etc
|   |- audio_effects.*.conf
|`- lib
|   |- soundfx
|   `-- libv4a.so
|    -- libv4a_fx.so
|
|`- priv-app
|  |- ViPER4Android
    `- ViPER4Android.apk</pre>
</pre>

##Getting Start & Test Manualy
1). Copy all file in your storage<br />
2). Copy <b>libv4a.so</b> on your <code>/root/system/etc/lib</code> and set permission are 644<br />
3). Copy dir <i>ViPER4Android</i> to your <code>/root/system/priv-app/</code> an set permission for dir 755 and .apk 644<br />
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
          path /system/lib/soundfx/libv4a_fx_xxx.so
        }
    </pre>
    Under “effects {“ add:
     <pre>
     v4a_standard_fx {
          library v4a_fx
          uuid 41d3c987-e6cf-11e3-a88a-11aba5d5c51b
        }
    </pre>
And if finis save, and reboot your device
6). After booting, open stock music app and play your song, than open ViPER4Android FX and swipe to right > drivers status
If working, the popup will be show like this
<blockquote>Driver version: xxxx
Status: Normal
Format audio: supported
Proccess: Yes</blockquote>

Clone this repository
<pre>git clone https://github.com/Miyaku/mkv4a.git</pre>
edit for your devices and make work
<pre>git checkout -b your_device_info
git add *
git commit -m "rom[info]-devices"
git push -u origin your_device_info
</pre>


