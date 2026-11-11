# 3DPPM – Häufige Fragen (FAQ)

[English](FAQ_EN.md)

Antworten zu Einrichtung, Updates und der täglichen Arbeit mit 3DPPM. Die Hinweise unter den Antworten nennen die passenden Abschnitte der Offline-Hilfe.

- [Installation, Datenbank und Updates](#faq-installation)
- [Daten sichern und erhalten](#faq-data)
- [Profile, Versuche und Parameter](#faq-profiles)
- [3MF, Auswertung und Unterstützung](#faq-workflow)

<a id="faq-installation"></a>

## Installation, Datenbank und Updates

<a id="faq-mysql"></a>

### Unterstützt 3DPPM externe Datenbanken wie MySQL?

Ja. Neben der lokalen SQLite-Datei unterstützt 3DPPM eine externe MySQL-Datenbank. Wählen Sie Einstellungen → Datenbank → Extern (MySQL). Die Serveradministration muss eine eigene leere Datenbank bereitstellen; 3DPPM erstellt keine Serverdatenbank und überträgt Ihre SQLite-Daten nicht automatisch. Tragen Sie die Verbindung ein, prüfen Sie sie und starten Sie nach der Einrichtung neu. Bei mehreren Rechnern benötigen die zugehörigen Dateien zusätzlich ein gemeinsam erreichbares Data-Verzeichnis.

**Ausführliche Anleitung in der Offline-Hilfe** — Einstellungen → Zentrale MySQL-Datenbank einrichten.

<a id="faq-inplace-update"></a>

### Wie aktualisiere ich 3DPPM im bestehenden Programmordner (Inplace-Update)?

Öffnen Sie Einstellungen → Allgemein → Updates. Prüfen Sie auf Updates oder wählen Sie ein vollständiges heruntergeladenes ZIP. Schließen Sie andere Instanzen und MySQL-Clients. Prüfen Sie Version und Schema und bestätigen Sie Sichern und Update installieren. Der Assistent sichert Programm, aktive Datenbank und Einstellungen vor dem Austausch; persönliche Daten, Bilder und Konfiguration bleiben erhalten. Nur die EXE auszutauschen genügt nicht. Fehlt Ihrer bisherigen Version der Assistent, folgen Sie der Anleitung zur manuellen Übernahme des vollständigen Programmordners.

**Ausführliche Anleitung in der Offline-Hilfe** — Einstellungen → 3DPPM aktualisieren.

<a id="faq-master-data-update"></a>

### Wie aktualisiere ich das Stammdatenpaket?

Sichern Sie vorher die Datenbank. Wählen Sie Einstellungen → Updates → Stammdatenpaket und öffnen Sie die JSON-Datei. Vergleichen Sie in der Vorschau Bisher und Nachher und bestätigen Sie die angezeigten Änderungen. Das Paket ergänzt oder aktualisiert anhand stabiler IDs und löscht keine vorhandenen Datensätze oder Beziehungen. Prüfen Sie deshalb auch Änderungen an eigenen Einträgen mit derselben ID. Gleichnamige Einträge mit anderer ID werden nicht automatisch zusammengeführt; Konflikte brechen die Übernahme ab. Kontrollieren Sie anschließend die betroffenen Stammdaten. Ein Stammdatenpaket aktualisiert nicht das Programm.

**Ausführliche Anleitung in der Offline-Hilfe** — Stammdaten – gemeinsame Grundlagen → Ein Stammdatenpaket in eine zweite Installation übernehmen.

<a id="faq-permission-denied"></a>

### Warum erscheint beim Start unter Program Files „Zugriff verweigert“ (WinError 5)?

Die portable Anwendung benötigt einen beschreibbaren Programmordner für ihre lokalen Dateien und Einstellungen. Ein geschützter Ordner wie C:\Program Files kann Schreibzugriffe verhindern. Entpacken Sie das vollständige Paket in einen Ordner, in dem Ihr Windows-Benutzer schreiben darf. Sichern Sie bei einer bestehenden Installation vorher Daten und Einstellungen und prüfen Sie danach die konfigurierten Pfade.

**Ausführliche Anleitung in der Offline-Hilfe** — Erste Schritte und Vorbereitung → 1. Programmpaket entpacken und starten.

<a id="faq-data"></a>

## Daten sichern und erhalten

<a id="faq-backup"></a>

### Was muss ich sichern: Datenbank, Dateien oder Einstellungen?

Alle drei Bereiche haben einen eigenen Zweck. Die Datenbank enthält strukturierte Anwendungsdaten; Profil-, Bild- und Versuchsdateien liegen separat. Die Konfiguration enthält Einstellungen und Pfade. Verwenden Sie die angebotenen Sicherungsarten unter Einstellungen → Sicherung und bewahren Sie zusammengehörige Stände auf. Auch bei MySQL ersetzt eine Datenbanksicherung nicht die Sicherung der zugehörigen Dateien.

**Ausführliche Anleitung in der Offline-Hilfe** — Einstellungen → Drei getrennte Sicherungsarten.

<a id="faq-move-database"></a>

### Wie verwende ich meine vorhandene Datenbank nach einem Ordnerwechsel weiter?

Erstellen Sie zuerst eine Datenbanksicherung und schließen Sie 3DPPM. Übernehmen Sie die gesicherte Datenbank nach dem beschriebenen Ablauf in einen eigenen Datenordner. Wählen Sie anschließend unter Einstellungen → Datenbank den Zielordner und Datenbank übernehmen. Die Auswahl eines leeren Ordners verschiebt Ihre bisherige Datenbank nicht. Prüfen Sie nach dem Neustart bekannte Profile und Versuche und richten Sie die getrennte Dateiablage passend ein.

**Ausführliche Anleitung in der Offline-Hilfe** — Einstellungen → Vorhandene Datenbank in einen anderen Ordner übernehmen.

<a id="faq-profiles"></a>

## Profile, Versuche und Parameter

<a id="faq-profile-experiment"></a>

### Was unterscheidet ein Profil, einen Versuch und eine Parameterdefinition?

Die Parameterdefinition in den Stammdaten beschreibt eine Einstellung mit Datentyp, Wertebereich und Slicerzuordnung. Das Profil verbindet die Druckumgebung mit konkreten Parameterwerten und Bewertungskriterien. Ein Versuch dokumentiert einen einzelnen Test mit eigenem Parameterstand, Ergebnissen und Messwerten. Neue Versuche übernehmen den Profilstand als Snapshot; spätere Profiländerungen ändern bestehende Versuchssnapshots nicht.

**Ausführliche Anleitung in der Offline-Hilfe** — Profildaten – Grundlage Ihrer Versuche → Profil, Parameterdefinition und Versuch unterscheiden.

<a id="faq-missing-parameters"></a>

### Warum fehlt ein Parameter in der Auswahl für mein Profil?

Prüfen Sie die aktive Definition und ihre Zuordnung zum ausgewählten Slicer sowie die gewählte Profilart Drucker, Prozess oder Filament. Bereits verwendete oder rechts ausgewählte Parameter sind links ausgeblendet. Prüfen Sie außerdem Suche, Filter Quelle und das gewählte Basisprofil. Ein fehlender Basiswert allein schließt eine passende aktive Slicerdefinition nicht aus: Sie kann unter Quelle Slicer mit ihrem Stammdaten-Standardwert angeboten werden.

**Ausführliche Anleitung in der Offline-Hilfe** — Profildaten – Grundlage Ihrer Versuche → Parameterquelle und technische Namen.

<a id="faq-parameter-source"></a>

### Was bedeutet die Parameterquelle „Basisprofil“ oder „Slicer“?

Basisprofil bedeutet, dass der effektive Wert aus dem gewählten Basisprofil einschließlich seiner Vererbung stammt. Slicer kennzeichnet zusätzliche passende Parameter aus den Profilparameter-Stammdaten, für die kein gültiger Basiswert verfügbar ist. Ihre Vorbelegung kommt aus dem Standardwert der Stammdaten und wird nicht aus dem laufenden Slicerprogramm gelesen. Der Filter Quelle bietet Alle, Basisprofil und Slicer.

**Ausführliche Anleitung in der Offline-Hilfe** — Profildaten – Grundlage Ihrer Versuche → Parameterquelle und technische Namen.

<a id="faq-technical-name"></a>

### Wie finde ich einen Parameter über seinen technischen Namen?

Geben Sie den technischen Namen in die Suche der verfügbaren Parameter ein, beispielsweise initial_layer_acceleration. Die Suche berücksichtigt die Spalte auch dann, wenn sie ausgeblendet ist. Über die Spaltenauswahl können Sie Technischer Name zusätzlich sichtbar machen.

**Ausführliche Anleitung in der Offline-Hilfe** — Profildaten – Grundlage Ihrer Versuche → Parameterquelle und technische Namen.

<a id="faq-percent-values"></a>

### Kann ich Parameterwerte absolut oder in Prozent eingeben?

Bei entsprechend unterstützten Parametern sind absolute und relative Angaben möglich, beispielsweise 6000 oder 15%. Das Prozentzeichen bleibt Teil des Werts; es erfolgt keine ungefragte Umrechnung. Datentyp und Wertebereich der Parameterdefinition gelten weiterhin. Bei skalaren Basiswerten aus einer Liste wird der erste Eintrag als Ausgangswert genutzt; echte Listenparameter bleiben Listen.

**Ausführliche Anleitung in der Offline-Hilfe** — Profildaten – Grundlage Ihrer Versuche → Basiswerte, Listen und Prozentangaben.

<a id="faq-workflow"></a>

## 3MF, Auswertung und Unterstützung

<a id="faq-3mf-mapping"></a>

### Warum fehlen nach dem 3MF-Import Drucker, Düse oder Filament?

Ein Wert aus der Datei kann fehlen oder keiner eindeutigen Stammdatenzuordnung entsprechen. Prüfen Sie die offenen Angaben im Abgleich und die Regeln unter Stammdaten → 3MF-Masterdaten-Mappings. Korrigieren Sie die passende Regel und lesen Sie dieselbe Datei erneut ein, um das Ergebnis zu kontrollieren.

**Ausführliche Anleitung in der Offline-Hilfe** — Stammdaten – gemeinsame Grundlagen → 3MF-Stammdaten-Zuordnungen prüfen und korrigieren.

<a id="faq-object-assignment"></a>

### Wie ordne ich einem Versuch ein Objekt auf einer bestimmten Druckplatte zu?

Öffnen Sie die Objektzuordnung für den Versuch, wählen Sie die passende Druckplatte und anschließend das gewünschte Objekt. Prüfen Sie nach dem Speichern die Zuordnung am Versuch. Im selben Ablauf können Sie eine bestehende Zuordnung ändern oder entfernen. Die Anleitung zeigt dies an einer 3MF mit zwei Druckplatten.

**Ausführliche Anleitung in der Offline-Hilfe** — Versuche vorbereiten und dokumentieren → Objekte und Druckplatten zuordnen.

<a id="faq-3mf-export"></a>

### Kann ich mehrere Versuche gemeinsam als 3MF exportieren?

Ja, wenn die Versuche für den gemeinsamen Export zusammenpassen. Eine 3MF hat einen gemeinsamen Druckerstand; unterschiedliche Druckerwerte oder konkurrierende Basisstände können den Export verhindern. Prüfen Sie die Hinweise und die Exportreferenzen. Sie können auch einen einzelnen Versuch exportieren und die erzeugte Datei anschließend im 3MF-Analyzer auf Platten, Objekte und Einstellungen kontrollieren.

**Ausführliche Anleitung in der Offline-Hilfe** — Profildaten – Grundlage Ihrer Versuche → Einen Versuch oder ein ganzes Projekt als 3MF exportieren.

<a id="faq-blocked-action"></a>

### Warum ist eine Aktion oder ein Statuswechsel gesperrt?

Workflow-Regeln können einen Übergang von Voraussetzungen abhängig machen, etwa von vollständigen Angaben oder einer Bewertung. Lesen Sie den Hinweis zur gesperrten Aktion und ergänzen Sie die erforderlichen Daten. Die Regeln werden in den Einstellungen konfiguriert; den Statuswechsel führen Sie am Profil oder Versuch aus.

**Ausführliche Anleitung in der Offline-Hilfe** — Einstellungen → Workflow-Regeln.

<a id="faq-rating"></a>

### Warum verändert die Kriteriengewichtung die Gesamtbewertung?

Die Gesamtbewertung berücksichtigt die Bewertungen der einzelnen Kriterien mit ihrer jeweiligen Gewichtung. Ein stärker gewichtetes Kriterium beeinflusst das Ergebnis stärker. Prüfen Sie Kriterien, Gewichte und Einzelbewertungen gemeinsam und nutzen Sie die Vorschau, bevor Sie Ergebnisse vergleichen.

**Ausführliche Anleitung in der Offline-Hilfe** — Ranking und Kriterienwichtung → Die gewichtete Gesamtbewertung lesen.

<a id="faq-help-zoom"></a>

### Kann ich die Hilfe unabhängig vom Programm bedienen und zoomen?

Das Hilfefenster lässt sich unabhängig bedienen. Mit Strg und Mausrad ändern Sie die Textgröße der Hilfe; die Anwendung behält ihre eigene Skalierung. Nutzen Sie Inhalt, Suche oder Stichwörter für den Wechsel zu einem Thema. Die genaue Bedienung und die Bildansicht sind im Hilfekapitel erläutert.

**Ausführliche Anleitung in der Offline-Hilfe** — Hilfe bedienen und unabhängig zoomen → Im Handbuch navigieren.

<a id="faq-report-error"></a>

### Wie melde ich einen Fehler, und welche Dateien gehören dazu?

Aktivieren Sie bei Bedarf Debug-Logging unter Einstellungen → Allgemein und starten Sie 3DPPM neu. Reproduzieren Sie den Fehler und notieren Sie Version, Zeitpunkt, Ausgangslage, Schritte sowie erwartetes und tatsächliches Ergebnis. Fügen Sie einen lesbaren Screenshot und Kopien von 3DPPM.log, 3DPPM-debug.log und 3DPPM-crash.log aus logs bei. Die ausführliche Anleitung erklärt fehlende oder leere Dateien und führt zum öffentlichen Community-Issue; prüfen Sie Anhänge vor dem Hochladen auf vertrauliche Inhalte.

**Ausführliche Anleitung in der Offline-Hilfe** — Fehler berichten und Debug-Logging verwenden → Vorlage für den Bericht.
