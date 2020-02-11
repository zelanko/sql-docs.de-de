---
title: Ausführungs Merkmale erweiterter gespeicherter Prozeduren
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], executing
- executing extended stored procedures [SQL Server]
ms.assetid: 6fe1f7e8-cc02-49df-8a2a-d47a96ec3567
author: rothja
ms.author: jroth
ms.custom: seo-dt-2019
ms.openlocfilehash: 74ecd20f28e58e133b5710d3cbd9d18b27ca7756
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "74095985"
---
# <a name="execution-characteristics-of-extended-stored-procedures"></a>Ausführungsmerkmale erweiterter gespeicherter Prozeduren
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]Verwenden Sie stattdessen die CLR-Integration.  
  
 Die Ausführung einer erweiterten gespeicherten Prozedur weist folgende Merkmale auf:  
  
-   Die Funktion der erweiterten gespeicherten Prozedur wird im Sicherheitskontext von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ausgeführt.  
  
-   Die Funktion der erweiterten gespeicherten Prozedur wird im Prozessraum von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt.  
  
-   Der mit der Ausführung der erweiterten gespeicherten Prozedur verknüpfte Thread ist derselbe wie derjenige, der für die Clientverbindung verwendet wird.  
  
    > [!IMPORTANT]  
    >  Bevor der Systemadministrator die erweiterte gespeicherte Prozedur dem Server hinzufügt und Benutzern Berechtigungen zum Ausführen der Prozedur gewährt, sollte er die Prozedur gründlich überprüfen, um sicherzustellen, dass sie keinen schädlichen oder bösartigen Code enthält.  
  
-  
  
 Nachdem die dll der erweiterten gespeicherten Prozedur geladen wurde, bleibt die dll in den Adressraum des Servers geladen, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bis beendet wird, oder der Administrator entlädt die dll explizit mithilfe von DBCC *DLL_Name* (Free).  
  
 Die erweiterte gespeicherte Prozedur kann in [!INCLUDE[tsql](../../includes/tsql-md.md)] mithilfe der EXECUTE-Anweisung als gespeicherte Prozedur ausgeführt werden:  
  
```  
EXECUTE @retval = xp_extendedProcName @param1, @param2 OUTPUT  
```  
  
## <a name="parameters"></a>Parameter  
 \@*retval*  
 Ein Rückgabewert.  
  
 \@*param1*  
 Ein Eingabeparameter.  
  
 \@*Param2*  
 Ein Eingabe-/Ausgabeparameter.  
  
> [!CAUTION]  
>  Erweiterte gespeicherte Prozeduren bieten Leistungssteigerungen und erweitern die Funktionalität von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Da die DLLs der erweiterten gespeicherten Prozeduren und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] jedoch denselben Adressraum nutzen, kann sich eine problematische Prozedur negativ auf die Funktionsweise von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auswirken. Von DLLs erweiterter gespeicherter Prozeduren ausgelöste Ausnahmen werden zwar von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] behandelt; es ist jedoch trotzdem möglich, dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbereiche beschädigt werden. Als Sicherheitsvorkehrung können nur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Systemadministratoren erweiterte gespeicherte Prozeduren zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] hinzufügen. Diese Prozeduren sollten vor der Installation gründlich getestet werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Programmierung von erweiterten gespeicherten Prozeduren](../../relational-databases/extended-stored-procedures-programming/database-engine-extended-stored-procedures-programming.md)   
 [Abfragen von in SQL Server installierten erweiterten gespeicherten Prozeduren](../../relational-databases/extended-stored-procedures-programming/querying-extended-stored-procedures-installed-in-sql-server.md)  
  
  
