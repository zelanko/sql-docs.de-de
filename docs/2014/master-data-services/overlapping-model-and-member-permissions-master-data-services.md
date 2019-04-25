---
title: Überlappende Modell- und Elementberechtigungen (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- models [Master Data Services], effective permissions
- permissions [Master Data Services], model and member overlaps
- members [Master Data Services], effective permissions
ms.assetid: 9fd7a555-43bf-4796-a8b6-1ca63a291216
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: e70b6dab6399026606382396bded3a467a9b639c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62764241"
---
# <a name="overlapping-model-and-member-permissions-master-data-services"></a>Überlappende Modell- und Elementberechtigungen (Master Data Services)
  Die einem Element zugewiesene Berechtigung kann mit einer einem Modellobjekt zugewiesenen Berechtigung überlappen. Bei einer Überlappung tritt die restriktivere Berechtigung in Kraft.  
  
 Wenn ein Element über eine Berechtigung verfügt, die sich von der des zugehörigen Modellobjekts unterscheidet, gelten die folgenden Regeln:  
  
-   Mit**Verweigern** werden alle anderen Berechtigungen überschrieben.  
  
-   **Nur-Lese** überschreibt **Update**.  
  
 Das folgende Bild zeigt, welche Berechtigungen für einen einzelnen Attributwert wirksam werden, wenn Attributberechtigungen sich von Elementberechtigungen unterscheiden.  
  
 ![mds_conc_security_member_overlap_table](../../2014/master-data-services/media/mds-conc-security-member-overlap-table.gif "mds_conc_security_member_overlap_table")  
  
## <a name="example-1"></a>Beispiel 1  
 ![mds_conc_overlap_model_1](../../2014/master-data-services/media/mds-conc-overlap-model-1.gif "mds_conc_overlap_model_1")  
  
 Auf der Registerkarte **Modelle** verfügt die Product-Entität über die zugewiesene Berechtigung **Aktualisieren** . Diese Berechtigung wird von allen Attributen in der Entität geerbt.  
  
 Auf der Registerkarte **Hierarchieelemente** verfügt der Unterkategorieknoten "Mountain Bikes" in einer abgeleiteten Hierarchie über die zugewiesene Berechtigung **Aktualisieren** .  
  
 Ergebnis: In **Explorer** verfügt der Benutzer über die Berechtigung **Aktualisieren** für alle Attributwerte für alle Elemente im Knoten „Mountain Bikes“. Alle anderen Elemente und Attribute werden ausgeblendet.  
  
 ![mds_conc_overlap_model_example_1](../../2014/master-data-services/media/mds-conc-overlap-model-example-1.gif "mds_conc_overlap_model_example_1")  
  
## <a name="example-2"></a>Beispiel 2  
 ![mds_conc_overlap_model_2](../../2014/master-data-services/media/mds-conc-overlap-model-2.gif "mds_conc_overlap_model_2")  
  
 Auf der Registerkarte **Modelle** verfügt das Subcategory-Attribut über die zugewiesene Berechtigung **Aktualisieren** .  
  
 Auf der **Hierarchieelemente** Registerkarte wird dem unterkategorieknoten "Mountain Bikes" in einer abgeleiteten Hierarchie explizit zugewiesen **schreibgeschützte** Berechtigung.  
  
 Ergebnis: In **Explorer**, der Benutzer hat **schreibgeschützte** -Berechtigung für die Subcategory-Attributwerte für die Elemente im Knoten "Mountain Bikes". Alle anderen Elemente und Attribute werden ausgeblendet.  
  
 ![mds_conc_overlap_model_example_2](../../2014/master-data-services/media/mds-conc-overlap-model-example-2.gif "mds_conc_overlap_model_example_2")  
  
## <a name="example-3"></a>Beispiel 3  
 ![mds_conc_overlap_model_3](../../2014/master-data-services/media/mds-conc-overlap-model-3.gif "mds_conc_overlap_model_3")  
  
 Auf der **Modelle** Registerkarte, um das Subcategory-Attribut hat **schreibgeschützte** zugewiesene Berechtigung.  
  
 Auf der Registerkarte **Hierarchieelemente** wird der Unterkategorie "Mountain Bikes" in einer abgeleiteten Hierarchie die Berechtigung **Aktualisieren** explizit zugewiesen.  
  
 Ergebnis: In **Explorer**, der Benutzer hat **schreibgeschützte** Berechtigung für die Attributwerte. Alle anderen Elemente und Attribute werden ausgeblendet.  
  
 ![mds_conc_overlap_model_example_2](../../2014/master-data-services/media/mds-conc-overlap-model-example-2.gif "mds_conc_overlap_model_example_2")  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Festlegen von Berechtigungen &#40;Master Data Services&#41;](how-permissions-are-determined-master-data-services.md)   
 [Überlappende Benutzer- und Gruppenberechtigungen &#40;Master Data Services&#41;](../../2014/master-data-services/overlapping-user-and-group-permissions-master-data-services.md)  
  
  
