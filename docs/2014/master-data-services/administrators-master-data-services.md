---
title: Administratoren (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- administrators [Master Data Services], about administrators
- administrators [Master Data Services]
- models [Master Data Services], administrators
ms.assetid: d330aa4e-6ade-4b09-b376-1b15d6c78f7d
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: aeedc1f735fd296169f704b794d1bb0e69adab22
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84972270"
---
# <a name="administrators-master-data-services"></a>Administratoren (Master Data Services)
  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] gibt es zwei Arten von Administratoren: Modelladministratoren und den [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]-Systemadministrator.  
  
## <a name="model-administrators"></a>Modelladministratoren  
 In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] ist ein Modell Administrator ein Benutzer, dem die Berechtigung **Aktualisieren** für das Modell Objekt der obersten Ebene auf der Registerkarte **Modell Objekte** und keine anderen zugewiesenen Berechtigungen zugewiesen ist.  
  
-   Wenn der Benutzer Zugriff auf den Funktionsbereich **Explorer** hat, kann er alle Masterdaten in diesem Bereich hinzufügen, löschen und aktualisieren.  
  
-   Wenn der Benutzer Zugriff auf andere Funktionsbereiche hat, kann der Benutzer alle im Funktionsbereich verfügbaren administrativen Tasks ausführen.  
  
 Jedes Modell kann mehrere Administratoren aufweisen. Ein Benutzer kann als Modelladministrator für ein Modell, mehrere oder alle Modelle in der [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Bereitstellung definiert sein.  
  
 Er wird entweder in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] oder programmgesteuert als Modelladministrator festgelegt. Weitere Informationen finden Sie unter [Erstellen eines Modelladministrators &#40;Master Data Services&#41;](create-a-model-administrator-master-data-services.md).  
  
## <a name="master-data-services-system-administrator"></a>Master Data Services-Systemadministrator  
 Es gibt nur einen [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]-Systemadministrator. Der Systemadministrator ist der Benutzer, der beim Erstellen der Datenbank für das **Administrator Konto** angegeben wurde [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
 Der [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]-Systemadministrator:  
  
-   Verfügt automatisch über Zugriff auf alle Funktionsbereiche.  
  
-   Können alle Master Daten für alle Modelle im Funktionsbereich **Explorer** hinzufügen, löschen und aktualisieren.  
  
 Sie können den Benutzer ändern, der als Systemadministrator festgelegt ist. Weitere Informationen finden Sie unter [Ändern des System Administrator Kontos &#40;Master Data Services&#41;](../../2014/master-data-services/change-the-system-administrator-account-master-data-services.md).  
  
## <a name="comparing-administrator-types"></a>Vergleichen von Administratortypen  
  
|Administratortyp|Beschreibung|  
|------------------------|-----------------|  
|[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]-Systemadministrator|Im [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] zugewiesene Berechtigungen wirken sich nicht auf den Zugriff des Administrators aus.<br /><br /> Verfügt automatisch über die Berechtigung **Aktualisieren** für alle Modelle.<br /><br /> Verfügt automatisch über Zugriff auf alle Funktionsbereiche.<br /><br /> In MDM. tbluser lautet der Wert in der **ID** -Spalte **1**.|  
|Modelladministrator|In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] zugewiesene Berechtigungen bestimmen, ob der Benutzer Modelladministrator ist.<br /><br /> Kann je nach den Berechtigungen, die explizit zugewiesen oder von einer Gruppe geerbt wurden, Modelladministrator sein.<br /><br /> Ist nur ein Administrator für Modelle, die über die Berechtigung **Aktualisieren** für das Modell Objekt der obersten Ebene verfügen, und keine weiteren Berechtigungen.<br /><br /> Verfügt nur über Zugriff auf Funktionsbereiche, für die ihm eine Berechtigung gewährt wurde.<br /><br /> In MDM. tbluser lautet der Wert in der **ID** -Spalte nicht **1**.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen Sie einen Modell Administrator &#40;Master Data Services&#41;](create-a-model-administrator-master-data-services.md)   
 [Ändern Sie das System Administrator Konto &#40;Master Data Services&#41;](../../2014/master-data-services/change-the-system-administrator-account-master-data-services.md)   
 [Erstellen einer Master Data Services Datenbank](install-windows/create-a-master-data-services-database.md)   
 [Benachrichtigungen &#40;Master Data Services&#41;](../../2014/master-data-services/notifications-master-data-services.md)  
  
  
