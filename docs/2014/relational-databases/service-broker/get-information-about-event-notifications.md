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
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63015312"
---
# <a name="get-information-about-event-notifications"></a>Abrufen von Informationen zu Ereignisbenachrichtigungen
  Zum Abfragen von Metadaten zu Ereignisbenachrichtigungen stehen die folgenden Katalogsichten zur Verfügung.  
  
 **So rufen Sie Informationen zu Ereignisbenachrichtigungen auf der Nichtserverebene ab**  
  
-   [sys.event_notifications &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-event-notifications-transact-sql)  
  
> [!NOTE]  
>  Um in **sys.event_notifications** Metadaten zu Ereignisbenachrichtigungen anzeigen zu können, die auf der Datenbankebene erstellt wurden, müssen folgende Voraussetzungen erfüllt sein: Sie müssen über CONTROL-, ALTER-, TAKE OWNERSHIP- oder VIEW DEFINITION-Berechtigungen für die Datenbank verfügen, Sie müssen der Besitzer der Ereignisbenachrichtigung sein oder über die ALTER ANY DATABASE EVENT NOTIFICATION-Berechtigung verfügen. Für Ereignisbenachrichtigungen, die für eine bestimmte Warteschlange erstellt wurden, müssen mindestens die folgenden Voraussetzungen erfüllt sein: Sie müssen über CONTROL-, ALTER-, TAKE OWNERSHIP- oder VIEW DEFINITION-Berechtigungen für das Objekt verfügen, Sie müssen der Besitzer der Ereignisbenachrichtigung sein oder über die ALTER ANY DATABASE EVENT NOTIFICATION-Berechtigung verfügen.  
  
 **So rufen Sie Informationen zu Ereignisbenachrichtigungen auf der Serverebene ab**  
  
-   [sys.server_event_notifications &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-server-event-notifications-transact-sql)  
  
> [!NOTE]  
>  Zum Anzeigen von Metadaten über Ereignisbenachrichtigungen in **sys.server_event_notifications**müssen mindestens die folgenden Voraussetzungen erfüllt sein: Sie müssen über die CONTROL- oder VIEW ANY DEFINITION-Berechtigung für den Server verfügen, Sie müssen der Anmeldename oder Besitzer der Ereignisbenachrichtigung sein, oder Sie müssen über die ALTER ANY EVENT NOTIFICATION-Berechtigung verfügen.  
  
 **So rufen Sie Informationen zu sämtlichen Ereignissen ab, die zur Auslösung von Ereignisbenachrichtigungen führen können**  
  
-   [sys.event_notification_event_types &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-event-notification-event-types-transact-sql)  
  
> [!NOTE]  
>  Diese Katalogsicht gibt keine Ereignisgruppen zurück.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ereignisbenachrichtigungen](event-notifications.md)  
  
  
