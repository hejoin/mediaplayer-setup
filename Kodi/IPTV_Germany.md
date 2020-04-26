# IPTV configuration for Germany

## Pre-configure out-of-the-box

To be written.

Install (how exactly?) the `pvr.iptvsimple` add-on into the SYSTEM squashfs. Also put there (where exactly?) a pre-configuration similar to the one below.

## Configure on the running system

Working.

Install the `pvr.iptvsimple` add-on.
Then, do:

```
cat > /storage/.kodi/userdata/addon_data/pvr.iptvsimple/settings.xml <<\EOF
<settings version="2">
    <setting id="epgCache">true</setting>
    <setting id="epgPath" default="true"></setting>
    <setting id="epgPathType">1</setting>
    <setting id="epgTimeShift" default="true">0</setting>
    <setting id="epgTSOverride" default="true">false</setting>
    <setting id="epgUrl" default="true">https://rytec.ricx.nl/epg_data/rytecDE_Basic.gz</setting>
    <setting id="logoBaseUrl" default="true"></setting>
    <setting id="logoFromEpg">1</setting>
    <setting id="logoPath" default="true"></setting>
    <setting id="logoPathType">1</setting>
    <setting id="m3uCache" default="true">true</setting>
    <setting id="m3uPath" default="true"></setting>
    <setting id="m3uPathType">1</setting>
    <setting id="m3uUrl">http://bit.ly/kn-kodi</setting>
    <setting id="startNum">1</setting>
</settings>
EOF
killall kodi.bin
```