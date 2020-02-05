---
title: Ändern einer Sitzung für erweiterte Ereignisse
ms.date: 05/24/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xevents
ms.topic: tutorial
ms.assetid: 114ec05b-7eca-4c87-b276-25e37b84be39
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 32a57c46cebb17df257f2002c25ab5f1d7107379
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "75255773"
---
# <a name="alter-an-extended-events-session"></a>Ändern einer Sitzung für erweiterte Ereignisse

[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

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
 [ALTER EVENT SESSION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-event-session-transact-sql.md)   
 [Erstellen einer Sitzung für erweiterte Ereignisse mit dem Abfrage-Editor](quick-start-extended-events-in-sql-server.md)  
  
  
