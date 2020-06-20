---
title: Anzeigen der Ziele für erweiterte Ereignisse für registrierte Pakete | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- targets [SQL Server extended events]
- viewing event targets
- extended events [SQL Server], viewing targets
ms.assetid: 4985aa5f-ac99-49f6-852c-9d25916549e9
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 8e796d141ef943399fc2469c232b34b1956cef3b
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84927306"
---
# <a name="view-the-extended-events-targets-for-registered-packages"></a>Anzeigen der Ziele von erweiterten Ereignissen für registrierte Pakete
  Bevor Sie eine [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Sitzung für erweiterte Ereignisse erstellen, sollten Sie zunächst herausfinden, welche Ziele für erweiterte Ereignisse verfügbar sind. Dazu gehört das Ausführen der folgenden Vorgehensweise mithilfe des Abfrage-Editors in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] .  
  
 Nach Abschluss der Anweisungen in dieser Prozedur zeigt die Registerkarte **Ergebnisse** des Abfrage-Editors die beiden folgenden Spalten an:  
  
-   package_name  
  
-   target_name  
  
## <a name="to-view-the-extended-events-targets-for-registered-packages-using-query-editor"></a>So zeigen Sie die Ziele für erweiterte Ereignisse für registrierte Pakete mittels Abfrage-Editor an  
  
-   Führen Sie im Abfrage-Editor die folgenden Anweisungen aus.  
  
    ```  
    USE msdb  
    SELECT p.name package_name, o.name target_name  
    FROM sys.dm_xe_objects o  
    JOIN sys.dm_xe_packages p  
         ON o.package_guid = p.guid  
    WHERE o.object_type = 'target'  
    ```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ziele für erweiterte Ereignisse SQL Server](../../2014/database-engine/sql-server-extended-events-targets.md)   
 [sys. dm_xe_objects &#40;Transact-SQL-&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql)   
 [sys.dm_xe_packages &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-packages-transact-sql)  
  
  
