# IT-Sicherheit

## Grundziele der IT-Sicherheit

Die drei Grundziele der IT-Sicherheit sind:

- Vertraulichkeit
- Integrität
- Verfügbarkeit

1. **Vertraulichkeit** - Informationen dürfen nur von berechtigten Personen gelesen werden.
2. **Integrität** - Daten dürfen nicht unbemerkt verändert werden.
3. **Verfügbarkeit** - Systeme, Software und Daten sind erreichbar, wenn sie gebraucht werden.

## Beispiel aus dem Alltag

Ein Online-Banking-System muss alle drei Ziele erfüllen:

- **Vertraulichkeit:** Nur der Kontoinhaber darf den Kontostand sehen.
- **Integrität:** Eine Überweisung darf nicht heimlich verändert werden.
- **Verfügbarkeit:** Das Banking-System muss erreichbar sein, wenn man es braucht.

## Merksatz

IT-Sicherheit bedeutet nicht nur: „Niemand darf rein.“

IT-Sicherheit bedeutet:

- richtige Personen dürfen auf richtige Daten zugreifen
- Daten bleiben korrekt
- Systeme bleiben nutzbar


# Angriffsvektoren - Angriffswege

Ein **Angriffsvektor** ist ein möglicher Weg, über den ein Angreifer versucht, ein System anzugreifen.

Beispiele:

- E-Mail
- Passwort
- offener Port
- veraltete Software
- USB-Stick
- öffentlich erreichbarer Server
- falsche Firewall-Regel
- fehlendes Zertifikat
- physischer Zugriff auf Geräte


## Phishing - Social Engineering

Phishing ist ein Angriff, bei dem Menschen getäuscht werden.

Der Angreifer versucht zum Beispiel, an Zugangsdaten zu kommen.

Typische Tricks:

- Zeitdruck
- Angst
- Gewinnversprechen
- Chef-Trick
- gefälschte Paketbenachrichtigung
- gefälschte Bank- oder Microsoft-Mail

## Beispiele

### Zeitdruck

Eine E-Mail sagt:

> Ihr Konto wird in 30 Minuten gesperrt. Klicken Sie sofort hier.

Problem:

- Die Person soll schnell handeln.
- Sie soll nicht in Ruhe prüfen.
- Dadurch klickt sie eher auf einen gefährlichen Link.

### Angst

Eine Nachricht sagt:

> Unbekannte Anmeldung erkannt. Bestätigen Sie sofort Ihr Passwort.

Problem:

- Die Person bekommt Angst.
- Sie will das Konto schützen.
- Dabei gibt sie vielleicht genau dem Angreifer das Passwort.

### Gewinnversprechen

Eine Nachricht sagt:

> Sie haben ein iPhone gewonnen. Geben Sie Ihre Daten ein.

Problem:

- Die Person wird neugierig.
- Sie gibt persönliche Daten ein.
- Die Daten können missbraucht werden.

### Chef-Trick

Eine Nachricht sieht so aus, als käme sie vom Chef:

> Bitte überweise dringend 4.000 Euro. Ich bin gerade im Meeting.

Problem:

- Die Nachricht wirkt dringend.
- Die Person will helfen.
- Es wird nicht sauber geprüft.

## Schutz gegen Phishing

- Absender prüfen
- Links nicht blind anklicken
- keine Passwörter über Links aus E-Mails eingeben
- bei Unsicherheit direkt über die echte Webseite einloggen
- verdächtige Mails melden
- Mehrfaktor-Authentifizierung nutzen


## Schwache Passwörter -> Brute Force

Ein schwaches Passwort ist ein häufiger Angriffsvektor.

**Brute Force** bedeutet:

Ein Angreifer probiert viele Passwörter automatisch aus.

Beispiele für schlechte Passwörter:

- 123456
- Passwort
- Admin123
- Sommer2026
- Firma2026!
- qwertz123

## Was macht ein gutes Passwort besser?

- Länge ist wichtig
- Groß- und Kleinbuchstaben
- Zahlen
- Sonderzeichen
- keine Namen
- keine Geburtsdaten
- keine einfachen Wörter
- nicht mehrfach verwenden

## Beispiele

Schlecht:

```text
Admin123
```

Besser:

```text
Kaffee!Mond!Fenster!87
```

Noch besser ist ein Passwortmanager, der zufällige Passwörter erstellt.

## Merksatz

Ein Passwort ist wie ein Schlüssel.

Wenn der Schlüssel unter der Fußmatte liegt, bringt die beste Tür wenig.


## Offene Ports

Ein Port ist wie eine Tür zu einem Dienst.

Beispiele:

- Port 22 = SSH
- Port 80 = HTTP
- Port 443 = HTTPS
- Port 3306 = MySQL

Wenn ein Port offen ist, kann darüber ein Dienst erreicht werden.

Das ist nicht automatisch schlecht.

Aber:

- nur notwendige Ports sollten offen sein
- unnötige Ports erhöhen die Angriffsfläche
- Datenbank-Ports sollten normalerweise nicht öffentlich erreichbar sein

## Beispiel

Ein Webserver braucht meistens:

- Port 80 für HTTP
- Port 443 für HTTPS

Ein Datenbankserver sollte meistens nicht öffentlich erreichbar sein:

- Port 3306 für MySQL
- Port 5432 für PostgreSQL


## Schwachstellen in der Software

Software kann Fehler enthalten.

Manche Fehler sind Sicherheitslücken.

Wenn diese Sicherheitslücken bekannt sind, können Angreifer sie ausnutzen.

Beispiele:

- altes Betriebssystem
- alter Webserver
- alte Datenbank
- altes Docker-Image
- veraltetes Plugin
- veraltete Bibliothek

## Schutz

- Updates installieren
- Systeme regelmäßig prüfen
- alte Software entfernen
- Sicherheitsupdates ernst nehmen
- klare Update-Richtlinie festlegen


## Physische Sicherheitslücken

Nicht alle Angriffe passieren über das Netzwerk.

Manchmal reicht physischer Zugriff.

Beispiele:

- jemand steckt einen USB-Stick ein
- ein Laptop wird gestohlen
- ein Serverraum ist nicht abgeschlossen
- Bildschirme sind für fremde Personen sichtbar
- Passwörter kleben auf einem Zettel am Monitor

## Schutz

- Geräte sperren
- Bildschirme sperren
- Serverräume abschließen
- keine unbekannten USB-Sticks nutzen
- Festplatten verschlüsseln
- Passwörter nicht aufschreiben


## Fehlende Zertifikate

Zertifikate sind wichtig für Vertrauen und verschlüsselte Verbindungen.

Ohne Zertifikat oder mit falschem Zertifikat kann es Probleme geben.

Beispiele:

- Webseite läuft nur über HTTP
- Browser zeigt Sicherheitswarnung
- Zertifikat ist abgelaufen
- Zertifikat passt nicht zur Domain

## Schutz

- HTTPS nutzen
- gültige Zertifikate verwenden
- Zertifikate rechtzeitig erneuern
- HTTP auf HTTPS weiterleiten


## USB-Sticks

USB-Sticks können gefährlich sein.

Problem:

- Sie können Schadsoftware enthalten.
- Man weiß oft nicht, woher sie kommen.
- Menschen stecken sie aus Neugier ein.

## Beispiel aus dem Alltag

Jemand findet auf dem Parkplatz einen USB-Stick mit der Aufschrift:

```text
Gehaltsliste 2026
```

Viele Menschen wären neugierig.

Genau diese Neugier kann ausgenutzt werden.

## Schutz

- keine unbekannten USB-Sticks einstecken
- USB-Nutzung im Unternehmen regeln
- Virenschutz nutzen
- Mitarbeitende sensibilisieren


# Sicherheitsrichtlinien

Sicherheitsrichtlinien sind Regeln für den sicheren Umgang mit IT-Systemen.

Sie helfen, dass Sicherheit nicht vom Zufall abhängt.

Beispiele:

- Passwortrichtlinien
- Update-Richtlinien
- Backup-Richtlinien
- Zugriffsrichtlinien
- Richtlinien für Sicherheitsvorfälle
- Richtlinien für private Geräte
- Richtlinien für USB-Sticks


## Passwortrichtlinien

Eine Passwortrichtlinie legt fest, wie Passwörter aussehen und genutzt werden sollen.

Beispiele:

- Mindestlänge festlegen
- Groß- und Kleinbuchstaben verwenden
- Zahlen verwenden
- Sonderzeichen verwenden
- keine mehrfach verwendeten Passwörter
- keine Standardpasswörter
- MFA für wichtige Konten

## Beispiel

```text
Passwörter müssen mindestens 12 Zeichen lang sein.
Admin-Konten müssen MFA verwenden.
Passwörter dürfen nicht per E-Mail verschickt werden.
```


## Updates installieren

Updates schließen oft Sicherheitslücken.

Eine Update-Richtlinie legt fest:

- wann Updates installiert werden
- wer dafür verantwortlich ist
- wie kritische Updates behandelt werden
- ob vorher getestet wird
- ob vorher ein Backup erstellt wird

## Beispiel

```text
Kritische Sicherheitsupdates werden innerhalb von 48 Stunden geprüft und installiert.
Normale Updates werden monatlich installiert.
Vor wichtigen Updates wird ein Backup erstellt.
```


## Zugriffe begrenzen - Least Privilege Principle

Das **Least Privilege Principle** bedeutet:

Jede Person bekommt nur die Rechte, die sie wirklich braucht.

## Beispiel aus dem Alltag

In einem Hotel bekommt ein Gast nur den Schlüssel für sein Zimmer.

Er bekommt nicht den Generalschlüssel für alle Zimmer, die Küche und den Technikraum.

## IT-Beispiele

- normale Benutzer bekommen keine Admin-Rechte
- Praktikanten bekommen keinen Zugriff auf Produktivdaten
- externe Dienstleister bekommen nur zeitlich begrenzten Zugriff
- alte Konten werden deaktiviert
- Admin-Zugänge werden besonders geschützt


## Backups erstellen

Backups schützen vor Datenverlust.

Beispiele für Gründe:

- Hardwaredefekt
- versehentliches Löschen
- Ransomware
- Softwarefehler
- falsches Update
- Brand oder Diebstahl

## Gute Backup-Regeln

- wichtige Daten regelmäßig sichern
- zum Beispiel 1x pro Tag
- Wiederherstellung testen
- zum Beispiel 1x pro Monat
- Backups getrennt vom Hauptsystem speichern
- Backups verschlüsseln
- Verantwortlichkeit festlegen

## Merksatz

Ein Backup ist erst dann wirklich gut, wenn die Wiederherstellung getestet wurde.


## Vorfälle melden

Sicherheitsvorfälle müssen gemeldet werden.

Beispiele:

- verdächtige E-Mail
- verlorenes Gerät
- fremde Anmeldung
- Passwort wurde versehentlich geteilt
- unbekannter USB-Stick wurde eingesteckt
- ungewöhnliche Serveraktivität

## Warum melden wichtig ist

Wenn ein Vorfall früh gemeldet wird, kann schneller reagiert werden.

Wenn ein Vorfall verschwiegen wird, kann der Schaden größer werden.

## Beispiel

Jemand klickt auf einen Phishing-Link.

Schlecht:

- Person sagt nichts
- Angreifer kann weiter aktiv bleiben

Besser:

- Person meldet es sofort
- Passwort wird geändert
- Konto wird geprüft
- weitere Schäden können verhindert werden


# Firewall-Konfiguration

Eine Firewall kontrolliert, erlaubt oder blockiert Netzwerkverkehr.

Ziel:

- Netzwerkverkehr kontrollieren
- unnötige Zugriffe verhindern
- nur gewünschte Verbindungen erlauben
- Angriffsfläche verkleinern

## Einfache Erklärung

Eine Firewall ist wie ein Türsteher.

Sie prüft:

- Wer möchte rein?
- Von wo kommt die Verbindung?
- Zu welchem Port geht die Verbindung?
- Ist diese Verbindung erlaubt?
- Soll die Verbindung blockiert werden?

## Wichtige Begriffe

### IP-Adresse

Eine IP-Adresse ist eine Adresse in einem Netzwerk.

Beispiel:

```text
192.168.1.10
```

### Port

Ein Port ist ein Zugang zu einem bestimmten Dienst.

Beispiele:

- 22 = SSH
- 80 = HTTP
- 443 = HTTPS
- 3306 = MySQL

### Regel

Eine Firewall-Regel sagt:

- was erlaubt ist
- was blockiert ist
- für welchen Port
- von welcher Quelle
- zu welchem Ziel


## Beispiel: SSH über Port 22

SSH wird genutzt, um sich mit einem Server zu verbinden.

Typischer Port:

```text
22
```

Wenn Port 22 erlaubt ist, kann man sich per SSH verbinden.

Wenn Port 22 nicht erlaubt ist, funktioniert die Verbindung nicht.


## Beispiel aus dem Unterricht: EC2-Maschine und Security Group

Wir haben in der Cloud eine EC2-Maschine erstellt.

Eine EC2-Maschine ist ein virtueller Server in AWS.

Zu dieser Maschine gehört eine **Security Group**.

Eine Security Group ist eine Art Firewall-Regelwerk für die EC2-Maschine.

## Schritt 1: EC2-Server erstellen

Wir haben einen Server erstellt.

Danach wollten wir uns per SSH verbinden.

Dafür wird Port 22 benötigt.

## Schritt 2: Port 22 erlauben

In der Security Group wurde eine eingehende Regel gesetzt:

```text
Typ: SSH
Port: 22
Quelle: erlaubte IP-Adresse oder 0.0.0.0/0
```

Dadurch war eine SSH-Verbindung möglich.

## Schritt 3: Verbindung testen

Solange Port 22 erlaubt war, konnte man sich mit der Maschine verbinden.

Beispiel:

```bash
ssh -i key.pem ubuntu@SERVER-IP
```

## Schritt 4: Firewall-Regel löschen

Danach wurde die Regel für Port 22 gelöscht.

Das bedeutet:

Die Erlaubnis für SSH existiert nicht mehr.

## Schritt 5: Verbindung erneut testen

Danach konnte man die Maschine nicht mehr per SSH erreichen.

Das zeigt:

Eine Firewall blockiert nicht unbedingt aktiv durch eine neue Block-Regel.

Oft reicht es, wenn eine Erlaubnis fehlt.

## Wichtige Erkenntnis

Wenn keine Regel existiert, die SSH erlaubt, wird die Verbindung blockiert.

Das ist ein Beispiel für das Prinzip:

```text
Alles ist verboten, außer es wurde ausdrücklich erlaubt.
```

Dieses Prinzip nennt man:

```text
Default Deny
```


## Beispiel-Regeln

### Sinnvolle Regel

```text
Erlaube Port 443 von überall zum Webserver.
```

Begründung:

HTTPS soll für Benutzer erreichbar sein.

### Riskante Regel

```text
Erlaube Port 3306 von überall zur Datenbank.
```

Begründung:

Eine Datenbank sollte normalerweise nicht öffentlich erreichbar sein.

### Sinnvolle Admin-Regel

```text
Erlaube Port 22 nur von der Admin-IP.
```

Begründung:

SSH wird für Administration gebraucht, sollte aber nicht für alle offen sein.

### Schlechte Regel

```text
Erlaube alle Ports von überall.
```

Begründung:

Dadurch wird die Angriffsfläche unnötig groß.


## Sicherheitsfrage

Bei jeder Portfreigabe sollte man fragen:

- Muss dieser Dienst erreichbar sein?
- Für wen muss er erreichbar sein?
- Muss er aus dem Internet erreichbar sein?
- Reicht ein internes Netzwerk?
- Gibt es eine Firewall-Regel?




# Kurze Wiederholung

## Grundziele

- Vertraulichkeit
- Integrität
- Verfügbarkeit

## Angriffsvektoren

- Phishing
- schwache Passwörter
- offene Ports
- veraltete Software
- physische Sicherheitslücken
- fehlende Zertifikate
- USB-Sticks

## Sicherheitsrichtlinien

- Passwortrichtlinien
- Updates installieren
- Zugriffe begrenzen
- Backups erstellen und testen
- Vorfälle melden

## Firewall

- kontrolliert Netzwerkverkehr
- erlaubt oder blockiert Verbindungen
- arbeitet nach Regeln
- fehlende Erlaubnis kann Verbindung verhindern
- Beispiel: Security Group bei EC2
- Port 22 erlaubt = SSH möglich
- Port 22 gelöscht = SSH nicht mehr möglich


# Merksätze

- Ein Angriffsvektor ist ein möglicher Weg für einen Angriff.
- Phishing nutzt oft menschliches Verhalten aus.
- Ein schwaches Passwort ist wie ein schlechter Schlüssel.
- Offene Ports sind wie offene Türen.
- Updates schließen oft bekannte Sicherheitslücken.
- Least Privilege bedeutet: nur die Rechte, die wirklich gebraucht werden.
- Eine Firewall ist wie ein Türsteher für Netzwerkverkehr.
- Eine Security Group ist eine Firewall für eine EC2-Maschine.
- Wenn Port 22 nicht erlaubt ist, funktioniert SSH nicht.
- Default Deny bedeutet: Alles ist verboten, außer es wurde erlaubt.
- Ein Backup muss getestet werden.
- Sicherheitsrichtlinien helfen nur, wenn sie verstanden und angewendet werden.
