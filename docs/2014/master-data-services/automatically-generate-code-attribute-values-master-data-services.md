---
title: Automatisches Generieren von Codeattributwerten (Master Data Services) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 19b354ee-2906-4cc7-ba2f-32b4543bddcf
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 9d6bdaf3e34ab6386cf4270c2610bd7b1a70e668
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "65483625"
---
# <a name="automatically-generate-code-attribute-values-master-data-services"></a>Automatisches Generieren von Codeattributwerten (Master Data Services)
  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] können Sie Werte für das Codeattribut einer Entität automatisch generieren lassen, wenn Sie möchten, dass dem Codewert bei jeder Erstellung eines neuen Elements automatisch eine ganze Zahl zugewiesen wird.  
  
## <a name="prerequisites"></a>Voraussetzungen  
 So führen Sie diese Prozedur aus  
  
-   Sie müssen über die Berechtigung verfügen, auf den Funktionsbereich **System Verwaltung** zuzugreifen.  
  
-   Sie müssen ein Modelladministrator sein. Weitere Informationen finden Sie unter [Administratoren &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
-   Die Entität muss vorhanden sein. Weitere Informationen finden Sie unter [Erstellen einer Entität &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-entity-master-data-services.md).  
  
### <a name="to-automatically-generate-code-values"></a>So generieren Sie automatisch Codewerte  
  
1.  Klicken Sie in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]auf **Systemverwaltung**.  
  
2.  Zeigen Sie auf der Seite **Modell-Explorer** auf der Menüleiste auf **Verwalten** , und klicken Sie auf **Entitäten**.  
  
3.  Wählen Sie auf der Seite **Entitätsverwaltung** aus der Liste **Modell** ein Modell aus.  
  
4.  Wählen Sie die Zeile für die Entität aus, für die Sie Codes generieren möchten.  
  
5.  Klicken Sie auf **Ausgewählte Entität bearbeiten**.  
  
6.  Aktivieren Sie das Kontrollkästchen **Codewerte automatisch erstellen** .  
  
7.  Geben Sie im Feld **Start bei** eine Zahl ein, die inkrementiert werden soll. Wenn Elemente bereits vorhanden sind, wird der Code auf Grundlage des höchsten vorhandenen Werts festgelegt. Wenn der höchste vorhandene Codewert z.B. 299 ist, wird der Codewert des nächsten Elements auf 300 festgelegt.  
  
8.  Klicken Sie auf **Entität speichern**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Automatische Code Erstellung &#40;Master Data Services&#41;](../../2014/master-data-services/automatic-code-creation-master-data-services.md)   
 [Automatisches Generieren von anderen Attributwerten als Code &#40;Master Data Services&#41;](../../2014/master-data-services/automatically-generate-attribute-values-other-than-code-master-data-services.md)  
  
  
