---
title: Verbinden von Komponenten in einem Datenfluss | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- components [Integration Services], connections
- connections [Integration Services], data flow components
ms.assetid: 70616a58-8921-4218-85bf-f3e90c5a9dbf
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 90d3e9e50ef16e51e9669a92cfb53f5f734c83ef
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62827918"
---
# <a name="connect-components-in-a-data-flow"></a>Verbinden von Komponenten in einem Datenfluss
  In diesem Verfahren wird das Verbinden der Ausgabe von Komponenten in einem Datenfluss mit anderen Komponenten innerhalb desselben Datenflusses beschrieben.  
  
### <a name="to-connect-components-in-a-data-flow"></a>So verbinden Sie Komponenten in einem Datenfluss  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] das [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Projekt mit dem gewünschten Paket.  
  
2.  Doppelklicken Sie im Projektmappen-Explorer auf das Paket, um es zu öffnen.  
  
3.  Klicken Sie auf die Registerkarte **Ablaufsteuerung** , und doppelklicken Sie anschließend auf den Datenflusstask, der den Datenfluss enthält, in dem Sie Komponenten verbinden möchten.  
  
4.  Wählen Sie auf der Entwurfsoberfläche der Registerkarte **Datenfluss** die Transformation oder Quelle aus, die Sie verbinden möchten.  
  
5.  Ziehen Sie den grünen Ausgabepfeil einer Transformation oder Quelle auf eine Transformation oder ein Ziel. Manche Datenflusskomponenten weisen Fehlerausgaben auf, die Sie auf die gleiche Weise verbinden können.  
  
    > [!NOTE]  
    >  Für manche Datenflusskomponenten sind mehrere Ausgaben möglich, und Sie können jede Ausgabe mit einer anderen Transformation oder einem anderen Ziel verbinden.  
  
6.  Klicken Sie im Menü **Datei** auf **Ausgewählte Elemente speichern** , um das aktualisierte Paket zu speichern.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Hinzufügen oder Löschen einer Komponente in einem Datenfluss](data-flow.md)   
 [Konfigurieren einer Fehlerausgabe in einer Datenfluss Komponente](../configure-an-error-output-in-a-data-flow-component.md)   
 [Datenfluss](data-flow.md)  
  
  
