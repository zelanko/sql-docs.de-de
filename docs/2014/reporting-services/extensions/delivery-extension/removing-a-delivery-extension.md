---
title: Entfernen einer Übermittlungserweiterung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- removing delivery extensions
- deleting delivery extensions
- delivery extensions [Reporting Services], removing
ms.assetid: dcb7caf2-d19a-4bc5-afb3-2b61ad11cac5
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 5efe51d0c91a0321a17e539aeddbb26f0dc3a5fe
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56036251"
---
# <a name="removing-a-delivery-extension"></a>Entfernen einer Übermittlungserweiterung
  Sie entfernen eine [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Übermittlungserweiterung, indem Sie einfach das **Erweiterungselement** für die Übermittlungserweiterung aus der Konfigurationsdatei entfernen. Nachdem Sie die Konfigurationsinformationen entfernt haben, steht die Übermittlungserweiterung nicht mehr auf dem Berichtsserver zur Verfügung.  
  
 Wenn das entsprechende **Erweiterungselement** für die Übermittlungserweiterung aus der Konfigurationsdatei entfernt wurde, ist die Übermittlungserweiterung nicht mehr auf dem Berichtsserver registriert. Der Berichtsserver entfernt den Eintrag aus der Liste der Übermittlungserweiterungen und deaktiviert alle Abonnements, die diese Übermittlungserweiterung verwenden. Nachdem Sie eine Übermittlungserweiterung entfernt haben, können Benutzer sie nicht mehr als Benachrichtigungsmethode auswählen.  
  
## <a name="see-also"></a>Siehe auch  
 [Implementieren von Übermittlungserweiterungen](implementing-a-delivery-extension.md)   
 [Reporting Services Extension Library (Reporting Services-Erweiterungsbibliothek)](../reporting-services-extension-library.md)  
  
  
