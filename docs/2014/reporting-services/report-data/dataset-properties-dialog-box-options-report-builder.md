---
title: Dataseteigenschaften (Dialogfeld), Optionen (Berichts-Generator) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10020"
ms.assetid: 43e50133-45ef-47a2-b575-34dfcc28ec98
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b174f9ad33ee38c2f47ffc8a684cddd7ea4376bf
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66107360"
---
# <a name="dataset-properties-dialog-box-options-report-builder"></a>Dataseteigenschaften (Dialogfeld), Optionen (Berichts-Generator)
  Wählen Sie im Dialogfeld **Dataseteigenschaften** die Option **Optionen** aus, um Datenoptionen, wie Sortierungsoptionen und die Behandlung von Zwischensummen als Detaildaten, für die Abfrage zu ändern. Weitere Informationen zu Sortierungen finden Sie unter [Sortierung und Unicode-Unterstützung](../../relational-databases/collations/collation-and-unicode-support.md) in der [SQL Server-Onlinedokumentation](https://go.microsoft.com/fwlink/?linkid=98335).  
  
 Datenoptionen, die Teil einer freigegebenen Datasetdefinition auf dem Berichtsserver sind, wirken sich auf alle Berichte aus, die das freigegebene Dataset verwenden. Sie können Optionen für das freigegebene Dataset überschreiben, nachdem es einem Bericht hinzugefügt wurde. Diese Änderungen wirken sich nur auf den Bericht aus, in dem sie definiert werden.  
  
 Datenoptionen für ein eingebettetes Dataset wirken sich nur auf den Bericht aus, in dem sie definiert werden.  
  
 Weitere Informationen finden Sie unter [Erstellen von Berichten zu eingebetteten und freigegebenen Datasets &#40;Berichts-Generator und SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).  
  
## <a name="options"></a>Optionen  
 **Sortierung**  
 Wählen Sie ein Gebietsschema aus, das die zum Sortieren der Daten verwendete Sortierreihenfolge bestimmt. Der Wert**Standard** gibt an, dass der Bericht diesen Wert vom Datenanbieter herleiten soll, wenn der Bericht ausgeführt wird. Falls der Wert nicht hergeleitet werden kann, wird der Standardwert von der Gebietsschemaeinstellung des Computers hergeleitet.  
  
 **Unterscheidung nach Groß-/Kleinschreibung**  
 Wählen Sie einen Wert aus, um die Unterscheidung nach Groß-/Kleinschreibung zu bestimmen. Mithilfe dieser Option wird angegeben, ob bei den Daten die Groß-/Kleinschreibung unterschieden wird. Sie können **Unterscheidung nach Groß-/Kleinschreibung** auf **Wahr**, **Falsch**oder **Automatisch**festlegen. Der Standardwert **Auto** (Automatisch) gibt an, dass der Berichtsserver diesen Wert vom Datenanbieter herleiten soll, wenn der Bericht ausgeführt wird. Falls der Datenanbieter keine Unterscheidung nach Groß- und Kleinschreibung unterstützt, wird der Bericht so ausgeführt, als sei **FALSE**festgelegt. Wenn Sie den Wert kennen und wissen, dass er unterstützt wird, wählen Sie **True**aus.  
  
 **Unterscheidung nach Akzent**  
 Wählen Sie einen Wert aus, um die Unterscheidung nach Akzent zu bestimmen. Mithilfe der Option**Unterscheidung nach Akzent** wird angegeben, ob bei den Daten nach Akzent unterschieden wird. Mögliche Werte sind **Wahr**, **Falsch**und **Automatisch**. Der Standardwert **Auto** (Automatisch) gibt an, dass der Berichtsserver diesen Wert vom Datenanbieter herleiten soll, wenn der Bericht ausgeführt wird. Falls der Datenanbieter keine Unterscheidung nach Akzent unterstützt, wird der Bericht so ausgeführt, als sei **False**festgelegt. Wenn Sie den Wert kennen und wissen, dass er unterstützt wird, wählen Sie **True**aus.  
  
 **Unterscheidung nach Kanatyp**  
 Wählen Sie einen Wert aus, um die Unterscheidung nach Kanatyp zu bestimmen. Mithilfe dieser Option wird angegeben, ob bei den Daten nach Kanatyp unterschieden wird. Mögliche Werte sind **Wahr**, **Falsch**und **Automatisch**. Der Standardwert **Auto** (Automatisch) gibt an, dass der Berichtsserver diesen Wert vom Datenanbieter herleiten soll, wenn der Bericht ausgeführt wird. Falls der Datenanbieter keine Unterscheidung nach Kanatyp unterstützt, wird der Bericht so ausgeführt, als sei **False**festgelegt. Wenn Sie den Wert kennen und wissen, dass er unterstützt wird, wählen Sie **True**aus.  
  
 **Unterscheidung nach Breite**  
 Wählen Sie einen Wert aus, um die Unterscheidung nach Breite zu bestimmen. Mithilfe dieser Option wird angegeben, ob bei den Daten nach Breite unterschieden wird. Mögliche Werte sind **TRUE**, **FALSE**oder **Auto**. Der Standardwert **Auto** (Automatisch) gibt an, dass der Berichtsserver diesen Wert vom Datenanbieter herleiten soll, wenn der Bericht ausgeführt wird. Falls der Datenanbieter keine Unterscheidung nach Breite unterstützt, wird der Bericht so ausgeführt, als sei **False**festgelegt. Wenn Sie den Wert kennen und wissen, dass er unterstützt wird, wählen Sie **True**aus.  
  
 **Teilergebnisse als Detailzeilen interpretieren**  
 Wählen Sie einen Wert aus, der angibt, ob Teilergebniszeilen als Detailzeilen statt als Aggregatzeilen interpretiert werden sollen. Der Standardwert **automatisch**, gibt an, dass die Teilergebniszeilen als Detailzeilen behandelt werden soll, wenn der Bericht nicht verwendet die `Aggregate`()-Funktion auf alle Felder im Dataset zugreifen. Wenn Teilergebniszeilen als Aggregatzeilen interpretiert werden sollen, wählen Sie **False**aus. Wenn die Teilergebniszeilen als Detailzeilen interpretiert werden sollen, und Sie wissen, dass sie nicht verwenden die `Aggregate`()-Funktion, wählen Sie **"true"**.  
  
## <a name="see-also"></a>Siehe auch  
 [Hilfe zu Dialogfeldern, Bereichen und Assistenten in Berichts-Generator](../report-builder-help-for-dialog-boxes-panes-and-wizards.md)   
 [Aggregatfunktion &#40;Berichts-Generator und SSRS&#41;](../report-design/report-builder-functions-aggregate-function.md)   
 [Filtern, Gruppieren und Sortieren von Daten &#40;Berichts-Generator und SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [Erstellen von Berichten zu eingebetteten und freigegebenen Datasets &#40;Berichts-Generator und SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)   
 [Dataseteigenschaften &#40;Dialogfeld&#41;, Abfrage &#40;Berichts-Generator&#41;](dataset-properties-dialog-box-query-report-builder.md)  
  
  
