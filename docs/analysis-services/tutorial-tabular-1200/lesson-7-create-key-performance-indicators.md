---
title: 'Lektion 7: Erstellen von Key Performance Indicators | Microsoft-Dokumentation'
ms.date: 05/07/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 21767c239ed3498e0e593e221203b1cde3b7ae69
ms.sourcegitcommit: 54c8420b62269f6a9e648378b15127b5b5f979c1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2019
ms.locfileid: "65403872"
---
# <a name="lesson-7-create-key-performance-indicators"></a>Lektion 7: Erstellen von Leistungskennzahlen
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../../includes/ssas-appliesto-sql2016-later-aas.md)]

In dieser Lektion erstellen Sie Leistungskennzahlen (Key Performance Indicators, KPIs). KPIs dienen zum Messen der Leistung eines Werts, der durch ein *Basismeasure* definiert wird, anhand eines *Zielwerts* , der ebenfalls durch ein Measure oder durch einen absoluten Wert definiert wird. In Clientanwendungen zur Berichtserstellung erhalten Geschäftsleute mit KPIs einen schnellen und einfachen Einblick in den insgesamten Geschäftserfolg bzw. können Trends leichter identifizieren. Weitere Informationen finden Sie unter [KPIs](../tabular-models/kpis-ssas-tabular.md).  
  
Geschätzte Zeit zum Abschließen dieser Lektion: **15 Minuten**  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
Dieses Thema ist Teil eines Lernprogramms zur Tabellenmodellierung, das in der entsprechenden Reihenfolge bearbeitet werden sollte. Bevor Sie die Aufgaben in dieser Lektion ausführen, sollten Sie die vorherige Lektion abgeschlossen haben: [Lektion 6: Erstellen von Measures](lesson-6-create-measures.md).   
  
## <a name="create-key-performance-indicators"></a>Erstellen von Leistungskennzahlen  
  
#### <a name="to-create-an-internetcurrentquartersalesperformance-kpi"></a>So erstellen Sie eine InternetCurrentQuarterSalesPerformance-KPI  
  
1.  Klicken Sie im Modell-Designer auf die **"factinternetsales"** Tabelle (Registerkarte).  
  
2.  Klicken Sie im Measureraster auf eine leere Zelle.  
  
3.  Geben Sie in der Bearbeitungsleiste über der Tabelle die folgende Formel ein: 
 
    ```  
    InternetCurrentQuarterSalesPerformance :=IFERROR([InternetCurrentQuarterSales]/[InternetPreviousQuarterSalesProportionToQTD],BLANK())  
    ```

    Dieses Measure dient als Basismeasure für den KPI.  
  
4.  Mit der rechten Maustaste **InternetCurrentQuarterSalesPerformance** > **KPI erstellen**.   
  
5.  Klicken Sie im Dialogfeld Key Performance Indicator (KPI) in **Ziel** wählen **Absolutwert**, und geben Sie dann **1.1**.  
  
7.  Geben Sie im linken (unteren) Schiebereglerfeld den Wert **1**und anschließend im rechten (oberen) Schiebereglerfeld **1,07**ein.  
  
8.  Wählen Sie unter **Symbolart auswählen**den Symboltyp Diamant (rot), Dreieck (gelb) oder Kreis (grün) aus.
  
    ![as-tabular-lesson7-kpi](media/as-tabular-lesson7-kpi.png)
    
    > [!TIP]  
    > Beachten Sie die erweiterbare **Beschreibungen** Bezeichnung unterhalb der verfügbaren symbolarten. Verwenden Sie diese Beschreibungen für die verschiedenen KPI-Elemente in Clientanwendungen leichter eingeben.  
  
9. Klicken Sie auf **OK** , um den KPI abzuschließen.  
  
    Beachten Sie im measureraster das Symbol neben dem **InternetCurrentQuarterSalesPerformance** Measure. Dieses Symbol gibt an, dass das Measure als Basiswert für einen KPI dient.  
  
#### <a name="to-create-an-internetcurrentquartermarginperformance-kpi"></a>So erstellen Sie eine InternetCurrentQuarterMarginPerformance-KPI  
  
1.  Das measureraster für die **"factinternetsales"** Tabelle, klicken Sie auf eine leere Zelle.  
  
2.  Geben Sie in der Bearbeitungsleiste über der Tabelle die folgende Formel ein:  

    ```
    InternetCurrentQuarterMarginPerformance :=IF([InternetPreviousQuarterMarginProportionToQTD]<>0,([InternetCurrentQuarterMargin]-[InternetPreviousQuarterMarginProportionToQTD])/[InternetPreviousQuarterMarginProportionToQTD],BLANK())  
    ```
 
3.  Mit der rechten Maustaste **"internetcurrentquartermarginperformance"** > **KPI erstellen**.  
  
4.  Klicken Sie im Dialogfeld Key Performance Indicator (KPI) in **Ziel** wählen **Absolutwert**, und geben Sie dann **1,25**.   
  
5.  Verschieben Sie unter **Statusschwellenwerte definieren**den linken (unteren) Schieberegler, bis im Feld der Wert **0,8**angezeigt wird. Verschieben Sie anschließend den rechten (oberen) Schieberegler, bis im Feld **1,03**angezeigt wird.  
  
6.  Wählen Sie unter **Symbolart auswählen**den Symboltyp Diamant (rot), Dreieck (gelb) oder Kreis (grün) aus. Klicken Sie anschließend auf **OK**.  
  
## <a name="whats-next"></a>Wie geht es weiter?
Wechseln Sie zur nächsten Lektion: [Lektion 8: Erstellen von Perspektiven](lesson-8-create-perspectives.md).
  
  
