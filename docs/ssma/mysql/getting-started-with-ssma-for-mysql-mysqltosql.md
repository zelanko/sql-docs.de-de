---
title: Erste Schritte mit SSMA für MySQL (MySQLToSQL)) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Getting started, MySQL metadata explorer
- Getting started, SQL Server or SQL Azure metadata explorer
- Getting started,Installing and licensing
ms.assetid: 8ebfa061-be6f-4a07-923f-8dc832a82f70
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 1ae91f90bf601e4ef17ae2f363260dbb47a2822e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63187151"
---
# <a name="getting-started-with-ssma-for-mysql-mysqltosql"></a>Erste Schritte mit SSMA für MySQL (MySqlToSql)
SQL Server Migration Assistant (SSMA) for MySQL können Sie schnell Konvertieren von MySQL-Datenbankschemas in SQL Server oder Azure SQL-Datenbank-Schemas, die resultierenden Schemas in SQL Server oder Azure SQL-Datenbank hochzuladen und Migrieren von Daten aus MySQL nach SQL Server oder Azure SQL-Datenbank.  
  
Dieses Thema führt während des Installationsvorgangs, und klicken Sie dann können Sie mit der SSMA-Benutzeroberfläche vertraut zu machen.  
  
## <a name="installing-ssma"></a>Installieren von SSMA  
Um SSMA verwenden zu können, müssen Sie zuerst das SSMA-Clientprogramm auf einem Computer installieren, die sowohl für die Source-MySQL-Datenbank als auch für die Zielinstanz von SQL Server oder Azure SQL-Datenbank zugreifen können. Anschließend installieren Sie die MySQL-Anbieter (MySQL ODBC 5.1-Treiber (vertrauenswürdig)), auf dem Computer, der SSMA-Clientprogramm ausgeführt wird. Installationsanweisungen finden Sie unter [Installieren von SSMA für MySQL &#40;MySqlToSql&#41;](../../ssma/mysql/installing-ssma-for-mysql-mysqltosql.md)  
  
Um SSMA zu starten, klicken Sie auf **starten**, zeigen Sie auf **Programme**, zeigen Sie auf **SQL Server Migration Assistant für MySQL**, und klicken Sie dann auf **Migration von SQL Server Assistant für MySQL**.  
  
## <a name="ssma-for-mysql-user-interface"></a>SSMA für die MySQL-Benutzeroberfläche  
Nach der SSMA installiert und lizenziert ist, können Sie SSMA zum Migrieren von MySQL-Datenbanken zu SQL Server oder Azure SQL-Datenbank verwenden. Es hilft, die mit der SSMA-Benutzeroberfläche vertraut zu machen, bevor Sie beginnen. Das folgende Diagramm zeigt die Benutzeroberfläche für SSMA, einschließlich der Metadaten-Explorer, Metadaten, Symbolleisten, Ausgabebereich und Fehler im Listenbereich an:  
  
![SSMA für MySql Grafische Benutzeroberfläche](../../ssma/mysql/media/ssmaformysqlgui.gif "SSMA für MySql-Benutzeroberfläche")  
  
Um eine Migration zu starten, müssen Sie folgende Aktionen ausführen:  
  
1.  Erstellen Sie ein neues Projekt.  
  
2.  Verbinden Sie mit einer MySQL-Datenbank.  
  
3.  Nach einer erfolgreichen Verbindung werden die MySQL-Schemas in der MySQL-Metadaten-Explorer angezeigt. Mit der rechten Maustaste-Objekte in der MySQL-Metadaten-Explorer für Aufgaben wie z. B. erstellen Berichte, die Konvertierungen in SQL Server/Azure SQL-Datenbank zu bewerten.  
  
Sie können auch diese Aufgaben ausführen, mit der Symbolleisten und Menüs.  
  
Sie müssen auch mit einer Instanz von SQL Server verbinden. Nach einer erfolgreichen Verbindung wird eine Hierarchie von SQL Server-Datenbanken in SQL Server-Metadaten-Explorer angezeigt. Nach dem Sie MySQL-Schemas in SQL Server-Schemas konvertieren, wählen Sie die konvertierte Schemas in SQL Server-Metadaten-Explorer, und klicken Sie dann synchronisieren Sie die Schemas mit SQL Server zu.  
  
Sie müssen mit Azure SQL-Datenbank verbinden, wenn Sie Azure SQL-Datenbank aus der Migration auf die Dropdownliste im Dialogfeld Neues Projekt ausgewählt haben. Nach einer erfolgreichen Verbindung wird eine Hierarchie von Azure SQL-Datenbanken in Azure SQL-DB-Metadaten-Explorer angezeigt. Nach dem Sie MySQL-Schemas in Azure SQL-Datenbank-Schemas konvertieren, wählen Sie die konvertierte Schemas in Azure SQL-DB-Metadaten-Explorer, und klicken Sie dann synchronisieren Sie die Schemas mit Azure SQL-Datenbank zu.  
  
Nachdem Sie konvertierte Schemas mit SQL Server oder Azure SQL-Datenbank synchronisiert haben, können Sie in MySQL-Metadaten-Explorer zurückkehren und Migrieren von Daten aus MySQL-Schemas in SQL Server oder Azure SQL-DB-Datenbanken.  
  
Weitere Informationen zu diesen Aufgaben und deren Ausführung finden Sie unter [Migrieren der MySQL-Datenbanken zu SQL Server - Azure SQL-Datenbank &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md).  
  
Die folgenden Abschnitte beschreiben die Funktionen der SSMA-Benutzeroberfläche.  
  
### <a name="metadata-explorers"></a>Metadaten-Explorer  
SSMA enthält zwei Metadaten-Explorer zum Durchsuchen und Ausführen von Aktionen für MySQL und SQL Server-Datenbanken.  
  
### <a name="mysql-metadata-explorer"></a>MySQL-Metadaten-Explorer  
MySQL-Metadaten-Explorer zeigt Informationen zu MySQL-Schemas. Mithilfe von MySQL-Metadaten-Explorer können Sie die folgenden Aufgaben ausführen:  
  
-   Durchsuchen Sie die Objekte in den einzelnen Schemas.  
  
-   Wählen Sie Objekte für die Konvertierung aus, und klicken Sie dann konvertieren Sie die Objekte in SQL Server-Syntax. Weitere Informationen finden Sie unter [MySQL-Datenbanken konvertieren &#40;MySQLToSQL&#41;](../../ssma/mysql/converting-mysql-databases-mysqltosql.md)  
  
-   Wählen Sie Tabellen, für die Datenmigration, und klicken Sie dann migrieren Sie die Daten aus diesen Tabellen in SQL Server. Weitere Informationen finden Sie unter [Migrieren von MySQL-Daten in SQL Server – Azure SQL-Datenbank &#40;MySQLToSQL&#41;](../../ssma/mysql/migrating-mysql-data-into-sql-server-azure-sql-db-mysqltosql.md)  
  
### <a name="sql-server-or-azure-sql-db-metadata-explorer"></a>SQLServer oder Azure SQL-DB-Metadaten-Explorer  
SQL Server oder Azure SQL-DB-Metadaten-Explorer zeigt Informationen zu einer Instanz von SQL Server oder Azure SQL-Datenbank. Wenn Sie eine Verbindung mit einer Instanz von SQL Server oder Azure SQL-Datenbank herstellen, werden SSMA Ruft Metadaten zu dieser Instanz ab und speichert sie in der Projektdatei.  
  
Sie können dieser Metadaten-Explorer, wählen Sie die konvertierten Objekte der MySQL-Datenbank verwenden und diese Objekte dann mit der Instanz von SQL Server oder Azure SQL-Datenbank synchronisieren.  
  
Weitere Informationen finden Sie unter [Synchronisierung (MySQL zu SQL Server / Azure SQL-Datenbank)](https://msdn.microsoft.com/ac993a6d-0283-4823-8793-6b217677dfa3)  
  
### <a name="metadata"></a>Metadaten  
Befinden sich rechts neben jeder Metadaten-Explorer Registerkarten, die das ausgewählte Objekt zu beschreiben. Wenn Sie eine Tabelle in der MySQL-Metadaten-Explorer auswählen, werden z. B. neun Registerkarten angezeigt: **Tabelle**, **SQL**, **Typzuordnung**, **Daten**, **Einstellungen**, **Charset-Zuordnung**, **SQL-Modi**, **Eigenschaften**, und **Bericht**. Die **Bericht** Registerkarte enthält Informationen, nachdem Sie einen Bericht erstellen, die das ausgewählte Objekt enthält. Wenn Sie eine Tabelle in SQL Server-Metadaten-Explorer auswählen, werden drei Registerkarten angezeigt: **Tabelle**, **SQL** und **Daten**.  
  
Die meisten Metadateneinstellungen für die sind schreibgeschützt. Allerdings können Sie die folgende Metadaten ändern:  
  
-   In der MySQL-Metadaten-Explorer können Sie typzuordnungen Charset zuordnen, SQL-Modus ändern. Um die geänderte replikationsdatentyp-Zuordnungen oder Charset zuordnen oder SQL-Modi zu konvertieren, können nehmen Sie Änderungen vor, bevor Sie Schemas konvertieren.  
  
-   In SQL Server-Metadaten-Explorer können Sie die Tabellen und Indizes Eigenschaften auf der Registerkarte "Tabelle" ändern. Um diese Änderungen in SQL Server anzuzeigen, werden nehmen Sie diese Änderungen vor, bevor Sie die Schemas in SQL Server laden.  
  
Änderungen in einem Metadaten-Explorer in den Projektmetadaten nicht in den Quell- oder Zieltabelle Datenbanken widergespiegelt.  
  
### <a name="toolbars"></a>Symbolleisten  
SSMA verfügt über zwei Symbolleisten: eine Projekt-Symbolleiste und eine Symbolleiste für die Migration.  
  
### <a name="the-project-toolbar"></a>Der Projekt-Symbolleiste  
Die Projekt-Symbolleiste enthält die Schaltflächen für das Arbeiten mit Projekten, eine Verbindung mit MySQL herstellen und eine Verbindung mit SQL Server oder Azure SQL-Datenbank herstellen. Diese Schaltflächen ähneln die Befehle auf den **Datei** Menü.  
  
### <a name="migration-toolbar"></a>Migration-Symbolleiste  
Die folgende Tabelle zeigt die Migration der Symbolleistenbefehle:  
  
|||  
|-|-|  
|**Button** (Schaltfläche)|**Funktion**|  
|**Bericht erstellen**|Konvertiert die ausgewählten MySQL-Objekten in SQL Server oder Azure SQL-Datenbank-Objekte, und erstellt dann einen Bericht, der zeigt, wie erfolgreich die Konvertierung war.<br /><br />Dieser Befehl ist deaktiviert, es sei denn, die Objekte in der MySQL-Metadaten-Explorer ausgewählt werden.|  
|**Schema konvertieren**|Konvertiert die ausgewählten MySQL-Objekten auf SQL Server oder Azure SQL-Datenbank-Objekte.<br /><br />Dieser Befehl ist deaktiviert, es sei denn, die Objekte in der MySQL-Metadaten-Explorer ausgewählt werden.|  
|**Migrieren von Daten**|Werden Daten aus der Datenbank für MySQL zu SQL Server oder Azure SQL-Datenbank migriert. Bevor Sie diesen Befehl ausführen müssen Sie die MySQL-Schemas in SQL Server oder Azure SQL-Datenbank-Schemas konvertieren und dann die Objekte in SQL Server oder Azure SQL-Datenbank laden.<br /><br />Dieser Befehl ist deaktiviert, es sei denn, die Objekte in der MySQL-Metadaten-Explorer ausgewählt werden.|  
|**Beenden**|Beendet den aktuellen Prozess an.|  
  
### <a name="menus"></a>Menüs  
Die folgende Tabelle zeigt die SSMA-Menüs.  
  
|||  
|-|-|  
|**Menü "**|**Beschreibung**|  
|**File**|Befehle zum Arbeiten mit Projekten, eine Verbindung mit MySQL herstellen und eine Verbindung mit SQL Server oder Azure SQL-Datenbank herstellen.|  
|**Bearbeiten**|Befehle zum Suchen von und Arbeiten mit Text in der Seiten. Zum Öffnen **Lesezeichen verwalten** Dialogfeld auf das Menü "Bearbeiten" klicken Sie auf die Lesezeichen zu verwalten. Im Dialogfeld sehen Sie eine Liste der vorhandenen Lesezeichen. Sie können die Schaltflächen auf der rechten Seite des Dialogfelds verwenden, um Lesezeichen zu verwalten.|  
|**Ansicht**|Enthält die **zu synchronisieren der Metadaten-Explorer** Befehl. Synchronisiert die Objekte zwischen MySQL-Metadaten-Explorer und SQL Server oder Azure SQL-DB-Metadaten-Explorer. Enthält auch Befehle zum ein- und Ausblenden der **Ausgabe** und **Fehlerliste** Bereiche und eine Option **Layouts** mit Layouts verwalten.|  
|**Tools**|Befehle zum Erstellen von Berichten, Schema konvertieren, aus der Datenbank aktualisieren, Migrieren von Objekten und Daten und speichern Sie als Skript. Bietet außerdem Zugriff auf die **globale Einstellungen, Projekt-Standardeinstellungen** und **Projekteinstellungen** Dialogfelder.|  
|**Hilfe**|Ermöglicht den Zugriff auf SSMA unterstützen und die **zu** Dialogfeld.|  
  
### <a name="output-pane-and-error-list-pane"></a>Ausgabebereich und Fehler im Listenbereich  
Die **Ansicht** Menü enthält Befehle zum Umschalten der Sichtbarkeit der Ausgabebereich und den Bereich Fehlerliste:  
  
-   Im Ausgabebereich zeigt die statusmeldungen aus SSMA während der objektkonvertierung objektsynchronisierung und Datenmigration.  
  
-   Der Bereich Fehlerliste werden Fehler-, Warn- und informationsmeldungen in einem sortierbaren angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
[Referenz zur Benutzeroberfläche &#40;MySQLToSQL&#41;](../../ssma/mysql/user-interface-reference-mysqltosql.md)  
[Migrieren von MySQL-Daten in SQLServer – Azure SQL-Datenbank &#40;MySQLToSQL&#41;](../../ssma/mysql/migrating-mysql-data-into-sql-server-azure-sql-db-mysqltosql.md)  
  
