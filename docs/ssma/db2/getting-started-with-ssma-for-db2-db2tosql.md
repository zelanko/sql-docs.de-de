---
title: Erste Schritte mit SSMA für DB2 (DB2ToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 48ca32fc-1830-4d1f-add7-480ba5ad02e8
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 86a931c9132a23d9ceb3d46b48fbdce23bf76f92
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63298866"
---
# <a name="getting-started-with-ssma-for-db2-db2tosql"></a>Erste Schritte mit SSMA für DB2 (DB2ToSQL)
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant (SSMA) für DB2 können Sie schnell, konvertieren Sie DB2-Datenbankschemas, um [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Schemas, Hochladen der resultierenden Schemas in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und Migrieren von Daten aus DB2 in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
Dieses Thema führt während des Installationsvorgangs, und klicken Sie dann können Sie mit der SSMA-Benutzeroberfläche vertraut zu machen.  
  
## <a name="installing-ssma"></a>Installieren von SSMA  
Um SSMA verwenden zu können, müssen Sie zunächst installieren das SSMA-Clientprogramm auf einem Computer, die die DB2-Quelldatenbank und der Zielinstanz von zugreifen können [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. DB2 OLE DB-Anbieter auf dem Computer, auf denen ausgeführt wird, ist [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Diese Komponenten unterstützen die Migration von Daten und die Emulation der DB2-Systemfunktionen. Installationsanweisungen finden Sie unter [Installieren von SSMA für DB2 &#40;DB2ToSQL&#41;](../../ssma/db2/installing-ssma-for-db2-db2tosql.md).  
  
Um SSMA zu starten, klicken Sie auf **starten**, zeigen Sie auf **Programme**, zeigen Sie auf  **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant für DB2**, und klicken Sie dann auf  **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant für DB2**.  
  
## <a name="ssma-for-db2-user-interface"></a>SSMA für DB2-Benutzeroberfläche  
Nach der SSMA installiert ist, können Sie SSMA Migrieren von DB2-Datenbanken zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Es hilft, die mit der SSMA-Benutzeroberfläche vertraut zu machen, bevor Sie beginnen. Das folgende Diagramm zeigt die Benutzeroberfläche für SSMA, einschließlich der Metadaten-Explorer, Metadaten, Symbolleisten, Ausgabebereich und Fehler im Listenbereich an:  
  
![SSMA-Benutzeroberfläche](../../ssma/db2/media/ssma_db2_ui.png "SSMA-Benutzeroberfläche")  
  
Um eine Migration zu starten, müssen Sie zunächst ein neues Projekt erstellen. Anschließend verbinden Sie mit einer DB2-Datenbank. Nach einer erfolgreichen Verbindung werden die DB2-Schemas in DB2-Metadaten-Explorer angezeigt. Sie können dann mit der rechten Maustaste-Objekte in der DB2-Metadaten-Explorer für Aufgaben wie z. B. Berichte erstellen, die Konvertierungen zu bewerten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Sie können auch diese Aufgaben ausführen, mit der Symbolleisten und Menüs.  
  
Sie müssen auch eine Verbindung herstellen mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Nach einer erfolgreichen Verbindung eine Hierarchie von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbanken erscheint im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Metadaten-Explorer. Nach der Konvertierung zu DB2-Schemas [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Schemas, wählen Sie die konvertierte Schemas im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Metadaten-Explorer, und klicken Sie dann zu synchronisieren der Schemas mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
Nach der Synchronisierung konvertierte Schemas mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], können Sie zurück zu DB2-Metadaten-Explorer und Migrieren von Daten aus DB2-Schemas in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbanken.  
  
Weitere Informationen zu diesen Aufgaben und deren Ausführung finden Sie unter [DB2-Datenbanken zu SQL Server Migration &#40;DB2ToSQL&#41;](../../ssma/db2/migrating-db2-databases-to-sql-server-db2tosql.md).  
  
Die folgenden Abschnitte beschreiben die Funktionen der SSMA-Benutzeroberfläche.  
  
### <a name="metadata-explorers"></a>Metadaten-Explorer  
SSMA enthält zwei Metadaten-Explorer zum Durchsuchen und Ausführen von Aktionen für DB2 und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbanken.  
  
#### <a name="db2-metadata-explorer"></a>DB2-Metadaten-Explorer  
DB2-Metadaten-Explorer zeigt Informationen zu DB2-Schemas. Mithilfe von DB2-Metadaten-Explorer können Sie die folgenden Aufgaben ausführen:  
  
-   Durchsuchen Sie die Objekte in den einzelnen Schemas.  
  
-   Wählen Sie Objekte für die Konvertierung konvertiert und dann die Objekte an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Syntax. Weitere Informationen finden Sie unter [Konvertieren von DB2 Schemas &#40;DB2ToSQL&#41;](../../ssma/db2/converting-db2-schemas-db2tosql.md).  
  
-   Wählen Sie die Tabellen für die Datenmigration aus, und klicken Sie dann die Daten aus diesen Tabellen zu migrieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Weitere Informationen finden Sie unter [DB2-Datenbanken zu SQL Server Migration &#40;DB2ToSQL&#41;](../../ssma/db2/migrating-db2-databases-to-sql-server-db2tosql.md).  
  
#### <a name="sql-server-metadata-explorer"></a>SQL Server Metadata Explorer  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Metadaten-Explorer zeigt Informationen zu einer Instanz des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Wenn Sie die Verbindung zu einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], SSMA Ruft Metadaten zu dieser Instanz ab und speichert sie in der Projektdatei.  
  
Sie können [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Metadaten-Explorer, wählen die konvertierte DB2-Datenbankobjekte aus, und klicken Sie dann die Objekte zu synchronisieren, mit der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
### <a name="metadata"></a>Metadaten  
Befinden sich rechts neben jeder Metadaten-Explorer Registerkarten, die das ausgewählte Objekt zu beschreiben. Wenn Sie eine Tabelle in DB2-Metadaten-Explorer auswählen, werden z. B. sechs Registerkarten angezeigt: **Tabelle**, **SQL**, **Typenzuordnung, Bericht**, **Eigenschaften**, und **Daten**. Die **Bericht** Registerkarte enthält Informationen, nachdem Sie einen Bericht erstellen, die das ausgewählte Objekt enthält. Bei Auswahl eine Tabelle in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Metadaten-Explorer, die drei Registerkarten angezeigt werden: **Tabelle**, **SQL**, und **Daten**.  
  
Die meisten Metadateneinstellungen für die sind schreibgeschützt. Allerdings können Sie die folgende Metadaten ändern:  
  
-   Im DB2-Metadaten-Explorer können Sie ändern die Prozeduren und datentypzuordnungen. Um die geänderten Verfahren konvertieren und datentypzuordnungen, können nehmen Sie Änderungen vor, bevor Sie Schemas konvertieren.  
  
-   In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Metadaten-Explorer können Sie ändern die [!INCLUDE[tsql](../../includes/tsql-md.md)] für gespeicherte Prozeduren. Diese Änderungen im anzeigen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], nehmen Sie diese Änderungen vor dem Laden der Schemas in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
Änderungen in einem Metadaten-Explorer in den Projektmetadaten nicht in den Quell- oder Zieltabelle Datenbanken widergespiegelt.  
  
### <a name="toolbars"></a>Symbolleisten  
SSMA verfügt über zwei Symbolleisten: eine Projekt-Symbolleiste und eine Symbolleiste für die Migration.  
  
#### <a name="the-project-toolbar"></a>Der Projekt-Symbolleiste  
Projekt enthält Schaltflächen für das Arbeiten mit Projekten, eine Verbindung mit DB2 und Herstellen einer Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Diese Schaltflächen ähneln die Befehle auf den **Datei** Menü.  
  
#### <a name="migration-toolbar"></a>Migration-Symbolleiste  
Die folgende Tabelle zeigt die Migration der Symbolleistenbefehle:  
  
|Schaltfläche|Funktion|  
|------|--------|  
|**Bericht erstellen**|Konvertiert die ausgewählten DB2-Objekte zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Syntax, und erstellt dann einen Bericht, der zeigt, wie erfolgreich die Konvertierung war.<br /><br />Dieser Befehl ist deaktiviert, es sei denn, die in DB2-Metadaten-Explorer Objekte ausgewählt sind.|  
|**Schema konvertieren**|Konvertiert die ausgewählten DB2-Objekte zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objekte.<br /><br />Dieser Befehl ist deaktiviert, es sei denn, die in DB2-Metadaten-Explorer Objekte ausgewählt sind.|  
|**Migrieren von Daten**|Migriert Daten von der DB2-Datenbank in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Bevor Sie diesen Befehl ausführen, müssen Sie die DB2-Schemas zum Konvertieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Schemas, und Laden Sie die Objekte an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br />Dieser Befehl ist deaktiviert, es sei denn, die in DB2-Metadaten-Explorer Objekte ausgewählt sind.|  
|**Beenden**|Beendet den aktuellen Prozess an.|  
  
### <a name="menus"></a>Menüs  
Die folgende Tabelle zeigt die SSMA-Menüs.  
  
|Menü "|Description|  
|----|-----------|  
|**File**|Enthält Befehle zum Arbeiten mit Projekten, eine Verbindung mit DB2 und Herstellen einer Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**Bearbeiten**|Enthält Befehle zum Suchen von und Arbeiten mit Text in der Seiten, z. B. das Kopieren [!INCLUDE[tsql](../../includes/tsql-md.md)] aus dem Bereich SQL-Details. Enthält auch die **Lesezeichen verwalten** Option, in dem Sie werden eine Liste der vorhandenen Lesezeichen angezeigt. Sie können die Schaltflächen auf der rechten Seite des Dialogfelds verwenden, um Lesezeichen zu verwalten.|  
|**Ansicht**|Enthält die **zu synchronisieren der Metadaten-Explorer** Befehl. Synchronisiert die Objekte zwischen DB2-Metadaten-Explorer und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Metadaten-Explorer. Enthält auch Befehle zum ein- und Ausblenden der **Ausgabe** und **Fehlerliste** Bereiche und eine Option **Layouts** Layouts zu verwalten.|  
|**Tools**|Enthält Befehle zum Erstellen von Berichten und Migrieren von Objekten und Daten. Bietet außerdem Zugriff auf die **globale Einstellungen** und **Projekteinstellungen** Dialogfelder.|  
|**Hilfe**|Ermöglicht den Zugriff auf SSMA unterstützen und die **zu** Dialogfeld.|  
  
### <a name="output-pane-and-error-list-pane"></a>Ausgabebereich und Fehler im Listenbereich  
Die **Ansicht** Menü enthält Befehle zum Umschalten der Sichtbarkeit der Ausgabebereich und den Bereich Fehlerliste:  
  
-   Im Ausgabebereich zeigt die statusmeldungen aus SSMA während der objektkonvertierung objektsynchronisierung und Datenmigration.  
  
-   Der Bereich Fehlerliste werden Fehler-, Warn- und informationsmeldungen in einem sortierbaren angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
[Migrieren von DB2-Daten in SQLServer &#40;DB2ToSQL&#41;](../../ssma/db2/migrating-db2-data-into-sql-server-db2tosql.md)  
[Referenz zur Benutzeroberfläche &#40;DB2ToSQL&#41;](../../ssma/db2/user-interface-reference-db2tosql.md)  
  
