---
title: Daten vor dem Laden Filtern (MDS-Add-in für Excel) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 9e30eae0-776b-4a09-aac3-0c0249d92ca5
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c864e95a075477b80bdbbe06912be37bba33fadf
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84961133"
---
# <a name="filter-data-before-loading-mds-add-in-for-excel"></a>Filtern von Daten vor dem Laden (MDS-Add-In für Excel)
  [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] Filtern Sie in Daten, wenn Sie die Größe oder den Bereich der Daten einschränken möchten, die Sie in Excel laden.  
  
## <a name="prerequisites"></a>Voraussetzungen  
 So führen Sie diese Prozedur aus  
  
-   Sie müssen über die Berechtigung für den Zugriff auf den Funktionsbereich **Explorer** verfügen.  
  
### <a name="to-filter-data-before-loading"></a>So filtern Sie Daten vor dem Laden  
  
1.  Öffnen Sie Excel, und stellen Sie auf der Registerkarte **Masterdaten** eine Verbindung mit einem MDS-Repository her. Weitere Informationen finden Sie unter [Herstellen einer Verbindung mit einem MDS-Repository &#40;MDS-Add-In für Excel&#41;](connect-to-an-mds-repository-mds-add-in-for-excel.md).  
  
2.  Wählen Sie im Bereich **Master Data Explorer** ein Modell und eine Version aus. Die Liste der Entitäten wird aufgefüllt.  
  
    -   Wenn der Bereich **Master Data Explorer** nicht sichtbar ist, klicken Sie in der Gruppe **Verbinden und Laden** auf **Explorer anzeigen**.  
  
    -   Wenn der Bereich **Master Data Explorer** deaktiviert ist, liegt dies daran, dass das vorhandene Blatt bereits von MDS verwaltete Daten enthält. Um den Bereich zu aktivieren, öffnen Sie ein neues Arbeitsblatt.  
  
3.  Klicken Sie im Bereich **Master Data Explorer** in der Liste der Entitäten auf die Entität, die Sie filtern möchten.  
  
4.  Klicken Sie im Menüband in der Gruppe **Verbinden und Laden** auf **Filtern**.  
  
5.  Vervollständigen Sie das Dialogfeld **Filtern** , indem Sie die anzuzeigenden Attribute (Spalten) auswählen, die Reihenfolge der Spalten festlegen und nach Bedarf die Daten so filtern, dass wenigere Zeilen zurückgegeben werden. Zeigen Sie den Bereich **Zusammenfassung** an, in dem angegeben ist, wie viele Daten zurückgegeben werden. Weitere Informationen finden Sie unter [Filtern &#40;Dialogfeld, MDS-Add-In für Excel&#41;](filter-dialog-box-mds-add-in-for-excel.md).  
  
6.  Klicken Sie auf **Daten laden**. Das Blatt wird mit von MDS verwalteten Daten aufgefüllt.  
  
    > [!NOTE]  
    >  -   Nur die erste eine Million von Elementen wird in Excel geladen.  
    > -   In Spalten, die eingeschränkte Listen (Domänen basierte Attribute) sind, werden nur die ersten 1000-Werte geladen.  
  
## <a name="next-steps"></a>Nächste Schritte  
 [Daten aus Excel in MDS &#40;MDS-Add-in für Excel veröffentlichen&#41;](import-data-from-excel-to-master-data-services-mds-add-in-for-excel.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Daten &#40;MDS-Add-in für Excel werden geladen&#41;](overview-exporting-data-to-excel-mds-add-in-for-excel.md)   
 [Dialog Feld "Filter" &#40;MDS-Add-in für Excel&#41;](filter-dialog-box-mds-add-in-for-excel.md)   
 [Neuanordnen von Spalten &#40;MDS-Add-In für Excel&#41;](reorder-columns-mds-add-in-for-excel.md)  
  
  
