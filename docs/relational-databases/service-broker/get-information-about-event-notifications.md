---
title: Abrufen von Informationen zu Ereignisbenachrichtigungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- event notifications [SQL Server], metadata
- status information [SQL Server], event notifications
- metadata [SQL Server], event notifications
ms.assetid: 8bc10867-66d6-4f57-ac32-a6c29f3327cd
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: fefdced57d611d241dbb96b71a0b220139683243
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68083833"
---
# <a name="get-information-about-event-notifications"></a>Abrufen von Informationen zu Ereignisbenachrichtigungen
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Zum Abfragen von Metadaten zu Ereignisbenachrichtigungen stehen die folgenden Katalogsichten zur Verfügung.  
  
 **So rufen Sie Informationen zu Ereignisbenachrichtigungen auf der Nichtserverebene ab**  
  
-   [sys.event_notifications &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-event-notifications-transact-sql.md)  
  
> [!NOTE]  
>  Zum Anzeigen von Metadaten über Ereignisbenachrichtigungen in **sys.event_notifications**, die auf Datenbankebene erstellt wurden, gelten folgende Voraussetzungen: Sie verfügen über die Berechtigung CONTROL, ALTER, TAKE OWNERSHIP oder VIEW DEFINITION für die Datenbank, Sie sind der Besitzer der Ereignisbenachrichtigung oder Sie verfügen über die Berechtigung ALTER ANY DATABASE EVENT NOTIFICATION. Für Ereignisbenachrichtigungen, die in einer bestimmten Warteschlange erstellt wurden, gelten folgende Voraussetzungen: Sie verfügen über die Berechtigung CONTROL, ALTER, TAKE OWNERSHIP oder VIEW DEFINITION für das Objekt, Sie sind der Besitzer der Ereignisbenachrichtigung oder Sie verfügen über die Berechtigung ALTER ANY DATABASE EVENT NOTIFICATION.  
  
 **So rufen Sie Informationen zu Ereignisbenachrichtigungen auf der Serverebene ab**  
  
-   [sys.server_event_notifications &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-event-notifications-transact-sql.md)  
  
> [!NOTE]  
>  Sie müssen mindestens folgende Voraussetzungen erfüllen: Sie verfügen über die Berechtigung CONTROL oder VIEW ANY DEFINITION für den Server, Sie sind der Anmeldename oder Besitzer der Ereignisbenachrichtigung, oder Sie verfügen über die Berechtigung ALTER ANY EVENT NOTIFICATION, um Metadaten über Ereignisbenachrichtigungen in **sys.server_event_notifications** anzuzeigen.  
  
 **So rufen Sie Informationen zu sämtlichen Ereignissen ab, die zur Auslösung von Ereignisbenachrichtigungen führen können**  
  
-   [sys.event_notification_event_types &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-event-notification-event-types-transact-sql.md)  
  
> [!NOTE]  
>  Diese Katalogsicht gibt keine Ereignisgruppen zurück.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ereignisbenachrichtigungen](../../relational-databases/service-broker/event-notifications.md)  
  
  
