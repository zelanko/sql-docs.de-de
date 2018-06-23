---
title: Überlappende Benutzer- und Gruppenberechtigungen (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- users [Master Data Services], resolving permissions
- permissions [Master Data Services], user and group overlaps
- groups [Master Data Services], resolving permissions
ms.assetid: 31c3cf7d-17d4-4474-b6a7-ffcb9fc45b37
caps.latest.revision: 5
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 6523603f7524af93bc21417f378a41bd907532d8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36161140"
---
# <a name="overlapping-user-and-group-permissions-master-data-services"></a>Überlappende Benutzer- und Gruppenberechtigungen (Master Data Services)
  Benutzerberechtigungen basieren auf:  
  
-   Berechtigungen aus Gruppenmitgliedschaften  
  
-   Dem Benutzer explizit zugewiesenen Berechtigungen  
  
 Wenn ein Benutzer mehreren Gruppen angehört und diese Gruppen Zugriff auf Master Data Manager haben, gelten die folgenden Regeln:  
  
-   Mit**Verweigern** werden alle anderen Berechtigungen überschrieben.  
  
-   **Update** überschreibt **schreibgeschützte**.  
  
 Diese Regeln gelten sowohl für die Registerkarte **Modelle** als auch für die Registerkarte **Hierarchieelemente** . Berechtigungen werden für jede Registerkarte aufgelöst und dann kombiniert. Weitere Informationen finden Sie unter [How Permissions Are Determined &#40;Master Data Services&#41;](how-permissions-are-determined-master-data-services.md).  
  
> [!NOTE]  
>  Sie können die Auflösung überlappender Benutzer- und Gruppenberechtigungen in der Benutzeroberfläche anzeigen. Sowohl die Registerkarte **Modelle** als auch die Registerkarte **Hierarchieelemente** verfügt über eine Dropdownliste, aus der Sie **Effektiv** auswählen können, um effektive Berechtigungen anzuzeigen.  
  
## <a name="example-1"></a>Beispiel 1  
 ![mds_conc_user_group_ex_1](../../2014/master-data-services/media/mds-conc-user-group-ex-1.gif "mds_conc_user_group_ex_1")  
  
 Der Benutzer gehört der Gruppe 1 und der Gruppe 2 an.  
  
 Der Benutzer hat **schreibgeschützte** Berechtigung für die Product-Entität.  
  
 Gruppe 1 verfügt für die Entität „Product“ über die Berechtigung **Aktualisieren** .  
  
 Gruppe 2 verfügt **schreibgeschützte** Berechtigung für die Product-Entität.  
  
 Ergebnis: Die effektive Berechtigung des Benutzers für die Entität „Product“ lautet **Aktualisieren** .  
  
## <a name="example-2"></a>Beispiel 2  
 ![mds_conc_user_group_ex_2](../../2014/master-data-services/media/mds-conc-user-group-ex-2.gif "mds_conc_user_group_ex_2")  
  
 Der Benutzer gehört der Gruppe 1 und der Gruppe 2 an.  
  
 Der Benutzer hat **schreibgeschützte** Berechtigung für die Product-Entität.  
  
 Gruppe 1 verfügt für die Entität „Product“ über die Berechtigung **Aktualisieren** .  
  
 Gruppe 2 verfügt für die Entität „Product“ über die Berechtigung **Verweigern** .  
  
 Ergebnis: Die effektive Berechtigung des Benutzers für die Entität „Product“ lautet **Verweigern** .  
  
## <a name="example-3"></a>Beispiel 3  
 ![mds_conc_user_group_ex_3](../../2014/master-data-services/media/mds-conc-user-group-ex-3.gif "mds_conc_user_group_ex_3")  
  
 Der Benutzer gehört der Gruppe 1 und der Gruppe 2 an.  
  
 Der Benutzer verfügt für eine Gruppe von Elementen unter einem Hierarchieknoten über die Berechtigung **Aktualisieren** .  
  
 Gruppe 1 verfügt **schreibgeschützte** Berechtigung für eine Gruppe von Elementen unter einem Hierarchieknoten.  
  
 Gruppe 2 verfügt **schreibgeschützte** Berechtigung für eine Gruppe von Elementen unter einem Hierarchieknoten.  
  
 Ergebnis: Die effektive Berechtigung des Benutzers für die Elemente lautet **Aktualisieren** .  
  
## <a name="see-also"></a>Siehe auch  
 [Wie Berechtigungen bestimmt &#40;Master Data Services&#41;](how-permissions-are-determined-master-data-services.md)   
 [Überlappende Modell- und Elementberechtigungen &#40;Master Data Services&#41;](../../2014/master-data-services/overlapping-model-and-member-permissions-master-data-services.md)  
  
  