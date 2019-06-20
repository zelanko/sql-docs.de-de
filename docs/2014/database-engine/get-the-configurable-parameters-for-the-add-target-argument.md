---
title: Abrufen der konfigurierbaren Parameter für das ADD TARGET-Argument | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- extended events [SQL Server], ADD TARGET argument
- xe
ms.assetid: 08454543-c5c8-4ca3-9af9-f1d82264471c
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a66a4e77b3858b769aef287e68cac18b8b8514ea
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66064803"
---
# <a name="get-the-configurable-parameters-for-the-add-target-argument"></a>Abrufen der konfigurierbaren Parameter für das ADD TARGET-Argument
  Das Ausführen dieser Aufgabe beinhaltet die Verwendung des Abfrage-Editors in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
 Nach Abschluss der Anweisungen in dieser Prozedur werden auf der Registerkarte **Ergebnisse** des Abfrage-Editors die folgenden Spalten angezeigt:  
  
-   package_name  
  
-   target_name  
  
-   parameter_name  
  
-   parameter_type  
  
-   erforderlich  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
 Vor dem Erstellen einer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Sitzung für erweiterte Ereignisse sollten Sie zunächst herausfinden, welche Parameter Sie festlegen können, wenn Sie das ADD TARGET-Argument in CREATE EVENT SESSION oder ALTER EVENT SESSION verwenden.  
  
### <a name="to-get-the-configurable-parameters-for-the-add-target-argument-using-query-editor"></a>So rufen Sie die konfigurierbaren Parameter für das ADD TARGET-Argument mit dem Abfrage-Editor ab  
  
-   Führen Sie im Abfrage-Editor die folgenden Anweisungen aus.  
  
    ```  
    SELECT p.name package_name, o.name target_name, c.name parameter_name,   
    c.type_name parameter_type, CASE c.capabilities_desc WHEN 'mandatory' THEN 'yes' ELSE 'no' END   
    required   
    FROM sys.dm_xe_objects o JOIN sys.dm_xe_packages p ON o.package_guid = p.guid   
    JOIN sys.dm_xe_object_columns c ON o.name = c.object_name AND c.column_type = 'customizable'  
    WHERE o.object_type = 'target'   
    ORDER BY package_name, target_name, required DESC  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 [CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql)   
 [ALTER EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-event-session-transact-sql)   
 [sys.dm_xe_objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql)   
 [sys.dm_xe_packages &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-packages-transact-sql)  
  
  
