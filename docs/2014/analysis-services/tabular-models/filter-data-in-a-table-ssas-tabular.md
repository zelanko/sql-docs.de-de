---
title: Filtern von Daten in einer Tabelle (SSAS-tabellarisch) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.customfilterdb.f1
- sql12.asvs.bidtoolset.autofiltermenu.f1
- sql12.asvs.bidtoolset.notallitemsshowing.f1
ms.assetid: 3223059d-f525-4835-bf88-ebc195d9dbdc
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 869185e56db9a4ffb07282d3ce51ced191a6bac8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66067128"
---
# <a name="filter-data-in-a-table-ssas-tabular"></a>Filtern von Daten in einer Tabelle (SSAS – tabellarisch)
  Sie können beim Importieren von Daten Filter anwenden, um zu steuern, welche Zeilen in eine Tabelle geladen werden. Nachdem Sie die Daten importiert haben, können Sie keine einzelnen Zeilen löschen. Sie können jedoch benutzerdefinierte Filter anwenden, um zu steuern, wie Zeilen angezeigt werden. Zeilen, die die Filterkriterien nicht erfüllen, werden ausgeblendet. Sie können nach einer oder mehreren Spalten filtern. Filter sind additiv. Das bedeutet, dass jeder zusätzliche Filter auf dem aktuellen Filter basiert und die Teilmenge der Daten weiter reduziert.  
  
> [!NOTE]  
>  Das Filtervorschaufenster schränkt die Anzahl der unterschiedlichen Werte ein, die angezeigt werden. Wenn die Grenze überschritten wird, wird eine Meldung angezeigt.  
  
### <a name="to-filter-data-based-on-column-values"></a>So filtern Sie Daten auf Grundlage von Spaltenwerten  
  
1.  Wählen Sie im Modell-Designer eine Tabelle aus, und klicken Sie dann auf den Pfeil in der Kopfzeile der Spalte, nach der Sie filtern möchten.  
  
2.  Führen Sie im Menü AutoFilter einen der folgenden Schritte aus:  
  
    -   Wählen Sie in der Liste der Spaltenwerte mindestens einen Wert aus, nach dem gefiltert werden soll, oder löschen Sie ihn, und klicken Sie dann auf **OK**.  
  
         Wenn die Anzahl der Werte sehr groß ist, kann es sein, dass einzelne Elemente nicht in der Liste angezeigt werden. Stattdessen wird eine Meldung angezeigt, dass zu viele Elemente zum Anzeigen vorhanden sind.  
  
    -   Klicken Sie je nach Typ der Spalte auf **Zahlen Filter** oder **Text Filter** , und klicken Sie dann auf die Befehle des Vergleichs Operators (z. b. ist **gleich**), oder klicken Sie auf **benutzerdefinierter Filter**. Erstellen Sie im Dialogfeld **Benutzerdefinierter Filter** den Filter, und klicken Sie dann auf **OK**.  
  
### <a name="to-clear-a-filter-for-a-column"></a>So löschen Sie einen Filter für eine Spalte  
  
1.  Klicken Sie auf den Pfeil in der Kopfzeile der Spalte, für die Sie den Filter löschen möchten.  
  
2.  Klicken Sie auf **Filter \<aus Spalten Name>löschen **.  
  
### <a name="to-clear-all-filters-for-a-table"></a>So löschen Sie alle Filter für eine Tabelle  
  
1.  Wählen Sie im Modell-Designer die Tabelle aus, für die Sie die Filter löschen möchten.  
  
2.  Klicken Sie auf das Menü **Spalte** und dann auf **Alle Filter löschen**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Filtern und Sortieren von Daten &#40;tabellarischen SSAS-&#41;](../filter-and-sort-data-ssas-tabular.md)   
 [Perspektiven &#40;tabellarischen SSAS-&#41;](perspectives-ssas-tabular.md)   
 [Rollen &#40;tabellarischen SSAS-&#41;](roles-ssas-tabular.md)  
  
  
