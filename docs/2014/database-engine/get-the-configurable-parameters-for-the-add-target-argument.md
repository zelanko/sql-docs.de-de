---
title: Abrufen der konfigurierbaren Parameter für das ADD TARGET-Argument | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- extended events [SQL Server], ADD TARGET argument
- xe
ms.assetid: 08454543-c5c8-4ca3-9af9-f1d82264471c
caps.latest.revision: 14
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d27a1983d71bd78399893ae63f90e19ca1e0fd08
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36148899"
---
# <a name="get-the-configurable-parameters-for-the-add-target-argument"></a>Abrufen der konfigurierbaren Parameter für das ADD TARGET-Argument
  Das Ausführen dieser Aufgabe beinhaltet die Verwendung des Abfrage-Editors in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
 Nach Abschluss der Anweisungen in dieser Prozedur werden auf der Registerkarte **Ergebnisse** des Abfrage-Editors die folgenden Spalten angezeigt:  
  
-   package_name  
  
-   target_name  
  
-   parameter_name  
  
-   parameter_type  
  
-   erforderlich  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
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
  
  
