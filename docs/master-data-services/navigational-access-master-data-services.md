---
title: Navigationszugriff (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
helpviewer_keywords:
- navigational access [Master Data Services]
- security [Master Data Services], navigational access
ms.assetid: 3403b7b0-44e2-48c3-a1b7-9c4612b874b8
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: b3a57de7e071a66fa1b8a6091d51fb4d799f2cbd
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47610308"
---
# <a name="navigational-access-master-data-services"></a>Navigationszugriff (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Der Navigationszugriff gilt für die Modellobjektsicherheit, die auf der Registerkarte **Modelle** zugewiesen wird.  
  
 Navigationszugriff ist der Zugriff auf höhere Ebenen als die Ebene, für die Ihnen Sicherheit zugewiesen wurde.  
  
 In diesem Beispiel werden einer Entität Berechtigungen zugewiesen, der Navigationszugriff wird daher auf der Modellebene gewährt.  
  
 ![mds_conc_inheritance_model](../master-data-services/media/mds-conc-inheritance-model.gif "mds_conc_inheritance_model")  
  
 **Entitäten**  
  
 Wenn Sie einer Entität, den Blattelementen oder konsolidierten Elementen Berechtigungen zuweisen, bedeutet Navigationszugriff, dass Sie den Namen und den Code für alle Elemente lesen oder aktualisieren können. Sie können auch den Modellnamen lesen.  
  
 **Attribute**  
  
 Wenn Sie einem Attribut Berechtigungen zuweisen, bedeutet Navigationszugriff, dass Sie den Namen und den Code für alle Elemente in der Entität lesen oder aktualisieren können. Sie können auch den Modellnamen lesen.  
  
 **Auflistungen**  
  
 Wenn Sie Auflistungen Berechtigungen zuweisen, können Sie den Namen, Code, die Beschreibung und Besitzer-ID lesen oder aktualisieren. Sie können auch den Modellnamen lesen.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Vorgehensweise: Festlegen von Berechtigungen &#40;Master Data Services&#41;](../master-data-services/how-permissions-are-determined-master-data-services.md)  
  
  
