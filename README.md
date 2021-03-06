# MacOS-High-Sierra-Virtual-Box
Eine kurze Anleitung zum Installieren einer virtuellen Maschine mit MacOS High Sierra

## Voraussetzung

### VDMK oder ISO Datei
Zunächst benötigst du eine Image Datei von macOS High Sierra. Die Dateien auf der Apple Webseite sind im DMG Format, sodass sie von dir in ein ISO oder VMDK Format umgewandelt werden müssen. Hier kannst du bereits Zeit sparen und eine vorgefertige VMDK Datei herunterladen
[VDMK MACOS HIGH SIERRA](https://www.mediafire.com/file/xe6vr0yvb5hqr5c/macOS_High_Sierra_10.13_%252817A365%2529_3_by_techrechard.com.vmdk/file)

### VirtualBox und das Extension Pack

Installiere sowohl Virtual Box mit den Standardeinstellungen als auch das Extension Pack auf deinem Rechner.

Links für VirtualBox abhängig vom Betriebssystem
 - [Windows](https://download.virtualbox.org/virtualbox/6.1.34/VirtualBox-6.1.34-150636-Win.exe)
 - [Mac](https://download.virtualbox.org/virtualbox/6.1.34/VirtualBox-6.1.34-150636-OSX.dmg)
 - [Linux](https://www.virtualbox.org/wiki/Linux_Downloads)
 
Link für [Extension Pack](https://download.virtualbox.org/virtualbox/6.1.34/Oracle_VM_VirtualBox_Extension_Pack-6.1.34.vbox-extpack)

## Installation

### Erstelle eine Virtuelle Maschine
Öffne die Virtual Box Anwendung und klicke auf das 'Neu' Icon, um eine neue virtuelle Maschine zu erstellen. Es öffnet sich ein Fenster, in dem du einige Grundeinstellungen eintragen kannst. Der Name und der Installationsordner deiner VM kann frei gewählt werden. Für Typ und Version kannst du dich an dem folgenden Beispiel orientieren. 

Die Speichergröße sollte mindestens 4096MB betragen. Zum Schluss wählst du "Vorhandene Festplatte verwenden" aus und trägst die VDMK oder ISO Datei, die du im ersten Schritt heruntergeladen oder selbst konvertiert hast, ein.

![Einstellungen Beispiel](/images/pic_1.png)

### Führe einige zusätzliche Kommandos aus
Nachdem du die virtuelle Maschine erstellt hast, schließt du die Virtual Box Anwendung und öffnest als **Administrator** die CMD (Windows-Eingabeaufforderung) auf.

Nun gibst du folgende Kommandos ein. **WICHTIG** ist, dass du den "VM Name" in den Kommandos in den Namen umänderst, den du im vorherigen Schritt für die VM vergeben hast. Im bisherigen Bespiel wäre es "MacOS High Sierra". 

**Tipp** *Du kannst einen beliebigen Texteditor nutzen und mit einem "Replace" Befehl alle Namen gleichzeitig umbenennen lassen.*

Die Kommandos lauten: 
```
cd "C:\Program Files\Oracle\VirtualBox\" 

VBoxManage.exe modifyvm "VM Name" --cpuidset 00000001 000106e5 00100800 0098e3fd bfebfbff 
VBoxManage setextradata "VM Name" "VBoxInternal/Devices/efi/0/Config/DmiSystemProduct" "iMac11,3" 
VBoxManage setextradata "VM Name" "VBoxInternal/Devices/efi/0/Config/DmiSystemVersion" "1.0" 
VBoxManage setextradata "VM Name" "VBoxInternal/Devices/efi/0/Config/DmiBoardProduct" "Iloveapple" 
VBoxManage setextradata "VM Name" "VBoxInternal/Devices/smc/0/Config/DeviceKey" "ourhardworkbythesewordsguardedpleasedontsteal(c)AppleComputerInc" 
VBoxManage setextradata "VM Name" "VBoxInternal/Devices/smc/0/Config/GetKeyFromRealSMC" 1
```
Schließe das CMD und öffne wieder die Virtual Box Anwendung

### Ändere einige Einstellungen der VM

Wähle die neu erstelle virtuelle Maschine aus und klicke auf *Einstellungen*. Folge den Beispielen für die Anpassungen der VM.

Unter System > Motherboard -> Deaktiviere Diskettenlaufwerk
![Unter System > Motherboard -> Deaktiviere Diskettenlaufwerk](/images/pic_2.png)

Unter System > Prozessor ->  Erhöhe die Anzahl an Prozessoren auf 2
![Unter System > Prozessor ->  Erhöhe die Anzahl an Prozessoren auf 2](/images/pic_3.png)

Unter Anzeige > Bildschirm -> erhöhe den Grafikspeicher auf dein Maximum
![Unter Anzeige > Bildschirm -> erhöhe den Grafikspeicher auf dein Maximum](/images/pic_4.png)

Anschließend kannst du die virtuelle Maschine starten. 

### Installation von macOS High Sierra

Nachdem du die virtuelle Maschine gestartet hast, öffnet sich innerhalb der VM ein Terminal. Dieser Vorgang kann einige Minuten dauern. Dies ist abhängig von deinem System. Schließlich öffnet sich der Installationsprozess für macOS High Sierra. 

## Nützliche Features

Falls das Fenster der VM für dich zu klein und ist und du die Auflösung vergrößern willst, kannst du folgende Kommandos ausführen.

Ändere einfach für "bxh" deine gewünschte Auflösung e.g. "1980x1080" oder "1280x720. Für "VM Name" solltest du wieder deinen VM Namen verwenden.
```
cd "C:\Program Files\Oracle\VirtualBox\"

VBoxManage setextradata "VM Name" VBoxInternal2/EfiGraphicsResolution "bxh"

```
Starte die VM und klicke auf *Ansicht* in der oberen Leiste und anschließend auf *Vollbildmodus*. Nun ist das VM auf deine eingestellte Bildschirmauflösung angepasst. 

Die Anleitung ist maßgeblich an folgendem Tutorial orientiert und kann für detaillierte Informationen genutzt werden. Ich habe sie lediglich etwas gekürzt und in deutsch übersetzt. [Tutorial von Geekrar](https://www.geekrar.com/install-macos-high-sierra-on-virtualbox-2021/#Install_macOS_High_Sierra_on_VirtualBox)
