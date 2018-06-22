---
title: Geben Sie die Trainingsdaten (Datamining-Assistent) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dm.dmwizard.specifytrainingdata.f1
ms.assetid: cb04deeb-0f89-4bba-b3f1-efccada16825
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: b6c6239831cc1e53ba1925b022d310f5cef907e7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36150431"
---
# <a name="specify-the-training-data-data-mining-wizard"></a>Trainingsdaten angeben (Data Mining-Assistent)
  Mithilfe der Seite **Trainingsdaten angeben** können Sie festlegen, welche Spalten in der Miningstruktur enthalten sein sollen. Sie können auch Spalten für die Struktur auswählen, wenn Sie sie nicht in allen Modellen verwenden möchten. Wenn Sie beispielsweise einen Drillthrough zu den Spalten vom Miningmodell ausführen möchten, können Sie die Spalten in die Struktur aufnehmen, aber nicht in das Modell.  
  
 Mindestens eine Schlüsselspalte ist für jede Tabelle erforderlich, die in die Struktur aufgenommen wird. Welche Spalte Sie als Schlüssel auswählen, hängt davon ab, ob die Tabelle eine Falltabelle oder eine geschachtelte Tabelle ist. Ist die Tabelle eine geschachtelte Tabelle, ist der Schlüssel häufig auch die vorhersagbare Spalte, nicht der relationale Fremdschlüssel. Weitere Informationen zu geschachtelten Schlüsseln finden Sie unter [Geschachtelte Tabellen &#40;Analysis Services – Data Mining&#41;](data-mining/nested-tables-analysis-services-data-mining.md).  
  
> [!NOTE]  
>  Unterschiedliche Miningalgorithmen verwenden Schlüssel auf unterschiedliche Art und Weise. Weitere Informationen über die verschiedenen Schlüsselarten finden Sie unter [Inhaltstypen &#40;Data Mining&#41;](data-mining/content-types-data-mining.md).  
  
 **Weitere Informationen:** [Miningstrukturen &#40;Analysis Services - Data Mining&#41;](data-mining/mining-structures-analysis-services-data-mining.md), [Miningmodellspalten](data-mining/mining-model-columns.md), [Data Mining-Assistent &#40;Analysis Services - Data Mining&#41;](data-mining/data-mining-wizard-analysis-services-data-mining.md), [Erstellen einer relationalen Miningstruktur](data-mining/create-a-relational-mining-structure.md)  
  
## <a name="options"></a>Tastatur  
 **Tabellen oder Spalten.**  
 Zeigt die Tabellen und Spalten an, die Sie auf der vorherigen Seite des Assistenten ausgewählt haben.  
  
 **\<das Kontrollkästchen >**  
 Wählen Sie die Spalten aus, die in die Miningstruktur aufgenommen werden sollen.  
  
 Wenn Ihre Datenquelle geschachtelte Tabellen oder mehrere Ansichten enthält, erweitern Sie die Spaltenliste, um die geschachtelten Tabellen anzuzeigen.  
  
 **Key**  
 Wählen Sie diese Option aus, um die Spalte als eindeutigen Bezeichner für die Daten auszuwählen.  
  
 Bei einer Falltabelle ist der Schlüssel in der Regel der eindeutige Bezeichner.  
  
 Bei einer geschachtelten Tabelle gibt der **Schlüssel** den Bezeichner einer Zeile im Kontext des verbundenen Falls an.  
  
 **Eingabe**  
 Wählen Sie diese Option aus, um die Spalte beim Erstellen von Vorhersagen zu verwenden.  
  
> [!NOTE]  
>  Diese Spalte ist nur verfügbar, wenn Sie zusammen mit der Miningstruktur ein Miningmodell erstellen.  
  
 **Vorhersagbare**  
 Wählen Sie diese Option aus, um zu aktivieren, dass die Tabelle oder die Spalte auf der Grundlage zukünftiger zusätzlicher Eingaben vorhergesagt werden können.  
  
 Wenn Sie eine geschachtelte Tabelle außerdem als vorhersagbar kennzeichnen, wird die gesamte geschachtelte Tabelle vorhersagbar. Wenn in der geschachtelten Tabelle keine Spalten als Eingabe oder als vorhersagbar gekennzeichnet sind, erscheint die geschachtelte Tabelle in der Miningstruktur, wird aber im Modell ignoriert.  
  
 **Hinweis** Diese Spalte ist nur verfügbar, wenn Sie zusammen mit der Miningstruktur ein Miningmodell erstellen.  
  
 **Vorschlagen**  
 Klicken Sie hierauf, um das Dialogfeld **Verbundene Spalten vorschlagen** zu öffnen, das eine Analyse einer Datenprobe durchführt, um auf der Grundlage der Entropie Eingabespalten zu ermitteln, die die engste Beziehung zur ausgewählten Spalte **Vorhersagbar** haben. Diese Analyse bezieht auch Spalten geschachtelter Tabellen oder Miningstrukturen ein, die auf OLAP-Quellen basieren.  
  
 **Hinweis** Diese Spalte ist nur verfügbar, wenn Sie zusammen mit der Miningstruktur ein Miningmodell erstellen.  
  
## <a name="see-also"></a>Siehe auch  
 [Data Mining-Assistent F1-Hilfe &#40;Analysis Services – Datamining&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md)   
 [Verbundene Spalten vorschlagen &#40;Datamining-Assistenten&#41;](suggest-related-columns-data-mining-wizard.md)   
 [Tabellentypen angeben &#40;Datamining-Assistenten&#41;](specify-table-types-data-mining-wizard.md)   
 [Geben Sie Inhalt und Datentyp der Spaltenwerts &#40;Datamining-Assistenten&#41;](specify-the-column-s-content-and-data-type-data-mining-wizard.md)  
  
  