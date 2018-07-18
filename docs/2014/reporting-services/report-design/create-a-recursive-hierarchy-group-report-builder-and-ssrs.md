---
title: Erstellen einer rekursiven Hierarchiegruppe (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 8b830ba5-4d64-4348-a2b1-76b9338a1462
caps.latest.revision: 7
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 3c4144787ac5085c4713781569d7e6d364ff7951
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37172171"
---
# <a name="create-a-recursive-hierarchy-group-report-builder-and-ssrs"></a>Erstellen einer rekursiven Hierarchiegruppe (Berichts-Generator und SSRS)
  Eine rekursive Hierarchiegruppe organisiert Daten aus einem Berichtsdataset, das mehrere hierarchische Ebenen aufweist, zum Beispiel eine Berichtsstruktur für die Beziehung zwischen Managern und Mitarbeitern in der Hierarchie einer Organisation.  
  
 Bevor Sie Daten in einer Tabelle als rekursive Hierarchiegruppe organisieren können, müssen Sie ein Dataset erstellen, das alle hierarchischen Daten enthält. Sie benötigen separate Felder für das zu gruppierende Element und das Element, nach dem gruppiert wird. Ein Dataset, in dem Sie Mitarbeiter rekursiv unter dem Manager gruppieren möchten, kann z. B. einen Namen, einen Mitarbeiternamen, eine Mitarbeiter-ID und eine Manager-ID enthalten.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-create-a-recursive-hierarchy-group"></a>So erstellen Sie eine rekursive Hierarchiegruppe  
  
1.  Fügen Sie in der Entwurfsansicht eine Tabelle hinzu, und ziehen Sie die anzuzeigenden Datasetfelder in die Tabelle. Normalerweise ist das Feld, das Sie als Hierarchie anzeigen möchten, in der ersten Spalte angeordnet.  
  
2.  Klicken Sie mit der rechten Maustaste in der Tabelle an einer beliebigen Stelle, um sie auszuwählen. Im Bereich Gruppierung wird die Detailgruppe für die gewählte Tabelle angezeigt. Klicken Sie im Bereich „Zeilengruppen“ mit der rechten Maustaste auf **Details**, und klicken Sie anschließend auf **Gruppe bearbeiten**. Das Dialogfeld **Gruppeneigenschaften** wird angezeigt.  
  
3.  Klicken Sie unter **Gruppierungsausdrücke**auf **Hinzufügen**. Im Raster wird eine neue Zeile angezeigt.  
  
4.  Wählen Sie in der Liste **Gruppieren nach** das zu gruppierende Feld aus, oder geben Sie es ein.  
  
5.  Klicken Sie auf **Erweitert**.  
  
6.  Wählen Sie in der Liste **Rekursives übergeordnetes Element** das Feld aus, nach dem gruppiert werden soll, oder geben Sie es ein.  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     Führen Sie den Bericht aus. Im Bericht wird die rekursive Hierarchiegruppe angezeigt. Die Anzeige erfolgt jedoch ohne einen Einzug, der die Hierarchie verdeutlichen würde.  
  
### <a name="to-format-a-recursive-hierarchy-group-with-indent-levels"></a>So formatieren Sie eine rekursive Hierarchiegruppe mit Einzugsebenen  
  
1.  Klicken Sie auf das Textfeld mit dem Feld, dem Sie Einzugsebenen hinzufügen möchten, um ein Hierarchieformat anzuzeigen. Die Eigenschaften für das Textfeld werden im Bereich Eigenschaften angezeigt.  
  
    > [!NOTE]  
    >  Wenn der Bereich Eigenschaften geschlossen ist, klicken Sie auf der Registerkarte **Ansicht** auf **Eigenschaften** .  
  
2.  Erweitern Sie im Bereich Eigenschaften den `Padding` Knoten, klicken Sie auf **Links**, und wählen Sie aus der Dropdown-Liste  **\<Ausdruck… >**.  
  
3.  Geben Sie im Ausdruckfenster den folgenden Ausdruck ein:  
  
     `=CStr(2 + (Level()*10)) + "pt"`  
  
     Die Auffüllung-Eigenschaften erfordern alle eine Zeichenfolge im Format *nnyy*. Dabei steht *nn* für eine Zahl und *yy* für die Maßeinheit. Beispielausdruck wird generiert, eine Zeichenfolge, verwendet der `Level` -Funktion erhöhen die Größe des Abstands basierend auf der Rekursionsebene. Eine Zeile mit der Ebene 1 hätte z.B. die Auffüllung (2 + (1\*10))=12pt, und eine Zeile mit der Ebene 3 hätte die Auffüllung (2 + (3\*10))=32pt. Informationen zu den `Level` funktionieren, finden Sie unter [Ebene](report-builder-functions-level-function.md).  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     Führen Sie den Bericht aus. Der Bericht zeigt eine hierarchische Ansicht der gruppierten Daten an.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von rekursiven Hierarchiegruppen &#40;Berichts-Generator und SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md)   
 [Filtern, Gruppieren und Sortieren von Daten &#40;Berichts-Generator und SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [Referenz zu Aggregatfunktionen &#40;Berichts-Generator und SSRS&#41;](report-builder-functions-aggregate-functions-reference.md)   
 [Tabellen (Berichts-Generator und SSRS)](tables-report-builder-and-ssrs.md)   
 [Matrizen (Berichts-Generator und SSRS)](create-a-matrix-report-builder-and-ssrs.md)   
 [Listen (Berichts-Generator und SSRS)](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)   
 [Tabellen, Matrizen und Listen &#40;Berichts-Generator und SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
