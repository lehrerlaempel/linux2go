# Tutorial: Linux als mobiles Betriebssystem auf einem USB-Stick (Eine Anleitung)
v 0.3 | Stand: November 2021 | Lizenz: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/deed.de)

Weitere Anleitungen von uns findet man [hier](https://lehrerlaempel.github.io/anleitungen/)!

# Vorwort
Diese Anleitung soll kurz zusammenfassen, wie man Linux auf einem USB-Stick installieren kann und wozu das ganze dann am Ende sinnvollerweise genutzt werden könnte. Wir gehen für diese Anleitung davon aus, dass Sie einen Computer verwenden, der nicht nur UEFI, sondern auch Legacy als Boot Mode unterstützt.

Wenn Sie sich nicht sicher sind, ob das bei Ihrem PC gegeben ist, öffnen Sie einfach das BIOS, indem Sie direkt nach dem Start des Computers wiederholt F2 ([je nach Hersteller kann es auch eine andere Taste sein](https://www.tomshardware.com/reviews/bios-keys-to-access-your-firmware,5732.html)) drücken, bis sich die BIOS-Einstellungen öffnen. Diese sehen je nach Hersteller und Gerät immer anders aus und sind auch anders sortiert. Aber irgendwo muss es unter einem Punkt "Boot" o.ä. die Option geben, neben dem Boot Mode **UEFI** auch **Legacy** zu wählen. Sie müssen hier nichts umstellen, sonst startet ggf. Ihr Windows Betriebssystem nicht mehr. Wichtig ist nur, dass Sie sicherstellen, dass Ihr PC Legacy unterstützt und diese Option auch erlaubt ist.

*Wer mit Computern ohne Legacy-Unterstüzung arbeiten möchte, kann einen Blick ins Kapitel 7 riskieren...*

# 1 Beschaffung des Notwendigen
Zunächst müssen wir ein paar Dinge vorbereiten:

## 1.1 USB-Stick
Wir benötigen zwei USB-Sticks mit jeweils mindestens 32 GB Speicherplatz. Wichtig ist, dass man hier nicht spart, sondern wirklich schnelle USB-Sticks nutzt, sonst wird alles Folgende zu einer echten Geduldsprobe. Man sollte daher darauf achten, dass man mindestens "USB 3.1"-Sticks nutzt, besser "USB 3.2", die auch bei längerer Nutzung nicht heiß werden. Wir haben z.B. mit [diesen hier](https://www.samsung.com/us/computing/memory-storage/usb-flash-drives/usb-3-1-flash-drive-fit-plus-32gb-muf-32ab-am/) gute Erfahrungen gemacht.

Wer mehr Speicherplatz benötigt, kann für das Kapitel 3 auch durchaus eine externe Festplatte wie z.B. [diese hier](https://shop.westerndigital.com/de-de/products/portable-drives/sandisk-extreme-usb-3-2-ssd) verwenden.

## 1.2 Installationsmedium
Wir benötigen außerdem das Installationsmedium der Linux-Distribution, die wir verwenden möchten. Für diese Anleitung nutzen wir [LinuxMint Xfce Edition](https://linuxmint.com/edition.php?id=290), da dies unserer Einschätzung nach ein guter Kompromiss zwischen einem ressourcenschonenden aber modernen und einfachen Betriebssystem ist.

Wichtig: Nach dem Download sollte man unbedingt die heruntergeladene ISO-Datei verifizieren, wie es z.B. [hier](https://linuxmint-installation-guide.readthedocs.io/en/latest/verify.html) erklärt wird. Mindestens sollte man aber die SHA256-Werte der heruntergeladenen Datei mit denen von der Downloadseite prüfen.

Unter Windows kann man dazu z.B. [7zip](https://www.7-zip.org/) installieren. Anschließend mit der rechten Maustaste auf die heruntergeladene ISO-Datei klicken und "CRC SHA", dann "SHA-256" wählen. Der dann angezeigte Wert muss unbedingt mit dem auf der Downloadseite übereinstimmen, sonst stimmt was ganz grundlegendes nicht!

Generell sollte man alle Software vor der Nutzung verifizieren, aber das Fass wollen wir hier heute nicht aufmachen...

## 1.3 Software zum Erstellen von Bootmedien
Wer Linux nutzt, kann diesen Punkt überspringen und nutzt dann einfach die meist vorhandene Software "Startmedienersteller ". 

Windows-Nutzer:innen benötigen eine Software, die aus dem heruntergeladenen ISO einen [bootfähigen USB-Stick](https://de.wikipedia.org/wiki/Bootf%C3%A4higes_Medium) erstellen kann. Wir nutzen für diese Anleitung den [Balena Etcher](https://www.balena.io/etcher/), weil dieser einfach zu benutzen und sehr schnell ist. Also: Herunterladen und installieren!

*Wer alternative Software mit mehr Einstellungsmöglichkeiten sucht, kann sich z.B. [Rufus](https://rufus.ie/de/) anschauen.*

# 2 Live-System
Das schöne an den meisten [Linux-Distributionen](https://de.wikipedia.org/wiki/Linux-Distribution) ist, dass man sie für die Nutzung nicht zwingend installieren muss. Im Gegenteil: Wer zum Beispiel ein robustes "Wegwerfsystem" für das Surfen in unhygienischen Umgebungen sucht oder wer auf den genutzten Geräten keine Spuren hinterlassen möchte, für den sind solche Systeme sehr interessant. Man startet das Linux vom USB-Stick und hat ein Betriebssystem, das sämtliche Änderungen nur im Arbeitsspeicher hinterlegt. Nach dem Herunterfahren ist also "alles weg" und nur noch das Linux im Werkszustand übrig.

Aber auch für die Installation von Linux auf einem Computer oder USB-Stick (Kapitel 3) benötigen wir ein solches Linux-Installationsmedium.

Das Erstellen geht erstaunlich einfach: Die Software zum erstellen von BootMedien (Kapitel 1.3) starten, heruntergeladene ISO-Datei (Kapitel 1.2) auswählen und Stick erstellen lassen. Fertig.

Um den Stick zu starten, einfach diesen in den ausgeschaltenen Computer stecken und dann so lange F12 (je nach Hersteller unterschiedlich) drücken, bis über das "one time boot menu" der USB-Stick als Startmedium ausgewählt werden kann. 

# 3 Linuxinstallation auf einem USB-Stick
Für die meisten Einsatzzwecke ist vermutlich ein Livesystem keine befriedigende Lösung. Meistens hat man ja Daten und Programme, die man gerne so speichern würde, dass sie den nächsten Neustart überleben. Also lassen Sie uns das Live-Medium aus Kapitel 2 nutzen, um auf einem zweiten USB-Stick Linux verschlüsselt zu installieren, so dass wir tatsächlich ein vollständiges mobiles Betriebssystem haben.

Wozu? Naja, das kommt ganz darauf an. Man könnte sich freuen, dass man ein leicht zu transportierendes und auch leicht zu versteckendes mobiles Betriebssystem hat, das auf dem benutzten Computer keine Spuren hinterlässt. Man könnte das ganze auch verwenden, um auf einem Computer viele verschiedene mobile Systeme zu nutzen, die nichts miteinander zu tun haben sollen. Man könnte sich freuen, dass die Sticks so gut verschlüsselt sind, dass ein Verlust kein Problem ist, solange man ein BackUp hat. Wenn man den im Zug verliert weiß man, dass niemand an die Daten kommt. 
Oder aber man freut sich einfach, dass man kann und will einfach ein bisschen rumspielen.

Was auch immer Sie konkret bewegt, der Weg dahin ist eigentlich erstaunlich einfach:

Zunächst Stecken wir in einen ausgeschaltenen Computer unsere Livemedium aus Kapitel 2. Dann erzwingen wir über das "one time boot menu" (meist F12, siehe oben), dass der Computer unter Legacy (wichtig!) von dem USB-Stick bootet. Nach kurzer Pause startet LinuxMint und wir sehen den Destkop des LiveSystems.

Nun stecken wir den zweiten USB-Stick in den Computer, auf den wir unser Linux installieren wollen und klicken auf das DesktopIcon mit dem Namen "Install Linux Mint".

Zuerst wählen wir Deutsch als Sprache. Auf der nächsten Seite dann das passende Tastaturlayout. In dem leeren Eingabefeld unter den zwei Auswahlfenstern kann man übrigens testen, ob man das richtige Layout gewählt hat.

Dann geht es weiter mit der Feststellung, dass wir uns jetzt nicht mit einem Netzwerk verbinden möchten. Aber wir akzeptieren gerne die Multimedia-Codecs auf der nächsten Seite, um später mehr Videoformate abspielen zu können.

Dann springt ein Fenster auf, in dem wir gerne erlauben, dass das Installationsprogramm versucht, den eingebundenen Datenträger auszuwerfen.

Auf der folgenden Seite wird es jetzt ernst: Wir wählen "Festplatte löschen und Linux Mint installieren" und außerdem unter den erweiterten Funktionen sowohl "LVM" als auch die Verschlüsselung der Installation. Wichtig!

Danach muss ein Passwort für die Festplattenverschlüsselung vergeben werden. Wichtig ist es, hier ein langes (!) Passwort zu vergeben, das am besten nur aus Buchstaben und Zahlen besteht. Verwenden Sie hier besser keine Sonderzeichen oder die Buchstaben "z, y, ä, ö, ü". Dann ist sichergestellt, dass Sie Ihr Passwort unabhängig vom Tastaturlayout immer eingeben können. 

Auf der nächsten Seite wählen wir dann als Laufwerk unseren USB-Stick oder wahlweise auch die externe SSD-Festplatte, auf die wir unser Betriebssystem installieren möchten und starten die Installation. Nachdem wir im aufspringenden Fenster nochmal bestätigt haben, dass wir das wirklich möchten, beginnt im Hintergrund bereits die Installation.

Wir wählen derweil unsere Zeitzone und vergeben einen Benutzername sowie ein Passwort. Da der Stick ja verschlüsselt ist, können wir gerne die automatische Anmeldung wählen.

Nach kurzer Wartezeit erscheint dann die Meldung, dass die Installation erfolgreich war. Wir wählen, dass wir das Ausprobieren fortsetzen möchten und fahren das System herunter. Nun entfernen wir das Livemedium und freuen uns über unsere Linux2Go :-)

Wann immer wir jetzt unser mobiles System nutzen möchten, können wir dieses einfach an einem beliebigen (Legacy unterstützenden) Rechner über das "one time boot menu" starten.

Wer häufiger vom USB-Stick bootet, kann auch erwägen, die Boot-Reihenfolge im BIOS so einzustellen, dass der Computer immer zuerst vom USB-Stick bootet und das Betriebssystem der Festplatte nur läd, wenn kein bootfähiger Stick im Rechner steckt. (Wie man das BIOS öffnet, steht im Vorwort.) 

Wird eine andere LinuxDistribution verwendet, verändern sich die Schritte zwar geringfügig, im Wesentlichen ändert sich am Vorgehen aber nichts.

# 4 Kombilösung: LiveSystem mit persistentem Speicher
Wer ein LiveSystem nutzen möchte, das nach jedem Start wieder im Urzustand ist, muss dennoch nicht völlig auf einen persistenten Speicher verzichten. Man kann entweder einfach auf einem zweiten USB-Stick Daten ablegen.

...oder man wählt folgende elegantere Lösung, die mit einem Stick auskommt: 

Zunächst laden Sie sich bitte das Tool [Ventoy](https://www.ventoy.net/en/index.html) herunter und verifizieren die heruntergeladene Datei. Unter Windows reicht anschließend das Entpacken des Archivs, eine Installation ist nicht notwendig.

Nach dem Start der Software kann man diese zunächst unter "Language" auf Deutsch umstellen.

Nun wählt man unter den Optionen bei der Partitionskonfiguration, das Ventoy ein paar Gigabyte am Ende des Sticks übrig lassen soll. Anschließend wird der gewünschte USB-Stick ausgewählt und Ventoy über einen Klick auf "Installieren" auf den Stick gebracht. 

Danach benötigt man die Software selbst nicht mehr. Ventoy ermöglicht es erfreulich einfach einen Stick zu erstellen, von dem aus man viele verschiedene Systeme booten kann. Einfach in der entstandenen Partition "Ventoy" alle gewünschten Startmedien (*.iso oder z.B. *.img) reinkopieren. Alle Startmedien die hier liegen kann man auswählen bzw. starten, wenn man zukünftig von dem Stick bootet. Hierhin kopieren wir jetzt also z.B. unsere Linux Mint ISO.

Jetzt müssen wir noch kurz einmalig den vorher extra von Ventoy erbetenen freien Speicherplatz formatieren. Dazu unter Windows das Startmenü öffenen und "Festplatten" eintippen. Es öffent sich "Festplattenpartitionen erstellen und formatieren". Hier kann man nun die freie Partition (schwarz?) suchen und ein neues Volume (FAT!) erstellen. 

Zukünftig kann man von dem Stick beliebige LiveSysteme starten und von diesen aus auf diesem formatierten Transferbereich Daten ablegen. Steckt man den USB-Stick in ein laufendes System oder startet ein anderes LiveSystem, kann ebenfalls auf die Daten zugegriffen werden.

Aber Vorsicht, die Daten sind erstmal nicht verschlüsselt!

# 5 Sonderweg Tails
Wer es gerne noch etwas paranoider hätte, sollte sich [Tails](https://tails.boum.org/) anschauen. Dieses mobile Betriebssystem kann auch mit dem BalenaEtcher auf einen USB-Stick kopiert werden. Tails zeichnet sich vor allem dadurch aus, dass es sämtlichen Datenverkehr über [Tor](https://www.torproject.org/) routet. Außerdem ist das System zwar ein Livesystem, kann sich aber selbst Updaten und bietet auf Wunsch auch dauerhafte verschlüsselte Speichermöglichkeiten. Eine gute Anleitung zur Nutzung des Systems findet man u.a. [hier](https://media.ccc.de/v/pw20-342-tails).

# 6 USB-Sticks "retten"
Hier noch eine kurze Anleitung, wie man unter Windows aus Linux-USB-Sticks wieder "normale" Speichermedien mit einer Partition erstellen kann.

Zunächst die Windows Taste drücken und "diskpart" eingeben.

In dem sich öffenden Fenster erscheint nach einer kurzen Pause "DISKPART>".

Hier geben wir jetzt den Befehl "list disk" ein. Nun müssen wir den zu formatierenden USB-Stick in der angezeigten Tabelle identifizieren und uns seine Nummer merken. In diesem Beispiel gehe ich mal davon aus, wir haben Datenträger 2, den wir gerne formatieren würden.

Also geben wir ein: "select disk 2". Danach geben wir ein "clean". Sobald das fertig ist "create partition primary". Anschließend erscheint der Stick als unformatiertes Laufwerk in unserem Arbeitsplatz. Diskpart können wir jetzt schließen. Über "Rechtsklick" und "Formatieren" können wir diesen mit einer Schnellformatierung wieder in den Auslieferungszustand versetzen.

# 7 Experiment: Linux2Go ohne Legacy
Es gibt durchaus auch Möglichkeiten, mobile Linux-Betriebssysteme auf Computern zu erstellen und zu nutzen, die keine Legacy-Unterstützung bieten. Im Gegensatz zu dem oben erwähnten Vorgehen ist das nun folgende aber ein nicht qualitätsgeprüftes experimentelles Vorgehen, das zwar meist funktioniert, aber eben nicht immer.

Der Plan ist folgender: Zuerst erstellt man sich mit einem Tool wie [Rufus](http://rufus.ie/de/) ein Linux-Livemedium. Dabei achtet man darauf, dass man als "Partitionsschema" "GPT" wählt, als Zielsystem "UEFI". Als Distribution würden wir persönlich für diesen Fall [MX Linux](https://mxlinux.org/) empfehlen. Alles Ubuntu-basierte macht erfahrungsgemäß unter UEFI Probleme.

Man schnappe sich dann ein Laptop und entfernt die Festplatte, damit bei der Installation auf dieser kein Bootloader landen kann.
Nun bootet man auf dem PC ohne Festplatte unter UFEI und ohne Secure Boot sein Livemedium und installiert das Linux auf einem zweiten USB-Stick.

Der so erstelle USB-Stick kann nun problemlos von allen Rechnern aus gestartet werden, die UEFI unterstützen. Lediglich Secure Boot muss bei Bedarf vor dem Start des USB-Sticks deaktiviert werden.

Festplatte wieder einbauen nicht vergessen ;-)

Wer die Festplatte auf einem PC ausgebaut hat, dessen Festplatte mit Bitlocker verschlüsselt war, sollte danach seinen Wiederherstellungs-Key parat haben. Wer den nicht mehr hat, kann sich den in Windows vorher anzeigen lassen. Am besten aber macht man soetwas mit einem Gerät, auf dem keine wichtigen Daten liegen und dessen Festplatte nicht verschlüsselt ist.

# Das Kleingedruckte
## Fehlerteufel
Diese Anleitung wurde von [lehrerlaempel](https://github.com/lehrerlaempel) nach bestem Wissen und Gewissen erstellt. Wir haben die feste Absicht, diese im Laufe der Zeit an Änderungen der erwähnten Software anzupassen und um weitere Aspekte zu ergänzen. Den Stand der Ihnen vorliegenden Version finden Sie ganz am Anfang der Seite.

Ihnen sind Fehler aufgefallen? Sie haben Verbesserungs- oder Änderungswünsche? Dann nehmen Sie gerne [Kontakt](https://lehrerlaempel.github.io/anleitungen/) mit uns auf. Wir sind tatsächlich sehr an Ihrer Rückmeldung interessiert!

Im Rahmen unserer Möglichkeiten haben wir auch versucht sicherzustellen, dass sowohl diese Seite selbst, als auch die von uns verlinkten Seiten sowohl legaler als auch legitimer Natur sind. Sollten uns Fehler unterlaufen sein oder wir änderungen verlinkter Seiten verpasst haben, geben Sie und gerne ein Zeichen, damit wir das zeitnah beheben können.

Wir übernehmen explizit keinerlei Haftung für die hier getroffenen Aussagen oder möglicherweise daraus entstandene Datenverluste oder sonstigen Schäden. Wir haben diese Texte nach bestem Wissen und Gewissen verfasst, sind aber wie alle Menschen fehlbar. Verstehen Sie diese Anleitungen also bitte als aufrichtig wohlmeindende Ratschläge auf Augenhöhe, jedoch ohne jede Gewähr.

## Lizenz
Dieser Text steht unter einer CC-Lizenz, ist also quasi schöpferisches Gemeingut.

Sie dürfen:
- **Teilen** das Material in jedwedem Format oder Medium vervielfältigen und weiterverbreiten
- **Bearbeiten** das Material remixen, verändern und darauf aufbauen

Der Lizenzgeber kann diese Freiheiten nicht widerrufen solange Sie sich an die Lizenzbedingungen halten.

Unter folgenden Bedingungen:
- **Namensnennung** Sie müssen angemessene Urheber- und Rechteangaben machen, einen Link zur Lizenz beifügen und angeben, ob Änderungen vorgenommen wurden. Diese Angaben dürfen in jeder angemessenen Art und Weise gemacht werden, allerdings nicht so, dass der Eindruck entsteht, der Lizenzgeber unterstütze gerade Sie oder Ihre Nutzung besonders.
- **Weitergabe unter gleichen Bedingungen** Wenn Sie das Material remixen, verändern oder anderweitig direkt darauf aufbauen, dürfen Sie Ihre Beiträge nur unter derselben Lizenz wie das Original verbreiten. 
- **Keine weiteren Einschränkungen** Sie dürfen keine zusätzlichen Klauseln oder technische Verfahren einsetzen, die anderen rechtlich irgendetwas untersagen, was die Lizenz erlaubt. 

Hinweise:
- Sie müssen sich nicht an diese Lizenz halten hinsichtlich solcher Teile des Materials, die gemeinfrei sind, oder soweit Ihre Nutzungshandlungen durch Ausnahmen und Schranken des Urheberrechts gedeckt sind.
- Es werden keine Garantien gegeben und auch keine Gewähr geleistet. Die Lizenz verschafft Ihnen möglicherweise nicht alle Erlaubnisse, die Sie für die jeweilige Nutzung brauchen. Es können beispielsweise andere Rechte wie Persönlichkeits- und Datenschutzrechte zu beachten sein, die Ihre Nutzung des Materials entsprechend beschränken.

*Dies war eine allgemeinverständliche Zusammenfassung der [Lizenz](https://creativecommons.org/licenses/by-sa/4.0/legalcode.de), die diese nicht ersetzt.*
