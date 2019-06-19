---
title: Automatische Codeerstellung (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 9adbd5e1-f28c-4fb5-afa7-082de2831f3e
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 7ee7e06829f72ab44fd036766907be94c95b7d90
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65483696"
---
# <a name="automatic-code-creation-master-data-services"></a>Automatische Codeerstellung (Master Data Services)
  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]können numerische Werte für das Codeattribut oder andere numerische Attributwerte automatisch generiert werden. Wenn Codes automatisch generiert werden, können Sie trotzdem andere Werte für Codes eingeben; es wird nur ein Anfangswert automatisch festgelegt.  
  
## <a name="generating-code-values"></a>Generieren von Codewerten  
 Administratoren können automatisch generierte Werte für das Code-Attribut konfigurieren, indem sie die Eigenschaften der zugeordneten Entität bearbeiten. Sie können einen Anfangswert angeben, und jeder nachfolgende Wert wird um 1 erhöht.  
  
 Wenn Sie Codewerte in MDS entweder in einem der Tools oder mit dem Stagingprozess eingeben, können Sie den Code-Wert leer lassen und ein Code-Wert wird automatisch generiert. Oder Sie können einen Codewert Ihrer Wahl angeben.  
  
## <a name="generating-other-attribute-values"></a>Generieren von anderen Attributwerten  
 Administratoren können Werte für andere Attribute als Code automatisch generieren, indem sie Geschäftsregeln erstellen. Sie können einen Anfangswert angeben und die Zahl angeben, um die jeder nachfolgende Wert inkrementiert wird.  
  
 Wenn Sie Attributwerte in MDS entweder in einem der Tools oder mit dem Stagingprozess eingeben, können Sie den Attributwert leer lassen. Wenn Geschäftsregeln angewendet werden, werden die Werte auf Grundlage des höchsten vorhandenen Werts inkrementiert. Wenn die Regel z.B. „Standardattribut für einen generierten Wert, der bei 1 startet und um 4 inkrementiert wird“ lautet und der höchste aktuelle Wert für das Attribut „700“ ist, beträgt der Wert für das nächste hinzugefügte Element „704“.  
  
## <a name="deleting-automatically-generated-values"></a>Löschen von automatisch generierten Werten  
 Nachdem ein Administrator automatisch generierte Werte für das Code-Attribut aktiviert hat, löschen Benutzer möglicherweise unbeabsichtigt ein Element, das über einen Code-Wert verfügte, den sie wiederverwenden möchten. Die Fehlermeldung "der Elementcode bereits von einem Element, das gelöscht wurde verwendet wird" wird angezeigt. Es gibt zwei mögliche Lösungen:  
  
-   In der **Versionsverwaltung** Funktionsbereich umkehren ein Administrator die Transaktion, die aufgetreten sind, wenn das Element gelöscht wurde. Dies bedeutet jedoch, dass alle Attribute und Mitgliedschaft in Hierarchien und Auflistungen des früheren Elements wiederhergestellt wird. Weitere Informationen finden Sie unter [Umkehren einer Transaktion &#40;Master Data Services&#41;](reverse-a-transaction-master-data-services.md).  
  
-   Ein Administrator kann das Element mithilfe des Stagingprozesses permanent löschen. Weitere Informationen finden Sie unter [deaktivieren oder Löschen von Elementen mithilfe des Stagingprozesses &#40;Master Data Services&#41;](add-update-and-delete-data-master-data-services.md).  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Taskbeschreibung|Thema|  
|----------------------|-----------|  
|Automatisches Generieren von Werten für das Codeattribut.|[Automatisches Generieren von Codeattributwerten &#40;Master Data Services&#41;](../../2014/master-data-services/automatically-generate-code-attribute-values-master-data-services.md)|  
|Generieren Sie automatisch Werte für andere Attribute.|[Automatisches Generieren von anderen Attributwerten als Code &#40;Master Data Services&#41;](../../2014/master-data-services/automatically-generate-attribute-values-other-than-code-master-data-services.md)|  
  
## <a name="related-content"></a>Verwandte Inhalte  
  
-   [Übersicht über Master Data Services](master-data-services-overview-mds.md)  
  
-   [Geschäftsregeln &#40;Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md)  
  
-   [Entitäten &#40;Master Data Services&#41;](../../2014/master-data-services/entities-master-data-services.md)  
  
  
