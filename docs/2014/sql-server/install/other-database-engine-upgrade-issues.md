---
title: Weitere Upgradeprobleme für die Datenbank-Engine | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- Database Engine [SQL Server], upgrading
ms.assetid: 78a1d8e8-fa97-476f-8777-84617d145340
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4fe890744f546e02c91630c5bb0115f5b5c8cb9a
ms.sourcegitcommit: 98324d9803edfa52508b6d5d3554614d0350a0b9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "52321636"
---
# <a name="other-database-engine-upgrade-issues"></a>Weitere Probleme beim Upgrade der Datenbank-Engine
  Die folgenden Upgradeprobleme können von der aktuellen Version von Upgrade Advisor nicht erkannt werden. Überprüfen Sie die nachfolgend aufgeführten Probleme, um ihre potenziellen Auswirkungen auf Ihre Systeme zu ermitteln.  
  
## <a name="multiple-database-engine-deprecated-features"></a>Mehrere Funktionen der Datenbank-Engine veraltet  
 Die folgenden [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisungen oder -Optionen sind veraltet:  
  
-   NO_LOG-Option und TRUNCATE_ONLY-Option von BACKUP LOG  
  
-   BACKUP TRANSACTION  
  
-   RESTORE TRANSACTION  
  
-   DUMP  
  
-   LOAD  
  
-   DBCC CONCURRENCYVIOLATION  
  
-   sp_addalias  
  
-   sp_addgroup  
  
-   sp_changegroup  
  
-   sp_dropgroup  
  
-   sp_helpgroup  
  
-   syssegments  
  
 Die Verwendung des VIA-Protokolls zum Herstellen einer Verbindung mit dem [!INCLUDE[ssDE](../../includes/ssde-md.md)] ist veraltet.  
  
## <a name="new-data-types"></a>Neue Datentypen  
 Die folgenden Systemtypen sind reserviert. Benennen Sie vorhandene, miteinander in Konflikt stehende benutzerdefinierte Typen vor oder nach dem Upgrade um.  
  
-   Geography  
  
-   Geometry  
  
-   Datetime2  
  
-   HierarchyID  
  
## <a name="target-table-of-the-output-into-clause-cannot-have-any-defined-triggers"></a>Die Zieltabelle der OUTPUT INTO-Klausel kann keine definierten Trigger enthalten  
 Ausgabe in eine Zieltabelle, wenn die Tabelle über aktivierte Trigger verfügt wird nicht unterstützt.  
  
## <a name="compile-time-error-for-udfs-when-the-target-of-an-output-into-clause-is-a-table"></a>Kompilieren von Zeitfehlern für UDFs, wenn das Ziel einer OUTPUT INTO-Klausel eine Tabelle ist  
 Mit benutzerdefinierten Funktionen (UDFs) können keine Aktionen ausgeführt werden, die den Status einer Datenbank ändern. Beispielsweise kann ein UDF keine DDL-Aktionen (CREATE/ALTER/DROP) oder DML-Aktionen (INSERT/UPDATE/DELETE) für Objekte ausführen, ausgenommen für Tabellenvariablen.  
  
## <a name="merge-is-a-reserved-keyword"></a>MERGE ist ein reserviertes Schlüsselwort  
 MERGE ist jetzt ein vollständig reserviertes Schlüsselwort. Anwendungen dürfen nicht länger Objekte (Tabellen, Spalten usw.) mit dem Namen MERGE enthalten.  
  
## <a name="rename-cdc-schema"></a>Umbenennen des CDC-Schemas  
 Es ist ein Schemaname mit dem Namen CDC vorhanden. Dieser Schemaname kann nicht in verwendet werden, wenn sein **Change Data Capture** für die Datenbank aktiviert ist.  
  
 Sie müssen das CDC-Schema löschen, bevor Sie die aktivieren **Change Data Capture** für die Datenbank. Dieser Schritt kann vor oder nach dem Upgrade ausgeführt werden. Gehen Sie folgendermaßen vor, um das Schema zu löschen:  
  
1.  Übertragen Sie die Objekte mit ALTER SCHEMA vom CDC-Schema auf einen neuen Schemanamen.  
  
2.  Überprüfen Sie die Berechtigungen für die Objekte im neuen Schema.  
  
3.  Nehmen Sie notwendige Änderungen an der Anwendung vor.  
  
4.  Löschen Sie das CDC-Schema mit DROP SCHEMA.  
  
## <a name="see-also"></a>Siehe auch  
 [Probleme beim Upgrade der Datenbank-Engine](../../../2014/sql-server/install/database-engine-upgrade-issues.md)  
  
  
