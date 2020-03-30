---
title: Hinzufügen eines Gesamtergebnisses zu einer Gruppe oder einem Tablix (Berichts-Generator und SSRS) | Microsoft-Dokumentation
description: In einem paginierten SQL Server Reporting Services-Bericht können Sie Gesamtergebnisse in einem Tablix-Datenbereich für eine Gruppe oder für den gesamten Datenbereich hinzufügen.
ms.date: 12/16/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: cf1b96c3-7f0f-4c94-ad08-5239c77ccfe4
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 8ad10f1ee83c4024b45c6d77572d0b935ff92dd5
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "75242528"
---
# <a name="add-a-total-to-a-group-or-tablix-data-region-report-builder-and-ssrs"></a>Hinzufügen eines Gesamtergebnisses zu einer Gruppe oder einem Tablix-Datenbereich (Berichts-Generator und SSRS)
 In einem paginierten [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] -Bericht können Sie Ergebnisse in einem Tablix-Datenbereich für eine Gruppe oder für den gesamten Datenbereich hinzufügen. Standardmäßig ist ein Ergebnis die Summe der numerischen Daten, die nicht NULL sind, in einer Gruppe oder einem Datenbereich nach Anwendung der Filter. Zum Hinzufügen von Ergebnissen für eine Gruppe klicken Sie im Gruppierungsbereich im Kontextmenü für die Gruppe auf **Gesamtergebnis hinzufügen** . Zum Hinzufügen von Ergebnissen für eine einzelne Zelle im Tablix-Textbereich klicken Sie im Kontextmenü für die Zelle auf **Gesamtergebnis hinzufügen** . Der Befehl **Gesamtergebnis hinzufügen** ist kontextbezogen und ist nur bei numerischen Feldern aktiviert. In Abhängigkeit von der ausgewählten Tablix-Zelle können Sie ein Ergebnis für eine einzelne Zelle hinzufügen, indem Sie eine Zelle im Tablix-Textbereich auswählen, oder für die gesamte Gruppe, indem Sie eine Zelle im Tablix-Zeilengruppen- oder -spaltenbereich auswählen. Weitere Informationen zu Tablix-Bereichen finden Sie unter [Tablix-Datenbereich &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/tablix-data-region-report-builder-and-ssrs.md).  
  
 Nach dem Hinzufügen einer Summe können Sie die Sum-Standardfunktion in eine andere Aggregatfunktion aus der Liste der integrierten Berichtsfunktionen ändern. Weitere Informationen finden Sie unter [Aggregatfunktionsreferenz &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/report-builder-functions-aggregate-functions-reference.md). [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="to-add-a-total-for-an-individual-value-in-the-tablix-body-area"></a>So fügen Sie ein Ergebnis für einen einzelnen Wert im Tablix-Textbereich hinzu  
  
-   Klicken Sie im Tablix-Datentextbereich mit der rechten Maustaste auf die Zelle, der Sie das Ergebnis hinzufügen möchten. Die Zelle muss ein numerisches Feld enthalten. Zeigen Sie auf **Gesamtergebnis hinzufügen**, und klicken Sie dann auf **Zeile** oder auf **Spalte**.  
  
     Dem Datenbereich wird außerhalb der aktuellen Gruppe eine neue Zeile oder Spalte hinzugefügt, die das Standardergebnis für das Feld in der Zelle enthält, auf die Sie geklickt haben.  
  
     Wenn der Tablix-Datenbereich eine Tabelle ist, wird eine Zeile automatisch hinzugefügt.  
  
## <a name="to-add-totals-for-a-row-group"></a>So fügen Sie Ergebnisse für eine Zeilengruppe hinzu  
  
-   Klicken Sie im Zeilengruppenbereich des Tablix-Datenbereichs mit der rechten Maustaste auf eine Zelle in dem Zeilengruppenbereich, dem Sie Ergebnisse hinzufügen möchten, zeigen Sie auf **Gesamtergebnis hinzufügen**, und klicken Sie dann auf **Vor** oder **Nach**.  
  
     Dem Datenbereich wird außerhalb der aktuellen Gruppe eine neue Zeile hinzugefügt, und für jedes numerische Feld in der Zeile wird dann ein Standardergebnis hinzugefügt.  
  
## <a name="to-add-totals-for-a-column-group"></a>So fügen Sie Ergebnisse für eine Spaltengruppe hinzu  
  
-   Klicken Sie im Zeilengruppenbereich des Tablix-Datenbereichs mit der rechten Maustaste auf eine Zelle in dem Spaltengruppenbereich, dem Sie Ergebnisse hinzufügen möchten, zeigen Sie auf **Gesamtergebnis hinzufügen**, und klicken Sie dann auf **Vor** oder **Nach**.  
  
     Dem Datenbereich wird außerhalb der aktuellen Gruppe eine neue Spalte hinzugefügt, und für jedes numerische Feld in der Spalte wird dann ein Standardergebnis hinzugefügt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausdrucksbereich für Gesamtwerte, Aggregate und integrierte Sammlungen &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md)   
 [Tablix-Datenbereich &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/tablix-data-region-report-builder-and-ssrs.md)   
 [Tabellen, Matrizen und Listen &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
