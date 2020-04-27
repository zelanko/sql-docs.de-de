---
title: Einfügen oder Löschen einer Spalte (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: e9db79e2-7e7d-4359-a706-cb746c94182a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e1d5f5d846a690676942e0d4ffcba0475a35595a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66105676"
---
# <a name="insert-or-delete-a-column-report-builder-and-ssrs"></a>Einfügen oder Löschen einer Spalte (Berichts-Generator und SSRS)
  Sie können Spalten zu einem Tablix-Datenbereich hinzufügen bzw. daraus entfernen. Der Tablix-Datenbereich kann eine Tabelle, eine Matrix oder eine Liste sein. Die folgenden Vorgehensweisen gelten nicht für Diagramm- und Messgerätdatenbereiche.  
  
 In Tablix-Datenbereichen können Spalten hinzugefügt werden, die mit einer Gruppe verknüpft sind (innerhalb einer Gruppe) oder die nicht mit einer Gruppe verknüpft sind (außerhalb einer Gruppe). Eine Spalte in einer Gruppe wiederholt sich einmal pro eindeutigem Gruppenwert. So wiederholt sich zum Beispiel eine Spalte in einer Gruppe, die auf dem Wert in einer Datenspalte mit Farbnamen basiert, einmal pro eindeutigem Farbnamen. Bei geschachtelten Gruppen kann sich die Spalte außerhalb der untergeordneten Gruppe, aber innerhalb der übergeordneten Gruppe befinden. In diesem Fall wiederholt sich die Zeile einmal für jeden eindeutigen Wert in der übergeordneten Gruppe.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-select-a-data-region-so-that-the-row-and-column-handles-appear"></a>So wählen Sie einen Datenbereich aus und zeigen die Zeilen- und Spaltenziehpunkte an  
  
-   Klicken Sie in der Entwurfsansicht auf die obere linke Ecke des Tablix-Datenbereichs, sodass die Spalten- und Zeilenziehpunkte über und neben dem Datenbereich angezeigt werden.  
  
     Weitere Informationen zu Datenbereichs Bereichen finden Sie unter [Listen &#40;Berichts-Generator und SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md).  
  
### <a name="to-insert-a-column-in-a-selected-data-region"></a>So fügen Sie eine Spalte in einen ausgewählten Datenbereich ein  
  
-   Klicken Sie mit der rechten Maustaste auf einen Spaltenziehpunkt an der Stelle, an der Sie eine Spalte einfügen möchten. Klicken Sie auf **Spalte einfügen**und dann auf **Links** bzw. **Rechts**.  
  
     – oder –  
  
-   Klicken Sie mit der rechten Maustaste auf eine Zelle in dem Datenbereich, in dem Sie eine Spalte einfügen möchten. Klicken Sie auf **Spalte einfügen**und dann auf **Links** bzw. **Rechts**.  
  
### <a name="to-delete-a-column-from-a-selected-data-region"></a>So löschen Sie eine Spalte aus einem ausgewählten Datenbereich  
  
-   Wählen Sie die Spalten aus, die Sie löschen möchten, klicken Sie mit der rechten Maustaste auf den Ziehpunkt für eine der ausgewählten Spalten, und klicken Sie dann auf **Spalten löschen**.  
  
     – oder –  
  
-   Klicken Sie mit der rechten Maustaste auf eine Zelle in dem Datenbereich, in dem Sie eine Spalte löschen möchten, und klicken Sie dann auf **Spalten löschen**.  
  
### <a name="to-insert-a-column-in-a-group-in-a-selected-data-region"></a>So fügen Sie eine Spalte in eine Gruppe in einem ausgewählten Datenbereich ein  
  
-   Klicken Sie mit der rechten Maustaste auf eine Spaltengruppenzelle im Spaltengruppenbereich eines Tablix-Datenbereichs, in dem Sie eine Spalte einfügen möchten, klicken Sie auf **Spalte einfügen**, und klicken Sie dann auf **Links - Außerhalb von Gruppe**, **Links - Innerhalb von Gruppe**, **Rechts - Innerhalb von Gruppe**oder **Rechts - Außerhalb von Gruppe**.  
  
     Die Spalte wird entweder innerhalb oder außerhalb der Gruppe eingefügt, die durch die Spaltengruppenzelle, auf die Sie geklickt haben, repräsentiert wird.  
  
### <a name="to-delete-a-column-from-a-group-in-a-selected-data-region"></a>So löschen Sie eine Spalte aus einer Gruppe in einem ausgewählten Datenbereich  
  
-   Klicken Sie mit der rechten Maustaste auf eine Spaltengruppenzelle im Spaltengruppenbereich eines Tablix-Datenbereichs, aus dem Sie eine Spalte löschen möchten, und klicken Sie dann auf **Spalten löschen**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Grundlegendes zu Gruppen &#40;Berichts-Generator und SSRS&#41;](understanding-groups-report-builder-and-ssrs.md)   
 [Tablix-Datenbereich &#40;Berichts-Generator und SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md)   
 [Tabellen (Berichts-Generator und SSRS)](tables-report-builder-and-ssrs.md)   
 [Matrizen (Berichts-Generator und SSRS)](create-a-matrix-report-builder-and-ssrs.md)   
 [Listen (Berichts-Generator und SSRS)](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)   
 [Listen (Berichts-Generator und SSRS)](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
