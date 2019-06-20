---
title: Anzeigen von Kopf- und Fußzeilen einer Gruppe (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 8eb7d648-4df2-491a-96cb-99e55629d617
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7b330b5aedaeff4cf73ad6dca3e88860dde0f90b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66106059"
---
# <a name="display-headers-and-footers-with-a-group-report-builder-and-ssrs"></a>Anzeigen von Kopf- und Fußzeilen einer Gruppe (Berichts-Generator und SSRS)
  Sie können bestimmen, ob eine statische Zeile wie eine Gruppenkopfzeile oder -fußzeile mit dynamischen Zeilen gerendert werden soll, die mit einer Gruppe in einem Tablix-Datenbereich verknüpft sind.  
  
 Wenn Sie alle Spalten- oder Zeilenüberschriften auf mehreren Seiten wiederholen möchten, können Sie Eigenschaften für den Tablix-Datenbereich festlegen. Weitere Informationen finden Sie unter [Anzeigen von Zeilen- und Spaltenüberschriften auf mehreren Seiten &#40;Berichts-Generator und SSRS&#41;](display-row-and-column-headers-on-multiple-pages-report-builder-and-ssrs.md).  
  
 Sie müssen Eigenschaften für das Tablix-Element festlegen, um das Renderingverhalten für dynamische, mit geschachtelten Gruppen verknüpfte Zeilen und Spalten oder für statische, mit Beschriftungen oder Zwischensummen verknüpfte Zeilen und Spalten zu bestimmen. Ein Tablix-Element stellt eine statische oder dynamische Zeile oder Spalte dar. Ein statisches Element wird einmal wiederholt. Beispiel: Eine Zeile mit einer Gesamtsumme ist eine statische Zeile. Ein dynamisches Element wird für jede Gruppeninstanz einmal wiederholt. Eine Zeile, die mit einer Gruppe mit dem Gruppierungsausdruck [Region] verknüpft ist, wird einmal für jeden eindeutigen Wert für eine Region wiederholt. Weitere Informationen zu Tablix-Member finden Sie unter [Zellen, Zeilen und Spalten des Tablix-Datenbereichs (Berichts-Generator und SSRS)](tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md).  
  
 Sie können ein Tablix-Element im Gruppierungsbereich auswählen und die Eigenschaften **KeepWithGroup**, **KeepTogether**und **RepeatOnNewPage** im Eigenschaftenbereich festlegen. Verwenden Sie **KeepWithGroup** , um Gruppenköpfe und Fußzeilen auf der gleichen Seite wie die Gruppe anzuzeigen. Verwenden Sie **KeepTogether** , um statische Elemente mit den Zeilen oder Spalten einer Gruppe anzuzeigen. Verwenden Sie **RepeatOnNewPage** , um den Gruppenkopf oder die Fußzeile auf jeder Seite zu wiederholen, auf der mindestens eine vollständige Instanz des mit dem **KeepWithGroup** -Wert festgelegten Zeilengruppenelements angezeigt wird. **RepeatOnNewPage** wird für Spaltengruppenelemente nicht unterstützt.  
  
> [!NOTE]  
>  **KeepWithGroup**, **KeepTogether** und **RepeatOnNewPage** sind Eigenschaften von Gruppenmitgliedern, die im **Erweiterten Modus** des Bereichs „Gruppierung“ festgelegt werden können. Weitere Informationen finden Sie unter [Gruppierungsbereich (Berichts-Generator)](grouping-pane-report-builder.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-keep-a-static-row-with-a-set-of-dynamic-rows-associated-with-a-row-group"></a>So behalten Sie eine statische Zeile mit einer Gruppe von dynamischen Zeilen bei, die mit einer Zeilengruppe verknüpft sind  
  
1.  Klicken Sie auf der Entwurfsoberfläche auf eine beliebige Stelle im Tablix-Datenbereich, um diesen auszuwählen. Im Gruppierungsbereich werden die Zeilen- und Spaltengruppen für den Datenbereich angezeigt.  
  
2.  Klicken Sie auf der rechten Seite des Gruppierungsbereichs auf den Pfeil nach unten und anschließend auf **Erweiterter Modus**. Im Bereich Zeilengruppen werden die hierarchischen statischen und dynamischen Elemente für die Zeilengruppenhierarchie angezeigt.  
  
3.  Klicken Sie auf das statische Element, das der Zeilenkopf- oder -fußzeile entspricht, die Sie für die Gruppenzeilen beibehalten wollen. Im Eigenschaftenbereich werden die Eigenschaften für das **Tablix-Element** angezeigt.  
  
4.  Klicken Sie im Eigenschaftenbereich auf **KeepWithGroup**, und wählen Sie in der Dropdownliste einen der folgenden Werte aus:  
  
    -   **Keine** Wählen Sie diese Option aus, wenn Sie keine Einstellung bezüglich der Beibehaltung dieses Elements für die Elemente der ausgewählten Zeilengruppe festlegen möchten.  
  
    -   **Vor** Wählen Sie diese Option aus, um das Element für die Elemente der vorherigen Gruppe beizubehalten. Sie könnten diese Option für Gruppenfußzeilen verwenden.  
  
    -   **Nach** Wählen Sie diese Option aus, um das Element für die Elemente der folgenden Gruppe beizubehalten. Sie können diese Option für Gruppenkopfzeilen verwenden.  
  
5.  (Optional) Zeigen Sie eine Vorschau des Berichts an. Wenn möglich, wird dieses Element vom Berichtsrenderer mit den angegebenen Zeilengruppenelementen beibehalten.  
  
### <a name="to-keep-a-static-column-with-a-set-of-dynamic-columns-associated-with-a-column-group"></a>So behalten Sie eine statische Spalte mit einer Gruppe von dynamischen Spalten bei, die mit einer Spaltengruppe verknüpft sind  
  
1.  Klicken Sie auf der Entwurfsoberfläche auf eine beliebige Stelle im Tablix-Datenbereich, um diesen auszuwählen. Im Gruppierungsbereich werden die Zeilen- und Spaltengruppen für den Datenbereich angezeigt.  
  
2.  Klicken Sie auf der rechten Seite des Gruppierungsbereichs auf den Pfeil nach unten und anschließend auf **Erweiterter Modus**. Im Bereich Spaltengruppen werden die hierarchischen statischen und dynamischen Elemente für die Spaltengruppenhierarchie angezeigt.  
  
3.  Klicken Sie auf das statische Element, das der Spaltenkopf- oder -fußzeile entspricht, die Sie für die Gruppenspalten beibehalten wollen. Im Eigenschaftenbereich werden die Eigenschaften für das **Tablix-Element** angezeigt.  
  
4.  Klicken Sie im Eigenschaftenbereich auf **KeepWithGroup**, und wählen Sie in der Dropdownliste einen der folgenden Werte aus:  
  
    -   **Keine** Wählen Sie diese Option aus, wenn Sie keine Einstellung bezüglich der Beibehaltung dieses Elements für die Elemente der ausgewählten Spaltengruppe festlegen möchten.  
  
    -   **Vor** Wählen Sie diese Option aus, um das Element für die Elemente der vorherigen Gruppe beizubehalten. Sie können diese Option für Spaltenbezeichnungen verwenden, die vor den angegebenen Spaltengruppenelementen angezeigt werden.  
  
    -   **Nach** Wählen Sie diese Option aus, um das Element für die Elemente der folgenden Gruppe beizubehalten. Sie können diese Option für Spaltengesamtwerte verwenden, die nach den angegebenen Spaltengruppenelementen angezeigt werden.  
  
5.  (Optional) Zeigen Sie eine Vorschau des Berichts an. Wo es möglich ist, wird dieses Element vom Berichtsrenderer mit den angegebenen Spaltengruppenelementen beibehalten.  
  
## <a name="see-also"></a>Siehe auch  
 [Tablix-Zellen, Zeilen und Spalten &#40;Berichts-Generator&#41; und SSRS](tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md)   
 [Tablix-Datenbereichen &#40;Berichts-Generator und SSRS&#41;](tablix-data-region-areas-report-builder-and-ssrs.md)   
 [Tablix-Datenbereich &#40;Berichts-Generator und SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md)   
 [Tabellen (Berichts-Generator und SSRS)](tables-report-builder-and-ssrs.md)   
 [Matrizen (Berichts-Generator und SSRS)](create-a-matrix-report-builder-and-ssrs.md)   
 [Listen (Berichts-Generator und SSRS)](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)   
 [Tabellen, Matrizen und Listen &#40;Berichts-Generator und SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
