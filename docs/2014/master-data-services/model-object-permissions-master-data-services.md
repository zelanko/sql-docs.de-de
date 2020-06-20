---
title: Berechtigungen für Modellobjekte (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- permissions [Master Data Services], model objects
- models [Master Data Services], object permissions
ms.assetid: fab6335b-4cae-47de-ae7c-6c4743e0680f
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 754920cac0a832ac5ae1ff8959e710815d68fd70
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84971190"
---
# <a name="model-object-permissions-master-data-services"></a>Berechtigungen für Modellobjekte (Master Data Services)
  Berechtigungen für Modellobjekte sind erforderlich. Sie bestimmen die Attribute, auf die ein Benutzer im Funktionsbereich **Explorer** der Benutzeroberfläche zugreifen kann.  
  
 Wenn Sie z.B. der Entität „Product“ die Benutzerberechtigung **Aktualisieren** zuweisen, kann der Benutzer alle Attribute der Entität „Product“ aktualisieren. Wenn Sie einem einzelnen Attribut die Berechtigung **Aktualisieren** zuweisen, kann der Benutzer nur dieses Attribut aktualisieren.  
  
 Um die jedem Attributwert zugewiesene Sicherheit zu ermitteln, werden Modellobjektberechtigungen mit Hierarchieelementberechtigungen kombiniert, die die Elemente bestimmen, auf die ein Benutzer zugreifen kann.  
  
 Um einem Benutzer Zugriff auf einen anderen Funktionsbereich als **Explorer**zu geben, muss der Benutzer ein Modell Administrator sein, der auch das Zuweisen von Berechtigungen für Modell Objekte umfasst. Weitere Informationen finden Sie unter [Administratoren &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
 Berechtigungen für Modell Objekte werden in der [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Benutzeroberfläche (User Interface, UI) im Funktionsbereich **Benutzer-und Gruppenberechtigungen** auf der Registerkarte **Modelle** zugewiesen. Auf dieser Registerkarte wird das Modell als Baumstruktur dargestellt. Wenn Sie einem Objekt in der Struktur eine Berechtigung zuweisen, wird diese Berechtigung von allen untergeordneten Objekten geerbt. Sie können die Vererbung überschreiben, indem Sie einzelnen Objekten eine Berechtigung zuweisen.  
  
 Sie können Modell Objekten die Berechtigung " **Lesen**", " **Aktualisieren**" oder " **verweigern** " zuweisen. Wenn Sie auf der Registerkarte **Modelle** keine Berechtigungen zuweisen, kann der Benutzer keine Modelle oder Daten in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]anzeigen.  
  
## <a name="best-practice"></a>Bewährte Methode  
 Im Allgemeinen sollten Sie dem Modell Objekt die Berechtigung **Aktualisieren** zuweisen und dann untergeordneten Objekten die Berechtigung explizit zuweisen. Wenn Sie untergeordneten Objekten keine Berechtigung zuweisen, werden die Berechtigungen geerbt, und der Benutzer ist Administrator.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Zuweisen von Berechtigungen für Modell Objekte &#40;Master Data Services&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md)   
 [Modell Berechtigungen &#40;Master Data Services&#41;](../../2014/master-data-services/model-permissions-master-data-services.md)   
 [Berechtigungen für Funktionsbereiche &#40;Master Data Services&#41;](../../2014/master-data-services/functional-area-permissions-master-data-services.md)   
 [Hierarchie Element Berechtigungen &#40;Master Data Services&#41;](../../2014/master-data-services/hierarchy-member-permissions-master-data-services.md)   
 [Vorgehensweise: Festlegen von Berechtigungen &#40;Master Data Services&#41;](../../2014/master-data-services/how-permissions-are-determined-master-data-services.md)  
  
  
