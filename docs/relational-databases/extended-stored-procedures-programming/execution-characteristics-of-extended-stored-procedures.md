---
title: Ausführungsmerkmale erweiterter gespeicherter Prozeduren | Microsoft-Dokumentation
ms.custom: ''
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
manager: craigg
ms.openlocfilehash: 93cb1b63e768623e39bcd5267c029a4ccb550c6c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62742416"
---
# <a name="execution-characteristics-of-extended-stored-procedures"></a>Ausführungsmerkmale erweiterter gespeicherter Prozeduren
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Verwenden Sie stattdessen die CLR-Integration.  
  
 Die Ausführung einer erweiterten gespeicherten Prozedur weist folgende Merkmale auf:  
  
-   Die Funktion erweiterte gespeicherte Prozedur ausgeführt wird, unter dem Sicherheitskontext des [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Die Funktion der erweiterten gespeicherten Prozedur wird im Prozessraum von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt.  
  
-   Der mit der Ausführung der erweiterten gespeicherten Prozedur verknüpfte Thread ist derselbe wie derjenige, der für die Clientverbindung verwendet wird.  
  
    > [!IMPORTANT]  
    >  Bevor der Systemadministrator die erweiterte gespeicherte Prozedur dem Server hinzufügt und Benutzern Berechtigungen zum Ausführen der Prozedur gewährt, sollte er die Prozedur gründlich überprüfen, um sicherzustellen, dass sie keinen schädlichen oder bösartigen Code enthält.  
  
-  
  
 Nachdem Sie die erweiterte gespeicherte Prozedur DLL wird geladen, die DLL bleibt so lange im Adressraum des Servers bis [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wurde beendet oder der Administrator explizit entlädt die DLL mithilfe von DBCC *DLL_name* (kostenlos).  
  
 Die erweiterte gespeicherte Prozedur kann in [!INCLUDE[tsql](../../includes/tsql-md.md)] mithilfe der EXECUTE-Anweisung als gespeicherte Prozedur ausgeführt werden:  
  
```  
EXECUTE @retval = xp_extendedProcName @param1, @param2 OUTPUT  
```  
  
## <a name="parameters"></a>Parameter  
 \@ *retval*  
 Ein Rückgabewert.  
  
 \@ *param1*  
 Ein Eingabeparameter.  
  
 \@ *param2*  
 Ein Eingabe-/Ausgabeparameter.  
  
> [!CAUTION]  
>  Erweiterte gespeicherte Prozeduren bieten Leistungssteigerungen und erweitern die Funktionalität von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Da die DLLs der erweiterten gespeicherten Prozeduren und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] jedoch denselben Adressraum nutzen, kann sich eine problematische Prozedur negativ auf die Funktionsweise von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auswirken. Von DLLs erweiterter gespeicherter Prozeduren ausgelöste Ausnahmen werden zwar von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] behandelt; es ist jedoch trotzdem möglich, dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbereiche beschädigt werden. Als Sicherheitsvorkehrung können nur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Systemadministratoren erweiterte gespeicherte Prozeduren zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] hinzufügen. Diese Prozeduren sollten vor der Installation gründlich getestet werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Programmieren erweiterter gespeicherter Prozeduren](../../relational-databases/extended-stored-procedures-programming/database-engine-extended-stored-procedures-programming.md)   
 [Abfragen von in SQL Server installierten erweiterten gespeicherten Prozeduren](../../relational-databases/extended-stored-procedures-programming/querying-extended-stored-procedures-installed-in-sql-server.md)  
  
  
