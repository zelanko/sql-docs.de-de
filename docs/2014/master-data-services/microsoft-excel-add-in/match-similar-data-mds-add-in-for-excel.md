---
title: Abgleichen ähnlicher Daten (MDS-Add-In für Excel) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- master-data-services
ms.topic: conceptual
ms.assetid: f6fd6fc1-3569-42a5-b6cb-87a921c88f3b
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 70ec67afde5651054078223d4286b8b6a3efcc2b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48158680"
---
# <a name="match-similar-data-mds-add-in-for-excel"></a>Abgleichen ähnlicher Daten (MDS-Add-In für Excel)
  Verwenden Sie in [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]die Data Quality Services-Funktion (DQS), um in den Daten nach Ähnlichkeiten zu suchen.  
  
 So führen Sie diese Prozedur aus  
  
-   Verwenden Sie die standardmäßige Data Quality Services-Wissensdatenbank, oder  
  
-   Erstellen Sie eine eigene benutzerdefinierte DQS-Wissensdatenbank und Abgleichrichtlinie. Weitere Informationen finden Sie unter [Create a Matching Policy](../../data-quality-services/create-a-matching-policy.md).  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
  
-   Sie müssen über ein Arbeitsblatt mit von MDS verwalteten Daten verfügen. Weitere Informationen finden Sie unter [Laden von Daten aus MDS in Excel](export-data-to-excel-from-master-data-services.md).  
  
-   Optional. Sie können andere Daten vor dem Überprüfen auf Ähnlichkeiten mit den von MDS verwalteten Daten kombinieren. Weitere Informationen finden Sie unter [Kombinieren von Daten &#40;MDS-Add-In für Excel&#41;](combine-data-mds-add-in-for-excel.md).  
  
### <a name="to-find-similarities-by-using-the-default-knowledge-base"></a>So suchen Sie mithilfe der Standard-Wissensdatenbank nach Ähnlichkeiten  
  
1.  Klicken Sie im Arbeitsblatt mit den von MDS verwalteten Daten in der Gruppe **Data Quality** auf **Daten abgleichen**.  
  
2.  Wählen Sie im Dialogfeld **Daten abgleichen** in der Liste **DQS-Wissensdatenbank** die Option **DQS-Daten (Standard)** aus.  
  
3.  Für jede Spalte, die abzugleichende Daten enthält, fügen Sie eine Zeile im Dialogfeld hinzu. Informationen zu den Feldern in diesem Dialogfeld finden Sie unter [How to Set Matching Rule Parameters](../../data-quality-services/create-a-matching-policy.md#MatchingRules).  
  
4.  Klicken Sie auf **OK**, wenn die Summe aller Gewichtungswerte 100 Prozent beträgt.  
  
### <a name="to-find-similarities-by-using-a-custom-knowledge-base"></a>So suchen Sie mithilfe einer benutzerdefinierten Wissensdatenbank nach Ähnlichkeiten  
  
1.  Klicken Sie im Arbeitsblatt mit den von MDS verwalteten Daten in der Gruppe **Data Quality** auf **Daten abgleichen**.  
  
2.  Wählen Sie in der Liste **DQS-Wissensdatenbank** den Namen der benutzerdefinierten Wissensdatenbank aus.  
  
3.  Wählen Sie für jede Spalte im Arbeitsblatt eine DQS-Domäne aus.  
  
4.  Klicken Sie auf **OK**, nachdem alle DQS-Domänen Spalten im Arbeitsblatt zugeordnet wurden.  
  
## <a name="next-steps"></a>Nächste Schritte  
  
-   Zeigen Sie weitere Informationen an, um zu ermitteln, welche Daten ähnlich sind. Weitere Informationen finden Sie unter [Spalten für Data Quality-Abgleich &#40;MDS-Add-In für Excel&#41;](data-quality-matching-columns-mds-add-in-for-excel.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Data Quality-Abgleich im MDS-Add-in für Excel](data-quality-matching-in-the-mds-add-in-for-excel.md)   
 [Datenabgleich](../../data-quality-services/data-matching.md)  
  
  
