---
title: Erweiterung für SQL Server 2019 (Vorschauversion)
titleSuffix: Azure Data Studio
description: Vorschauversion der SQL Server 2019-Erweiterung für Azure Data Studio
ms.custom: seodec18
ms.date: 08/15/2019
ms.reviewer: alayu; sstein
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: yualan
ms.author: alayu
ms.openlocfilehash: 5def1291480b4b2dbe1eca289f02e5c9cfd6b8d7
ms.sourcegitcommit: f5807ced6df55dfa78ccf402217551a7a3b44764
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/15/2019
ms.locfileid: "69494042"
---
# <a name="sql-server-2019-extension-preview"></a>Erweiterung für SQL Server 2019 (Vorschauversion)

Die SQL Server 2019-Erweiterung (Vorschauversion) umfasst die Unterstützung von neuen Features und Tools, die im Lieferumfang von [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] enthalten sind. Dies umfasst die Unterstützung für die Vorschau von [Big-Data-Clustern für SQL Server 2019](../big-data-cluster/big-data-cluster-overview.md), eine integrierte [Notebookfunktion](../big-data-cluster/notebooks-guidance.md), und einen PolyBase-[Assistenten für die Erstellung externer Tabellen](../relational-databases/polybase/data-virtualization.md?toc=/sql/toc/toc.json).

## <a name="install-the-sql-server-2019-extension-preview"></a>Installieren der Erweiterung für SQL Server 2019 (Vorschauversion)

Damit Sie die Erweiterung für SQL Server 2019 (Vorschauversion) installieren können, müssen Sie die zugehörige VSIX-Datei herunterladen und installieren.

1. Speichern Sie die VSIX-Datei für die SQL Server 2019-Erweiterung (Vorschauversion) in einem lokalen Verzeichnis:

   |Platform|Herunterladen|Veröffentlichungsdatum|Versionsoptionen
   |:---|:---|:---|:---|
   |Windows|[.vsix](https://go.microsoft.com/fwlink/?linkid=2101241)|15. August 2019 |0.15.0
   |macOS|[.vsix](https://go.microsoft.com/fwlink/?linkid=2101240)|15. August 2019 |0.15.0
   |Linux|[.vsix](https://go.microsoft.com/fwlink/?linkid=2101239)|15. August 2019 |0.15.0

1. Klicken Sie in Azure Data Studio im Menü **Datei** auf die Option **Install Extension from VSIX Package** (Erweiterung aus VSIX-Paket installieren), und wählen Sie die heruntergeladene VSIX-Datei aus.

1. Klicken Sie auf **Ja**, wenn Sie aufgefordert werden, die Installation zu bestätigen, und warten Sie auf die Benachrichtigung, dass die Installation erfolgreich abgeschlossen wurde.

1. Klicken Sie auf **Reload** (Erneut laden), um die Erweiterung zu aktivieren (nur bei der ersten Installation einer Erweiterung erforderlich).

1. Nach dem erneuten Laden installiert die Erweiterung Abhängigkeiten. Dies kann einige Minuten dauern. Den Status können Sie über das Ausgabefenster verfolgen.

1. Nachdem die Installation der Abhängigkeiten abgeschlossen ist, sollten Sie Azure Data Studio schließen und anschließend erneut öffnen. Der Verbindungstyp **SQL Server big data cluster** (Big-Data-Cluster für SQL Server) ist erst verfügbar, nachdem Sie Azure Data Studio neu gestartet haben.

## <a name="changes-in-release-015"></a>Änderungen in Release 0.15
* Assistent für die Erstellung externer Tabellen:
  * Reduzierung der Zeit zum Laden von Tabellen- und Spalteninformationen auf der Objektzuordnungsseite.
  * Es wurde ein Fehler in Verbindung mit dem Laden vorhandener datenbankweit gültiger Anmeldeinformationen auf der Verbindungsdetailsseite behoben.
* Assistent zum Erstellen einer externen Tabelle aus CSV-Dateien:
  * Erweiterte standardmäßige Stichprobengröße, die für die PROSE-Analyse verwendet wird.

## <a name="changes-in-release-0141"></a>Änderungen im Version 0.14.1
* Unterstützung für CTP 3.1-Datenquellen

## <a name="changes-in-release-0121"></a>Änderungen in Version 0.12.1

* Der Verbindungstyp **SQL Server big data cluster** (Big-Data-Cluster für SQL Server) wurde aus dieser Version entfernt. Alle Funktionen, die zuvor über die Verbindung mit dem Big-Data-Cluster für SQL Server zur Verfügung standen, sind jetzt Teil der SQL Server-Verbindung.
* Die HDFS-Suche ist über den Ordner **Data Services** möglich.
* Für Notebooks funktionieren PySpark und andere Big-Data-Kernels, wenn eine Verbindung mit der SQL Server-Masterinstanz im Big-Data-Cluster für SQL Server besteht.
* Assistent für die Erstellung externer Tabellen:
  * Das Erstellen externer Tabelle mithilfe von vorhandenen externen Datenquellen wird nun unterstützt.
  * Die Leistung verschiedener Funktionen des Assistenten wurde verbessert.
  * Die Verarbeitung von Objektnamen mit Sonderzeichen wurde verbessert. In einigen Fällen wurden dabei Fehler im Assistenten ausgelöst.
  * Die Zuverlässigkeit der Seite „Object Mapping“ (Objektzuordnung) wurde verbessert.
  * Die Systemdatenbanken „DWConfiguration“, „DWDiagnostics“, „DWQueue“ wurden aus der Dropdownliste „Datenbanken“ entfernt.
  * Der Name des externen Dateiformatobjekts im Assistenten für die **Erstellung externer Tabellen aus CSV-Dateien** kann jetzt festgelegt werden.
  * Die Schaltfläche „Aktualisieren“ wurde zur ersten Seite des Assistenten für die **Erstellung externer Tabellen aus CSV-Dateien** hinzugefügt.

## <a name="release-notes-v0110"></a>Hinweise zu Version 0.11.0

* Jupyter Notebook (insbesondere die Kernel für Python3 und Spark) wird nun in Azure Data Studio unterstützt. Diese Erweiterung ist nicht mehr erforderlich, damit Notebooks verwendet werden kann.
* Es wurden mehrere Fehlerbehebungen der Assistenten für externe Daten behoben:
  * Die Typzuordnungen für Oracle wurden entsprechend den Änderungen aktualisiert, die an SQL Server 2019 CTP 2.3 vorgenommen wurden.
  * Behoben: Neue Schemas, die in die Steuerelemente für die Tabellenzuordnung eingegeben wurden, gehen verloren.
  * Behoben: Beim Überprüfen eines Datenbankknotens in den Tabellenzuordnungen werden nicht alle Tabellen und Ansichten berücksichtigt.


## <a name="release-notes-v0102"></a>Hinweise zu Version 0.10.2
### <a name="sql-server-2019-support"></a>Unterstützung für SQL Server 2019
Die Unterstützung für SQL Server 2019 wurde aktualisiert. Beim Herstellen einer Verbindung mit einer Big-Data-Clusterinstanz für SQL Server wird ein neuer _Data Services_-Ordner in der Explorer-Strukturansicht angezeigt. Dies umfasst Startpunkte für Aktionen wie das Öffnen eines neuen Notebooks für die Verbindung, das Übermitteln von Spark-Aufträgen und das Arbeiten mit HDFS. Beachten Sie, dass für einige Aktionen wie _Create External Data_ (Externe Daten erstellen) über eine HDFS-Datei bzw. einen HDFS-Ordner die Erweiterung für _SQL Server 2019 (Vorschauversion)_ installiert werden muss.

### <a name="notebook-support"></a>Notebook-Unterstützung
Wir haben in dieser Version wichtige Updates an der Benutzeroberfläche für Notebooks vorgenommen. Der Fokus lag dabei darauf, dass freigegebene Notebooks einfach gelesen werden können. Deshalb werden die Konturen um Zellen jetzt nur noch angezeigt, wenn mit dem Mauszeiger darauf gezeigt oder auf diese geklickt wird. Außerdem wurde Hoversupport für einfache Aktionen auf Zellenebene hinzugefügt, sodass nun nicht mehr auf die Zellen geklickt werden muss, und der Ausführungsstatus ist nun genauer, da u. a. eine Ausführungsanzahl und eine animierte Schaltfläche _zum Beenden der Ausführung_ hinzugefügt wurde. Zudem wurden Tastenkombinationen für die Optionen _New Notebook_ (Neues Notebook, `Ctrl+Shift+N`), _Run Cell_ (Zelle ausführen, `F5`), _New Code Cell_ (Neue Codezelle, `Ctrl+Shift+C`) und _New Text Cell_ (Neue Textzelle, `Ctrl+Shift+T`) hinzugefügt. In Zukunft sollen alle wichtigen Aktionen über Tastenkombinationen gestartet werden. Sie können uns gern Feedback zu noch fehlenden Tastenkombinationen geben.

Weitere Verbesserungen und Fehlerbehebungen:
* Die Benutzer der Erweiterung für _SQL Server 2019 (Vorschauversion)_ werden jetzt dazu aufgefordert, ein Installationsverzeichnis für Python-Abhängigkeiten auszuwählen. Außerdem ist Python nicht mehr in der `.vsix file` enthalten, wodurch die Gesamtgröße der Erweiterung verringert wird. Die Python-Abhängigkeiten werden zur Unterstützung der Kernel für Spark und Python3 benötigt. Wenn Sie diese Kernel verwenden möchten, muss diese Erweiterung deshalb installiert sein.
* Neue Notebooks können nun über die Befehlszeile gestartet werden. Über die Argumente `--command=notebook.command.new --server=myservername` sollten Sie ein neues Notebook öffnen und eine Verbindung mit diesem Server herstellen können.
* Es wurden Leistungskorrekturen für Notebooks mit sehr langen Codezellen vorgenommen. Wenn Codezellen mehr als 250 Zeilen umfassen, werden sie nun mit einer Scrollleiste versehen.
* IPYNB-Dateien werden nun besser unterstützt. Es werden jetzt alle Versionen ab Version 3 unterstützt. Hinweis: Dateien werden beim Speichern auf Version 4 oder höher aktualisiert.
* Die Benutzereinstellung `notebook.enabled` wurde entfernt, da der integrierte Notebookviewer jetzt stabil ist.
* Das Design mit hohem Kontrast wird nun mit einer Reihe von Korrekturen des Objektlayouts unterstützt.
* Fehler 3680 wurde behoben: Ausgaben enthalten manchmal eine Reihe von falschen `,,,`-Zeichen.
* Fehler 3602 wurde behoben: Der Editor wird für Zellen ausgeblendet, wenn nicht durch Azure Data Studio navigiert wird.
* Die Verwendung von Rasteransichten für den MIME-Ausgabetyp `application/vnd.dataresource+json` wurde hinzugefügt. Dadurch werden die Tabellenausgaben bei Notebooks übersichtlicher (wenn beispielswiese `pd.options.display.html.table_schema` in Python-Notebooks festgelegt wird) Fehler 3959 wurde behoben: Azure Data Studio versucht nach dem Schließen eines Notebooks zweimal, den Notebookserver herunterzufahren.

#### <a name="known-issues"></a>Bekannte Probleme
* Wenn ein Notebook geöffnet wird, wird das Dialogfeld „Install Python“ (Python installieren) angezeigt. Wenn diese Installation abgebrochen wird, zeigen die Kernel und die Dropdownlisten unter „Anfügen an“ nicht die erwarteten Werte an. Sie können das Problem umgehen, indem Sie die Python-Installation abschließen.
* Wenn ein Notebook mit einem Kernel geöffnet wird, der nicht unterstützt wird, kann die Verwendung der Dropdownlisten für die Kernel oder für die Option _Anfügen an_ dazu führen, das Azure Data Studio nicht mehr reagiert. Dann müssen Sie Azure Data Studio schließen und sicherstellen, dass Sie einen unterstützten Kernel verwenden (Python3, Spark | R, Spark | Scala, Pyspark, PySpark3)
* Der Link zur Spark-Benutzeroberfläche löst einen Fehler aus, wenn PySpark3 oder andere Spark-Kernel für den SQL Server-Endpunkt verwendet werden. Sie können dieses Problem umgehen, indem Sie auf dem Dashboard auf „Spark UI“ (Spark-Benutzeroberfläche) klicken oder eine Verbindung über den Verbindungstyp „SQL Server Big-Data Cluster“ (Big-Data-Cluster für SQL Server) herstellen. Dabei sollte automatisch der richtige Link zur Spark-Benutzeroberfläche verwendet werden.

### <a name="extensibility-improvements"></a>Verbesserungen der Erweiterbarkeit
Zu dieser Version wurde eine Reihe von Verbesserungen zur Extenderunterstützung hinzugefügt:
* Eine neue `ObjectExplorerNodeProvider`-API ermöglicht es Erweiterungen, Ordner zu SQL Server-Instanzen oder anderen Verbindungsknoten hinzuzufügen. Auf diese Weise wird der Knoten `Data Services` zu SQL Server 2019-Instanzen hinzugefügt. Dieser kann jedoch auch verwendet werden, um problemlos Ordner zur Überwachung oder andere Ordner zur Benutzeroberfläche hinzuzufügen.
* Es sind zwei neue Kontextschlüsselwerte verfügbar, mit denen Sie Dashboardbeiträge anzeigen bzw. ausblenden können.
  * `mssql:iscluster` gibt an, ob es sich um ein Big-Data-Cluster für SQL Server 2019 handelt.
  * `mssql:servermajorversion` gibt die Serverversion an (15 für SQL Server 2019, 14 für SQL Server 2017 usw.). Dies kann hilfreich sein, wenn beispielsweise bestimmte Features nur für SQL Server 2017 oder höher angezeigt werden sollen.


## <a name="release-notes-v080"></a>Hinweise zu Version 0.8.0
*Notebooks:*
* Sie können jetzt Zellen vor oder nach bereits vorhandenen Zellen eingefügt werden, indem Sie für die jeweilige Zelle auf die Schaltfläche „Weitere Aktionen“ klicken.
* Die Option **Neue Verbindung hinzufügen** wurde zu den Verbindungen hinzugefügt, die in der Dropdownliste „Anfügen an“ enthalten sind.
* Der Befehl **Reinstall Notebook Dependencies** (Notebookabhängigkeiten erneut installieren) wurde hinzugefügt, um Paketupdates für Python zu unterstützen und Probleme zu beheben, bei denen die Installation durch das Schließen der Anwendung abgebrochen wurde. Sie können diesen Befehl über die Befehlspalette ausführen (verwenden Sie dafür die Tastenkombination `Ctrl/Cmd+Shift+P`, und geben Sie `Reinstall Notebook Dependencies` ein).
* Das Python-Paket „PROSE“ wurde auf die Version 1.1.0 aktualisiert, mit der eine Reihe von Fehlern behoben wird. Verwenden Sie den Befehl **Reinstall Notebook Dependencies** (Notebookabhängigkeiten erneut installieren), um dieses Paket zu aktualisieren.
* Der Befehl **Ausgabe löschen** wird jetzt unterstützt, wenn Sie auf die Zellenschaltfläche **Weitere Aktionen** klicken.
* Die folgenden von Kunden gemeldeten Probleme wurden behoben:
  * Die Notebooksitzung kann aufgrund von PATH-Problemen nicht unter Windows gestartet werden.
  * Das Notebook kann nicht über den Stammordner eines Laufwerks (z. B. C:\ oder D:\) gestartet werden.
  * [2820](https://github.com/Microsoft/azuredatastudio/issues/2820): Über ADS in VS Code erstellte Notebooks können nicht bearbeitet werden.
  * Der Link zur Spark-Benutzeroberfläche funktioniert nun, wenn ein Spark-Kernel ausgeführt wird.
  * Die Option „Managed Packages“ (Verwaltete Pakete) wurde in „Install Packages“ (Pakete installieren) umbenannt.

*Create External Data* (Externe Daten erstellen):

* Fehlermeldungen können kopiert werden und wurden der Einfachheit halber in eine Zusammenfassung und eine detaillierte Ansicht aufgeteilt.
* Das Layout der Benutzeroberflächen, die Zuverlässigkeit und die Fehlerbehandlung wurden deutlich verbessert.
* Die folgenden von Kunden gemeldeten Probleme wurden behoben:
  * Tabellen mit ungültigen Spaltenzuordnungen werden als „Deaktiviert“ angezeigt, und der Fehler wird in einer Warnung erläutert.

## <a name="release-notes-v072"></a>Hinweise zu Version 0.7.2
* Der Azure-Ressourcen-Explorer ist nun in Azure Data Studio integriert und wurde aus dieser Erweiterung entfernt. Vielen Dank für Ihr Feedback!
* Die Leistung von Notebooks wurde mithilfe mehrerer Markdownzellen verbessert.
* Die Größe von Codezellen in Notebooks wird automatisch angepasst. Anhand der Zellensymbolleiste wird eine Mindestgröße festgelegt.
* Benachrichtigen Sie den Benutzer, wenn Sie Notebookabhängigkeiten installieren. Insbesondere unter Windows kann dies einige Zeit in Anspruch nehmen, weshalb Benachrichtigungen jetzt in der Ansicht „Tasks“ (Aufgaben) angezeigt werden.
* Die erneute Installation von Notebookabhängigkeiten wird jetzt unterstützt. Dies ist hilfreich, wenn der Benutzer zuvor Azure Data Studio vor dem Abschluss der Installation geschlossen hat.
* Die Zellenausführung in Notebooks kann nun abgebrochen werden.
* Die Zuverlässigkeit bei der Verwendung des Assistenten für die Erstellung externer Tabellen wurde insbesondere bei Verbindungsfehlern verbessert.
* Die Verwendung des Assistenten für die Erstellung externer Tabellen wird jetzt blockiert, wenn PolyBase nicht aktiviert ist oder nicht auf dem Zielserver ausgeführt wird.
* Fehler in Bezug auf die Rechtschreibung und Benennung im Zusammenhang mit SQL Server 2019 und dem Assistenten für die Erstellung externer Tabellen wurden behoben.
* Es wurde mehrere Fehler aus der Debugging-Konsole für Azure Data Studio entfernt.

##  <a name="sql-server-2019-big-data-cluster-support"></a>Unterstützung von Big-Data-Clustern für SQL Server 2019

* Klicken Sie im *Objekt-Explorer* auf **Verbindung hinzufügen**, und wählen Sie den Verbindungstyp **SQL Server big data cluster** (Big-Data-Cluster für SQL Server) aus.

   > [!TIP]
   > Wenn der Verbindungstyp **SQL Server big data cluster** (Big-Data-Cluster für SQL Server) nicht angezeigt wird, sollten Sie Azure Data Studio neu starten.

* Geben Sie den Hostnamen oder die IP-Adresse des Clusterendpunkts sowie den Benutzernamen und das Kennwort ein, das Sie für die Verbindungsherstellung verwendet haben.
* Fügen Sie optional einen Anzeigenamen in das Feld **Name** ein.
* Klicken Sie auf **Verbinden**. Dann können Sie allgemeine Aufgaben über das Dashboard starten, **HDFS** im Objekt-Explorer durchsuchen und über diesen kontextbezogene Aufgaben ausführen.
* Wenn Sie einen Spark-Auftrag für den Cluster übermitteln möchten, klicken Sie im *Objekt-Explorer* erst mit der rechten Maustaste auf den Serverknoten und anschließend mit der linken auf **Submit Spark Job** (Spark-Auftrag übermitteln), damit das Dialogfeld für die Übermittlung geöffnet wird.
* Informationen zum Öffnen eines Notebooks finden Sie im nächsten Abschnitt.

Weitere Informationen finden Sie unter [Big-Data-Cluster](../big-data-cluster/big-data-cluster-overview.md).


## <a name="azure-data-studio-notebooks"></a>Azure Data Studio-Notebooks

* Sie haben die folgenden Möglichkeiten, um ein Notebook zu öffnen:
  * Öffnen Sie ein neues Notebook über die *Befehlspalette*.
  * Öffnen Sie die Strukturansicht des HDFS-Objekt-Explorers für einen Big-Data-Cluster für SQL Server 2019, und wählen Sie eine der folgenden beiden Optionen aus:
    * Klicken Sie erst mit der rechten Maustaste auf den Serverknoten und anschließend mit der linken auf **New Jupyter Notebook** (Neue Jupyter Notebook-Datei).
    * Klicken Sie erst mit der rechten Maustaste auf eine CSV-Datei und anschließend mit der linken auf **Analyze in Notebook** (In Notebook analysieren).
  * Öffnen Sie im Menü **Datei** oder im Datei-Explorer eine bereits vorhandene IPYNB-Datei *(IPYNB-Dateien müssen auf Version 4 oder höher aktualisiert werden, damit Sie ordnungsgemäß geladen werden können).*
* Wählen Sie einen Kernel aus. Klicken Sie für die lokale Notebookausführung auf die Option „Python 3“. Klicken Sie für die Remoteausführung auf die Optionen „PySpark“ oder „Spark | Scala“.
* Wählen Sie einen Big-Data-Clusterendpunkt für SQL Server aus, mit dem eine Verbindung hergestellt werden soll, wenn Sie sich für eine Remoteausführung entscheiden (dies ist für die lokale Entwicklung mit Python 3 nicht erforderlich).
* Fügen Sie über die Schaltflächen im Notebookheader Code oder Markdownzellen hinzu. Über das Papierkorbsymbol links neben den einzelnen Zellen können Sie bei Bedarf Zellen löschen.
* Über die Wiedergabeschaltfläche für Codezellen können Sie Zellen ausführen, und wenn Sie auf das Augensymbol klicken, können Sie zwischen Markdownbearbeitung und Vorschau wechseln.

## <a name="polybase-create-external-table-wizard"></a>PolyBase-Assistent für die Erstellung externer Tabellen

* Es gibt drei Möglichkeiten, den *Assistenten für die Erstellung externer Tabellen* über eine SQL Server 2019-Instanz zu öffnen:
  * Klicken Sie erst mit der rechten Maustaste auf einen Server und dann mit der linken auf **Verwalten**. Klicken Sie dann erst auf die Registerkarte für SQL Server 2019 (Vorschauversion) und anschließend auf **Create External Table** (Externe Tabelle erstellen).
  * Wenn Sie eine SQL Server 2019-Instanz im *Objekt-Explorer* ausgewählt haben, sollten Sie den *Assistenten für die Erstellung externer Tabellen* über die *Befehlspalette* öffnen.
  * Klicken Sie im *Objekt-Explorer* erst mit der rechten Maustaste auf eine SQL Server 2019-Datenbank und dann mit der linken auf **Create External Table** (Externe Tabelle erstellen).
* In dieser Version der Erweiterung können externe Tabellen erstellt werden, um auf Remoteinstanzen von SQL Server und Oracle-Tabellen zuzugreifen.

  > [!NOTE]
  > Obwohl die Funktionen zur Erstellung externer Tabellen im Lieferumfang von SQL Server 2019 enthalten ist, kann auf der Remoteinstanz von SQL Server eine frühere Version ausgeführt werden.

* Wählen Sie auf der ersten Seite des Assistenten aus, ob Sie auf SQL Server oder Oracle zugreifen möchten, und fahren Sie fort.
* Wenn noch kein Datenbankhauptschlüssel vorhanden ist, werden Sie aufgefordert, einen zu erstellen (Kennwörter, die nicht komplex genug sind, werden blockiert).
* Erstellen Sie eine Datenquellenverbindung und benannte Anmeldeinformationen für den Remoteserver.
* Wählen Sie aus, welche Objekte der neuen externen Tabelle zugeordnet werden sollen.
* Klicken Sie auf **Skript generieren** oder **Erstellen**, um den Assistenten zu schließen.
* Sobald die externe Tabelle erstellt wurde, wird sie in der Objektstrukturansicht der Datenbank angezeigt, in der sie erstellt wurde.


## <a name="known-issues"></a>Bekannte Probleme

* Wenn das Kennwort beim Erstellen einer Verbindung nicht gespeichert wird, können einige Aktionen wie das Übermitteln von Spark-Aufträgen möglicherweise nicht ausgeführt werden.
* Vorhandene IPYNB-Notebooks müssen auf Version 4 oder höher aktualisiert werden, damit Inhalte in den Viewer geladen werden können.
* Wenn Sie den Befehl **Reinstall Notebook Dependencies** (Notebookabhängigkeiten erneut installieren) ausführen, werden möglicherweise zwei Aufgaben in der Aufgabenansicht angezeigt, von denen eine fehlschlägt. Dies führt aber nicht dazu, dass die gesamte Installation fehlschlägt.
* Wenn Sie in einem Notebook erst auf **Neue Verbindung hinzufügen** und dann auf „Abbrechen“ klicken, wird die Option **Verbindung auswählen** angezeigt. Dies ist auch der Fall, wenn bereits eine Verbindung hergestellt wurde.
