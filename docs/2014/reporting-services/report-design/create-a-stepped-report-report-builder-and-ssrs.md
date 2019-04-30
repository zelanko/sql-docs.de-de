---
title: Erstellen von abgestuften Berichten (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 5933c4f0-c713-4ecb-b521-ff46c9c63fff
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f2e83f23870d355394241550ffab24838a6b43f1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63206440"
---
# <a name="create-a-stepped-report-report-builder-and-ssrs"></a>Erstellen von abgestuften Berichten (Berichts-Generator und SSRS)
  Ein abgestufter Bericht zeigt Detailzeilen oder Untergruppen wie im folgenden Beispiel unter einer übergeordneten Gruppe eingerückt in der gleichen Spalte an.  
  
 ![Gerenderter abgestufter Bericht](../media/steppedreportrendered.gif "Rendered stepped report")  
  
 Bei herkömmlichen Tabellenberichten wird die übergeordnete Gruppe in einer angrenzenden Spalte im Bericht platziert. Der neue Tablix-Datenbereich ermöglicht es Ihnen, eine Gruppe und Detailzeilen bzw. Untergruppen zur gleichen Spalte hinzuzufügen. Um die Gruppenzeilen von den Detailzeilen oder Zeilen untergeordneter Gruppen zu unterscheiden, können Sie entweder eine Formatierung wie eine Schriftfarbe anwenden oder die Detailzeilen mit einem Einzug versehen.  
  
 Die Verfahren in diesem Thema veranschaulichen das manuelle Erstellen eines abgestuften Berichts. Sie können jedoch auch den Assistenten zum Erstellen neuer Tabellen und Matrizen verwenden. Der Assistent stellt das Layout für abgestufte Berichte bereit und erleichtert die Berichterstellung. Nachdem Sie den Assistenten abgeschlossen haben, können Sie den Bericht optimieren.  
  
> [!NOTE]  
>  Der Assistent ist nur in Berichts-Generator verfügbar.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-create-a-stepped-report"></a>So erstellen Sie einen abgestuften Bericht  
  
1.  Erstellen Sie einen Tabellenbericht. Fügen Sie z. B. einen Tablix-Datenbereich ein, und fügen Sie der Datenzeile Felder hinzu.  
  
2.  Fügen Sie dem Bericht eine übergeordnete Gruppe hinzu.  
  
    1.  Klicken Sie in der Tabelle an einer beliebigen Stelle, um sie auszuwählen. Im Gruppierungsbereich wird die Gruppe Details im Bereich Zeilengruppen angezeigt.  
  
    2.  Klicken Sie im Gruppierungsbereich mit der rechten Maustaste auf die Gruppe „Details“, zeigen Sie auf **Gruppe hinzufügen**, und klicken Sie dann auf **Übergeordnete Gruppe**.  
  
    3.  Geben Sie im Dialogfeld **Tablix-Gruppe** einen Namen für die Gruppe an, und wählen Sie in der Dropdownliste einen Gruppierungsausdruck aus, bzw. geben Sie manuell einen Ausdruck ein. Die Dropdownliste zeigt die einfachen Feldausdrücke an, die im Berichtsdatenbereich verfügbar sind. Zum Beispiel ist [PLZ] ein einfacher Feldausdruck für das Feld PLZ in einem Dataset.  
  
    4.  Wählen Sie **Gruppenkopf hinzufügen**. Hierdurch wird eine statische Zeile für Gruppenbezeichnung und Gruppengesamtwerte über der Gruppe eingefügt. Ebenso können Sie **Gruppenfuß hinzufügen** auswählen, um unter der Gruppe eine statische Zeile hinzuzufügen. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
     Sie haben jetzt einen grundlegenden Tabellenbericht. Beim Rendern werden eine Spalte mit dem Gruppeninstanzwert und eine oder mehrere weitere Spalten mit gruppierten Detaildaten angezeigt. Die folgende Abbildung zeigt, wie der Datenbereich auf der Entwurfsoberfläche aussehen könnte.  
  
     ![Tabellendatenbereich mit Gruppe](../media/tabledataregionwithgroup.gif "Table data region with group")  
  
     Die folgende Abbildung zeigt, wie der gerenderte Datenbereich beim Anzeigen des Berichts aussehen könnte.  
  
     ![Gerenderter gruppierter Bericht](../media/tablereportrendered.gif "Rendered grouped report")  
  
3.  Für einen abgestuften Bericht benötigen Sie die erste Spalte, die die Gruppeninstanz enthält, nicht. Kopieren Sie stattdessen den Wert in der Gruppenkopfzelle, löschen Sie die Gruppenspalte, und fügen Sie den Wert in das erste Textfeld in der Gruppenkopfzeile ein. Um die Gruppenspalte zu entfernen, klicken Sie mit der rechten Maustaste auf die Gruppenspalte oder die Zelle, und klicken Sie auf **Spalten löschen**. Die folgende Abbildung zeigt, wie der Datenbereich auf der Entwurfsoberfläche aussehen könnte.  
  
     ![Datenbereich mit Gruppenkopfzeile](../media/tabledataregiongroupheader.gif "Data region with group header row")  
  
4.  Ändern Sie die Auffüllung der Detaildatenzelle, um die Detailzeilen unter der Gruppenkopfzeile in der gleichen Spalte einzurücken.  
  
    1.  Wählen Sie die Zelle mit dem Detailfeld aus, das Sie einrücken möchten. Die Eigenschaften für das Textfeld dieser Zelle werden im Eigenschaftenbereich angezeigt.  
  
    2.  Erweitern Sie im Eigenschaftenbereich unter **Ausrichtung**die Eigenschaften für **Auffüllung**.  
  
    3.  Für **Links**, geben Sie einen neuen auffüllungswert ein, z. B. `.5in`. Durch die Auffüllung wird der Text in der Zelle um den angegebenen Wert eingerückt. Die Standardauffüllung ist 2 Punkt. Gültige Werte für die Auffüllungseigenschaften sind Zahlen über null (0) gefolgt von einem Größenkennzeichner.  
  
         Die folgenden Größenkennzeichner sind verfügbar:  
  
        |||  
        |-|-|  
        |`in`|Zoll (1 Zoll = 2,54 Zentimeter)|  
        |`cm`|Zentimeter|  
        |`mm`|Millimeter|  
        |`pt`|Punkte (1 Punkt = 1/72 Zoll)|  
        |`pc`|Picas (1 Pica = 12 Punkte)|  
  
     Ihr Datenbereich sollte dem folgenden Beispiel ähneln.  
  
     ![Datenbereich für abgestuften Bericht](../media/steppedreportdataregion.gif "Data region for stepped report")  
  
     **Datenbereich für abgestuftes Berichtslayout**  
  
     Klicken Sie auf der Registerkarte **Home** auf **Ausführen**. Der Bericht zeigt die Gruppe mit eingezogenen Ebenen für die Untergruppenwerte an.  
  
### <a name="to-create-a-stepped-report-with-multiple-groups"></a>So erstellen Sie einen abgestuften Bericht mit mehreren Gruppen  
  
1.  Erstellen Sie einen Bericht wie in der vorherigen Vorgehensweise beschrieben.  
  
2.  Fügen Sie zusätzliche Gruppen zum Bericht hinzu.  
  
    1.  Klicken Sie im Bereich Zeilengruppen mit der rechten Maustaste auf die Gruppe, klicken Sie auf **Gruppe hinzufügen**, und wählen Sie dann den Gruppentyp aus, den Sie hinzufügen möchten.  
  
        > [!NOTE]  
        >  Es gibt mehrere Möglichkeiten, einem Datenbereich Gruppen hinzuzufügen. Weitere Informationen finden Sie unter [Hinzufügen oder Löschen einer Gruppe in einem Datenbereich &#40;Berichts-Generator und SSRS&#41;](add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md).  
  
    2.  Geben Sie im Dialogfeld **Tablix-Gruppe** einen Namen ein.  
  
    3.  Geben Sie in **Gruppierungsausdruck**einen Ausdruck ein, oder wählen Sie ein Datasetfeld aus, nach dem gruppiert wird. Zum Erstellen eines Ausdrucks klicken Sie auf die Ausdrucksschaltfläche (**fx**), um das Dialogfeld **Ausdruck** zu öffnen.  
  
    4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
3.  Ändern Sie die Auffüllung für die Zelle, die die Gruppendaten enthält.  
  
## <a name="see-also"></a>Siehe auch  
 [Seitenkopf- und Seitenfußzeilen &#40;Berichts-Generator und SSRS&#41;](page-headers-and-footers-report-builder-and-ssrs.md)   
 [Formatieren von Berichtselementen &#40;Berichts-Generator und SSRS&#41;](formatting-report-items-report-builder-and-ssrs.md)   
 [Tablix-Datenbereich &#40;Berichts-Generator und SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md)   
 [Tabellen (Berichts-Generator und SSRS)](tables-report-builder-and-ssrs.md)   
 [Matrizen (Berichts-Generator und SSRS)](create-a-matrix-report-builder-and-ssrs.md)   
 [Listen (Berichts-Generator und SSRS)](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)   
 [Tabellen, Matrizen und Listen &#40;Berichts-Generator und SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
