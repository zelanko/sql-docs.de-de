---
description: Auflistungsberechtigungen (Master Data Services)
title: Auflistungsberechtigungen
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- collections [Master Data Services], permissions
- permissions [Master Data Services], collections
ms.assetid: 703e1bf5-4b4b-4830-8a5b-f979b09f677d
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 04ffb34b92aa43c521a9a454a8068e74cf4fd615
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88390286"
---
# <a name="collection-permissions-master-data-services"></a>Auflistungsberechtigungen (Master Data Services)

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  Auflistungsberechtigungen gelten für alle Auflistungen in einer Entität. Es kann keine Berechtigung für eine bestimmte Auflistung erteilt werden; Berechtigungen gelten für alle Auflistungen.  
  
> [!NOTE]  
>  Diese Berechtigungen gelten nur für den Funktionsbereich **Explorer** der Benutzeroberfläche.  
  
|Berechtigung|BESCHREIBUNG|  
|----------------|-----------------|  
|**Lesen**|Der Benutzer kann Elemente der Auflistung und die Elementattribute lesen.|  
|**Erstellen**|Der Benutzer kann Auflistungselemente erstellen und Attributwerte zuweisen.|  
|**Aktualisieren**|Der Benutzer kann Auflistungselemente, Attribute und Beziehungen aktualisieren.|  
|**Löschen**|Der Benutzer kann Elemente der Auflistung löschen.|  
|**Deny**|Jeglicher Zugriff auf die Elemente der Auflistung wird verweigert.|  
  
 Die Berechtigungen Lesen, Erstellen, Aktualisieren und Löschen können kombiniert werden. Wenn Erstellen, Aktualisieren und Löschen zugewiesen werden, wird die Leseberechtigung automatisch zugewiesen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Zuweisen von Berechtigungen für Modell Objekte &#40;Master Data Services&#41;](../master-data-services/assign-model-object-permissions-master-data-services.md)   
 [Sammlungen &#40;Master Data Services&#41;](../master-data-services/collections-master-data-services.md)   
 [Berechtigungen für Modellobjekte &#40;Master Data Services&#41;](../master-data-services/model-object-permissions-master-data-services.md)  
  
  
