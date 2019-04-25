---
title: Löschen von Hierarchieelementberechtigungen (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- deleting member permissions [Master Data Services]
- members [Master Data Services], deleting permissions
- permissions [Master Data Services], deleting member permissions
ms.assetid: 7f22d5e2-70c1-422c-99c2-e995a47d812a
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: b8698d910ad74181a04a851334bddd4d112bbbd4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62765617"
---
# <a name="delete-hierarchy-member-permissions-master-data-services"></a>Löschen von Hierarchieelementberechtigungen (Master Data Services)
  Löschen Sie in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]Modellobjektberechtigungen, um erfolgte Zuweisungen zu entfernen.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 So führen Sie diese Prozedur aus  
  
-   Sie müssen über die Berechtigung verfügen, auf den Funktionsbereich **Benutzer- und Gruppenberechtigungen** zuzugreifen.  
  
-   Sie müssen ein Modelladministrator sein. Weitere Informationen finden Sie unter [Administratoren &#40;Master Data Services&#41;](administrators-master-data-services.md)zuzugreifen.  
  
### <a name="to-delete-hierarchy-member-permissions"></a>So löschen Sie Hierarchieelementberechtigungen  
  
1.  Klicken Sie in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]auf **Benutzer- und Gruppenberechtigungen**.  
  
2.  Wählen Sie auf der Seite **Benutzer** oder **Gruppen** die Zeile für den Benutzer oder die Gruppe aus, den bzw. die Sie bearbeiten möchten.  
  
3.  Klicken Sie auf **Ausgewähltem Benutzer bearbeiten**.  
  
4.  Klicken Sie auf die Registerkarte **Hierarchieelemente** .  
  
5.  Wählen Sie aus der Liste **Modell** ein Modell aus.  
  
6.  Wählen Sie aus der Liste **Version** eine Version aus.  
  
7.  In der **Zusammenfassung der Hierarchieelementberechtigungen** Bereich, wählen Sie die Zeile für die Berechtigung, die Sie löschen möchten.  
  
8.  Klicken Sie auf **ausgewählte Berechtigung löschen**.  
  
    > [!NOTE]  
    >  Sie können keine Berechtigung von einem Benutzer entfernen, wenn die Berechtigung von einer Gruppe geerbt wird. Sie müssen stattdessen die Berechtigung von der Gruppe entfernen.  
  
## <a name="see-also"></a>Siehe auch  
 [Berechtigungen für Hierarchieelemente &#40;Master Data Services&#41;](../../2014/master-data-services/hierarchy-member-permissions-master-data-services.md)   
 [Zuweisen von Hierarchieelementberechtigungen &#40;Master Data Services&#41;](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md)  
  
  
