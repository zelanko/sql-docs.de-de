---
title: Trainingsdaten angeben (Data Mining-Assistent) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.dmwizard.specifytrainingdata.f1
ms.assetid: cb04deeb-0f89-4bba-b3f1-efccada16825
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c3bbeb708cdb0c2882b85d55081446b3dc12b56b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66068068"
---
# <a name="specify-the-training-data-data-mining-wizard"></a>Trainingsdaten angeben (Data Mining-Assistent)
  Mithilfe der Seite **Trainingsdaten angeben** können Sie festlegen, welche Spalten in der Miningstruktur enthalten sein sollen. Sie können auch Spalten für die Struktur auswählen, wenn Sie sie nicht in allen Modellen verwenden möchten. Wenn Sie beispielsweise einen Drillthrough zu den Spalten vom Miningmodell ausführen möchten, können Sie die Spalten in die Struktur aufnehmen, aber nicht in das Modell.  
  
 Mindestens eine Schlüsselspalte ist für jede Tabelle erforderlich, die in die Struktur aufgenommen wird. Welche Spalte Sie als Schlüssel auswählen, hängt davon ab, ob die Tabelle eine Falltabelle oder eine geschachtelte Tabelle ist. Ist die Tabelle eine geschachtelte Tabelle, ist der Schlüssel häufig auch die vorhersagbare Spalte, nicht der relationale Fremdschlüssel. Weitere Informationen zu geschachtelten Schlüsseln finden Sie unter [Geschachtelte Tabellen &#40;Analysis Services – Data Mining&#41;](data-mining/nested-tables-analysis-services-data-mining.md).  
  
> [!NOTE]  
>  Unterschiedliche Miningalgorithmen verwenden Schlüssel auf unterschiedliche Art und Weise. Weitere Informationen über die verschiedenen Schlüsselarten finden Sie unter [Inhaltstypen &#40;Data Mining&#41;](data-mining/content-types-data-mining.md).  
  
 **Weitere Informationen:** [Miningstrukturen &#40;Analysis Services - Data Mining&#41;](data-mining/mining-structures-analysis-services-data-mining.md), [Miningmodellspalten](data-mining/mining-model-columns.md), [Data Mining-Assistent &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-wizard-analysis-services-data-mining.md), [Erstellen einer relationalen Miningstruktur](data-mining/create-a-relational-mining-structure.md)  
  
## <a name="options"></a>Optionen  
 **Tabellen/Spalten**  
 Zeigt die Tabellen und Spalten an, die Sie auf der vorherigen Seite des Assistenten ausgewählt haben.  
  
 **\<Kontrollkästchen>**  
 Wählen Sie die Spalten aus, die in die Miningstruktur aufgenommen werden sollen.  
  
 Wenn Ihre Datenquelle geschachtelte Tabellen oder mehrere Ansichten enthält, erweitern Sie die Spaltenliste, um die geschachtelten Tabellen anzuzeigen.  
  
 **Schlüssel**  
 Wählen Sie diese Option aus, um die Spalte als eindeutigen Bezeichner für die Daten auszuwählen.  
  
 Bei einer Falltabelle ist der Schlüssel in der Regel der eindeutige Bezeichner.  
  
 Bei einer geschachtelten Tabelle gibt der **Schlüssel** den Bezeichner einer Zeile im Kontext des verbundenen Falls an.  
  
 **Eingabe**  
 Wählen Sie diese Option aus, um die Spalte beim Erstellen von Vorhersagen zu verwenden.  
  
> [!NOTE]  
>  Diese Spalte ist nur verfügbar, wenn Sie zusammen mit der Miningstruktur ein Miningmodell erstellen.  
  
 **Vorhersagbar**  
 Wählen Sie diese Option aus, um zu aktivieren, dass die Tabelle oder die Spalte auf der Grundlage zukünftiger zusätzlicher Eingaben vorhergesagt werden können.  
  
 Wenn Sie eine geschachtelte Tabelle außerdem als vorhersagbar kennzeichnen, wird die gesamte geschachtelte Tabelle vorhersagbar. Wenn in der geschachtelten Tabelle keine Spalten als Eingabe oder als vorhersagbar gekennzeichnet sind, erscheint die geschachtelte Tabelle in der Miningstruktur, wird aber im Modell ignoriert.  
  
 **Hinweis** Diese Spalte ist nur verfügbar, wenn Sie zusammen mit der Miningstruktur ein Miningmodell erstellen.  
  
 **Verbesserungs**  
 Klicken Sie hierauf, um das Dialogfeld **Verbundene Spalten vorschlagen** zu öffnen, das eine Analyse einer Datenprobe durchführt, um auf der Grundlage der Entropie Eingabespalten zu ermitteln, die die engste Beziehung zur ausgewählten Spalte **Vorhersagbar** haben. Diese Analyse bezieht auch Spalten geschachtelter Tabellen oder Miningstrukturen ein, die auf OLAP-Quellen basieren.  
  
 **Hinweis** Diese Spalte ist nur verfügbar, wenn Sie zusammen mit der Miningstruktur ein Miningmodell erstellen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Assistent (F1-Hilfe &#40;Analysis Services-Data Mining-&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md)   
 [Verwandte Spalten &#40;Data Mining-Assistenten vorschlagen&#41;](suggest-related-columns-data-mining-wizard.md)   
 [Geben Sie die Tabellentypen &#40;Data Mining-Assistenten an&#41;](specify-table-types-data-mining-wizard.md)   
 [Geben Sie den Inhalt und den Datentyp der Spalte &#40;Data Mining-Assistenten an&#41;](specify-the-column-s-content-and-data-type-data-mining-wizard.md)  
  
  
