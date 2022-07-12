# Tag 3

## Deployment

Akutell nutzen wir einen Entwicklungsserver von mkdocs, um die Inhalte darzustellen. Wie können wir die Inhalte öffentlich verfügbar machen?

## Web hosting

Die einfachste Möglichkeit für die Veröffentlichung einer Webseite ist **Webhosting**.
Öffne die folgende Webseite und prüfe, welche **Webhosting**-Angebote es gibt.

[Netcup Webhosting](https://www.netcup.de/hosting/)

## Linux Server

Für eine statische Webseite wie die Unsere ist **Webhosting** eine gute Lösung.
Wenn man mehr Flexibilität für das Deployment haben möchte, braucht man einen richtigen Server.
Häufig wird hier ein Linux Server angewendet, weil es viele stabile kostenlose Linuxvarianten gibt.
Eine der am häufigsten eingesetzten Linuxvariante ist "Ubuntu". Für Server brauchen wir die "Ubuntu Server" Version.

Server muss man nicht immer physisch selbst betreiben. Es gibt viele Virtual Server Angebote, die ziehmlich günstig sind.

[Netcup Virtual Server](https://www.netcup.de/vserver/vps.php)

## SSH (Secure SHell )

Zugriff auf einen Linux-Server erfolgt meistens über SSH.
Lese den folgenden Artikel, um grob zu verstehen, was SSH ist. 
Du mussst nicht alles verstehen. Überspringe die Inhalte, die für die zu schwer sind.

[Was ist SSH?](https://www.computerweekly.com/de/definition/Secure-Shell-SSH)

### Verbindung zu unserem Testserver

Passwort bekommst du via E-Mail.

```powershell
ssh sam@kiatest
```

Anmeldung über Passwort ist in der Regel nicht sicher. Lasst uns die Publickey-Anmeldung einrichten.

[How to Set Up SSH Keys on Ubuntu 22.04](https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys-on-ubuntu-22-04)



## SFTP

benötigt um die Dateien vom lokalen Rechner auf den Server zu kopieren

## SCP

benötigt um die Dateien vom lokalen Rechner auf den Server zu kopieren

## Mkdocs build

Mit dem folgenden Befehl kannst du die Dateien für das Deployment generieren.

```powershel
mkdocs build
```