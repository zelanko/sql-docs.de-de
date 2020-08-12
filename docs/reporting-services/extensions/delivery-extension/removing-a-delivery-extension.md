---
title: Entfernen einer Übermittlungserweiterung | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Sie eine Übermittlungserweiterung aus Reporting Services entfernen, damit der Berichtsserver diese nicht als verfügbar auflistet und Abonnements deaktiviert, die diese verwenden.
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: extensions
ms.topic: reference
helpviewer_keywords:
- removing delivery extensions
- deleting delivery extensions
- delivery extensions [Reporting Services], removing
ms.assetid: dcb7caf2-d19a-4bc5-afb3-2b61ad11cac5
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 6f4f23d58836dbadb9393be49dd34425c89a15c3
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2020
ms.locfileid: "84529486"
---
# <a name="removing-a-delivery-extension"></a>Entfernen einer Übermittlungserweiterung
  Sie entfernen eine [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Übermittlungserweiterung, indem Sie einfach das **Erweiterungselement** für die Übermittlungserweiterung aus der Konfigurationsdatei entfernen. Nachdem Sie die Konfigurationsinformationen entfernt haben, steht die Übermittlungserweiterung nicht mehr auf dem Berichtsserver zur Verfügung.  
  
 Wenn das entsprechende **Erweiterungselement** für die Übermittlungserweiterung aus der Konfigurationsdatei entfernt wurde, ist die Übermittlungserweiterung nicht mehr auf dem Berichtsserver registriert. Der Berichtsserver entfernt den Eintrag aus der Liste der Übermittlungserweiterungen und deaktiviert alle Abonnements, die diese Übermittlungserweiterung verwenden. Nachdem Sie eine Übermittlungserweiterung entfernt haben, können Benutzer sie nicht mehr als Benachrichtigungsmethode auswählen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Implementieren von Übermittlungserweiterungen](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Reporting Services Extension Library (Reporting Services-Erweiterungsbibliothek)](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
