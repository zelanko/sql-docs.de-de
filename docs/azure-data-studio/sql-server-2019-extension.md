---
title: SQL Server-2019-Erweiterung (Vorschau)
titleSuffix: Azure Data Studio
description: 2019-Vorschau von SQL Server-Erweiterung für Azure Data Studio
ms.custom: seodec18
ms.date: 05/09/2019
ms.reviewer: alayu; sstein
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: yualan
ms.author: alayu
manager: craigg
ms.openlocfilehash: 045152d472029c1ff3fe50230b20b69a851d9dcb
ms.sourcegitcommit: 603d5ef9b45c2f111d36d11864dc032917e4a321
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/08/2019
ms.locfileid: "65450100"
---
# <a name="sql-server-2019-extension-preview"></a>SQL Server-2019-Erweiterung (Vorschau)

Die SQL Server-2019-Erweiterung (Vorschau) bietet vorschauunterstützung für die neuen Features und Tools, die Unterstützung des Protokollversands [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]. Dies schließt die Unterstützung für die Vorschauversion [big Data-Cluster für SQL Server-2019](../big-data-cluster/big-data-cluster-overview.md), eine integrierte [notebookfeatures](../big-data-cluster/notebooks-guidance.md), und eine PolyBase [Create External Table-Assistenten](../relational-databases/polybase/data-virtualization.md?toc=/sql/toc/toc.json).

## <a name="install-the-sql-server-2019-extension-preview"></a>Installieren der Erweiterung für SQL Server-2019 (Vorschau)

Klicken Sie zum Installieren der SQL Server-2019-Erweiterungs (Vorschauversion) herunter, und installieren Sie die zugehörigen VSIX-Datei.

1. Laden Sie die SQL Server-2019-Erweiterung (Vorschauversion) VSIX-Datei in ein lokales Verzeichnis herunter:

   |Platform|Herunterladen|Veröffentlichungsdatum|Version
   |:---|:---|:---|:---|
   |Windows|[.vsix](https://go.microsoft.com/fwlink/?linkid=2092118)|8 Mai 2019 |0.13.0
   |macOS|[.vsix](https://go.microsoft.com/fwlink/?linkid=2092117)|8 Mai 2019 |0.13.0
   |Linux|[.vsix](https://go.microsoft.com/fwlink/?linkid=2092116)|8 Mai 2019 |0.13.0

1. Wählen Sie in Azure Data Studio **Erweiterung aus der VSIX-Paket installieren** aus der **Datei** Menü, und wählen Sie die heruntergeladene VSIX-Datei.

1. Wählen Sie **Ja** bei der Aufforderung zum Bestätigen der Installation und warten Sie, bis die Benachrichtigung, die die Installation erfolgreich war.

1. Wählen Sie **Reload** zum Aktivieren der Erweiterung (nur beim ersten eine Erweiterung der Installation erforderlich).

1. Nach erneutem Laden, wird die Erweiterung Abhängigkeiten zu installieren. Sehen Sie den Fortschritt im Ausgabefenster angezeigt, und es kann einige Minuten dauern.

1. Nach den Abhängigkeiten die abgeschlossen Sie Installation, schließen Sie und erneut öffnen Sie Studio für Azure Data. Die **SQL Server-big Data-Cluster** Verbindungstyp ist nicht verfügbar, solange Sie Azure Data Studio neu starten.

## <a name="changes-in-release-0121"></a>Änderungen in Version 0.12.1

* Die **SQL Server-big Data-Cluster** Verbindungstyp wurde in dieser Version entfernt. Alle Funktionen, die zuvor von SQL Server-Verbindung für die big Data-Cluster zur Verfügung steht jetzt in der SQL Server-Verbindung.
* Durchsuchen von HDFS finden Sie unter den **Datendienste** Ordner
* Für Notebooks die die PySpark und andere big Data-Kernels funktionsfähig, wenn es sich bei Verbindung mit der master SQL Server-Instanz in Ihrer SQL Server-big Data-Cluster.
* Erstellen Sie externer Tabellen-Assistent:
  * Unterstützung für externe Tabelle, die vorhandene externe Datenquelle zu erstellen.
  * Leistungsverbesserungen in den Assistenten.
  * Verbesserte Behandlung von Objektnamen mit Sonderzeichen. In einigen Fällen verursacht dies zum Fehlschlagen des Assistenten
  * Verbesserungen der Zuverlässigkeit für die Seite Objekt zuordnen.
  * Entfernte-Systemdatenbanken – 'DWConfiguration', 'DWDiagnostics', 'DWQueue' - aus der Dropdownliste "Datenbanken".
  * Unterstützung für das External File Format-Objekt-Name der Einstellung in der **Create External Table aus CSV-Dateien** Assistenten.
  * Eine Schaltfläche zum Aktualisieren der ersten Seite des hinzugefügt der **Create External Table aus CSV-Dateien** Assistenten.

## <a name="release-notes-v0110"></a>Anmerkungen zu dieser Version (v0.11.0)

* Unterstützung für Jupyter-Notebook, insbesondere Unterstützung für die Python3 und Spark-Kernel wurde in Azure Data Studio verschoben. Diese Erweiterung ist nicht mehr erforderlich, um die Notebooks verwenden.
* Mehrere Fehlerbehebungen in den Assistenten für die externen Daten:
  * Oracle-datentypzuordnungen wurden Änderungen, die im Lieferumfang von SQL Server 2019 CTP 2.3 entsprechend aktualisiert.
  * Ein Problem behoben, in denen wurden neue Schemas, die in die Table-Steuerelemente Zuordnung eingegeben verloren gehen.
  * Ein Problem behoben, in dem einen Datenbankknoten in der tabellenzuordnungen überprüfen nicht alle Tabellen und Sichten, die zu überprüfende führten.


## <a name="release-notes-v0102"></a>Anmerkungen zu dieser Version (v0.10.2)
### <a name="sql-server-2019-support"></a>Unterstützung für SQL Server-2019
Unterstützung für SQL Server-2019 wurde aktualisiert. Für das Herstellen einer Verbindung mit einer SQL Server für Big Data-Cluster-Instanz eine neue _Datendienste_ Ordner wird angezeigt, in der Explorer-Struktur. Dies hat Startpunkte für Aktionen wie z. B. ein neues Notebook für die Verbindung öffnen, Spark-Aufträge übermitteln und Arbeiten mit HDFS. Beachten Sie, dass bei einigen Aktionen wie z. B. _Create External Data_ über eine HDFS-Datei/Ordner, der _Vorschau von SQL Server-2019_ Erweiterung muss installiert sein.

### <a name="notebook-support"></a>Notebook-Unterstützung
Mit der Notebook-Benutzeroberfläche in dieser Version haben wir wichtige Aktualisierungen vorgenommen. Unser Fokus lag auf erleichtert, Notizbücher lesen, die für Sie freigegeben wurden. Dies bedeutete, entfernen alle Kontrollkästchen, um Zellen beschreiben, es sei denn, die ausgewählt oder gezeigt, Hover-Unterstützung hinzufügen, für leichte auf Zellenebene Aktionen ohne eine Zelle auswählen und Klarstellung Ausführungsstatus durch das Hinzufügen der Ausführungsanzahl, die einen animierten _Anhalten ausgeführt_ Schaltfläche und vieles mehr. Wir auch Tastenkombinationen für hinzugefügt _neues Notizbuch_ (`Ctrl+Shift+N`), _ausführen Zelle_ (`F5`), _neue Codezelle_ (`Ctrl+Shift+C`),  _Neue Textzelle_ (`Ctrl+Shift+T`). Die Zukunft streben wir damit alle wichtige startfähige Aktionen vom Kontextmenü also lassen Sie uns wissen, was Sie versäumt haben wird.

Weitere Verbesserungen und Fehlerbehebungen enthalten:
* Die _Vorschau von SQL Server-2019_ Erweiterung nun Anweisungen verwendet, wählen Sie ein Installationsverzeichnis ein, für die Python-Abhängigkeiten. Darüber hinaus nicht mehr enthält, Python, die in der `.vsix file`, Reduzieren der Gesamtgröße der Erweiterung. Die Python-Abhängigkeiten sind für die Spark- und Python3-Kernel, zu unterstützen, damit die Installation dieser Erweiterung erforderlich ist, um diese verwenden, erforderlich.
* Unterstützung für das Starten eines neuen Notebooks über die Befehlszeile wurde hinzugefügt. Starten Sie mit den Argumenten `--command=notebook.command.new --server=myservername` sollte ein neues Notebook zu öffnen und eine Verbindung mit diesem Server herstellen.
* Leistungskorrekturen für Notebooks, die mit einer großen Länge in Zellen. Wenn codezellen mehr als 250 Zeilen sind, müssen sie eine Bildlaufleiste hinzugefügt.
* Verbesserte Unterstützung für ipynb-Datei. Version 3 oder höher wird jetzt unterstützt. Beachten Sie, dass zum Speichern von Dateien auf Version 4 oder höher aktualisiert werden.
* Die `notebook.enabled` wurde von Benutzer-Einstellung entfernt jetzt die integrierten Viewer ist im Notebook stabil
* Design "hoher Kontrast" wird jetzt in diesem Fall mit einer Zahl mit dem das Objektlayout unterstützt.
* #3680 Ausgaben, in dem auch eine Anzahl von gezeigt festen `,,,` Zeichen falsch
* Für Zellen festen #3602-Editor nicht mehr angezeigt wird, nach Azure Data Studio verlassen
* Unterstützung für Raster-Ansichten verwenden hinzugefügt wurde die `application/vnd.dataresource+json` Ausgabe MIME-Typ. Dies bedeutet, dass viele Notebooks, die diese verwenden (z. B. durch Festlegen von `pd.options.display.html.table_schema` in einem Python-Notebook) müssen nützlicher tabellarische Ausgaben festen #3959 Azure Data Studio, Herunterfahren Notebook-Server, versucht zweimal nach dem Schließen des Notebooks

#### <a name="known-issues"></a>Bekannte Probleme
* Öffnen Sie ein Notebook wird das Dialogfeld "Python installieren" angezeigt. Abbrechen der Installation führt zu den Kernels und Anhängen an Dropdownlisten nicht angezeigt. erwartete Werte. Die problemumgehung besteht darin, die Python-Installation abzuschließen.
* Wenn ein Notebook mit einem Kernel geöffnet wird, die nicht unterstützt wird, den Kernel und _Anfügen an_ Dropdownlisten führt dazu, dass Azure Data Studio nicht mehr reagiert. Sie müssen Azure Data Studio zu schließen, und stellen Sie sicher, Sie verwenden einen Kernel, die unterstützt wird (Python3, Spark | R, Spark | Scala, PySpark, PySpark3)
* Spark-Benutzeroberfläche Link schlägt fehl, wenn PySpark3 oder andere Spark-Kernel für den SQL Server-Endpunkt verwenden. Als problemumgehung klicken Sie auf die Spark-Benutzeroberfläche, über das Dashboard und das Herstellen einer Verbindung mit der SQL Server big Data-Cluster-Verbindungstyp aus, wie dies mit den richtigen Link für Spark-Benutzeroberfläche hat

### <a name="extensibility-improvements"></a>Verbesserungen der Erweiterbarkeit
In dieser Version wurden eine Reihe von Verbesserungen, mit denen Extender hinzugefügt.
* Ein neues `ObjectExplorerNodeProvider` -API können Sie Erweiterungen für die Ordner in SQL Server oder anderen Verbindungsknoten beitragen. Dies ist die `Data Services` Knoten unter 2019 für SQL Server-Instanzen hinzugefügt, aber verwendet werden, um die Überwachung oder eine andere Ordner einfach die Benutzeroberfläche hinzufügen.
* Zwei neue Kontext Schlüsselwerte sind verfügbar, die ein-/ausblenden-Beiträge an das Dashboard zu unterstützen.
  * `mssql:iscluster` Gibt an, ob dies eine SQL Server 2019 Big Data-Cluster
  * `mssql:servermajorversion` hat die Server-Version (15 für SQL Server-2019, 14 für SQL Server 2017 und So weiter). Dies kann helfen, wenn Funktionen nur für SQL Server 2017 oder höher, z. B. angezeigt werden soll.


## <a name="release-notes-v080"></a>Anmerkungen zu dieser Version (Version 0.8.0)
*Notebooks*:
* Hinzufügen von Zellen vor und nach vorhandenen Zellen werden jetzt mit der Schaltfläche "Weitere Aktionen" Zelle
* **Neue Verbindung hinzufügen** Option wurde hinzugefügt, die Verbindungen in der Dropdownliste "Fügen Sie zu"
* Ein **Notebook-Abhängigkeiten installieren** Befehl wurde mit Python-Paket-Updates zu unterstützen, und lösen Fälle, in dem Installation sich teilweise auf die Anwendung schließen angehalten wurde. Dies kann ausgeführt werden, über die befehlspalette (verwenden Sie `Ctrl/Cmd+Shift+P` und `Reinstall Notebook Dependencies`)
* Das PROSE-Python-Paket wurde auf 1.1.0 aktualisiert und umfasst eine Reihe von Fehlerbehebungen. Verwenden der **Notebook-Abhängigkeiten installieren** Befehl aus, um dieses Paket zu aktualisieren.
* Ein **Ausgabe löschen** Befehl wird jetzt unterstützt, indem Sie auf die **Weitere Aktionen** zellenschaltfläche
* Die folgenden festen Kunden gemeldeten Probleme:
  * Notebook-Sitzung konnte nicht auf Windows aufgrund von Problemen mit Pfad gestartet.
  * Notebook konnte aus dem Stammordner des Laufwerks, z. B. C:\ oder D:\ nicht gestartet werden
  * [#2820](https://github.com/Microsoft/azuredatastudio/issues/2820) kann nicht zum Bearbeiten des Notebooks, die von WERBEEINBLENDUNGEN in Visual Studio Code erstellt
  * Spark-Benutzeroberfläche-Link funktioniert jetzt beim Ausführen eines Spark-Kernels
  * Umbenannt von "Verwalteten Pakete" auf "Pakete installieren"

*Erstellen von externen Daten*:

* Fehlermeldungen kopiert werden und wurden aufgeteilt in eine Zusammenfassungsdaten und detaillierten Ansicht für einfachere
* Verbesserte Layout der Benutzeroberfläche und deutlich verbesserte Zuverlässigkeit und Fehlerbehandlung
* Die folgenden festen Kunden gemeldeten Probleme:
  * Tabellen mit ungültigen spaltenzuordnungen werden als deaktiviert angezeigt, und eine Warnung wird den Fehler erläutert.

## <a name="release-notes-v072"></a>Anmerkungen zu dieser Version (v0.7.2)
* Azure-Ressourcen-Explorer ist nun in Azure Data Studio integriert und von dieser Erweiterung entfernt wurde. Vielen Dank für Ihr Feedback dazu.
* Verbesserte Leistung von Notebooks mit vielen Markdown-Zellen.
* Automatische Größenänderung codezellen im Notebook. Dies hat immer noch eine Mindestgröße, die basierend auf der Symbolleiste der Zelle.
* Benachrichtigen Sie Benutzer aus, wenn der Notebook Abhängigkeiten installiert. Auf Windows dauert insbesondere dies sehr lange, damit Benachrichtigungen nun in der Aufgabenansicht angezeigt werden.
* Neuinstallation Notebook-Abhängigkeiten zu unterstützen. Dies ist hilfreich, wenn der Benutzer zuvor Studio für Azure Data eines durch die Installation geschlossen werden.
* Unterstützung im Notebook-zellenausführung Abbrechen.
* Verbesserte Zuverlässigkeit beim Erstellen von externen Daten-Assistenten verwenden, auftreten, insbesondere wenn Verbindungsfehler.
* Blockieren Sie mithilfe des Assistenten für externe Daten zu erstellen, wenn PolyBase nicht aktiviert ist oder auf dem Zielserver ausgeführt wird.
* Rechtschreibung und Benennung von Fehlerbehebungen im Zusammenhang mit SQL Server-2019 und externe Daten zu erstellen.
* Eine große Anzahl von Fehlern entfernt aus der Azure Data Studio Debugging-Konsole.

##  <a name="sql-server-2019-big-data-cluster-support"></a>Unterstützung für SQL Server 2019 Big Data-Cluster

* Klicken Sie auf **Verbindung hinzufügen** in *Objekt-Explorer* , und wählen Sie **SQL Server-big Data-Cluster** als Verbindungstyp.

   > [!TIP]
   > Wenn Sie nicht sehen die **SQL Server-big Data-Cluster** Verbindungstyp, starten Sie Azure Data Studio neu.

* Geben Sie den Hostnamen oder die IP-Adresse der clusterendpunkt sowie den Benutzernamen und das Kennwort, die die Verbindung verwendet.
* Optional, enthalten einen Anzeigenamen in den **Namen** Feld.
* Klicken Sie auf **Connect** und allgemeine Aufgaben klicken Sie dann starten auf dem Dashboard Durchsuchen **HDFS** im Objekt-Explorer, und die Ausführung von Tasks im Kontext von dort aus.
* Um einen Spark-Auftrag für den Cluster zu übermitteln, mit der Maustaste, auf den Serverknoten im *Objekt-Explorer* , und wählen Sie **Submit Spark Job** , um das Dialogfeld "Senden" zu öffnen.
* Um ein Notebook zu öffnen, finden Sie im nächsten Abschnitt aus.

Weitere Informationen finden Sie unter [Big Data-Cluster](../big-data-cluster/big-data-cluster-overview.md).


## <a name="azure-data-studio-notebooks"></a>Azure Data Studio Notebooks

* Öffnen Sie ein Notebook in einem der folgenden Methoden:
  * Öffnen Sie ein neues Notebook, aus der *Befehlspalette*.
  * Öffnen Sie die HDFS-Objekt-Explorer-Struktur für eine SQL Server-2019 big Data-Cluster und entweder ein:
    * Klicken Sie mit der rechten Maustaste auf den Serverknoten und wählen Sie **neuen Jupyter Notebooks**.
    * Klicken Sie mit der rechten Maustaste auf eine CSV-Datei, und wählen **Analysieren im Notebook**.
  * Öffnen Sie eine vorhandene ipynb-Datei aus dem **Datei** Menü- oder Datei-Explorer *(ipynb-Dateien müssen auf Version 4 oder höher, um das Laden von aktualisiert werden)*
* Wählen Sie einen Kernel. Wählen Sie für die Ausführung der lokalen Notebooks Python 3 ein. Wählen Sie für die Remoteausführung, PySpark oder Spark | Scala.
* Wählen Sie einen SQL Server-big Data-Cluster-Endpunkt für die Verbindung, wenn Remote ausgeführten (Dies ist nicht erforderlich, für die lokale Entwicklung mit Python 3).
* Hinzufügen von Code oder in Markdown Zellen, über die Schaltflächen im Header Notebooks. Zellen, die das Papierkorbsymbol auf der linken Seite jeder Zelle zu entfernen.
* Führen Sie Zellen mit die Wiedergabeschaltfläche für codezellen, umschalten Markdown bearbeiten und Vorschau mit das Augensymbol

## <a name="polybase-create-external-table-wizard"></a>PolyBase Erstellen externer Tabellen-Assistent

* Von einer Instanz von SQL Server-2019 der *Assistenten zum Erstellen von externen Tabelle* kann auf drei verschiedene Arten geöffnet werden:
  * Klicken Sie mit der rechten Maustaste auf einen Server, wählen Sie **verwalten**, klicken Sie auf der Registerkarte für SQL Server-2019 (Vorschau), und wählen **Create External Table**.
  * Mit einer 2019 für SQL Server-Instanz, die im ausgewählten *Objekt-Explorer*, rufen Sie *externe Assistenten zum Erstellen von* über die *Befehlspalette*.
  * Klicken Sie mit der rechten Maustaste auf eine 2019 für SQL Server-Datenbank in *Objekt-Explorer* , und wählen Sie **Create External Table**.
* In dieser Version der Erweiterung können externe Tabellen erstellt werden, um den Zugriff auf remote SQL Server und Oracle-Tabellen.

  > [!NOTE]
  > Während die Funktionalität der externen Tabelle einer SQL-2019-Funktion ist, kann SQL-Remoteserver eine frühere Version von SQL Server ausgeführt werden.

* Wählen Sie, ob Sie SQL Server oder Oracle auf der ersten Seite des Assistenten zugreifen und fortsetzen.
* Werden Sie aufgefordert, eine Datenbank-Hauptschlüssel zu erstellen, wenn dieser nicht bereits erstellt wurde (Kennwörter von nicht genügend Komplexität blockiert werden).
* Erstellen Sie eine datenquellenverbindung und mit dem Namen Anmeldeinformationen für den Remoteserver.
* Wählen Sie die Objekte aus, um Ihre neue externe Tabelle zuzuordnen.
* Wählen Sie **-Skript generieren** oder **erstellen** um den Assistenten abzuschließen.
* Nach der Erstellung der externen Tabelle wird er sofort in der Objektstruktur der Datenbank, in dem es erstellt wurde.


## <a name="known-issues"></a>Bekannte Probleme

* Wenn das Kennwort nicht gespeichert wird, wenn Sie eine Verbindung zu erstellen, können einige Aktionen, z. B. per Übermittlung von Spark-Auftrag nicht erfolgreich.
* Vorhandene ipynb-Notebooks müssen auf Version 4 oder höher zum Laden von Inhalt im Viewer aktualisiert werden.
* Ausführen der **Notebook-Abhängigkeiten installieren** Befehl möglicherweise 2 Aufgaben angezeigt, in der Aufgabenansicht, von denen ein Fehler auftritt. Dies ist keine Installation nicht mehr funktionsfähig.
* Auswahl **neue Verbindung hinzufügen** in ein Notebook, und klicken Sie auf "Abbrechen" führt dazu, dass **Verbindung auswählen** angezeigt werden muss, auch wenn Sie bereits verbunden waren.
