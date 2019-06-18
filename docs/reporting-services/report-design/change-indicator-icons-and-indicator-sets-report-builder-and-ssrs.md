---
title: Ändern von Indikatorsymbolen und Indikatorsätzen (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 8a056adf-4473-473d-9b0c-314675af7bfd
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: a73198264f13725b7c7050b5344c2af3df4ada8f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65581718"
---
# <a name="change-indicator-icons-and-indicator-sets-report-builder-and-ssrs"></a>Ändern von Indikatorsymbolen und Indikatorsätzen (Berichts-Generator und SSRS)
  Möglicherweise stellen die vorkonfigurierten Indikatorsätze, die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] für paginierte Berichte bereitstellt, die Daten nicht immer effektiv dar und können im übermittelten Bericht nicht optimal verwendet werden. Dieses Thema enthält Vorgehensweisen, um die Darstellung von Indikatorsymbolen zu ändern und die Indikatorsätze anzupassen, sodass andere, mehr oder weniger Indikatorsymbole enthalten sind.  
  
 Optionen wie Farben können mit Ausdrücken festgelegt werden. Weitere Informationen finden Sie unter [Ausdrücke &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md).  
  
## <a name="to-change-the-color-of-an-indicator-icon"></a>So ändern Sie die Farbe eines Indikatorsymbols  
  
1.  Klicken Sie mit der rechten Maustaste auf den Indikator, der geändert werden soll, und klicken Sie auf **Indikatoreigenschaften**.  
  
2.  Klicken Sie im linken Bereich auf **Wert und Status** .  
  
3.  Klicken Sie in der Spalte **Farbe** neben dem Symbol, das geändert werden soll, auf den Nach-unten-Pfeil, und wählen Sie dann die gewünschte Farbe, **Keine Farbe**oder **Weitere Farben**.  
  
     Klicken Sie optional auf die Schaltfläche **Ausdruck** (*fx*), um einen Ausdruck zu bearbeiten, mit dem der Wert der Option **Farbe** festgelegt wird.  
  
     Wenn Sie auf **Weitere Farben**geklickt haben, wird das Dialogfeld **Farbe auswählen** geöffnet, in dem Sie zwischen vielen verschiedenen Farben auswählen können. Weitere Informationen zu den zugehörigen Optionen finden Sie unter [Farbe auswählen (Dialogfeld) (Berichts-Generator und SSRS)](https://msdn.microsoft.com/library/ac7089a3-5c7b-4f53-8348-180610e86da2). Klicken Sie auf **OK** , um das Dialogfeld **Farbe auswählen** zu schließen.  
  
4.  Klicken Sie auf **OK**.  
  
## <a name="to-change-the-icon"></a>So ändern Sie das Symbol  
  
1.  Klicken Sie mit der rechten Maustaste auf den Indikator, der geändert werden soll, und klicken Sie auf **Indikatoreigenschaften**.  
  
2.  Klicken Sie im linken Bereich auf **Wert und Status** .  
  
3.  Klicken Sie auf den Nach-unten-Pfeil neben dem Symbol, das Sie ändern möchten, und wählen Sie ein anderes Symbol aus.  
  
     Klicken Sie optional auf die Schaltfläche **Ausdruck** (*fx*), um einen Ausdruck zu bearbeiten, der den Wert der Option **Symbol** festlegt.  
  
4.  Klicken Sie auf **OK**.  
  
## <a name="to-use-a-custom-image-as-an-indicator-icon"></a>So verwenden Sie ein benutzerdefiniertes Bild als Indikatorsymbol  
  
1.  Klicken Sie mit der rechten Maustaste auf den Indikator, der geändert werden soll, und klicken Sie auf **Indikatoreigenschaften**.  
  
2.  Klicken Sie im linken Bereich auf **Wert und Status** .  
  
3.  Klicken Sie auf den Nach-unten-Pfeil neben dem Symbol, das Sie ändern möchten, und wählen Sie **Bild**aus.  
  
4.  Klicken Sie in der Liste **Bildquelle auswählen** auf **Extern**, **Eingebettet**oder **Datenbank**.  
  
5.  Führen Sie abhängig von der Bildquelle eine der folgenden Aktionen aus:  
  
    -   Wenn Sie ein Bild verwenden, das außerhalb des Berichts gespeichert ist, klicken Sie auf **Durchsuchen** , und navigieren Sie zu dem Bild. Der Bericht enthält einen Verweis auf das Bild.  
  
    -   Wenn Sie ein Bild verwenden möchten, das in den Bericht eingebettet ist, klicken Sie auf **Importieren** , und navigieren Sie zu dem Bild. Das Bild wird der Berichtsdefinition hinzugefügt und zusammen damit gespeichert.  
  
    -   Wenn Sie ein Bild verwenden möchten, das sich in einer Datenbank in der Liste **Dieses Feld verwenden** befindet, wählen Sie das Feld aus der Liste aus. Wählen Sie danach in der Liste **Diesen MIME-Typ verwenden** den MIME-Typ des Bilds aus.  
  
6.  Klicken Sie auf **OK**.  
  
## <a name="to-add-an-icon-to-the-indicator-set"></a>So fügen Sie dem Indikatorsatz ein Symbol hinzu  
  
1.  Klicken Sie mit der rechten Maustaste auf den Indikator, der geändert werden soll, und klicken Sie auf **Indikatoreigenschaften**.  
  
2.  Klicken Sie im linken Bereich auf **Wert und Status** .  
  
3.  Klicken Sie auf **Hinzufügen**. Ein Indikator wird mithilfe des Standardsymbols und der Option **Keine Farbe** hinzugefügt.  
  
     Konfigurieren Sie den indictor, um das gewünschte Symbol und die gewünschte Farbe zu verwenden. In den Vorgehensweisen weiter oben in diesem Thema werden die entsprechenden Schritte erläutert.  
  
4.  Klicken Sie auf **OK**.  
  
## <a name="to-delete-an-icon-to-the-indicator-set"></a>So löschen Sie ein Symbol im Indikatorsatz  
  
1.  Klicken Sie mit der rechten Maustaste auf den Indikator, der geändert werden soll, und klicken Sie auf **Indikatoreigenschaften**.  
  
2.  Klicken Sie im linken Bereich auf **Wert und Status** .  
  
3.  Wählen Sie den Indikator aus, der gelöscht werden soll, und klicken Sie dann auf **Löschen**.  
  
4.  Klicken Sie auf **OK**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Indikatoren &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-design/indicators-report-builder-and-ssrs.md)  
  
  
