---
title: Beginnen Sie mit der SQL Server Migration Assistant für den Zugriff | Microsoft-Dokumentation
description: Beginnen Sie mit der Verwendung von SSMA, um Access Database Objects in SQL Server-oder Azure SQL-Datenbankobjekte zu konvertieren, die resultierenden Objekte hochzuladen und Daten zu migrieren
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
ms.openlocfilehash: b27d773bc8fd928e7db2e29c7a01492fb97df78f
ms.sourcegitcommit: 777704aefa7e574f4b7d62ad2a4c1b10ca1731ff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/06/2020
ms.locfileid: "87823947"
---
# <a name="getting-started-with-sql-server-migration-assistant-for-access-accesstosql"></a>Ersten Schritte mit SQL Server Migration Assistant für den Zugriff (Access Token)
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Migration Assistant (SSMA) für den Zugriff ermöglicht Ihnen das schnelle Konvertieren von Access-Datenbankobjekten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbankobjekte, das Hochladen der resultierenden Objekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank sowie das Migrieren von Daten aus dem Zugriff auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank. Bei Bedarf können Sie auch Zugriffs Tabellen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mit oder Azure SQL-Datenbanktabellen verknüpfen, sodass Sie weiterhin Ihre vorhandenen Access-Front-End-Anwendungen mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank verwenden können.  
  
Dieses Thema enthält eine Einführung in den Installationsvorgang und hilft Ihnen, Sie mit der SSMA-Benutzeroberfläche vertraut zu machen.  
  
## <a name="installing-ssma"></a>Installieren von SSMA  
Zum Verwenden von SSMA müssen Sie zuerst das SSMA-Client Programm auf einem Computer installieren, der auf die zu migrierenden Datenbanken und die Ziel Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank zugreifen kann. Installationsanweisungen finden Sie unter [Installieren von SQL Server Migration Assistant für Access &#40;accesstosql&#41;](../../ssma/access/installing-sql-server-migration-assistant-for-access-accesstosql.md).  
  
Klicken Sie zum Starten von SSMA auf **Start**, zeigen Sie auf **Alle Programme**, zeigen Sie auf **SQL Server Migration Assistant für Zugriff**, und wählen Sie dann **SQL Server Migration Assistant für den Zugriff aus**.  
  
## <a name="using-ssma"></a>Verwenden von SSMA  
Nach der Installation von SSMA sollten Sie sich mit der SSMA-Benutzeroberfläche vertraut machen, bevor Sie das Tool verwenden, um Access-Datenbanken zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank zu migrieren. Die SSMA-Benutzeroberfläche, einschließlich der Metadaten-Explorer, Metadaten, Symbolleisten, Ausgabebereich und Fehlerlisten Bereich, wird in der folgenden Abbildung dargestellt:  
  
![SSMA für die grafische Access-Benutzeroberfläche](../../ssma/access/media/ssmaforaccessgui.gif "SSMA für die grafische Access-Benutzeroberfläche")  
  
Um eine Migration zu starten, erstellen Sie ein neues Projekt, und fügen Sie dann Access-Datenbanken zum Zugreifen auf den metadatenexplorer hinzu Sie können dann in Access Metadata Explorer mit der rechten Maustaste auf Objekte klicken, um folgende Aufgaben auszuführen:
- Exportieren eines Bestands von Access-Datenbankobjekten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank.
- Erstellen von Berichten, die Konvertierungen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank bewerten.
- Die Zugriffs Schemas werden in- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbankschemas umgerechnet.

Sie können diese Aufgaben auch mithilfe der Symbolleisten und Menüs ausführen.  
  
Sie müssen auch eine Verbindung mit einer Instanz von herstellen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Nach einer erfolgreichen Verbindung wird eine Hierarchie von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbanken im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] metadatenexplorer angezeigt. Nachdem Sie Zugriffs Schemas in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Schemas konvertiert haben, können Sie diese konvertierten Schemas im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] metadatenexplorer auswählen und dann die Schemas in Laden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
Wenn Sie im Dialogfeld Neues Projekt die Option Azure SQL-Datenbank im Dropdown Menü Migrieren zu ausgewählt haben, müssen Sie eine Verbindung mit Azure SQL-Datenbank herstellen. Nach einer erfolgreichen Verbindung wird eine Hierarchie von Azure SQL-Daten Bank Datenbanken im metadatenexplorer von Azure SQL-Datenbank angezeigt. Nachdem Sie Zugriffs Schemas in Azure SQL-Datenbankschemas konvertiert haben, können Sie diese konvertierten Schemas im metadatenexplorer von Azure SQL-Datenbank auswählen und dann die Schemas in Laden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
Nachdem Sie konvertierte Schemas in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank geladen haben, können Sie auf den Metadaten-Explorer zugreifen und Daten aus Access-Datenbanken in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Daten Bank Datenbanken migrieren. Bei Bedarf können Sie auch Zugriffs Tabellen mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbanktabellen verknüpfen.  
  
Weitere Informationen zu diesen Aufgaben und deren Ausführung finden Sie in den folgenden Themen:  
  
-   [Vorbereiten der Zugriffs Datenbanken für die Migration](preparing-access-databases-for-migration-accesstosql.md)  
  
-   [Migration von Access-Datenbanken zu SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
  
-   [Verknüpfen von Zugriffs Anwendungen mit SQL Server](linking-access-applications-to-sql-server-azure-sql-db-accesstosql.md)  
  
In den folgenden Abschnitten werden die Features der SSMA-Benutzeroberfläche beschrieben.  
  
### <a name="metadata-explorers"></a>Metadatenexplorer  
SSMA enthält zwei metadatenexplorer, die Sie zum Durchsuchen und Ausführen von Aktionen für den Zugriff und die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Azure SQL-Datenbank-Datenbanken verwenden können.  
  
#### <a name="access-metadata-explorer"></a>Access-Metadaten-Explorer  
Access Metadata Explorer zeigt Informationen über die Access-Datenbanken an, die dem Projekt hinzugefügt wurden. Wenn Sie eine Access-Datenbank hinzufügen, ruft SSMA Metadaten zu dieser Datenbank ab. Dies sind die Metadaten, die im Access Metadata Explorer verfügbar sind.  
  
Sie können den Zugriff auf den Metadaten-Explorer verwenden, um die folgenden Aufgaben auszuführen:  
  
-   Durchsuchen Sie die Tabellen in jeder Access-Datenbank.  
  
-   Wählen Sie Objekte für die Konvertierung aus, und konvertieren Sie die Objekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Syntax. Weitere Informationen finden Sie unter [umstellen von Access-Datenbankobjekten](converting-access-database-objects-accesstosql.md).  
  
-   Wählen Sie Objekte für die Datenmigration aus, und migrieren Sie die Daten von diesen Objekten zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Weitere Informationen finden Sie unter [Migrieren von Zugriffsdaten in SQL Server](migrating-access-data-into-sql-server-azure-sql-db-accesstosql.md).  
  
-   Verknüpfen und Aufheben der Verknüpfung von Access und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Tabellen.  
  
#### <a name="sql-server-or-azure-sql-database-metadata-explorer"></a>SQL Server oder Metadaten-Explorer von Azure SQL-Datenbank  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]oder der Metadaten-Explorer von Azure SQL-Datenbank zeigt Informationen zu einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank an. Wenn Sie eine Verbindung mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder mit Azure SQL-Datenbank herstellen, ruft SSMA Metadaten zu dieser Instanz ab und speichert Sie in der Projektdatei.  
  
Sie können die SQL Server oder den metadatenexplorer von Azure SQL-Datenbank verwenden, um konvertierte Access-Datenbankobjekte auszuwählen und diese Objekte in die Instanz von oder Azure SQL-Datenbank zu laden (zu synchronisieren) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
Weitere Informationen finden Sie unter [Laden von konvertierten Datenbankobjekten in SQL Server](loading-converted-database-objects-into-sql-server-accesstosql.md).  
  
### <a name="metadata"></a>Metadaten  
Auf der rechten Seite jedes metadatenexplorers sind Registerkarten, die das ausgewählte Objekt beschreiben. Wenn Sie z. b. eine Tabelle in Access Metadata Explorer auswählen, werden vier Registerkarten angezeigt: **Table**, **Type Mapping**, **Properties**und **Data**. Wenn Sie eine Tabelle im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] metadatenexplorer auswählen, werden drei Registerkarten angezeigt: **Table**, **SQL**und **Data**.  
  
Die meisten metadateneinstellungen sind schreibgeschützt. Sie können jedoch die folgenden Metadaten ändern:  
  
-   In Access Metadata Explorer können Sie Typzuordnungen ändern. Stellen Sie sicher, dass Sie diese Änderungen vornehmen, bevor Sie Berichte erstellen oder Schemas konvertieren.  
  
-   Im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] metadatenexplorer können Sie Tabellen-und Index Eigenschaften auf der Registerkarte **Tabelle** ändern. nehmen Sie diese Änderungen vor, bevor Sie die Schemas in Laden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Weitere Informationen finden Sie unter [umstellen von Access-Datenbankobjekten](converting-access-database-objects-accesstosql.md).  
  
### <a name="toolbars"></a>Symbolleisten  
SSMA verfügt über zwei Symbolleisten: eine Projektsymbol Leiste und eine Migrations Symbolleiste.  
  
#### <a name="the-project-toolbar"></a>Die Projektsymbol Leiste  
Die Projektsymbol Leiste enthält Schaltflächen zum Arbeiten mit Projekten, zum Hinzufügen von Access-Datenbankdateien sowie zum Herstellen einer Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank Diese Schaltflächen ähneln den Befehlen im Menü **Datei** .  
  
#### <a name="the-migration-toolbar"></a>Die Migrations Symbolleiste  
Die Migrations Symbolleiste enthält die folgenden Befehle:  
  
|Schaltfläche|Funktion|  
|----------|------------|  
|**Konvertieren, Laden und Migrieren**|Konvertiert Zugriffs Datenbanken, lädt die konvertierten Objekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank und migriert Daten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in einem einzigen Schritt in oder Azure SQL-Datenbank.|  
|**Erstellen von Berichten**|Konvertiert das ausgewählte Zugriffs Schema in die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Daten Bank Syntax und erstellt dann einen Bericht, der die erfolgreiche Konvertierung der Konvertierung anzeigt.<br /><br />Dieser Befehl ist nur verfügbar, wenn Objekte im Access Metadata Explorer ausgewählt werden.|  
|**Schema konvertieren**|Konvertiert das ausgewählte Zugriffs Schema in- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbankschemas.<br /><br />Dieser Befehl ist nur verfügbar, wenn Objekte im Access Metadata Explorer ausgewählt werden.|  
|**Migrieren von Daten**|Migriert Daten von der Access-Datenbank zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank. Vor dem Ausführen dieses Befehls müssen Sie die Zugriffs Schemas in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -oder Azure SQL-Datenbankschemas konvertieren und dann die Objekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank laden.<br /><br />Dieser Befehl ist nur verfügbar, wenn Objekte im Access Metadata Explorer ausgewählt werden.|  
|**Beenden**|Beendet den aktuellen Prozess, z. b. das Umstellen von Objekten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder die Azure SQL-Daten Bank Syntax.|  
  
### <a name="menus"></a>Menüs  
SSMA enthält die folgenden Menüs:  
  
|Menü|BESCHREIBUNG|  
|--------|---------------|  
|**File**|Enthält Befehle für den Migrations-Assistenten, das Arbeiten mit Projekten, das Hinzufügen und Entfernen von Access-Datenbankdateien und das Herstellen einer Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank|  
|**Bearbeiten**|Enthält Befehle zum Suchen und arbeiten mit Text auf den Detailseiten, z. b [!INCLUDE[tsql](../../includes/tsql-md.md)] . zum Kopieren aus dem SQL-Detailbereich. Um das Dialogfeld **Lesezeichen verwalten** zu öffnen, klicken Sie im Menü Bearbeiten auf Lesezeichen verwalten. Im Dialogfeld wird eine Liste vorhandener Lesezeichen angezeigt. Sie können die Schaltflächen auf der rechten Seite des Dialog Felds verwenden, um die Lesezeichen zu verwalten.|  
|**Anzeigen**|Enthält den Befehl Metadaten-Explorer **Synchronisieren** . Dadurch werden die Objekte zwischen Access Metadata Explorer und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder dem Metadaten-Explorer von Azure SQL-Datenbank synchronisiert. Enthält auch Befehle zum Anzeigen und Ausblenden der **Ausgabe** -und **Fehlerliste** Bereiche sowie ein Options **Layout** , das mit den Layouts verwaltet werden soll.|  
|**Extras**|Enthält Befehle zum Erstellen von Berichten, Exportieren von Daten, Migrieren von Objekten und Daten, Verknüpfen von Tabellen und Bereitstellen des Zugriffs auf die Dialogfelder für globale und Projekteinstellungen.|  
|**Hilfe**|Bietet Zugriff **auf die** SSMA-Hilfe und das Dialogfeld Info.|  
  
### <a name="output-pane-and-error-list-pane"></a>Ausgabebereich und Fehlerliste Bereich  
Das Menü **Ansicht** enthält Befehle zum Umschalten der Sichtbarkeit des Ausgabe Bereichs und des Fehlerliste Bereichs:  
  
-   Im Ausgabebereich werden Statusmeldungen von SSMA während der Objekt Konvertierung, der Objekt Synchronisierung und der Datenmigration angezeigt.  
  
-   Im Fehlerliste Bereich werden Fehler-, Warn-und Informationsmeldungen in einer Liste angezeigt, die Sie sortieren können.  
  
## <a name="see-also"></a>Weitere Informationen  
[Migration von Access-Datenbanken zu SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
  
