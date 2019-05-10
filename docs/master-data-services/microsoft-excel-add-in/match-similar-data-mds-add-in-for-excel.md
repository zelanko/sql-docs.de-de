---
title: Abgleichen ähnlicher Daten (MDS-Add-In für Excel) | Microsoft-Dokumentation
ms.custom: microsoft-excel-add-in
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: f6fd6fc1-3569-42a5-b6cb-87a921c88f3b
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 0e4861ad317b71fd646ee8f6f91e73494bee9264
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/09/2019
ms.locfileid: "65476975"
---
# <a name="match-similar-data-mds-add-in-for-excel"></a>Abgleichen ähnlicher Daten (MDS-Add-In für Excel)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Verwenden Sie in [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]die Data Quality Services-Funktion (DQS), um in den Daten nach Ähnlichkeiten zu suchen.  
  
 So führen Sie diese Prozedur aus  
  
-   Verwenden Sie die standardmäßige Data Quality Services-Wissensdatenbank, oder  
  
-   Erstellen Sie eine eigene benutzerdefinierte DQS-Wissensdatenbank und Abgleichrichtlinie. Weitere Informationen finden Sie unter [Create a Matching Policy](../../data-quality-services/create-a-matching-policy.md).  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
  
-   Sie müssen über ein Arbeitsblatt mit von MDS verwalteten Daten verfügen. Weitere Informationen finden Sie unter [Export Data to Excel from Master Data Services](../../master-data-services/microsoft-excel-add-in/export-data-to-excel-from-master-data-services.md)(Exportieren von Daten nach Excel aus Master Data Services).  
  
-   Optional. Sie können andere Daten vor dem Überprüfen auf Ähnlichkeiten mit den von MDS verwalteten Daten kombinieren. Weitere Informationen finden Sie unter [Kombinieren von Daten &#40;MDS-Add-In für Excel&#41;](../../master-data-services/microsoft-excel-add-in/combine-data-mds-add-in-for-excel.md).  
  
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
  
-   Zeigen Sie weitere Informationen an, um zu ermitteln, welche Daten ähnlich sind. Weitere Informationen finden Sie unter [Spalten für Data Quality-Abgleich &#40;MDS-Add-In für Excel&#41;](../../master-data-services/microsoft-excel-add-in/data-quality-matching-columns-mds-add-in-for-excel.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Data Quality-Abgleich im MDS-Add-In für Excel](../../master-data-services/microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md)   
 [Datenabgleich](../../data-quality-services/data-matching.md)  
  
  
