---
title: Beginnen Sie mit der SQL Server Migration Assistant für den Zugriff | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 08/15/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- error list pane
- getting started
- menus
- metadata explorers
- output pane
- toolbars
- user interface
- user interface overview
ms.assetid: 462a731f-08f1-44e1-9eeb-4deac6d2f6c5
author: Shamikg
ms.author: Shamikg
manager: murato
ms.openlocfilehash: 863e62dc9e2970f7531bba15f7242c73c5b0f9e7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68259924"
---
# <a name="getting-started-with-sql-server-migration-assistant-for-access-accesstosql"></a>Ersten Schritte mit SQL Server Migration Assistant für den Zugriff (Access Token)
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Migration Assistant (SSMA) für den Zugriff ermöglicht Ihnen das schnelle Konvertieren von Access- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbankobjekten in oder Azure SQL-Datenbankobjekte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , das Hochladen der resultierenden Objekte in oder Azure SQL- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank sowie das Migrieren von Daten aus dem Zugriff auf oder Azure SQL-Datenbank. Bei Bedarf können Sie auch Zugriffs Tabellen mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbanktabellen verknüpfen, sodass Sie weiterhin Ihre vorhandenen Access-Front-End-Anwendungen mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank verwenden können.  
  
Dieses Thema enthält eine Einführung in den Installationsvorgang und hilft Ihnen, Sie mit der SSMA-Benutzeroberfläche vertraut zu machen.  
  
## <a name="installing-ssma"></a>Installieren von SSMA  
Zum Verwenden von SSMA müssen Sie zuerst das SSMA-Client Programm auf einem Computer installieren, der auf die zu migrierenden Datenbanken und die Ziel Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank zugreifen kann. Installationsanweisungen finden Sie unter [Installieren von SQL Server Migration Assistant für Access &#40;accesstosql&#41;](../../ssma/access/installing-sql-server-migration-assistant-for-access-accesstosql.md).  
  
Klicken Sie zum Starten von SSMA auf **Start**, zeigen Sie auf **Alle Programme**, zeigen Sie auf **SQL Server Migration Assistant für Zugriff**, und wählen Sie dann **SQL Server Migration Assistant für den Zugriff aus**.  
  
## <a name="using-ssma"></a>Verwenden von SSMA  
Nach der Installation von SSMA sollten Sie sich mit der SSMA-Benutzeroberfläche vertraut machen, bevor Sie das Tool zum Migrieren von Access-Datenbanken zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank verwenden. Die SSMA-Benutzeroberfläche, einschließlich der Metadaten-Explorer, Metadaten, Symbolleisten, Ausgabebereich und Fehlerlisten Bereich, wird in der folgenden Abbildung dargestellt:  
  
![SSMA für die grafische Access-Benutzeroberfläche](../../ssma/access/media/ssmaforaccessgui.gif "SSMA für die grafische Access-Benutzeroberfläche")  
  
Um eine Migration zu starten, erstellen Sie ein neues Projekt, und fügen Sie dann Access-Datenbanken zum Zugreifen auf den metadatenexplorer hinzu Sie können dann in Access Metadata Explorer mit der rechten Maustaste auf Objekte klicken, um folgende Aufgaben auszuführen:
- Exportieren eines Bestands von Access-Daten Bank [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objekten in oder Azure SQL-Datenbank.
- Erstellen von Berichten, die Konvertierungen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank bewerten.
- Die Zugriffs Schemas werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in-oder Azure SQL-Datenbankschemas umgerechnet.

Sie können diese Aufgaben auch mithilfe der Symbolleisten und Menüs ausführen.  
  
Sie müssen auch eine Verbindung mit einer Instanz [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]von herstellen. Nach einer erfolgreichen Verbindung wird eine Hierarchie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von Datenbanken [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im metadatenexplorer angezeigt. Nachdem Sie Zugriffs Schemas in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Schemas konvertiert haben, können Sie diese konvertierten Schemas [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im metadatenexplorer auswählen und dann die Schemas [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]in laden.  
  
Wenn Sie im Dialogfeld Neues Projekt im Dropdown Menü Migrieren zu die Option Azure SQL-Datenbank ausgewählt haben, müssen Sie eine Verbindung mit Azure SQL-Datenbank herstellen. Nach einer erfolgreichen Verbindung wird eine Hierarchie von Azure SQL-Datenbanken im metadatenexplorer von Azure SQL DB angezeigt. Nachdem Sie Zugriffs Schemas in Azure SQL-Datenbankschemas konvertiert haben, können Sie diese konvertierten Schemas im metadatenexplorer von Azure SQL-Datenbank auswählen und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]dann die Schemas in laden.  
  
Nachdem Sie konvertierte Schemas in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank geladen haben, können Sie auf den Metadaten-Explorer zugreifen und Daten aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Access-Datenbanken in oder Azure SQL-Datenbanken migrieren. Bei Bedarf können Sie auch Zugriffs Tabellen mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbanktabellen verknüpfen.  
  
Weitere Informationen zu diesen Aufgaben und deren Ausführung finden Sie in den folgenden Themen:  
  
-   [Vorbereiten einer Access-Datenbank für die Migration](preparing-access-databases-for-migration-accesstosql.md)  
  
-   [Migration von Access-Datenbanken zu SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
  
-   [Verknüpfen von Zugriffs Anwendungen mit SQL Server](linking-access-applications-to-sql-server-azure-sql-db-accesstosql.md)  
  
In den folgenden Abschnitten werden die Features der SSMA-Benutzeroberfläche beschrieben.  
  
### <a name="metadata-explorers"></a>Metadatenexplorer  
SSMA enthält zwei metadatenexplorer, die Sie zum Durchsuchen und Ausführen von Aktionen bei [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Access und oder Azure SQL DB-Datenbanken verwenden können.  
  
#### <a name="access-metadata-explorer"></a>Access-Metadaten-Explorer  
Access Metadata Explorer zeigt Informationen über die Access-Datenbanken an, die dem Projekt hinzugefügt wurden. Wenn Sie eine Access-Datenbank hinzufügen, ruft SSMA Metadaten zu dieser Datenbank ab. Dies sind die Metadaten, die im Access Metadata Explorer verfügbar sind.  
  
Sie können den Zugriff auf den Metadaten-Explorer verwenden, um die folgenden Aufgaben auszuführen:  
  
-   Durchsuchen Sie die Tabellen in jeder Access-Datenbank.  
  
-   Wählen Sie Objekte für die Konvertierung aus, und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] konvertieren Sie die Objekte in Syntax. Weitere Informationen finden Sie unter [umstellen von Access-Datenbankobjekten](converting-access-database-objects-accesstosql.md).  
  
-   Wählen Sie Objekte für die Datenmigration aus, und migrieren Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]die Daten von diesen Objekten zu. Weitere Informationen finden Sie unter [Migrieren von Zugriffsdaten in SQL Server](migrating-access-data-into-sql-server-azure-sql-db-accesstosql.md).  
  
-   Verknüpfen und Aufheben der Verknüpfung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Access und Tabellen.  
  
#### <a name="sql-server-or-azure-sql-db-metadata-explorer"></a>SQL Server oder Azure SQL-Datenbank-metadatenexplorer  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]oder der Azure SQL-Datenbank-metadatenexplorer zeigt Informationen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zu einer Instanz von oder Azure SQL-Datenbank an. Wenn Sie eine Verbindung mit einer Instanz [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von oder mit Azure SQL-Datenbank herstellen, ruft SSMA Metadaten zu dieser Instanz ab und speichert Sie in der Projektdatei.  
  
Sie können die SQL Server oder den metadatenexplorer von Azure SQL-Datenbank verwenden, um konvertierte Access-Datenbankobjekte auszuwählen und diese Objekte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in die Instanz von oder Azure SQL-Datenbank zu laden (zu synchronisieren).  
  
Weitere Informationen finden Sie unter [Laden von konvertierten Datenbankobjekten in SQL Server](loading-converted-database-objects-into-sql-server-accesstosql.md).  
  
### <a name="metadata"></a>Metadaten  
Auf der rechten Seite jedes metadatenexplorers sind Registerkarten, die das ausgewählte Objekt beschreiben. Wenn Sie z. b. eine Tabelle in Access Metadata Explorer auswählen, werden vier Registerkarten angezeigt: **Table**, **Type Mapping**, **Properties**und **Data**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Wenn Sie eine Tabelle im metadatenexplorer auswählen, werden drei Registerkarten angezeigt: **Table**, **SQL**und **Data**.  
  
Die meisten metadateneinstellungen sind schreibgeschützt. Sie können jedoch die folgenden Metadaten ändern:  
  
-   In Access Metadata Explorer können Sie Typzuordnungen ändern. Stellen Sie sicher, dass Sie diese Änderungen vornehmen, bevor Sie Berichte erstellen oder Schemas konvertieren.  
  
-   Im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] metadatenexplorer können Sie Tabellen-und Index Eigenschaften auf der Registerkarte **Tabelle** ändern. nehmen Sie diese Änderungen vor, bevor Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]die Schemas in laden. Weitere Informationen finden Sie unter [umstellen von Access-Datenbankobjekten](converting-access-database-objects-accesstosql.md).  
  
### <a name="toolbars"></a>Symbolleisten  
SSMA verfügt über zwei Symbolleisten: eine Projektsymbol Leiste und eine Migrations Symbolleiste.  
  
#### <a name="the-project-toolbar"></a>Die Projektsymbol Leiste  
Die Projektsymbol Leiste enthält Schaltflächen zum Arbeiten mit Projekten, zum Hinzufügen von Access- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbankdateien sowie zum Herstellen einer Verbindung mit oder Azure SQL DB. Diese Schaltflächen ähneln den Befehlen im Menü **Datei** .  
  
#### <a name="the-migration-toolbar"></a>Die Migrations Symbolleiste  
Die Migrations Symbolleiste enthält die folgenden Befehle:  
  
|Schaltfläche|Funktion|  
|----------|------------|  
|**Konvertieren, Laden und Migrieren**|Konvertiert Access-Datenbanken, lädt die konvertierten Objekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank und migriert Daten in einem einzigen Schritt in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-DB.|  
|**Erstellen von Berichten**|Konvertiert das ausgewählte Zugriffs Schema in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die-oder Azure SQL-Daten Bank Syntax und erstellt dann einen Bericht, der die erfolgreiche Konvertierung der Konvertierung anzeigt.<br /><br />Dieser Befehl ist nur verfügbar, wenn Objekte im Access Metadata Explorer ausgewählt werden.|  
|**Schema konvertieren**|Konvertiert das ausgewählte Zugriffs Schema in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbankschemas.<br /><br />Dieser Befehl ist nur verfügbar, wenn Objekte im Access Metadata Explorer ausgewählt werden.|  
|**Migrieren von Daten**|Migriert Daten von der Access-Datenbank [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zu oder Azure SQL-Datenbank. Vor dem Ausführen dieses Befehls müssen Sie die Zugriffs Schemas in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -oder Azure SQL-Datenbankschemas konvertieren und die Objekte anschließend in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank laden.<br /><br />Dieser Befehl ist nur verfügbar, wenn Objekte im Access Metadata Explorer ausgewählt werden.|  
|**Beenden**|Beendet den aktuellen Prozess, z. b. das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] umstellen von Objekten in oder die Azure SQL-Daten Bank Syntax.|  
  
### <a name="menus"></a>Menüs  
SSMA enthält die folgenden Menüs:  
  
|Menü|BESCHREIBUNG|  
|--------|---------------|  
|**Datei**|Enthält Befehle für den Migrations-Assistenten, das Arbeiten mit Projekten, das Hinzufügen und Entfernen von Access- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbankdateien und das Herstellen einer Verbindung mit oder Azure SQL DB.|  
|**Bearbeiten**|Enthält Befehle zum Suchen und arbeiten mit Text auf den Detailseiten, z. b [!INCLUDE[tsql](../../includes/tsql-md.md)] . zum Kopieren aus dem SQL-Detailbereich. Um das Dialogfeld **Lesezeichen verwalten** zu öffnen, klicken Sie im Menü Bearbeiten auf Lesezeichen verwalten. Im Dialogfeld wird eine Liste vorhandener Lesezeichen angezeigt. Sie können die Schaltflächen auf der rechten Seite des Dialog Felds verwenden, um die Lesezeichen zu verwalten.|  
|**Ansicht**|Enthält den Befehl Metadaten-Explorer **Synchronisieren** . Dadurch werden die Objekte zwischen Access Metadata Explorer und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL DB Metadata Explorer synchronisiert. Enthält auch Befehle zum Anzeigen und Ausblenden der **Ausgabe** -und **Fehlerliste** Bereiche sowie ein Options **Layout** , das mit den Layouts verwaltet werden soll.|  
|**Tools**|Enthält Befehle zum Erstellen von Berichten, Exportieren von Daten, Migrieren von Objekten und Daten, Verknüpfen von Tabellen und Bereitstellen des Zugriffs auf die Dialogfelder für globale und Projekteinstellungen.|  
|**Hilfe**|Bietet Zugriff **auf die** SSMA-Hilfe und das Dialogfeld Info.|  
  
### <a name="output-pane-and-error-list-pane"></a>Ausgabebereich und Fehlerliste Bereich  
Das Menü **Ansicht** enthält Befehle zum Umschalten der Sichtbarkeit des Ausgabe Bereichs und des Fehlerliste Bereichs:  
  
-   Im Ausgabebereich werden Statusmeldungen von SSMA während der Objekt Konvertierung, der Objekt Synchronisierung und der Datenmigration angezeigt.  
  
-   Im Fehlerliste Bereich werden Fehler-, Warn-und Informationsmeldungen in einer Liste angezeigt, die Sie sortieren können.  
  
## <a name="see-also"></a>Weitere Informationen  
[Migration von Access-Datenbanken zu SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
  
