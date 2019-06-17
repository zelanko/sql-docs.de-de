---
title: Hinzufügen einer Detailgruppe (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 5ef8efba-6d48-4aeb-a3b9-a02ba5a44614
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fe6fffc96a816c9b71c003926d6267e8287a1c48
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66106861"
---
# <a name="add-a-details-group-report-builder-and-ssrs"></a>Hinzufügen einer Detailgruppe (Berichts-Generator und SSRS)
  Die Detaildaten aus einem Berichtsdataset werden als Gruppe ohne Gruppierungsausdruck angegeben. Fügen Sie einem Tablix-Datenbereich eine Detailgruppe hinzu, wenn die Detaildaten für eine Matrix angezeigt, wenn aus einer Tabelle bzw. Liste gelöschte Detaildaten wieder hinzugefügt oder wenn zusätzliche Detailgruppen hinzugefügt werden sollen. Weitere Informationen zu Gruppen finden Sie unter [Grundlegendes zu Gruppen &#40;Berichts-Generator und SSRS&#41;](understanding-groups-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-details-group-to-a-tablix-data-region"></a>So fügen Sie einem Tablix-Datenbereich eine Detailgruppe hinzu  
  
1.  Klicken Sie auf der Entwurfsoberfläche auf eine beliebige Stelle im Tablix-Datenbereich, um diesen auszuwählen. Im Bereich Gruppierung werden die Zeilengruppen und Spaltengruppen für den derzeit ausgewählten Tablix-Datenbereich angezeigt.  
  
2.  Klicken Sie im Bereich „Gruppierung“ mit der rechten Maustaste auf eine Gruppe, die die innerste untergeordnete Gruppe darstellt. Klicken Sie auf **Gruppe hinzufügen**und dann auf **Untergeordnete Gruppe**. Das Dialogfeld **Tablix-Gruppe** wird geöffnet.  
  
3.  Geben Sie in **Gruppierungsausdruck**keinen Ausdruck ein. Eine Detailgruppe verfügt über keinen Ausdruck.  
  
4.  Wählen Sie **Detaildaten anzeigen**aus.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     Im Bereich Gruppierung wird eine neue Detailgruppe als untergeordnete Gruppe hinzugefügt, und vom Zeilenhandle für die in Schritt 1 ausgewählte Gruppe wird das Symbol für die Detailgruppe angezeigt. Weitere Informationen zu Handles finden Sie unter [Zellen, Zeilen und Spalten des Tablix-Datenbereichs (Berichts-Generator und SSRS)](tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Hinzufügen oder Löschen einer Gruppe in einem Datenbereich &#40;Berichts-Generator und SSRS&#41;](add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md)   
 [Grundlegendes zu Gruppen &#40;Berichts-Generator und SSRS&#41;](understanding-groups-report-builder-and-ssrs.md)   
 [Tablix-Datenbereich &#40;Berichts-Generator und SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md)   
 [Tabellen (Berichts-Generator und SSRS)](tables-report-builder-and-ssrs.md)   
 [Matrizen (Berichts-Generator und SSRS)](create-a-matrix-report-builder-and-ssrs.md)   
 [Listen (Berichts-Generator und SSRS)](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)   
 [Tabellen, Matrizen und Listen &#40;Berichts-Generator und SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
