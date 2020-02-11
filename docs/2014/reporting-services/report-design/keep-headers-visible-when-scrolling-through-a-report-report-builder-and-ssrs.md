---
title: Sichtbarhalten von Kopfzeilen beim Scrollen durch einen Bericht (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 6d9192a4-fd5c-41ad-b9ef-f88f9496afed
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 37c3dc20ab537e7cb8bf69099dbd6d24ff384731
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66105599"
---
# <a name="keep-headers-visible-when-scrolling-through-a-report-report-builder-and-ssrs"></a>Sichtbarhalten von Kopfzeilen beim Durchführen eines Bildlaufs durch einen Bericht (Berichts-Generator und SSRS)
  Damit Zeilen- und Spaltenbezeichnungen nach dem Rendern des Berichts bei einem Bildlauf nicht aus der Sicht verschwinden, können Sie die Zeilen- oder Spaltenüberschriften fixieren.  
  
 Wie Sie die Zeilen und Spalten steuern, hängt davon ab, ob Sie eine Tabelle oder eine Matrix verwenden. Bei einer Tabelle konfigurieren Sie statische Elemente (Zeilen- und Spaltenüberschriften) so, dass diese sichtbar bleiben. Bei einer Matrix konfigurieren Sie die Kopfzeilen von Zeilen- und Spaltengruppen so, dass diese sichtbar bleiben.  
  
 Wenn Sie den Bericht in Excel exportieren, wird der Header nicht automatisch fixiert. Sie können den Bereich in Excel fixieren. Weitere Informationen finden Sie im Abschnitt **Seitenkopfzeilen und -fußzeilen** unter [Exportieren nach Microsoft Excel (Berichts-Generator und SSRS)](../report-builder/exporting-to-microsoft-excel-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  Selbst wenn eine Tabelle Zeilen- und Spaltengruppen enthält, ist es nicht möglich festzulegen, dass die Kopfzeilen dieser Gruppen beim Durchführen eines Bildlaufs immer sichtbar bleiben sollen.  
  
 Die folgende Abbildung zeigt eine Tabelle.  
  
 ![Table](../media/table.png "Tabelle")  
  
 Die folgende Abbildung zeigt eine Matrix.  
  
 ![Matrix](../media/matrix.png "Matrix")  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-keep-matrix-group-headers-visible-while-scrolling"></a>So halten Sie die Gruppenkopfzeilen einer Matrix beim Bildlauf sichtbar  
  
1.  Klicken Sie im Tablix-Datenbereich mit der rechten Maustaste auf den Zeilen-, Spalten- oder Eckziehpunkt, und klicken Sie anschließend auf **Tablix-Eigenschaften**.  
  
2.  Wählen Sie auf der Registerkarte **Allgemein** unter **Zeilenköpfe** oder **Spaltenüberschriften**die Option **Die Kopfzeile sollte beim Ausführen eines Bildlaufs sichtbar bleiben**aus.  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-keep-a-static-tablix-member-row-or-column-visible-while-scrolling"></a>So halten Sie ein statisches Tablix-Element (Zeile oder Spalte) bei einem Bildlauf sichtbar  
  
1.  Klicken Sie auf der Entwurfsoberfläche auf eine beliebige Stelle in der Tabelle, um statische Elemente sowie Gruppen im Gruppierungsbereich anzuzeigen.  
  
     ![Gruppierungs Bereich](../media/grouppane-updated.png "Gruppierungs Bereich")  
  
     In den Bereichen Zeilengruppen und Spaltengruppen werden die hierarchischen statischen und dynamischen Elemente für die Zeilengruppenhierarchie bzw. Spaltengruppenhierarchie angezeigt.  
  
2.  Klicken Sie auf der rechten Seite des Gruppierungs Bereichs auf den Pfeil nach unten, und klicken Sie dann auf erweiterter **Modus**.  
  
3.  Klicken Sie auf das statische Element (Zeile oder Spalte), das bei einem Bildlauf sichtbar bleiben soll. Im Eigenschaftenbereich werden die Eigenschaften für das **Tablix-Element** angezeigt.  
  
     ![Tablix-Element (Eigenschaften)](../media/grouppane-tablixmember-updated.png "Tablix-Element (Eigenschaften)")  
  
4.  Legen Sie im Eigenschaften Bereich **FixedData** auf `True`fest.  
  
5.  Wiederholen Sie diesen Schritt für die angrenzenden Elemente, die bei einem Bildlauf sichtbar bleiben sollen.  
  
6.  Zeigen Sie eine Vorschau des Berichts an.  
  
 Während Sie durch den Bericht blättern, bleiben die statischen Tablix-Elemente sichtbar.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Tablix-Datenbereich &#40;Berichts-Generator und SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md)   
 [Suchen, Anzeigen und Verwalten von Berichten (Berichts-Generator und SSRS)](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)   
 [Exportieren von Berichten &#40;Berichts-Generator und SSRS&#41;](../report-builder/export-reports-report-builder-and-ssrs.md)   
 [Anzeigen von Kopf-und Fußzeilen mit einer Gruppe &#40;Berichts-Generator und SSRS&#41;](display-headers-and-footers-with-a-group-report-builder-and-ssrs.md)   
 [Anzeigen von Zeilen-und Spaltenüberschriften auf mehreren Seiten &#40;Berichts-Generator und SSRS&#41;](display-row-and-column-headers-on-multiple-pages-report-builder-and-ssrs.md)   
 [Gruppierungsbereich (Berichts-Generator)](grouping-pane-report-builder.md)  
  
  
