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
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: d9e2838e2ba3cfcb713c0353b89054ca549e4e5c
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52799092"
---
# <a name="model-object-permissions-master-data-services"></a>Berechtigungen für Modellobjekte (Master Data Services)
  Berechtigungen für Modellobjekte sind erforderlich. Sie bestimmen die Attribute, auf die ein Benutzer im Funktionsbereich **Explorer** der Benutzeroberfläche zugreifen kann.  
  
 Wenn Sie z.B. der Entität „Product“ die Benutzerberechtigung **Aktualisieren** zuweisen, kann der Benutzer alle Attribute der Entität „Product“ aktualisieren. Wenn Sie einem einzelnen Attribut die Berechtigung **Aktualisieren** zuweisen, kann der Benutzer nur dieses Attribut aktualisieren.  
  
 Um die jedem Attributwert zugewiesene Sicherheit zu ermitteln, werden Modellobjektberechtigungen mit Hierarchieelementberechtigungen kombiniert, die die Elemente bestimmen, auf die ein Benutzer zugreifen kann.  
  
 Um einem Benutzerzugriff auf den Funktionsbereich außer geben **Explorer**, die Benutzer muss ein modelladministrator sein, der Objektmodellen auch Zuweisen von Berechtigungen für Modellobjekte. Weitere Informationen finden Sie unter [Administratoren &#40;Master Data Services&#41;](administrators-master-data-services.md)zuzugreifen.  
  
 Berechtigungen für Modellobjekte werden in der [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]-Benutzeroberfläche im Funktionsbereich **Benutzer- und Gruppenberechtigungen** auf der Registerkarte **Modelle** zugewiesen. Auf dieser Registerkarte wird das Modell als Baumstruktur dargestellt. Wenn Sie einem Objekt in der Struktur eine Berechtigung zuweisen, wird diese Berechtigung von allen untergeordneten Objekten geerbt. Sie können die Vererbung überschreiben, indem Sie einzelnen Objekten eine Berechtigung zuweisen.  
  
 Sie können zuweisen **schreibgeschützte**, **Update**, oder **Verweigern** Berechtigungen für Modellobjekte. Wenn Sie auf der Registerkarte **Modelle** keine Berechtigungen zuweisen, kann der Benutzer keine Modelle oder Daten in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]anzeigen.  
  
## <a name="best-practice"></a>Bewährte Methoden  
 Im Allgemeinen sollten Sie zuweisen **Update** für das Modellobjekt verfügen, und klicken Sie dann Berechtigung explizit zuweisen untergeordneten Objekten. Wenn Sie untergeordneten Objekten keine Berechtigung zuweisen, werden die Berechtigungen geerbt, und der Benutzer ist Administrator.  
  
## <a name="see-also"></a>Siehe auch  
 [Zuweisen von Berechtigungen für Modellobjekte &#40;Master Data Services&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md)   
 [Modellberechtigungen &#40;Master Data Services&#41;](../../2014/master-data-services/model-permissions-master-data-services.md)   
 [Berechtigungen für Funktionsbereiche &#40;Master Data Services&#41;](../../2014/master-data-services/functional-area-permissions-master-data-services.md)   
 [Berechtigungen für Hierarchieelemente &#40;Master Data Services&#41;](../../2014/master-data-services/hierarchy-member-permissions-master-data-services.md)   
 [Vorgehensweise: Festlegen von Berechtigungen &#40;Master Data Services&#41;](../../2014/master-data-services/how-permissions-are-determined-master-data-services.md)  
  
  
