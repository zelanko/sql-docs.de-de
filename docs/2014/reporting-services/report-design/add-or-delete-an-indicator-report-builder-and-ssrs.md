---
title: Hinzufügen oder Löschen eines Indikators (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a8b1aac1-53ef-47a4-afc0-8fa866c6c480
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 763d39ef4804a986fb190c3b5e9d8039a827bd63
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66106578"
---
# <a name="add-or-delete-an-indicator-report-builder-and-ssrs"></a>Hinzufügen oder Löschen eines Indikators (Berichts-Generator und SSRS)
  Indikatoren sind minimale Messgeräte, die den Zustand eines einzelnen Datenwerts auf einen Blick wiedergeben. Weitere Informationen dazu finden Sie unter [Indikatoren &#40;Berichts-Generator und SSRS&#41;](indicators-report-builder-and-ssrs.md).  
  
 Indikatoren werden im Allgemeinen in einer Tabelle oder einer Matrix in Zellen eingefügt, aber Sie können Indikatoren auch parallel mit Messgeräten, eingebettet in Messgeräte oder eigenständig verwenden.  
  
 Beim ersten Hinzufügen eines Indikators wird er standardmäßig so konfiguriert, dass Prozentsätze als Maßeinheiten verwendet werden. Die Prozentbereiche sind gleichmäßig über die Elemente des Indikatorsatzes verteilt, und der vom Indikator angezeigte Wertebereich entspricht dem übergeordneten Element des Indikators, z. B. einer Tabelle oder Matrix.  
  
 Sie können die Werte und die Status von Indikatoren aktualisieren. Weitere Informationen finden Sie in den folgenden Themen:  
  
-   [Ändern von Indikator Symbolen und Indikator Sätzen &#40;Berichts-Generator und SSRS&#41;](change-indicator-icons-and-indicator-sets-report-builder-and-ssrs.md)  
  
-   [Festlegen und Konfigurieren von Maßeinheiten &#40;Berichts-Generator und SSRS&#41;](set-and-configure-measurement-units-report-builder-and-ssrs.md)  
  
-   [Festlegen des Synchronisierungs Bereichs &#40;Berichts-Generator und SSRS&#41;](set-synchronization-scope-report-builder-and-ssrs.md)  
  
 Da ein Indikator im Messgerätebereich positioniert wird, müssen Sie den Indikator statt des Bereichs auswählen, wenn Sie den Indikator mit dem Dialogfeld **Indikatoreigenschaften** oder dem Bereich **Eigenschaften** konfigurieren möchten. Die folgende Abbildung enthält einen ausgewählten Indikator in dessen Messgerätbereich.  
  
 ![rs_GaugePanelWithIndicator](../media/rs-gaugepanelwithindicator.gif "rs_GaugePanelWithIndicator")  
  
> [!NOTE]  
>  Abhängig von der Spaltenbreite und Länge der Datenwerte kann der Text in Tabellen- oder Matrixzellen umbrochen und in mehreren Zeilen angezeigt werden. In diesem Fall kann das Indikatorsymbol gestreckt und in der Form verändert werden, wodurch u. U. seine Lesbarkeit beeinträchtigt wird. Platzieren Sie den Indikator in einem Rechteck, um sicherzustellen, dass das Symbol nicht verzerrt wird.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-an-indicator-to-a-table-or-matrix"></a>So fügen Sie einer Tabelle oder einer Matrix einen Indikator hinzu  
  
1.  Öffnen Sie einen vorhandenen Bericht, oder erstellen Sie einen neuen Bericht, der eine Tabelle und eine Matrix mit den anzuzeigenden Daten enthält. Weitere Informationen finden Sie unter [Tabellen &#40;Berichts-Generator und SSRS&#41;](tables-report-builder-and-ssrs.md) oder [Matrizen &#40;Berichts-Generator und SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md).  
  
2.  Fügen Sie eine Spalte in die Tabelle oder Matrix ein. Weitere Informationen finden Sie unter [Einfügen oder Löschen einer Spalte (Berichts-Generator und SSRS)](insert-or-delete-a-column-report-builder-and-ssrs.md).  
  
3.  Klicken Sie optional auf der Registerkarte **Einfügen** auf **Rechteck**, und klicken Sie dann in der neuen Spalte auf eine Zelle.  
  
4.  Klicken Sie auf der Registerkarte **Einfügen** auf **Indikator**, und klicken Sie dann in der neuen Spalte auf eine Zelle.  
  
     Falls Sie einer Zelle ein Rechteck hinzugefügt haben, klicken Sie auf diese Zelle.  
  
5.  Klicken Sie im linken Bereich des Dialogfelds **Indikatorart auswählen** auf den gewünschten Indikatortyp und dann auf den Indikatorsatz.  
  
6.  Klicken Sie auf **OK**.  
  
7.  Klicken Sie auf den Indikator. Der Bereich **Messgerätdaten** wird geöffnet.  
  
8.  Klicken Sie im Bereich **Werte** in der Dropdownliste **(Keine Angabe)** auf das Feld, dessen Werte Sie als Indikator anzeigen lassen möchten.  
  
     Der Indikator ist so konfiguriert, dass Standardwerte verwendet werden. Standardmäßig sind Indikatoren so konfiguriert, dass Prozentsätze als Maßeinheiten verwendet werden, und die Prozentbereiche werden über die Elemente des Indikators gleichmäßig verteilt. Der vom Indikator gelieferte Wert verwendet den Bereich der nächsten Gruppe.  
  
### <a name="to-delete-an-indicator-to-a-table-or-matrix"></a>So löschen Sie einen Indikator für eine Tabelle oder eine Matrix  
  
1.  Klicken Sie mit der rechten Maustaste auf den Indikator, und klicken Sie dann auf **Löschen**.  
  
    > [!NOTE]  
    >  Ein Indikator kann in einem Messgerätbereich positioniert sein, der andere Indikatoren oder Messgeräte enthält. Wenn die Messgerätbereiche mehrere Elemente enthalten, stellen Sie sicher, dass Sie zum Löschen auf den Indikator klicken und nicht auf den Messgerätbereich. Wenn Sie klicken und den Messgerätbereich entfernen, werden die Messgerätbereiche und alle Elemente darin gelöscht.  
  
2.  Klicken Sie auf **Löschen**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Indikatoren &#40;Berichts-Generator und SSRS&#41;](indicators-report-builder-and-ssrs.md)  
  
  
