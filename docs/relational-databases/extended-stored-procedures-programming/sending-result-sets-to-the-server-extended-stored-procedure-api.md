---
title: Senden von Resultsets an den Server (API für erweiterte gespeicherte Prozeduren)
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], sending result sets
- result sets [SQL Server], extended stored procedures
ms.assetid: 9d54673d-ea9d-4ac6-825a-f216ad8b0e34
author: rothja
ms.author: jroth
ms.custom: seo-dt-2019
ms.openlocfilehash: 4a54ad922e7033737ccd256c1b3a0a34f543a6dd
ms.sourcegitcommit: 15fe0bbba963d011472cfbbc06d954d9dbf2d655
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/14/2019
ms.locfileid: "74095934"
---
# <a name="sending-result-sets-to-the-server-extended-stored-procedure-api"></a>Senden von Resultsets an den Server (API für erweiterte gespeicherte Prozeduren)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Verwenden Sie stattdessen die CLR-Integration.  
  
 Wenn ein Resultset an [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]gesendet wird, sollte die erweiterte gespeicherte Prozedur wie folgt die entsprechende API abrufen:  
  
-   Die **srv_sendmsg** -Funktion kann in beliebiger Reihenfolge aufgerufen werden, bevor oder nachdem alle Zeilen (sofern vorhanden) mit **srv_sendrow**gesendet wurden. Alle Nachrichten müssen an den Client gesendet werden, bevor der Abschluss Status mit **srv_senddone**gesendet wird.  
  
-   Die **srv_sendrow** -Funktion wird einmal für jede an den Client gesendete Zeile aufgerufen. Alle Zeilen müssen an den Client gesendet werden, bevor Nachrichten, Statuswerte oder Abschluss Status mit **srv_sendmsg**, dem **srv_status** -Argument von **srv_pfield**oder **srv_senddone**gesendet werden.  
  
-   Beim Senden einer Zeile, für die nicht alle Spalten mit **srv_describe** definiert wurden, wird von der Anwendung eine Informations Fehlermeldung ausgegeben, und es wird ein Fehler an den Client zurückgegeben. In diesem Fall wird die Zeile nicht gesendet.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen erweiterter gespeicherter Prozeduren](../../relational-databases/extended-stored-procedures-programming/creating-extended-stored-procedures.md)  
  
  
