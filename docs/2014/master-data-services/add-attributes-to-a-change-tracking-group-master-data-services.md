---
title: Hinzufügen von Attributen zu einer Änderungsnachverfolgungsgruppe (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- change tracking groups [Master Data Services]
- attributes [Master Data Services], change tracking groups
- change tracking groups [Master Data Services], adding attributes
ms.assetid: e153eb5f-70ca-4c6f-89d8-1f937ed3917d
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 8e700942f9cebc08241cf4e159dceedc7d515a94
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65480126"
---
# <a name="add-attributes-to-a-change-tracking-group-master-data-services"></a>Hinzufügen von Attributen zu einer Änderungsnachverfolgungsgruppe (Master Data Services)
  Fügen Sie in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]einer Änderungsnachverfolgungsgruppe Attribute hinzu, wenn Sie Änderungen an den Werten des Attributs nachverfolgen möchten.  
  
> [!NOTE]  
>  Nachdem Sie einer Änderungsnachverfolgungsgruppe ein Attribut hinzugefügt haben, wird das Attribut in der [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Datenbank als geändert markiert, wenn die Werte für das Attribut geändert werden. Erstellen Sie eine Geschäftsregel, um auf der Grundlage der Änderung zu handeln.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 So führen Sie diese Prozedur aus  
  
-   Sie müssen über die Berechtigung verfügen, auf den Funktionsbereich **Systemverwaltung** zuzugreifen.  
  
-   Sie müssen ein Modelladministrator sein. Weitere Informationen finden Sie unter [Administratoren &#40;Master Data Services&#41;](administrators-master-data-services.md)zuzugreifen.  
  
-   Attribute müssen vorhanden sein, um sie der Änderungsnachverfolgungsgruppe hinzufügen zu können. Weitere Informationen finden Sie unter [Create a Text Attribute &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-text-attribute-master-data-services.md).  
  
### <a name="to-add-attributes-to-a-change-tracking-group"></a>So fügen Sie einer Änderungnachverfolgungsgruppe Attribute hinzu  
  
1.  Klicken Sie in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]auf **Systemverwaltung**.  
  
2.  Auf der **Modell-Explorer** Seite zeigen Sie auf der Menüleiste **verwalten** , und klicken Sie auf **Entitäten**.  
  
3.  Wählen Sie auf der Seite **Entitätsverwaltung** aus der Liste **Modell** ein Modell aus.  
  
4.  Wählen Sie die Zeile für die Entität aus, für die Sie Attributwerte verfolgen möchten.  
  
5.  Klicken Sie auf **Ausgewählte Entität bearbeiten**.  
  
6.  Auf der Seite **Entität bearbeiten** .  
  
    -   Wenn das Attribut für Blattelemente in der **Blattelemente Attribute** Bereich, wählen Sie das Attribut, und klicken Sie auf **blattattribut bearbeiten**.  
  
    -   Wenn das Attribut für konsolidierte Elemente bestimmt, in ist der **konsolidierte Attribute** Bereich, wählen Sie das Attribut, und klicken Sie auf **konsolidiertes Attribut bearbeiten**.  
  
    -   Wenn das Attribut für Sammlungen, in der **Auflistungsattribute** Bereich, wählen Sie das Attribut, und klicken Sie auf **auflistungsattribut bearbeiten**.  
  
7.  Aktivieren Sie das Kontrollkästchen **Änderungsverfolgung aktivieren** .  
  
8.  Geben Sie im Feld **Änderungsverfolgungsgruppe** eine Zahl für die Gruppe ein.  
  
9. Klicken Sie auf **Attribut speichern**.  
  
10. Klicken Sie auf der Seite **Entitätsverwaltung** auf **Entität speichern**.  
  
11. Wiederholen Sie diese Prozedur für alle Attribute, die Sie in die Gruppe einschließen möchten. Verwenden Sie die gleiche Änderungsnachverfolgungs-Gruppennummer für jedes Attribut in der Gruppe.  
  
## <a name="next-steps"></a>Nächste Schritte  
  
-   [Initiieren von Aktionen auf der Grundlage von Attributwertänderungen &#40;Master Data Services&#41;](../../2014/master-data-services/initiate-actions-based-on-attribute-value-changes-master-data-services.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen eines Textattributs &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-text-attribute-master-data-services.md)   
 [Erstellen eines domänenbasierten Attributs &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md)  
  
  
