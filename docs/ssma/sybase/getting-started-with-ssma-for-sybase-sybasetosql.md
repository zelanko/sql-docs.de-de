---
title: Erste Schritte mit SSMA für SAP ASE (SybaseToSQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/30/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: c4098516-f0fc-4690-97bb-3766dfd43156
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 7e308589ab565b5702bbf2cba939835a50c08d8e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47678368"
---
# <a name="getting-started-with-ssma-for-sap-ase-sybasetosql"></a>Erste Schritte mit SSMA für SAP ASE (SybaseToSQL)
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant (SSMA) für SAP ASE können Sie schnell, konvertieren Sie Datenbankschemas SAP Adaptive Server Enterprise (ASE), um [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank-Schemas, Hochladen der resultierenden Schemas in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank und Migrieren von Daten aus SAP ASE [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank.  
  
Dieses Thema führt während des Installationsvorgangs, und klicken Sie dann können Sie mit der SSMA-Benutzeroberfläche vertraut zu machen.  
  
## <a name="installing-and-licensing-ssma"></a>Installieren und lizenzieren SSMA  
Um SSMA verwenden zu können, müssen Sie zunächst installieren das SSMA-Clientprogramm auf einem Computer, die sowohl die Quellinstanz, von SAP ASE als auch die Zielinstanz des zugreifen können [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank. Um serverseitige Datenmigration zu verwenden, müssen Sie Erweiterungspaket und mindestens einem der SAP ASE-Anbieter (OLE DB oder ADO.NET) installieren, auf dem Computer, auf denen ausgeführt wird, ist [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Diese Komponenten unterstützen die Migration von Daten und die Emulation von SAP ASE-Systemfunktionen. Installationsanweisungen finden Sie unter [Installieren von SSMA für SAP ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-for-sybase-sybasetosql.md).  
  
Um SSMA zu starten, klicken Sie auf **starten**, zeigen Sie auf **Programme**, zeigen Sie auf  **[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant für Sybase**, und wählen Sie dann auf  **[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant für Sybase**. Zum ersten Mal starten Sie SSMA wird ein Dialogfeld für die Terminaldienstelizenzierung angezeigt. Sie müssen die SSMA lizenzieren, mithilfe einer Windows Live ID, bevor Sie SSMA verwenden können. Lizenzierung Anweisungen sind im Lieferumfang von den Anweisungen in der [Installieren von SSMA für Sybase Client &#40;SybaseToSQL&#41; ](../../ssma/sybase/installing-ssma-for-sybase-client-sybasetosql.md) Thema.  
  
## <a name="ssma-for-sap-ase-user-interface"></a>SSMA für SAP ASE-Benutzeroberfläche  
Nach der SSMA installiert und lizenziert ist, können Sie SSMA um SAP ASE-Datenbanken zu migrieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank. Es hilft, die mit der SSMA-Benutzeroberfläche vertraut zu machen, bevor Sie beginnen. Das folgende Diagramm zeigt die Benutzeroberfläche für SSMA, einschließlich der Metadaten-Explorer, Metadaten, Symbolleisten, Ausgabebereich und Fehler im Listenbereich an:  
  
![SSMA für SAP ASE-Benutzeroberfläche](../../ssma/sybase/media/ssmaforsybaseuserinterface.jpg "SSMA für SAP ASE-Benutzeroberfläche")  
  
Um eine Migration zu starten, müssen Sie zunächst ein neues Projekt erstellen. Anschließend verbinden Sie bei SAP ASE auf. Nach einer erfolgreichen Verbindung wird eine Hierarchie von SAP ASE-Datenbanken in der Sybase-Metadaten-Explorer angezeigt. Sie können dann mit der rechten Maustaste-Objekte in der Sybase-Metadaten-Explorer zum Ausführen von Aufgaben wie z. B. Berichte erstellen, die Konvertierungen zu bewerten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank. Sie können auch dieser Aufgaben mithilfe von Symbolleisten und Menüs durchführen.  
  
Sie auch müssen eine Verbindung herstellen mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank. Nach einer erfolgreichen Verbindung eine Hierarchie von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbanken werden angezeigt, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Metadaten-Explorer. Nach der Konvertierung zu SAP ASE-Schemas [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank-Schemas, wählen Sie die konvertierte Schemas im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Metadaten-Explorer, und Laden Sie die Schemas in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank.  
  
Laden Sie konvertierte Schemas in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank, die Sie in der Sybase-Metadaten-Explorer zurückkehren und Migrieren von Daten aus SAP ASE-Datenbanken in können [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbanken.  
  
Weitere Informationen zu diesen Aufgaben und deren Ausführung finden Sie unter [SAP ASE-Datenbanken zu SQL Server - Azure SQL-Datenbank migrieren &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md).  
  
Die folgenden Abschnitte beschreiben die Funktionen der SSMA-Benutzeroberfläche.  
  
### <a name="metadata-explorers"></a>Metadaten-Explorer  
SSMA enthält zwei Metadaten-Explorer zum Durchsuchen und Ausführen von Aktionen für SAP ASE und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbanken.  
  
#### <a name="sybase-metadata-explorer"></a>Sybase-Metadaten-Explorer  
Sybase-Metadaten-Explorer zeigt Informationen zu Datenbanken auf der Quellinstanz, von SAP ASE an.  
  
Mithilfe von Sybase-Metadaten-Explorer können Sie die folgenden Aufgaben ausführen:  
  
-   Durchsuchen Sie die Tabellen in jeder Datenbank.  
  
-   Wählen Sie Objekte für die Konvertierung konvertiert und dann die Objekte an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL Database-Syntax. Weitere Informationen finden Sie unter [Konvertieren von SAP ASE-Datenbankobjekten &#40;SybaseToSQL&#41;](../../ssma/sybase/converting-sybase-ase-database-objects-sybasetosql.md).  
  
-   Wählen Sie Objekte für die Datenmigration aus, und klicken Sie dann die Daten aus diesen Objekten zu migrieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank. Weitere Informationen finden Sie unter [SAP ASE-Daten in SQL Server – Azure SQL-Datenbank migrieren &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-data-into-sql-server-azure-sql-db-sybasetosql.md).  
  
#### <a name="sql-server-or-sql-azure-metadata-explorer"></a>SQLServer oder SQL Azure-Metadaten-Explorer  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Metadaten-Explorer zeigt Informationen zu einer Instanz des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank. Wenn Sie die Verbindung zu einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank, SSMA Ruft Metadaten zu dieser Instanz ab und speichert sie in der Projektdatei.  
  
Können Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Metadaten-Explorer, wählen konvertierte SAP ASE-Datenbankobjekten aus, und klicken Sie dann zu laden (synchronisieren) die Objekte in der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank.  
  
Weitere Informationen finden Sie unter [konvertiert Datenbankobjekte in SQL Server laden &#40;SybaseToSQL&#41;](../../ssma/sybase/loading-converted-database-objects-into-sql-server-sybasetosql.md).  
  
### <a name="metadata"></a>Metadaten  
Befinden sich rechts neben jeder Metadaten-Explorer Registerkarten, die das ausgewählte Objekt zu beschreiben. Beispielsweise wenn Sie eine Tabelle in der Sybase-Metadaten-Explorer auswählen, die sechs Registerkarten angezeigt: **Tabelle**, **SQL**, **Type Mapping**, **Daten**,  **Eigenschaften**, und **Bericht**. Die **Bericht** Registerkarte enthält Informationen, nachdem Sie einen Bericht mit dem ausgewählten Objekt erstellt. Bei Auswahl eine Tabelle in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Metadaten-Explorer, drei Registerkarten angezeigt: **Tabelle**, **SQL**, und **Daten**.  
  
Die meisten Metadateneinstellungen für die sind schreibgeschützt. Allerdings können Sie die folgende Metadaten ändern:  
  
-   In Sybase-Metadaten-Explorer können Sie Prozeduren alter und datentypzuordnungen. Nehmen Sie diese Änderungen vor, bevor Sie die Schemas konvertieren.  
  
-   In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Metadaten-Explorer können Sie ändern die [!INCLUDE[tsql](../../includes/tsql-md.md)] für gespeicherte Prozeduren. Diese Änderungen vornehmen, bevor Sie die Schemas in laden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
Änderungen in einem Metadaten-Explorer in den Projektmetadaten nicht in den Quell- oder Zieltabelle Datenbanken widergespiegelt.  
  
### <a name="toolbars"></a>Symbolleisten  
SSMA verfügt über zwei Symbolleisten: eine Projekt-Symbolleiste und eine Symbolleiste für die Migration.  
  
#### <a name="the-project-toolbar"></a>Der Projekt-Symbolleiste  
Projekt enthält Schaltflächen für das Arbeiten mit Projekten, eine Verbindung mit SAP ASE und Herstellen einer Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank. Diese Schaltflächen ähneln die Befehle auf den **Datei** Menü.  
  
#### <a name="the-migration-toolbar"></a>Die Symbolleiste für die Migration  
Die Migrations-Symbolleiste enthält die folgenden Befehle aus:  
  
|Schaltfläche|Funktion|  
|----------|------------|  
|**Bericht erstellen**|Konvertiert die ausgewählten SAP ASE-Objekte zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Syntax, und erstellt dann einen Bericht, der zeigt, wie erfolgreich die Konvertierung war.<br /><br />Mit diesem Befehl steht nur, wenn Objekte in der Sybase-Metadaten-Explorer ausgewählt werden.|  
|**Schema konvertieren**|Konvertiert die ausgewählten SAP ASE-Objekte zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank-Objekte.<br /><br />Mit diesem Befehl steht nur, wenn Objekte in der Sybase-Metadaten-Explorer ausgewählt werden.|  
|**Migrieren von Daten**|Migration von Daten aus der SAP ASE-Datenbank für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank. Bevor Sie diesen Befehl ausführen, müssen Sie die SAP ASE-Schemas zum Konvertieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank-Schemas, und Laden Sie die Objekte an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank.<br /><br />Mit diesem Befehl steht nur, wenn Objekte in der Sybase-Metadaten-Explorer ausgewählt werden.|  
|**Beenden**|Beendet den aktuellen Prozess, z. B. Konvertieren von Objekten zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL Database-Syntax.|  
  
### <a name="menus"></a>Menüs  
SSMA enthält die folgenden Menüs:  
  
|Menü "|Description|  
|--------|---------------|  
|**File**|Enthält Befehle zum Arbeiten mit Projekten, eine Verbindung mit SAP ASE und Herstellen einer Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank.|  
|**Bearbeiten**|Enthält Befehle zum Suchen von und Arbeiten mit Text in der Seiten, z. B. das Kopieren [!INCLUDE[tsql](../../includes/tsql-md.md)] aus dem Bereich SQL-Details. Enthält auch die **Lesezeichen verwalten** Option hier Sie eine Liste der vorhandenen Lesezeichen sehen. Sie können die Schaltflächen auf der rechten Seite des Dialogfelds verwenden, um Lesezeichen zu verwalten.|  
|**Ansicht**|Enthält die **zu synchronisieren der Metadaten-Explorer** Befehl. Hiermit erfolgt die Synchronisierung der Objekte zwischen Sybase-Metadaten-Explorer und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure-Metadaten-Explorer. Enthält auch Befehle zum Anzeigen oder Ausblenden der **Ausgabe** und **Fehlerliste** Bereiche und eine Option **Layouts** Layouts zu verwalten.|  
|**Tools**|Befehle zum Erstellen von Berichten, Exportieren von Daten und Objekte und Daten migrieren. Bietet außerdem Zugriff auf die **globale Einstellungen** und **Projekteinstellungen** Dialogfelder.|  
|**Tester**|Enthält Befehle zum Erstellen von Testfällen, Anzeigen von Testergebnissen und Befehle für die sicherungsverwaltung Datenbank an.|  
|**Hilfe**|Ermöglicht den Zugriff auf SSMA unterstützen und die **zu** Dialogfeld.|  
  
### <a name="output-pane-and-error-list-pane"></a>Ausgabe und Fehlerliste  
Die **Ansicht** Menü enthält Befehle zum Umschalten der Sichtbarkeit der Ausgabebereich und den Bereich Fehlerliste:  
  
-   Im Ausgabebereich zeigt die statusmeldungen aus SSMA während der objektkonvertierung objektsynchronisierung und Datenmigration.  
  
-   Der Bereich Fehlerliste zeigt Fehler-, Warn- und informationsmeldungen in einer Liste, die Sie sortieren können.  
  
## <a name="see-also"></a>Siehe auch  
[Migrieren von SAP ASE-Datenbanken zu SQLServer – Azure SQL-Datenbank &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
[Referenz zur Benutzeroberfläche &#40;SybaseToSQL&#41;](../../ssma/sybase/user-interface-reference-sybasetosql.md)  
