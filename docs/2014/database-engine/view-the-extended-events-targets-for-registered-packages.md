---
title: Anzeigen der Ziele von erweiterten Ereignissen für registrierte Pakete | Microsoft Docs
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
- targets [SQL Server extended events]
- viewing event targets
- extended events [SQL Server], viewing targets
ms.assetid: 4985aa5f-ac99-49f6-852c-9d25916549e9
caps.latest.revision: 12
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1c5552ca54f3297226fad6a15de2d5c80bc49067
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36047252"
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
  
## <a name="see-also"></a>Siehe auch  
 [Ziele für erweiterte Ereignisse von SQL Server](../../2014/database-engine/sql-server-extended-events-targets.md)   
 [sys.dm_xe_objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql)   
 [sys.dm_xe_packages &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-packages-transact-sql)  
  
  
