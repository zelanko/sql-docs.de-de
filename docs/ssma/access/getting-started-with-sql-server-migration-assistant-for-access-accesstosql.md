---
title: Erste Schritte mit SQL Server Migration Assistant für Access | Microsoft-Dokumentation
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
ms.openlocfilehash: 1168609d35a266f2ac5fe6641aee7ca131bc9d89
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62759926"
---
# <a name="getting-started-with-sql-server-migration-assistant-for-access-accesstosql"></a>Erste Schritte mit SQL Server Migration Assistant für Access (AccessToSQL)
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant (SSMA) für den Zugriff ermöglicht den Zugriff auf Datenbankobjekte zu schnell Konvertierung [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank-Objekte, laden Sie die resultierenden Objekte in hoch [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank, und Migrieren von Daten aus den Zugriff auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank. Wenn erforderlich, Sie auch zugreifen auf Tabellen zu verknüpfen können [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder den Tabellen von Azure SQL-Datenbank, damit Sie fortfahren können, verwenden Sie die vorhandenen Access-Front-End-Anwendungen mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank.  
  
Dieses Thema führt während des Installationsvorgangs und trägt dazu bei, die um Sie mit der SSMA-Benutzeroberfläche vertraut zu machen.  
  
## <a name="installing-ssma"></a>Installieren von SSMA  
Um SSMA verwenden zu können, müssen Sie zunächst installieren das SSMA-Clientprogramm auf einem Computer, die beide Datenbanken zugreifen können, Sie migrieren möchten, und die Zielinstanz des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank. Installationsanweisungen finden Sie unter [Installieren von SQL Server Migration Assistant für Access &#40;AccessToSQL&#41;](../../ssma/access/installing-sql-server-migration-assistant-for-access-accesstosql.md).  
  
Um SSMA zu starten, klicken Sie auf **starten**, zeigen Sie auf **Programme**, zeigen Sie auf **SQL Server Migration Assistant für Access**, und wählen Sie dann **Migration von SQL Server Assistant für Access**.  
  
## <a name="using-ssma"></a>Verwenden des SSMA  
Nach dem Installieren von SSMA, ist es hilfreich, mit der SSMA-Benutzeroberfläche vertraut wird, bevor Sie mit dem Tool zum Migrieren von Access-Datenbanken zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank. Der SSMA-Benutzeroberfläche, einschließlich der Metadaten-Explorer, Metadaten, Symbolleisten, Ausgabebereich und Fehler im Listenbereich sind in der folgenden Abbildung dargestellt:  
  
![SSMA für die Grafische Benutzeroberfläche für Access](../../ssma/access/media/ssmaforaccessgui.gif "SSMA für die Grafische Benutzeroberfläche für Access")  
  
Um eine Migration zu starten, erstellen Sie ein neues Projekt und klicken Sie dann hinzu Metadaten-Explorer für den Zugriff auf Access-Datenbanken. Sie können dann Objekte in den Metadaten-Explorer für den Zugriff für Aufgaben wie z. B. mit der rechten Maustaste:
- Exportieren ein Inventar von den Zugriff auf Datenbankobjekte zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank.
- Erstellen von Berichten, die Konvertierungen zu bewerten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank.
- Konvertieren von Access-Schemas zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank-Schemas.

Sie können auch diese Aufgaben ausführen, mit der Symbolleisten und Menüs.  
  
Sie müssen auch eine Verbindung herstellen mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Nach einer erfolgreichen Verbindung eine Hierarchie von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbanken wird in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Metadaten-Explorer. Nach der Konvertierung zu Access-Schemas [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Schemas können Sie auswählen, die konvertierte Schemas im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Metadaten-Explorer, und Laden Sie die Schemas in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
Wenn Sie Azure SQL-Datenbank aus der Migration auf die Dropdownliste im Dialogfeld Neues Projekt ausgewählt haben, müssen Sie mit Azure SQL-Datenbank verbinden. Nach einer erfolgreichen Verbindung wird Sie eine Hierarchie von Azure SQL-Datenbanken in Azure SQL-DB-Metadaten-Explorer angezeigt. Nach der Konvertierung von Schemas für den Zugriff auf Azure SQL-Datenbank-Schemas können Sie die konvertierte Schemas in Azure SQL-DB-Metadaten-Explorer auswählen und dann laden Sie die Schemas in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
Laden Sie konvertierte Schemas in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank, die Sie in der Access-Metadaten-Explorer zurückkehren und Migrieren von Daten aus Access-Datenbanken in können [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbanken. Wenn erforderlich, Sie auch zugreifen auf Tabellen zu verknüpfen können [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-DB-Tabellen.  
  
Weitere Informationen zu diesen Aufgaben und deren Ausführung finden Sie unter den folgenden Themen:  
  
-   [Access-Datenbanken vorbereitet für die Migration.](preparing-access-databases-for-migration-accesstosql.md)  
  
-   [Migrieren von Access-Datenbanken zu SQLServer](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
  
-   [Verknüpfen den Zugriff auf Anwendungen mit SQLServer](linking-access-applications-to-sql-server-azure-sql-db-accesstosql.md)  
  
Die folgenden Abschnitte beschreiben die Funktionen der SSMA-Benutzeroberfläche.  
  
### <a name="metadata-explorers"></a>Metadaten-Explorer  
SSMA enthält zwei Metadaten-Explorer, die Sie verwenden können, durchsuchen und Ausführen von Aktionen für den Zugriff und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbanken.  
  
#### <a name="access-metadata-explorer"></a>Zugriff auf Metadaten-Explorer  
Access-Metadaten-Explorer zeigt Informationen zu den Access-Datenbanken, die dem Projekt hinzugefügt wurden. Wenn Sie eine Access-Datenbank hinzufügen, ruft SSMA Metadaten zu der Datenbank, die Metadaten, die im Metadaten-Explorer für den Zugriff verfügbar ist.  
  
Access-Metadaten-Explorer können die folgenden Aufgaben ausführen:  
  
-   Durchsuchen Sie die Tabellen in jeder Datenbank zugreifen.  
  
-   Wählen Sie Objekte für die Konvertierung und konvertieren Sie die Objekte an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Syntax. Weitere Informationen finden Sie unter [den Zugriff auf Datenbankobjekte konvertieren](converting-access-database-objects-accesstosql.md).  
  
-   Wählen Sie Objekte für die Datenmigration und migrieren Sie die Daten aus diesen Objekten zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Weitere Informationen finden Sie unter [Migrieren von Microsoft Access-Daten in SQL Server](migrating-access-data-into-sql-server-azure-sql-db-accesstosql.md).  
  
-   Verknüpfen und den Zugriff aufzuheben und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Tabellen.  
  
#### <a name="sql-server-or-azure-sql-db-metadata-explorer"></a>SQLServer oder Azure SQL-DB-Metadaten-Explorer  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-DB-Metadaten-Explorer zeigt Informationen zu einer Instanz des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank. Wenn Sie die Verbindung zu einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank, SSMA Ruft Metadaten zu dieser Instanz ab und speichert sie in der Projektdatei.  
  
Können Sie die SQL Server oder Azure SQL-DB-Metadaten-Explorer konvertierte den Zugriff auf Datenbankobjekte auswählen und laden (synchronisieren) die Objekte in der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank.  
  
Weitere Informationen finden Sie unter [konvertiert Datenbankobjekte in SQL Server laden](loading-converted-database-objects-into-sql-server-accesstosql.md).  
  
### <a name="metadata"></a>Metadaten  
Befinden sich rechts neben jeder Metadaten-Explorer Registerkarten, die das ausgewählte Objekt zu beschreiben. Wenn Sie eine Tabelle in der Access-Metadaten-Explorer auswählen, werden z. B. vier Registerkarten angezeigt: **Tabelle**, **Typzuordnung**, **Eigenschaften**, und **Daten**. Bei Auswahl eine Tabelle in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Metadaten-Explorer, drei Registerkarten angezeigt: **Tabelle**, **SQL**, und **Daten**.  
  
Die meisten Metadateneinstellungen für die sind schreibgeschützt. Allerdings können Sie die folgende Metadaten ändern:  
  
-   In den Metadaten-Explorer für den Zugriff können Sie die replikationsdatentyp-Zuordnungen ändern. Achten Sie darauf, um diese Änderungen vorzunehmen, bevor Sie Berichte erstellen, oder Konvertieren von Schemas.  
  
-   In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Metadaten-Explorer können Sie die Eigenschaften von Tabellen und Indizes ändern, auf die **Tabelle** Registerkarte. Diese Änderungen vornehmen, bevor Sie die Schemas in laden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Weitere Informationen finden Sie unter [den Zugriff auf Datenbankobjekte konvertieren](converting-access-database-objects-accesstosql.md).  
  
### <a name="toolbars"></a>Symbolleisten  
SSMA verfügt über zwei Symbolleisten: eine Projekt-Symbolleiste und eine Symbolleiste für die Migration.  
  
#### <a name="the-project-toolbar"></a>Der Projekt-Symbolleiste  
Projekt enthält Schaltflächen zum Arbeiten mit Projekten, Hinzufügen von Access-Datenbankdateien und Herstellen einer Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank. Diese Schaltflächen ähneln die Befehle auf den **Datei** Menü.  
  
#### <a name="the-migration-toolbar"></a>Die Symbolleiste für die migration  
Die Migrations-Symbolleiste enthält die folgenden Befehle aus:  
  
|Schaltfläche|Funktion|  
|----------|------------|  
|**Convert, Load, and Migrate (Konvertieren, Laden und Migrieren)**|Konvertiert den Zugriff auf Datenbanken, lädt die konvertierten Objekte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank, und Migrieren von Daten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank, in einem Schritt.|  
|**Bericht erstellen**|Konvertiert das ausgewählte Schema für den Zugriff auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank-Syntax, und erstellt dann einen Bericht, der zeigt, wie erfolgreich die Konvertierung war.<br /><br />Mit diesem Befehl steht nur, wenn Objekte in der Access-Metadaten-Explorer ausgewählt werden.|  
|**Schema konvertieren**|Konvertiert das ausgewählte Schema für den Zugriff auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank-Schemas.<br /><br />Mit diesem Befehl steht nur, wenn Objekte in der Access-Metadaten-Explorer ausgewählt werden.|  
|**Migrieren von Daten**|Migriert Daten aus der Access-Datenbank für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank. Bevor Sie diesen Befehl ausführen, müssen Sie die Access-Schemas zum Konvertieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank-Schemas, und Laden Sie die Objekte an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank.<br /><br />Mit diesem Befehl steht nur, wenn Objekte in der Access-Metadaten-Explorer ausgewählt werden.|  
|**Beenden**|Beendet den aktuellen Prozess, z. B. Konvertieren von Objekten zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank-Syntax.|  
  
### <a name="menus"></a>Menüs  
SSMA enthält die folgenden Menüs:  
  
|Menü "|Beschreibung|  
|--------|---------------|  
|**File**|Enthält Befehle für die Migrations-Assistenten arbeiten mit Projekten, hinzufügen und Entfernen von Access-Datenbankdateien und Herstellen einer Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-Datenbank.|  
|**Bearbeiten**|Enthält Befehle zum Suchen von und Arbeiten mit Text in der Seiten, z. B. das Kopieren [!INCLUDE[tsql](../../includes/tsql-md.md)] aus dem Bereich SQL-Details. Zum Öffnen der **Lesezeichen verwalten** Dialogfeld auf das Menü "Bearbeiten", klicken Sie auf die Lesezeichen zu verwalten. Klicken Sie im Dialogfeld sehen Sie eine Liste der vorhandenen Lesezeichen. Sie können die Schaltflächen auf der rechten Seite des Dialogfelds verwenden, um Lesezeichen zu verwalten.|  
|**Ansicht**|Enthält die **zu synchronisieren der Metadaten-Explorer** Befehl. Hiermit erfolgt die Synchronisierung der Objekte zwischen Access-Metadaten-Explorer und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder Azure SQL-DB-Metadaten-Explorer. Enthält auch Befehle zum Anzeigen oder Ausblenden der **Ausgabe** und **Fehlerliste** Bereiche und eine Option **Layouts** mit Layouts verwalten.|  
|**Tools**|Enthält Befehle zum Erstellen von Berichten, Exportieren von Daten, Objekte und Daten migrieren, verknüpfen Sie Tabellen aus, und stellt den Zugriff auf globale und projekteinstellungen Dialogfelder bereit.|  
|**Hilfe**|Ermöglicht den Zugriff auf SSMA unterstützen und die **zu** Dialogfeld.|  
  
### <a name="output-pane-and-error-list-pane"></a>Ausgabe und Fehlerliste  
Die **Ansicht** Menü enthält Befehle zum Umschalten der Sichtbarkeit der Ausgabebereich und den Bereich Fehlerliste:  
  
-   Im Ausgabebereich zeigt die statusmeldungen aus SSMA während der objektkonvertierung objektsynchronisierung und Datenmigration.  
  
-   Der Bereich Fehlerliste zeigt Fehler-, Warn- und informationsmeldungen in einer Liste, die Sie sortieren können.  
  
## <a name="see-also"></a>Siehe auch  
[Migrieren von Access-Datenbanken zu SQLServer](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
  
