---
title: Ersten Schritte mit SSMA für MySQL (mysqlto SQL) | Microsoft-Dokumentation
description: Erfahren Sie mehr über die SQL Server Migration Assistant (SSMA) für die MySQL-Installation, und machen Sie sich mit der SSMA-Benutzeroberfläche vertraut.
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
ms.openlocfilehash: c1cc8f5ddbe1efc1a1038bf2e9d6595e31ff3102
ms.sourcegitcommit: 777704aefa7e574f4b7d62ad2a4c1b10ca1731ff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/06/2020
ms.locfileid: "87823650"
---
# <a name="getting-started-with-ssma-for-mysql-mysqltosql"></a>Erste Schritte mit SSMA für MySQL (MySqlToSql)
Mit SQL Server Migration Assistant (SSMA) für MySQL können Sie schnell MySQL-Datenbankschemas in SQL Server-oder Azure SQL-Datenbankschemas konvertieren, die resultierenden Schemas in SQL Server oder Azure SQL-Datenbank hochladen und Daten aus MySQL in SQL Server oder Azure SQL-Datenbank migrieren.  
  
Dieses Thema enthält eine Einführung in den Installationsvorgang und hilft Ihnen dabei, Sie mit der SSMA-Benutzeroberfläche vertraut zu machen.  
  
## <a name="installing-ssma"></a>Installieren von SSMA  
Zum Verwenden von SSMA müssen Sie zuerst das SSMA-Client Programm auf einem Computer installieren, der auf die MySQL-Quelldatenbank und die Ziel Instanz von SQL Server oder Azure SQL-Datenbank zugreifen kann. Installieren Sie dann die MySQL-Anbieter (MySQL ODBC 5,1 Driver (Trusted)) auf dem Computer, auf dem das SSMA-Client Programm ausgeführt wird. Installationsanweisungen finden Sie unter [Installieren von SSMA für MySQL &#40;mysqlto SQL&#41;](../../ssma/mysql/installing-ssma-for-mysql-mysqltosql.md)  
  
Klicken Sie zum Starten von SSMA auf **Start**, zeigen Sie auf **Alle Programme**, zeigen Sie auf **SQL Server Migration Assistant für MySQL**, und klicken Sie dann auf **SQL Server Migration Assistant für MySQL**.  
  
## <a name="ssma-for-mysql-user-interface"></a>SSMA für die MySQL-Benutzeroberfläche  
Nachdem SSMA installiert und lizenziert wurde, können Sie SSMA zum Migrieren von MySQL-Datenbanken zu SQL Server oder Azure SQL-Datenbank verwenden. Es hilft Ihnen, sich mit der SSMA-Benutzeroberfläche vertraut zu machen, bevor Sie beginnen. Das folgende Diagramm zeigt die Benutzeroberfläche für SSMA, einschließlich der Metadaten-Explorer, Metadaten, Symbolleisten, Ausgabebereich und Fehlerlisten Bereich:  
  
![SSMA für die grafische MySql-Benutzeroberfläche](../../ssma/mysql/media/ssmaformysqlgui.gif "SSMA für die grafische MySql-Benutzeroberfläche")  
  
Zum Starten einer Migration müssen Sie die folgenden Schritte ausführen:  
  
1.  Erstellen Sie ein neues Projekt.  
  
2.  Herstellen einer Verbindung mit einer MySQL-Datenbank  
  
3.  Nach einer erfolgreichen Verbindung werden MySQL-Schemas im MySQL-metadatenexplorer angezeigt. Klicken Sie mit der rechten Maustaste auf Objekte im MySQL-metadatenexplorer, um Aufgaben wie das Erstellen von Berichten, die Konvertierungen in SQL Server/Azure SQL-Datenbank bewerten  
  
Sie können diese Aufgaben auch mithilfe der Symbolleisten und Menüs ausführen.  
  
Sie müssen auch eine Verbindung mit einer Instanz von SQL Server herstellen. Nach einer erfolgreichen Verbindung wird eine Hierarchie von SQL Server Datenbanken in SQL Server Metadaten-Explorer angezeigt. Nachdem Sie MySQL-Schemas in SQL Server Schemas konvertiert haben, wählen Sie diese konvertierten Schemas in SQL Server Metadaten-Explorer aus, und synchronisieren Sie dann die Schemas mit SQL Server.  
  
Sie müssen eine Verbindung mit Azure SQL-Datenbank herstellen, wenn Sie im Dialogfeld Neues Projekt im Dropdown Menü Migrieren zu die Option Azure SQL-Datenbank ausgewählt haben. Nach einer erfolgreichen Verbindung wird eine Hierarchie von Azure SQL-Daten Bank Datenbanken im metadatenexplorer von Azure SQL-Datenbank angezeigt. Nachdem Sie MySQL-Schemas in Azure SQL-Datenbankschemas konvertiert haben, wählen Sie diese konvertierten Schemas im metadatenexplorer von Azure SQL-Datenbank aus, und synchronisieren Sie dann die Schemas mit Azure SQL-Datenbank  
  
Nachdem Sie konvertierte Schemas mit SQL Server oder Azure SQL-Datenbank synchronisiert haben, können Sie zum MySQL-metadatenexplorer zurückkehren und Daten aus MySQL-Schemas in SQL Server oder Azure SQL-Datenbank-Datenbanken migrieren.  
  
Weitere Informationen zu diesen Aufgaben und deren Durchführung finden Sie unter [Migrieren von MySQL-Datenbanken zu SQL Server-Azure SQL-Datenbank &#40;mysqldesql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md).  
  
In den folgenden Abschnitten werden die Features der SSMA-Benutzeroberfläche beschrieben.  
  
### <a name="metadata-explorers"></a>Metadatenexplorer  
SSMA enthält zwei metadatenexplorer zum Durchsuchen und Ausführen von Aktionen für MySQL-und SQL Server-Datenbanken.  
  
### <a name="mysql-metadata-explorer"></a>MySQL-metadatenexplorer  
MySQL-metadatenexplorer zeigt Informationen zu MySQL-Schemas an. Mit dem MySQL-metadatenexplorer können Sie die folgenden Aufgaben ausführen:  
  
-   Durchsuchen Sie die Objekte in den einzelnen Schemas.  
  
-   Wählen Sie die Objekte für die Konvertierung aus, und konvertieren Sie dann die Objekte in SQL Server-Syntax. Weitere Informationen finden Sie unter [umstellen von MySQL-Datenbanken &#40;mysqlto SQL&#41;](../../ssma/mysql/converting-mysql-databases-mysqltosql.md)  
  
-   Wählen Sie Tabellen für die Datenmigration aus, und migrieren Sie dann die Daten aus diesen Tabellen zu SQL Server. Weitere Informationen finden Sie unter [Migrieren von MySQL-Daten in SQL Server Azure SQL-Datenbank &#40;mysqlto SQL&#41;](../../ssma/mysql/migrating-mysql-data-into-sql-server-azure-sql-db-mysqltosql.md)  
  
### <a name="sql-server-or-azure-sql-database-metadata-explorer"></a>SQL Server oder Metadaten-Explorer von Azure SQL-Datenbank  
SQL Server oder der Metadaten-Explorer von Azure SQL-Datenbank zeigt Informationen zu einer Instanz von SQL Server oder Azure SQL-Datenbank an. Wenn Sie eine Verbindung mit einer Instanz von SQL Server oder Azure SQL-Datenbank herstellen, ruft SSMA Metadaten zu dieser Instanz ab und speichert Sie in der Projektdatei.  
  
Mit diesem metadatenexplorer können Sie konvertierte MySQL-Datenbankobjekte auswählen und diese Objekte dann mit der Instanz von SQL Server oder Azure SQL-Datenbank synchronisieren.  
  
Weitere Informationen finden Sie unter [Synchronisierung (MySQL zu SQL Server/Azure SQL-Datenbank)](https://msdn.microsoft.com/ac993a6d-0283-4823-8793-6b217677dfa3) .  
  
### <a name="metadata"></a>Metadaten  
Auf der rechten Seite jedes metadatenexplorers sind Registerkarten, die das ausgewählte Objekt beschreiben. Wenn Sie z. b. eine Tabelle im MySQL-metadatenexplorer auswählen, werden neun Registerkarten angezeigt: **Tabelle**, **SQL**, **Typzuordnung**, **Daten**, **Einstellungen**, Zeichen **Satz Zuordnung**, **SQL-Modi**, **Eigenschaften**und **Bericht**. Die Registerkarte **Bericht** enthält nur Informationen, nachdem Sie einen Bericht erstellt haben, der das ausgewählte Objekt enthält. Wenn Sie eine Tabelle in SQL Server Metadaten-Explorer auswählen, werden drei Registerkarten angezeigt: **Table**, **SQL** und **Data**.  
  
Die meisten metadateneinstellungen sind schreibgeschützt. Sie können jedoch die folgenden Metadaten ändern:  
  
-   Im MySQL-metadatenexplorer können Sie Typzuordnungen, CharSet-Zuordnung und SQL-Modi ändern. Nehmen Sie vor dem Konvertieren von Schemas Änderungen vor, um die geänderten Typzuordnungen oder die charset-Zuordnung oder die SQL-Modi zu konvertieren.  
  
-   In SQL Server metadatenexplorer können Sie die Tabellen-und Index Eigenschaften auf der Registerkarte Tabelle ändern. Um diese Änderungen in SQL Server anzuzeigen, nehmen Sie diese Änderungen vor, bevor Sie die Schemas in SQL Server laden.  
  
Änderungen, die in einem metadatenexplorer vorgenommen werden, werden in den Projekt Metadaten, nicht in der Quell-oder Zieldatenbank widergespiegelt.  
  
### <a name="toolbars"></a>Symbolleisten  
SSMA verfügt über zwei Symbolleisten: eine Projektsymbol Leiste und eine Migrations Symbolleiste.  
  
### <a name="the-project-toolbar"></a>Die Projektsymbol Leiste  
Die Projektsymbol Leiste enthält Schaltflächen für das Arbeiten mit Projekten, das Herstellen einer Verbindung mit MySQL und das Herstellen einer Verbindung mit SQL Server oder Azure SQL-Datenbank. Diese Schaltflächen ähneln den Befehlen im Menü **Datei** .  
  
### <a name="migration-toolbar"></a>Migrations Symbolleiste  
In der folgenden Tabelle werden die Befehle für die Migrations Symbolleiste angezeigt:  
  
|||  
|-|-|  
|**Schaltfläche**|**Function**|  
|**Erstellen von Berichten**|Konvertiert die ausgewählten MySQL-Objekte in SQL Server-oder Azure SQL-Datenbankobjekte und erstellt dann einen Bericht, der anzeigt, wie erfolgreich die Konvertierung war.<br /><br />Dieser Befehl ist deaktiviert, es sei denn, im MySQL-metadatenexplorer sind Objekte ausgewählt.|  
|**Schema konvertieren**|Konvertiert die ausgewählten MySQL-Objekte in SQL Server-oder Azure SQL-Datenbankobjekte.<br /><br />Dieser Befehl ist deaktiviert, es sei denn, im MySQL-metadatenexplorer sind Objekte ausgewählt.|  
|**Migrieren von Daten**|Migriert Daten aus der MySQL-Datenbank in SQL Server oder Azure SQL-Datenbank. Vor dem Ausführen dieses Befehls müssen Sie die MySQL-Schemas in SQL Server-oder Azure SQL-Datenbankschemas konvertieren und dann die Objekte in SQL Server oder Azure SQL-Datenbank laden.<br /><br />Dieser Befehl ist deaktiviert, es sei denn, im MySQL-metadatenexplorer sind Objekte ausgewählt.|  
|**Beenden**|Beendet den aktuellen Prozess.|  
  
### <a name="menus"></a>Menüs  
In der folgenden Tabelle sind die SSMA-Menüs aufgeführt.  
  
|||  
|-|-|  
|**Menü**|**Beschreibung**|  
|**File**|Enthält Befehle für das Arbeiten mit Projekten, das Herstellen einer Verbindung mit MySQL und das Herstellen einer Verbindung mit SQL Server oder Azure SQL-Datenbank.|  
|**Bearbeiten**|Enthält Befehle zum Suchen und arbeiten mit Text auf den Detailseiten. Um das Dialogfeld **Lesezeichen verwalten** zu öffnen, klicken Sie im Menü Bearbeiten auf Lesezeichen verwalten. Im Dialogfeld wird eine Liste vorhandener Lesezeichen angezeigt. Sie können die Schaltflächen auf der rechten Seite des Dialog Felds verwenden, um die Lesezeichen zu verwalten.|  
|**Anzeigen**|Enthält den Befehl Metadaten-Explorer **Synchronisieren** . Damit werden die Objekte zwischen dem MySQL-metadatenexplorer und SQL Server oder dem Metadaten-Explorer von Azure SQL-Datenbank synchronisiert. Enthält auch Befehle zum Anzeigen und Ausblenden der **Ausgabe** -und **Fehlerliste** Bereiche sowie ein Options **Layout** , das mit den Layouts verwaltet werden soll.|  
|**Extras**|Enthält Befehle zum Erstellen von Berichten, zum Konvertieren von Schemas, zum Aktualisieren von Datenbanken, zum Migrieren von Objekten und Daten und zum Speichern als Skript. Bietet auch Zugriff auf die Dialogfelder " **globale Einstellungen", "Standard Projekteinstellungen** " und " **Projekteinstellungen** ".|  
|**Hilfe**|Bietet Zugriff **auf die** SSMA-Hilfe und das Dialogfeld Info.|  
  
### <a name="output-pane-and-error-list-pane"></a>Ausgabebereich und Fehlerliste Bereich  
Das Menü **Ansicht** enthält Befehle zum Umschalten der Sichtbarkeit des Ausgabe Bereichs und des Fehlerliste Bereichs:  
  
-   Im Ausgabebereich werden Statusmeldungen von SSMA während der Objekt Konvertierung, der Objekt Synchronisierung und der Datenmigration angezeigt.  
  
-   Im Fehlerliste Bereich werden Fehler-, Warn-und Informationsmeldungen in einer sortierbaren Liste angezeigt.  
  
## <a name="see-also"></a>Weitere Informationen  
[Referenz zur Benutzeroberfläche &#40;mysqltosql&#41;](../../ssma/mysql/user-interface-reference-mysqltosql.md)  
[Migrieren von MySQL-Daten in SQL Server Azure SQL-Datenbank &#40;mysqlto SQL&#41;](../../ssma/mysql/migrating-mysql-data-into-sql-server-azure-sql-db-mysqltosql.md)  
  
