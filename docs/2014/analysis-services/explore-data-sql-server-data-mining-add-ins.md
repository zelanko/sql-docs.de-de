---
title: Durchsuchen von Daten (SQL Server Data Mining-Add-ins) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data preparation
- histogram [data mining]
- data visualization
ms.assetid: 714845a9-4c27-461a-9ba3-149e1e818386
caps.latest.revision: 20
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 813da97a8128464ef105d27780f459060867f11c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37177027"
---
# <a name="explore-data-sql-server-data-mining-add-ins"></a>Daten durchsuchen (SQL Server Data Mining-Add-Ins)
  ![Daten-Assistenten Durchsuchen](media/dmc-explore.gif "Durchsuchen von Daten-Assistenten")  
  
 Die **Stichprobenoptionen** Assistenten können Sie die Art und Menge der Daten in der Datentabelle zu verstehen. Der Assistent stellt die Verteilung und Werte für die ausgewählten Spalten spaltenweise grafisch dar. Anschließend können Sie die Gruppierung der Daten versuchsweise ändern oder das Diagramm, in dem der Inhalt angezeigt wird, zur Überprüfung in eine Excel-Arbeitsmappe kopieren.  
  
 Wenn Ihre Daten fortlaufende numerische Daten enthalten, können Sie zwischen den folgenden beiden Ansichten wechseln:  
  
-   **Liniendiagramm.** Dieses Diagramm Diagramme die Datenwerte auf der X-Achse und die Anzahl der Fälle auf der y-Achse.  
  
-   **Balkendiagramm.** Im Balkendiagramm werden die Werte nach der Anzahl von Fällen für jeden Wert gruppiert.  
  
 Wenn der Assistent Gruppen in den Daten findet, verwendet er die tatsächliche Verteilung der Datenwerte. Folglich werden im Balkendiagramm die numerischen Werte nicht in den typischen Ganzzahlunterteilungen auf den Achsen gruppiert (z. B. Zehner- oder Hundertergruppen). Stattdessen können die im Balkendiagramm angezeigten Bereiche durch Zahlen wie 43521-55603 (für die Einkommensspalte) angezeigt werden.  
  
 Wenn Sie die Daten in anderen Bereichen gruppieren möchten, sollten Sie diese Unterteilung in Excel vornehmen, bevor Sie die Daten analysieren. Oder Sie können die Daten neu bezeichnen, mit der [neu bezeichnen](relabel-sql-server-data-mining-add-ins.md) Assistenten.  
  
## <a name="using-the-explore-data-wizard"></a>Verwenden des Assistenten zum Durchsuchen von Daten  
  
1.  In der **Data Mining** des Menübands, klicken Sie auf **Stichprobenoptionen**.  
  
2.  In der **Quelle auswählen** Dialogfeld Feld, wählt die Tabelle oder einen Zellbereich, der die Daten enthalten.  
  
3.  In der **Spalte auswählen** Dialogfeld auf die Spalte zu analysieren, aus den Beispieldaten, die im Bereich angezeigt.  
  
4.  In der **Stichprobenoptionen** Dialogfeld auf die Diagrammtypen zum Anzeigen der Verteilung von Daten.  
  
5.  Sie können optional auch neue Spalten zu den Daten hinzufügen, die Segmentierung der Daten ändern oder das Diagramm in Excel kopieren.  
  
### <a name="requirements"></a>Anforderungen  
 Verwenden der **Stichprobenoptionen** -Assistenten muss Ihre Daten in einer Excel-Datentabelle.   
  
## <a name="see-also"></a>Siehe auch  
 [Prüfliste der Vorbereitung für Data Mining](checklist-of-preparation-for-data-mining.md)  
  
  
