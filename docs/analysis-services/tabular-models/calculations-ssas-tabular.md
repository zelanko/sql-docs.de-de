---
title: Berechnungen in tabellarischen Modellen von Analysis Services | Microsoft-Dokumentation
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c7096cac1f4721531f1905b11f2ca3b901661204
ms.sourcegitcommit: a6949111461eda0cc9a71689f86b517de3c5d4c1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2019
ms.locfileid: "67263427"
---
# <a name="calculations-in-tabular-models"></a>Berechnungen in tabellarischen Modellen
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Nachdem Sie Daten in das Modell importiert haben, können Sie Berechnungen hinzufügen, um Daten zu aggregieren, filtern, erweitern, kombinieren und schützen. Tabellarische Modelle verwenden Data Analysis Expressions (DAX), eine neue Formelsprache zum Erstellen von benutzerdefinierten Berechnungen. In tabellarischen Modellen werden die Berechnungen, die Sie mit DAX-Formeln erstellen, in *berechneten Spalten*, *Measures*und *Zeilenfiltern*verwendet.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|Description|  
|-----------|-----------------|  
|[Grundlegendes zu DAX in tabellarischen Modellen](../../analysis-services/tabular-models/understanding-dax-in-tabular-models-ssas-tabular.md)|Beschreibt die Data Analysis Expressions (DAX)-Formelsprache, die zum Erstellen von Berechnungen für berechnete Spalten, Measures und Zeilenfilter in tabellarischen Modellen verwendet wird.|  
|[DAX-formelkompatibilität im DirectQuery-Modus](http://msdn.microsoft.com/981b6a68-434d-4db6-964e-d92f8eb3ee3e)|Beschreibt die Unterschiede und listet die Funktionen auf, die nicht im DirectQuery-Modus unterstützt werden. Des Weiteren werden die Funktionen aufgelistet, die unterstützt werden, aber andere Ergebnisse zurückgeben können.|  
|[DAX-Referenz (Data Analysis Expressions)](/dax/data-analysis-expressions-dax-reference)|Dieser Abschnitt enthält ausführliche Beschreibungen der DAX-Syntax, -Operatoren und -Funktionen.|  
  
> [!NOTE]  
>  Dieser Abschnitt enthält keine Schritt-für-Schritt-Anweisungen zum Erstellen von Berechnungen. Da Berechnungen in berechneten Spalten, Measures und Zeilenfiltern (in Rollen) angegeben werden, werden die Anweisungen zum Erstellen von DAX-Formeln in Aufgaben für diese Funktionen bereitgestellt. Weitere Informationen finden Sie unter [Erstellen einer berechneten Spalte](../../analysis-services/tabular-models/ssas-calculated-columns-create-a-calculated-column.md), [erstellen und Verwalten von Measures](../../analysis-services/tabular-models/create-and-manage-measures-ssas-tabular.md), und [erstellen und Verwalten von Rollen](../../analysis-services/tabular-models/create-and-manage-roles-ssas-tabular.md).  
  
> [!NOTE]  
>  Obwohl DAX auch zum Abfragen eines tabellarischen Modells verwendet werden kann, wird in den Themen dieses Abschnitts schwerpunktmäßig das Erstellen von Berechnungen mithilfe von DAX-Formeln behandelt.  
  
  
