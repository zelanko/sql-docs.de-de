---
title: Hinzufügen einer Gruppe (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- groups [Master Data Services], adding
- adding groups [Master Data Services]
ms.assetid: c7a88381-3b2c-4af7-9cf7-3a930c1abdee
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 1245b637eeb31ab8dee9bf498a6d076925d1dae3
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62765983"
---
# <a name="add-a-group-master-data-services"></a>Hinzufügen einer Gruppe (Master Data Services)
  Fügen Sie der Liste **Gruppen** in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] eine Gruppe hinzu, um damit zu beginnen, Berechtigungen für die Webanwendung zuzuweisen. Bevor ein Benutzer in der Gruppe auf [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]zugreifen kann, müssen Sie einem oder mehr Funktionsbereichen und Modellobjekten die Gruppenberechtigung geben.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 So führen Sie diese Prozedur aus  
  
-   Sie müssen über die Berechtigung verfügen, auf den Funktionsbereich **Benutzer- und Gruppenberechtigungen** zuzugreifen.  
  
### <a name="to-add-a-group"></a>So fügen Sie eine Gruppe hinzu  
  
1.  Klicken Sie in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]auf **Benutzer- und Gruppenberechtigungen**.  
  
2.  Klicken Sie auf der Seite **Benutzer** auf der Menüleiste auf **Gruppen verwalten**.  
  
3.  Klicken Sie auf **Gruppen hinzufügen**.  
  
4.  Geben Sie den Namen der Gruppe ein, und stellen Sie diesem den Active Directory-Domänennamen oder den Namen des Servercomputers voran, z.B. *Domäne\Gruppenname* oder *Computer\Gruppenname*.  
  
5.  Klicken Sie optional auf **Namen überprüfen**.  
  
6.  Klicken Sie auf **OK**.  
  
    > [!NOTE]  
    >  Wenn der Benutzer zum ersten Mal auf den [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]zugreift, wird der Name des Benutzers zur Benutzerliste des [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] hinzugefügt.  
  
## <a name="next-steps"></a>Nächste Schritte  
  
-   [Zuweisen von Berechtigungen für Funktionsbereiche &#40;Master Data Services&#41;](assign-functional-area-permissions-master-data-services.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Sicherheit &#40;Master Data Services&#41;](../../2014/master-data-services/security-master-data-services.md)  
  
  
