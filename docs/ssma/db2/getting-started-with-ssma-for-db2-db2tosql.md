---
title: Getting Started with SSMA for DB2 (DB2ToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 48ca32fc-1830-4d1f-add7-480ba5ad02e8
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 0eab4f23e342c95d83baa70dd03aba2f5d4bc8d1
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67989641"
---
# <a name="getting-started-with-ssma-for-db2-db2tosql"></a>Getting Started with SSMA for DB2 (DB2ToSQL)
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Migration Assistant (SSMA) für DB2 ermöglicht Ihnen das schnelle Konvertieren von DB2-Daten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Bank Schemas in Schemas, das Hochladen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] der resultierenden Schemas in und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]das Migrieren von Daten von DB2 zu.  
  
Dieses Thema enthält eine Einführung in den Installationsvorgang und hilft Ihnen dabei, Sie mit der SSMA-Benutzeroberfläche vertraut zu machen.  
  
## <a name="installing-ssma"></a>Installieren von SSMA  
Zum Verwenden von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]SSMA müssen Sie zuerst das SSMA-Client Programm auf einem Computer installieren, der auf die DB2-Quelldatenbank und die-Ziel Instanz zugreifen kann. DB2-OLEDB-Anbieter auf dem Computer, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]auf dem ausgeführt wird. Diese Komponenten unterstützen die Datenmigration und die Emulation von DB2-Systemfunktionen. Installationsanweisungen finden Sie unter [Installieren von SSMA für DB2 &#40;DB2ToSQL&#41;](../../ssma/db2/installing-ssma-for-db2-db2tosql.md).  
  
Klicken Sie zum Starten von SSMA auf **Start**, zeigen Sie auf **Alle Programme**, zeigen Sie auf ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant für DB2**, und klicken Sie ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dann auf Migration Assistant für DB2**.  
  
## <a name="ssma-for-db2-user-interface"></a>SSMA für DB2-Benutzeroberfläche  
Nach der Installation von SSMA können Sie SSMA zum Migrieren von DB2- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Datenbanken zu verwenden. Es hilft Ihnen, sich mit der SSMA-Benutzeroberfläche vertraut zu machen, bevor Sie beginnen. Das folgende Diagramm zeigt die Benutzeroberfläche für SSMA, einschließlich der Metadaten-Explorer, Metadaten, Symbolleisten, Ausgabebereich und Fehlerlisten Bereich:  
  
![SSMA-Benutzeroberfläche](../../ssma/db2/media/ssma_db2_ui.png "SSMA-Benutzeroberfläche")  
  
Um eine Migration zu starten, müssen Sie zunächst ein neues Projekt erstellen. Anschließend stellen Sie eine Verbindung mit einer DB2-Datenbank her. Nach einer erfolgreichen Verbindung werden DB2-Schemas im DB2-metadatenexplorer angezeigt. Sie können dann mit der rechten Maustaste auf Objekte im DB2-metadatenexplorer klicken, um Aufgaben wie das Erstellen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]von Berichten, die Konvertierungen in bewerten, auszuführen Sie können diese Aufgaben auch mithilfe der Symbolleisten und Menüs ausführen.  
  
Sie müssen auch eine Verbindung mit einer Instanz [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]von herstellen. Nach einer erfolgreichen Verbindung wird eine Hierarchie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von Datenbanken im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] metadatenexplorer angezeigt. Nachdem Sie DB2-Schemas in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Schemas konvertiert haben, wählen Sie diese konvertierten Schemas im metadatenexplorer aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]synchronisieren Sie dann die Schemas mit.  
  
Nachdem Sie konvertierte Schemas mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]synchronisiert haben, können Sie zum DB2-metadatenexplorer zurückkehren und Daten aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DB2-Schemas in Datenbanken migrieren.  
  
Weitere Informationen zu diesen Aufgaben und deren Durchführung finden Sie unter [Migrieren von DB2-Datenbanken zu SQL Server &#40;DB2ToSQL&#41;](../../ssma/db2/migrating-db2-databases-to-sql-server-db2tosql.md).  
  
In den folgenden Abschnitten werden die Features der SSMA-Benutzeroberfläche beschrieben.  
  
### <a name="metadata-explorers"></a>Metadatenexplorer  
SSMA enthält zwei metadatenexplorer zum Durchsuchen und Ausführen von Aktionen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in DB2 und Datenbanken.  
  
#### <a name="db2-metadata-explorer"></a>DB2-metadatenexplorer  
Der DB2-metadatenexplorer zeigt Informationen zu DB2-Schemas an. Mit dem DB2-metadatenexplorer können Sie die folgenden Aufgaben ausführen:  
  
-   Durchsuchen Sie die Objekte in den einzelnen Schemas.  
  
-   Wählen Sie die Objekte für die Konvertierung aus, und konvertieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Sie dann die Objekte in die Syntax. Weitere Informationen finden Sie unter [umstellen von DB2-Schemas &#40;DB2ToSQL&#41;](../../ssma/db2/converting-db2-schemas-db2tosql.md).  
  
-   Wählen Sie Tabellen für die Datenmigration aus, und migrieren Sie dann die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Daten aus diesen Tabellen zu. Weitere Informationen finden Sie unter [Migrieren von DB2-Datenbanken zu SQL Server &#40;DB2ToSQL&#41;](../../ssma/db2/migrating-db2-databases-to-sql-server-db2tosql.md).  
  
#### <a name="sql-server-metadata-explorer"></a>Metadatenexplorer SQL Server  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Im metadatenexplorer werden Informationen zu einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Instanz von angezeigt. Wenn Sie eine Verbindung mit einer Instanz [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]von herstellen, ruft SSMA Metadaten zu dieser Instanz ab und speichert Sie in der Projektdatei.  
  
Sie können den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] metadatenexplorer verwenden, um konvertierte DB2-Datenbankobjekte auszuwählen und diese Objekte dann [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]mit der Instanz von zu synchronisieren.  
  
### <a name="metadata"></a>Metadaten  
Auf der rechten Seite jedes metadatenexplorers sind Registerkarten, die das ausgewählte Objekt beschreiben. Wenn Sie z. b. eine Tabelle im DB2-metadatenexplorer auswählen, werden sechs Registerkarten angezeigt: **Table**, **SQL**, **Type Mapping, Report**, **Properties**und **Data**. Die Registerkarte **Bericht** enthält nur Informationen, nachdem Sie einen Bericht erstellt haben, der das ausgewählte Objekt enthält. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Wenn Sie eine Tabelle im metadatenexplorer auswählen, werden drei Registerkarten angezeigt: **Table**, **SQL**und **Data**.  
  
Die meisten metadateneinstellungen sind schreibgeschützt. Sie können jedoch die folgenden Metadaten ändern:  
  
-   Im DB2-metadatenexplorer können Sie Prozeduren und Typzuordnungen ändern. Nehmen Sie vor dem Konvertieren von Schemas Änderungen vor, um die geänderten Prozeduren und Typzuordnungen zu konvertieren.  
  
-   Im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] metadatenexplorer können Sie die [!INCLUDE[tsql](../../includes/tsql-md.md)] für gespeicherte Prozeduren ändern. Um diese Änderungen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]anzuzeigen, nehmen Sie diese Änderungen vor, bevor Sie die Schemas in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]laden.  
  
Änderungen, die in einem metadatenexplorer vorgenommen werden, werden in den Projekt Metadaten, nicht in der Quell-oder Zieldatenbank widergespiegelt.  
  
### <a name="toolbars"></a>Symbolleisten  
SSMA verfügt über zwei Symbolleisten: eine Projektsymbol Leiste und eine Migrations Symbolleiste.  
  
#### <a name="the-project-toolbar"></a>Die Projektsymbol Leiste  
Die Projektsymbol Leiste enthält Schaltflächen zum Arbeiten mit Projekten, zum Herstellen einer Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]DB2 und zum Herstellen einer Verbindung mit. Diese Schaltflächen ähneln den Befehlen im Menü **Datei** .  
  
#### <a name="migration-toolbar"></a>Migrations Symbolleiste  
In der folgenden Tabelle werden die Befehle für die Migrations Symbolleiste angezeigt:  
  
|Schaltfläche|Funktion|  
|------|--------|  
|**Erstellen von Berichten**|Konvertiert die ausgewählten DB2-Objekte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in die-Syntax und erstellt dann einen Bericht, der die erfolgreiche Konvertierung der Konvertierung anzeigt.<br /><br />Dieser Befehl ist deaktiviert, es sei denn, Objekte sind im DB2-metadatenexplorer ausgewählt.|  
|**Schema konvertieren**|Konvertiert die ausgewählten DB2-Objekte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in-Objekte.<br /><br />Dieser Befehl ist deaktiviert, es sei denn, Objekte sind im DB2-metadatenexplorer ausgewählt.|  
|**Migrieren von Daten**|Migriert Daten von der DB2-Datenbank [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zu. Vor dem Ausführen dieses Befehls müssen Sie die DB2-Schemas in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Schemas konvertieren und dann die Objekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]laden.<br /><br />Dieser Befehl ist deaktiviert, es sei denn, Objekte sind im DB2-metadatenexplorer ausgewählt.|  
|**Beenden**|Beendet den aktuellen Prozess.|  
  
### <a name="menus"></a>Menüs  
In der folgenden Tabelle sind die SSMA-Menüs aufgeführt.  
  
|Menü|Beschreibung|  
|----|-----------|  
|**File**|Enthält Befehle für das Arbeiten mit-Projekten, das Herstellen einer Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]DB2 und das Herstellen einer Verbindung mit.|  
|**Bearbeiten**|Enthält Befehle zum Suchen und arbeiten mit Text auf den Detailseiten, z. b [!INCLUDE[tsql](../../includes/tsql-md.md)] . zum Kopieren aus dem SQL-Detailbereich. Enthält auch die Option **Lesezeichen verwalten** , in der eine Liste vorhandener Lesezeichen angezeigt werden kann. Sie können die Schaltflächen auf der rechten Seite des Dialog Felds verwenden, um die Lesezeichen zu verwalten.|  
|**Ansicht**|Enthält den Befehl Metadaten-Explorer **Synchronisieren** . , Der die Objekte zwischen dem DB2-metadatenexplorer und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dem metadatenexplorer synchronisiert. Enthält auch Befehle zum Anzeigen und Ausblenden der **Ausgabe** -und **Fehlerliste** Bereiche sowie ein Options **Layout** zum Verwalten der Layouts.|  
|**Tools**|Enthält Befehle zum Erstellen von Berichten und zum Migrieren von Objekten und Daten. Bietet auch Zugriff auf die Dialogfelder **globale Einstellungen** und **Projekteinstellungen** .|  
|**Hilfe**|Bietet Zugriff **auf die** SSMA-Hilfe und das Dialogfeld Info.|  
  
### <a name="output-pane-and-error-list-pane"></a>Ausgabebereich und Fehlerliste Bereich  
Das Menü **Ansicht** enthält Befehle zum Umschalten der Sichtbarkeit des Ausgabe Bereichs und des Fehlerliste Bereichs:  
  
-   Im Ausgabebereich werden Statusmeldungen von SSMA während der Objekt Konvertierung, der Objekt Synchronisierung und der Datenmigration angezeigt.  
  
-   Im Fehlerliste Bereich werden Fehler-, Warn-und Informationsmeldungen in einer sortierbaren Liste angezeigt.  
  
## <a name="see-also"></a>Weitere Informationen  
[Migrieren von DB2-Daten in SQL Server &#40;DB2ToSQL-&#41;](../../ssma/db2/migrating-db2-data-into-sql-server-db2tosql.md)  
[Referenz zur Benutzeroberfläche &#40;DB2ToSQL&#41;](../../ssma/db2/user-interface-reference-db2tosql.md)  
  
