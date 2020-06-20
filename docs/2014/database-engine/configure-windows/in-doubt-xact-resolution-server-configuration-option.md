---
title: Lösung für unklare Transaktion (Serverkonfigurationsoption) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- distributed transactions [SQL Server], unresolved transactions
- unresolved transactions
- in-doubt xact resolution option
ms.assetid: 3426fd32-cad2-4f2f-8ca9-e0296cc12703
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6b8db57ef2a4ee85d65e8c25de28ff7ada7994e1
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84935261"
---
# <a name="in-doubt-xact-resolution-server-configuration-option"></a>Lösung für unklare Transaktion (Serverkonfigurationsoption)
  Mit der Option **in-doubt xact resolution** steuern Sie das Standardergebnis von Transaktionen, die der [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator (MS DTC) nicht auflösen kann. Die mangelnde Fähigkeit zur Auflösung von Transaktionen kann mit der Ausfalldauer des MS DTC zusammenhängen oder auch mit einem unbekannten Transaktionsergebnis zum Zeitpunkt der Wiederherstellung.  
  
 Die nachstehende Tabelle enthält die möglichen Ergebniswerte für das Auflösen einer unsicheren Transaktion.  
  
|Ergebniswert|BESCHREIBUNG|  
|-------------------|-----------------|  
|0|Keine Annahme. Die Wiederherstellung erzeugt einen Fehler, falls der MS DTC keine unsicheren Transaktionen auflösen kann.|  
|1|Commit annehmen. Alle unsicheren MS DTC-Transaktionen werden als übermittelt angesehen.|  
|2|Abbruch annehmen. Alle unsicheren MS DTC-Transaktionen werden als abgebrochen angesehen.|  
  
 Um die Gefahr längerer Ausfallzeiten zu minimieren, kann ein Administrator diese Option so konfigurieren, dass entweder die Übermittlung oder der Abbruch angenommen wird, wie im nachstehenden Beispiel dargestellt.  
  
```  
sp_configure 'show advanced options', 1  
GO  
RECONFIGURE  
GO  
sp_configure 'in-doubt xact resolution', 2 -- presume abort  
GO  
RECONFIGURE  
GO  
sp_configure 'show advanced options', 0  
GO  
RECONFIGURE  
GO  
  
```  
  
 Alternativ hat der Administrator die Möglichkeit, die Standardeinstellung beizubehalten (also keine Annahmen) und das Fehlschlagen der Wiederherstellung zuzulassen, damit ein eventueller DTC-Ausfall sofort bemerkt werden kann, wie im nachstehenden Beispiel erläutert.  
  
```  
sp_configure 'show advanced options', 1  
GO  
RECONFIGURE  
GO  
sp_configure 'in-doubt xact resolution', 1 -- presume commit  
GO  
reconfigure  
GO  
ALTER DATABASE pubs SET ONLINE -- run recovery again  
GO  
sp_configure 'in-doubt xact resolution', 0 -- back to no assumptions  
GO  
sp_configure 'show advanced options', 0  
GO  
RECONFIGURE  
GO  
  
```  
  
 Bei **in-doubt xact resolution** handelt es sich um eine erweiterte Option. Wenn Sie die Einstellung mithilfe der gespeicherten Systemprozedur **sp_configure** ändern, können Sie **in-doubt xact resolution** nur ändern, wenn **Erweiterte Optionen anzeigen** auf 1 festgelegt ist. Die Einstellung tritt ohne Neustarten des Servers sofort in Kraft.  
  
> [!NOTE]  
>  Die konsistente Konfiguration dieser Option auf allen [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanzen, die an verteilten Transaktionen beteiligt sind, trägt dazu bei, Inkonsistenzen in den Daten zu vermeiden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
