---
title: Abrufen von Informationen zu Ereignisbenachrichtigungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: 9786faaf44724b1a2452bd5304b63deb2c9ea54e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63015312"
---
# <a name="get-information-about-event-notifications"></a>Abrufen von Informationen zu Ereignisbenachrichtigungen
  Zum Abfragen von Metadaten zu Ereignisbenachrichtigungen stehen die folgenden Katalogsichten zur Verfügung.  
  
 **So rufen Sie Informationen zu Ereignisbenachrichtigungen auf der Nichtserverebene ab**  
  
-   [sys.event_notifications &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-event-notifications-transact-sql)  
  
> [!NOTE]  
>  Zum Anzeigen von Metadaten über ereignisbenachrichtigungen in **Sys. event_notifications** erstellt in der Datenbank, die mindestens benötigen Sie Folgendes: STEUERN, Alter-, TAKE Ownership- oder VIEW DEFINITION-Berechtigung für die Datenbank, der Besitzer der ereignisbenachrichtigung sein oder über die ALTER ANY DATABASE EVENT NOTIFICATION-Berechtigung verfügen. Für ereignisbenachrichtigungen, die für eine bestimmte Warteschlange erstellt werden müssen mindestens die folgenden sein: STEUERN, Alter-, TAKE Ownership- oder VIEW DEFINITION-Berechtigung für das Objekt, der Besitzer der ereignisbenachrichtigung sein oder über die ALTER ANY DATABASE EVENT NOTIFICATION-Berechtigung verfügen.  
  
 **So rufen Sie Informationen zu Ereignisbenachrichtigungen auf der Serverebene ab**  
  
-   [sys.server_event_notifications &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-event-notifications-transact-sql)  
  
> [!NOTE]  
>  Mindestens benötigen Sie Folgendes: Steuern oder VIEW ANY DEFINITION-Berechtigung für den Server, die Anmeldung oder der Besitzer der ereignisbenachrichtigung sein oder über die ALTER ANY EVENT NOTIFICATION-Berechtigung zum Anzeigen von Metadaten über ereignisbenachrichtigungen in **server_event_notifications**.  
  
 **So rufen Sie Informationen zu sämtlichen Ereignissen ab, die zur Auslösung von Ereignisbenachrichtigungen führen können**  
  
-   [sys.event_notification_event_types &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-event-notification-event-types-transact-sql)  
  
> [!NOTE]  
>  Diese Katalogsicht gibt keine Ereignisgruppen zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [Ereignisbenachrichtigungen](event-notifications.md)  
  
  
