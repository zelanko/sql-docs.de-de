---
title: Erste Schritte mit SSMA für Oracle (OracleToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- SSMA for Oracle, Metadata Explorers
- SSMA for Oracle, Toolbars
ms.assetid: df79664c-972e-4bef-865a-ce609789fee7
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: 80fc86c4b3d9385dc056b0c0ea9633f9f5f26675
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47782068"
---
# <a name="getting-started-with-ssma-for-oracle-oracletosql"></a>Erste Schritte mit SSMA für Oracle (OracleToSQL)
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant (SSMA) für Oracle können Sie schnell, konvertieren Sie Oracle-Datenbankschemas, um [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Schemas, Hochladen der resultierenden Schemas in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und Migrieren von Daten aus Oracle in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
Dieses Thema führt während des Installationsvorgangs, und klicken Sie dann können Sie mit der SSMA-Benutzeroberfläche vertraut zu machen.  
  
## <a name="installing-ssma"></a>Installieren von SSMA  
Um SSMA verwenden zu können, müssen Sie zunächst installieren das SSMA-Clientprogramm auf einem Computer, die sowohl für die Oracle-Quelldatenbank als auch für die Zielinstanz des zugreifen können [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Dann müssen Sie ein Erweiterungspaket und installieren mindestens eines Oracle-Anbieter (OLE DB oder [!INCLUDE[vstecado](../../includes/vstecado_md.md)]) auf dem Computer, auf denen ausgeführt wird, ist [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Diese Komponenten unterstützen die Migration von Daten und die Emulation von Oracle-System-Funktionen. Installationsanweisungen finden Sie unter [Installieren von SSMA für Oracle &#40;OracleToSQL&#41;](../../ssma/oracle/installing-ssma-for-oracle-oracletosql.md).  
  
Um SSMA zu starten, klicken Sie auf **starten**, zeigen Sie auf **Programme**, zeigen Sie auf  **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant für Oracle**, und klicken Sie dann auf  **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Migration Assistant für Oracle**.  
  
## <a name="ssma-for-oracle-user-interface"></a>SSMA für Oracle-Benutzeroberfläche  
Nach der SSMA installiert ist, können Sie SSMA Migrieren von Oracle-Datenbanken zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Es hilft, die mit der SSMA-Benutzeroberfläche vertraut zu machen, bevor Sie beginnen. Das folgende Diagramm zeigt die Benutzeroberfläche für SSMA, einschließlich der Metadaten-Explorer, Metadaten, Symbolleisten, Ausgabebereich und Fehler im Listenbereich an:  
  
![SSMA für Oracle-Benutzeroberfläche](../../ssma/oracle/media/ssma_oracle_ui.jpg "SSMA für Oracle-Benutzeroberfläche")  
  
Um eine Migration zu starten, müssen Sie zunächst ein neues Projekt erstellen. Anschließend verbinden Sie mit einer Oracle-Datenbank. Nach einer erfolgreichen Verbindung werden die Oracle-Schemas in Oracle-Metadaten-Explorer angezeigt. Sie können dann mit der rechten Maustaste-Objekte in der Oracle-Metadaten-Explorer für Aufgaben wie z. B. Berichte erstellen, die Konvertierungen zu bewerten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Sie können auch diese Aufgaben ausführen, mit der Symbolleisten und Menüs.  
  
Sie müssen auch eine Verbindung herstellen mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Nach einer erfolgreichen Verbindung eine Hierarchie von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbanken erscheint im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Metadaten-Explorer. Nach der Konvertierung zu Oracle-Schemas [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Schemas, wählen Sie die konvertierte Schemas im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Metadaten-Explorer, und klicken Sie dann zu synchronisieren der Schemas mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
Nach der Synchronisierung konvertierte Schemas mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Sie können auch zu Oracle-Metadaten-Explorer zurückkehren und Migrieren von Daten aus Oracle-Schemas in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbanken.  
  
Weitere Informationen zu diesen Aufgaben und deren Ausführung finden Sie unter [Migrieren von Oracle-Datenbanken zu SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md).  
  
Die folgenden Abschnitte beschreiben die Funktionen der SSMA-Benutzeroberfläche.  
  
### <a name="metadata-explorers"></a>Metadaten-Explorer  
SSMA enthält zwei Metadaten-Explorer zum Durchsuchen und Ausführen von Aktionen für Oracle und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbanken.  
  
#### <a name="oracle-metadata-explorer"></a>Oracle-Metadaten-Explorer  
Oracle-Metadaten-Explorer zeigt Informationen zu Oracle-Schemas. Mithilfe von Oracle-Metadaten-Explorer können Sie die folgenden Aufgaben ausführen:  
  
-   Durchsuchen Sie die Objekte in den einzelnen Schemas.  
  
-   Wählen Sie Objekte für die Konvertierung konvertiert und dann die Objekte an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Syntax. Weitere Informationen finden Sie unter [Konvertieren von Oracle Schemas &#40;OracleToSQL&#41;](../../ssma/oracle/converting-oracle-schemas-oracletosql.md).  
  
-   Wählen Sie die Tabellen für die Datenmigration aus, und klicken Sie dann die Daten aus diesen Tabellen zu migrieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Weitere Informationen finden Sie unter [Migrieren von Oracle-Daten in SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/migrating-oracle-data-into-sql-server-oracletosql.md).  
  
#### <a name="sql-server-metadata-explorer"></a>SQL Server-Metadaten-Explorer  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Metadaten-Explorer zeigt Informationen zu einer Instanz des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Wenn Sie die Verbindung zu einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], SSMA Ruft Metadaten zu dieser Instanz ab und speichert sie in der Projektdatei.  
  
Sie können [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Metadaten-Explorer, wählen Sie konvertierte Objekte der Oracle-Datenbank, und klicken Sie dann die Objekte zu synchronisieren, mit der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
Weitere Informationen finden Sie unter [konvertiert Datenbankobjekte in SQL Server laden &#40;OracleToSQL&#41;](../../ssma/oracle/loading-converted-database-objects-into-sql-server-oracletosql.md).  
  
### <a name="metadata"></a>Metadaten  
Befinden sich rechts neben jeder Metadaten-Explorer Registerkarten, die das ausgewählte Objekt zu beschreiben. Beispielsweise wenn Sie eine Tabelle in Oracle-Metadaten-Explorer auswählen, sechs Registerkarten werden angezeigt: **Tabelle**, **SQL**, **Type Mapping, Bericht**, **Eigenschaften**, und **Daten**. Die **Bericht** Registerkarte enthält Informationen, nachdem Sie einen Bericht erstellen, die das ausgewählte Objekt enthält. Bei Auswahl eine Tabelle in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Metadaten-Explorer, die drei Registerkarten angezeigt werden: **Tabelle**, **SQL**, und **Daten**.  
  
Die meisten Metadateneinstellungen für die sind schreibgeschützt. Allerdings können Sie die folgende Metadaten ändern:  
  
-   Im Oracle-Metadaten-Explorer können Sie Prozeduren alter und datentypzuordnungen. Um die geänderten Verfahren konvertieren und datentypzuordnungen, können nehmen Sie Änderungen vor, bevor Sie Schemas konvertieren.  
  
-   In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Metadaten-Explorer können Sie ändern die [!INCLUDE[tsql](../../includes/tsql-md.md)] für gespeicherte Prozeduren. Diese Änderungen im anzeigen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], nehmen Sie diese Änderungen vor dem Laden der Schemas in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
Änderungen in einem Metadaten-Explorer in den Projektmetadaten nicht in den Quell- oder Zieltabelle Datenbanken widergespiegelt.  
  
### <a name="toolbars"></a>Symbolleisten  
SSMA verfügt über zwei Symbolleisten: eine Projekt-Symbolleiste und eine Symbolleiste für die Migration.  
  
#### <a name="the-project-toolbar"></a>Der Projekt-Symbolleiste  
Projekt enthält Schaltflächen für die Arbeit mit Projekten und Herstellen einer Verbindung mit Oracle Herstellen einer Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Diese Schaltflächen ähneln die Befehle auf den **Datei** Menü.  
  
#### <a name="migration-toolbar"></a>Migration-Symbolleiste  
Die folgende Tabelle zeigt die Migration der Symbolleistenbefehle:  
  
|Schaltfläche|Funktion|  
|------|--------|  
|**Bericht erstellen**|Konvertiert die ausgewählte Oracle-Objekte zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Syntax, und erstellt dann einen Bericht, der zeigt, wie erfolgreich die Konvertierung war.<br /><br />Dieser Befehl ist deaktiviert, es sei denn, die Objekte in der Oracle-Metadaten-Explorer ausgewählt werden.|  
|**Schema konvertieren**|Konvertiert die ausgewählte Oracle-Objekte zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objekte.<br /><br />Dieser Befehl ist deaktiviert, es sei denn, die Objekte in der Oracle-Metadaten-Explorer ausgewählt werden.|  
|**Migrieren von Daten**|Migriert Daten aus der Oracle-Datenbank für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Bevor Sie diesen Befehl ausführen, müssen Sie die Oracle-Schemas zum Konvertieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Schemas, und Laden Sie die Objekte an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br />Dieser Befehl ist deaktiviert, es sei denn, die Objekte in der Oracle-Metadaten-Explorer ausgewählt werden.|  
|**Beenden**|Beendet den aktuellen Prozess an.|  
  
### <a name="menus"></a>Menüs  
Die folgende Tabelle zeigt die SSMA-Menüs.  
  
|Menü "|Description|  
|----|-----------|  
|**File**|Enthält Befehle zum Arbeiten mit Projekten und Herstellen einer Verbindung mit Oracle Herstellen einer Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**Bearbeiten**|Enthält Befehle zum Suchen von und Arbeiten mit Text in der Seiten, z. B. das Kopieren [!INCLUDE[tsql](../../includes/tsql-md.md)] aus dem Bereich SQL-Details. Enthält auch die **Lesezeichen verwalten** Option, in dem Sie werden eine Liste der vorhandenen Lesezeichen angezeigt. Sie können die Schaltflächen auf der rechten Seite des Dialogfelds verwenden, um Lesezeichen zu verwalten.|  
|**Ansicht**|Enthält die **zu synchronisieren der Metadaten-Explorer** Befehl. Synchronisiert die Objekte zwischen Oracle-Metadaten-Explorer und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Metadaten-Explorer. Enthält auch Befehle zum ein- und Ausblenden der **Ausgabe** und **Fehlerliste** Bereiche und eine Option **Layouts** Layouts zu verwalten.|  
|**Tools**|Enthält Befehle zum Erstellen von Berichten und Migrieren von Objekten und Daten. Bietet außerdem Zugriff auf die **globale Einstellungen** und **Projekteinstellungen** Dialogfelder.|  
|**Tester**|Befehle zum Erstellen und Verwenden von Testfällen, Repository und backup-Management-System.|  
|**Hilfe**|Ermöglicht den Zugriff auf SSMA unterstützen und die **zu** Dialogfeld.|  
  
### <a name="output-pane-and-error-list-pane"></a>Ausgabebereich und Fehler im Listenbereich  
Die **Ansicht** Menü enthält Befehle zum Umschalten der Sichtbarkeit der Ausgabebereich und den Bereich Fehlerliste:  
  
-   Im Ausgabebereich zeigt die statusmeldungen aus SSMA während der objektkonvertierung objektsynchronisierung und Datenmigration.  
  
-   Der Bereich Fehlerliste werden Fehler-, Warn- und informationsmeldungen in einem sortierbaren angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
[Migrieren von Oracle-Daten in SQLServer &#40;OracleToSQL&#41;](../../ssma/oracle/migrating-oracle-data-into-sql-server-oracletosql.md)  
[Referenz zur Benutzeroberfläche &#40;OracleToSQL&#41;](../../ssma/oracle/user-interface-reference-oracletosql.md)  
  
