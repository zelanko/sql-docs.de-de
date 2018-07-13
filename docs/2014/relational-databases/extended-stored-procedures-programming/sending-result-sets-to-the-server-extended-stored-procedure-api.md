---
title: Senden von Resultsets an den Server (API für erweiterte gespeicherte Prozeduren) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], sending result sets
- result sets [SQL Server], extended stored procedures
ms.assetid: 9d54673d-ea9d-4ac6-825a-f216ad8b0e34
caps.latest.revision: 15
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 590565f15ac9d53b7209fa6808c4c24baeee6344
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37182247"
---
# <a name="sending-result-sets-to-the-server-extended-stored-procedure-api"></a>Senden von Resultsets an den Server (API für erweiterte gespeicherte Prozeduren)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Verwenden Sie stattdessen die CLR-Integration.  
  
 Beim Senden eines Resultsets an [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], die erweiterte gespeicherte Prozedur sollte die entsprechende API wie folgt aufrufen:  
  
-   Die **Srv_sendmsg** -Funktion in einer beliebigen Reihenfolge aufgerufen, bevor oder nachdem alle Zeilen (sofern vorhanden) mit gesendet wurden **Srv_sendrow**. Alle Nachrichten müssen an den Client gesendet werden, bevor der Abschlussstatus. dabei gesendet werden **Srv_senddone**.  
  
-   Die **srv_sendrow** -Funktion wird einmal für jede an den Client gesendete Zeile aufgerufen. Alle Zeilen gesendet werden müssen, an den Client, bevor Nachrichten, Statuswerte oder Abschlussstatus mit gesendet werden **Srv_sendmsg**, **Srv_status** Argument **Srv_pfield**, oder **Srv_senddone**.  
  
-   Beim Senden einer Zeile, die nicht alle Spalten, die mit hatte **Srv_describe** bewirkt, dass die Anwendung eine informationsfehlermeldung an und gibt FAIL zurück an den Client. In diesem Fall wird die Zeile nicht gesendet.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen erweiterter gespeicherter Prozeduren](creating-extended-stored-procedures.md)  
  
  
