---
title: Abrufen der Felder für alle Ereignisse | Microsoft Docs
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
- extended events [SQL Server], getting fields
- xe
ms.assetid: 4e4ee03f-5bca-42ed-a37c-db1c82e3aad2
caps.latest.revision: 11
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: fac62e2160086d920e3e73e770eaaf1cc82e0b88
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36159419"
---
# <a name="get-the-fields-for-all-events"></a>Abrufen der Felder für alle Ereignisse
  Das Ausführen dieser Aufgabe beinhaltet die Verwendung des Abfrage-Editors in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
 Nach Abschluss der Anweisungen in dieser Prozedur werden auf der Registerkarte **Ergebnisse** des Abfrage-Editors die folgenden Spalten angezeigt:  
  
-   package_name  
  
-   event_name  
  
-   event_field  
  
-   field_type  
  
-   column_type  
  
 Sie können die vorangehenden Informationen verwenden, wenn Sie Ereignissitzungen konfigurieren, die das Bucketzuordnungsziel verwenden. Weitere Informationen finden Sie unter [SQL Server Extended Events Targets](../../2014/database-engine/sql-server-extended-events-targets.md).  
  
## <a name="before-you-begin"></a>Vorbereitungen  
 Bevor Sie eine [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Sitzung für erweiterte Ereignisse erstellen, sollten Sie Informationen über die mit Ereignissen verbundenen Felder abrufen.  
  
## <a name="to-get-the-fields-for-all-events-using-query-editor"></a>So rufen Sie die Felder für alle Ereignisse mittels Abfrage-Editor ab  
  
-   Führen Sie im Abfrage-Editor die folgenden Anweisungen aus.  
  
    ```  
    select p.name package_name, o.name event_name, c.name event_field, c.type_name field_type, c.column_type column_type  
    from sys.dm_xe_objects o  
    join sys.dm_xe_packages p  
          on o.package_guid = p.guid  
    join sys.dm_xe_object_columns c  
          on o.name = c.object_name  
    where o.object_type = 'event'  
    order by package_name, event_name  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 [sys.dm_xe_objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql)   
 [sys.dm_xe_packages &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-packages-transact-sql)  
  
  
