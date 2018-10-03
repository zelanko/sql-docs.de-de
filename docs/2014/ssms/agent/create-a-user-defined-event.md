---
title: Erstellen eines benutzerdefinierten Ereignisses | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent alerts, user-defined events
- user-defined events [SQL Server]
- multiple language support [SQL Server], alerts
- languages [SQL Server], alerts
- severity levels [SQL Server]
- global considerations [SQL Server], alerts
- events [SQL Server], user-defined
- SQL Server Agent alerts, multiple-language environments
- alerts [SQL Server], user-defined events
- alerts [SQL Server], multiple-language environments
- custom events [SQL Server Agent]
- international considerations [SQL Server], alerts
ms.assetid: 03d71a35-97fa-4bba-aa9a-23ac9c9cf879
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9b1a099543f7161c672037c57985ccee69906d99
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48146230"
---
# <a name="create-a-user-defined-event"></a>Erstellen eines benutzerdefinierten Ereignisses
  Sie können benutzerdefinierte Ereignisse erstellen, wenn Sie zusätzlich zu den von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vordefinierten Ereignissen weitere Ereignisse überwachen möchten. Sie können allen benutzerdefinierten Ereignissen auch einen Schweregrad zuweisen.  
  
> [!NOTE]  
>  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]sollten Sie für die Meldungen aller benutzerdefinierten Ereignisse die Option **In Windows-Anwendungsereignisprotokoll schreiben** auswählen, um sicherzustellen, dass die Meldungen protokolliert werden. Benutzerdefinierte Meldungen mit einem Schweregrad kleiner als 19 werden standardmäßig nicht im [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Anwendungsereignisprotokoll protokolliert. Benutzerdefinierte Meldungen mit einem Schweregrad kleiner als 19 lösen daher keine Warnungen des SQL Server-Agents aus.  
  
 Benutzerdefinierte Ereignisse müssen eine eindeutige Meldungsnummer besitzen. Die Meldungsnummern für ein benutzerdefiniertes Ereignis müssen größer als 50.000 sein. Meldungen für das Ereignis können in mehreren Sprachen definiert werden. Allerdings muss vor dem Hinzufügen von Meldungen in anderen Sprachen eine Fehlermeldung in **En-US** vorhanden sein.  
  
 Wenn Sie eine mehrsprachige [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Umgebung verwalten, sollten Sie in allen unterstützten Sprachen benutzerdefinierte Meldungen erstellen. Wenn Sie beispielsweise eine neue Ereignismeldung erstellen, die sowohl auf einem deutschen als auch auf einem englischen Server verwendet werden soll, können Sie für beide dieselbe Meldungsnummer und denselben Schweregrad verwenden, müssen ihnen jedoch unterschiedliche Sprachen zuweisen.  
  
 In den folgenden Aufgaben werden Informationen bereitgestellt, wie Sie benutzerdefinierte Ereignisse und die dazugehörigen Warnungen erstellen:  
  
 **So erstellen Sie eine Warnung auf der Grundlage einer Meldungsnummer**  
  
-   [SQL Server Management Studio](create-an-alert-using-an-error-number.md)  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-add-alert-transact-sql)  
  
 **So erstellen Sie eine Warnung auf der Grundlage von Schweregraden**  
  
-   [SQL Server Management Studio](create-an-alert-using-severity-level.md)  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-add-alert-transact-sql)  
  
 **So definieren Sie die Antwort auf eine Warnung**  
  
-   [SQL Server Management Studio](../sql-server-management-studio-ssms.md)  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-add-notification-transact-sql)  
  
 **So erstellen Sie eine benutzerdefinierte Ereignisfehlermeldung**  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-addmessage-transact-sql)  
  
 **So ändern Sie eine benutzerdefinierte Ereignisfehlermeldung**  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-altermessage-transact-sql)  
  
 **So löschen Sie eine benutzerdefinierte Ereignisfehlermeldung**  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-dropmessage-transact-sql)  
  
 **So deaktivieren oder reaktivieren Sie eine Warnung**  
  
-   [SQL Server Management Studio](disable-or-reactivate-an-alert.md)  
  
-   [Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-update-alert-transact-sql)  
  
## <a name="see-also"></a>Siehe auch  
 [Sp_update_alert &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-alert-transact-sql)  
  
  
