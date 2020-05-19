---
title: Ändern einer Sitzung für erweiterte Ereignisse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xevents
ms.topic: conceptual
ms.assetid: 114ec05b-7eca-4c87-b276-25e37b84be39
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 66108d50898610949cb5cab7fb3bdd2dcc726801
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/01/2020
ms.locfileid: "82706789"
---
# <a name="alter-an-extended-events-session"></a>Ändern einer Sitzung für erweiterte Ereignisse
  Nachdem Sie eine Sitzung für erweiterte Ereignisse erstellt haben, können Sie diese je nach Bedarf mithilfe des **SQL Server-Assistenten für erweiterte Ereignisse**ändern.  
  
## <a name="before-you-begin"></a>Voraussetzungen  
 Sie können kein Ziel für aktive und inaktive Sitzungen ändern, und Sie können zudem für eine aktive Sitzung die Konfigurationen für erweiterte Eigenschaften nicht ändern.  
  
 Folgende Änderungen sind sowohl für aktive als auch inaktive Ereignissitzungen möglich:  
  
-   Ereignisse können der Sitzung hinzugefügt oder von dieser entfernt werden. Zudem lassen sich die Ereigniskonfigurationen wie Ereignisfelder, -filter und -aktionen ändern.  
  
-   Sie können der Ereignissitzung ein Ziel hinzufügen oder von dieser entfernen.  
  
-   Aktivieren Sie die Option **Ereignissitzung beim Serverstart starten** .  
  
 Folgende zusätzliche Änderungen sind für eine inaktive Ereignissitzung möglich:  
  
-   Aktivieren Sie die Option zum **Nachverfolgen der Beziehung zwischen Ereignissen**.  
  
-   Ändern Sie die Konfiguration für erweiterte Eigenschaften.  
  
> [!NOTE]  
>  Der **SQL Server-Assistent für erweiterte Ereignisse** unterstützt keine Änderung von Ereignissitzungen.  
  
## <a name="how-to-alter-an-extended-events-session-using-the-sql-server-extended-events-wizard"></a>Ändern einer Sitzung für erweiterte Ereignisse mithilfe des SQL Server-Assistenten für erweiterte Ereignisse  
  
-   Erweitern Sie im Objekt-Explorer **Verwaltung**, erweitern Sie **Erweiterte Ereignisse**, und erweitern Sie dann **Sitzungen**.  
  
-   Klicken Sie mit der rechten Maustaste auf die zu ändernde Sitzung, und klicken Sie anschließend auf **Eigenschaften**.  
  
-   Nehmen Sie im Dialogfeld **Eigenschaften** die entsprechenden Änderungen vor, und klicken Sie dann auf **OK**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Alter Event Session &#40;Transact-SQL-&#41;](/sql/t-sql/statements/alter-event-session-transact-sql)   
 [Erstellen einer Sitzung für erweiterte Ereignisse mit dem Abfrage-Editor](../../database-engine/create-an-extended-events-session-using-query-editor.md)  
  
  
