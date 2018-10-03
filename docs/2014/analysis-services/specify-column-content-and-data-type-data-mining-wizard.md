---
title: Angeben von Spalteninhalt und Datentyp (Datamining-Assistent) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: 0634be64-4c38-4381-9b19-fe9a5889306c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a5625919d0a7b8cbc729a001caa649604de7b16e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48213470"
---
# <a name="specify-column-content-and-data-type-data-mining-wizard"></a>Inhalt und Datentyp der Spalten angeben (Data Mining-Assistent)
  Auf der Seite **Inhalt und Datentyp der Spalten angeben** geben Sie die Verwendung und den Datentyp für jede Spalte an, die Sie auf der vorherigen Seite des Assistenten ausgewählt haben. Wenn Sie die Spalte ignorieren möchten, klicken Sie auf **Zurück** , um zur Seite **Trainingsdaten**zurückzukehren, und deaktivieren Sie alle Kontrollkästchen.  
  
 Die Verwendung einer Spalte gibt an, wie die Daten im Modell verwendet werden. Eine Spalte kann als Schlüssel zum Identifizieren einer Reihe, als Eingabewert zur Verwendung in Analysen oder als der Wert verwendet werden, den Sie vorhersagen möchten. Spalten können sowohl für Vorhersagen als auch als Eingabe verwendet werden.  
  
 Der Datentyp gibt zusätzliche Details zum Typ der in der Spalte enthaltenen Daten und zur Verwendung der Daten während des Trainings an. Einige Inhaltstypen erfordern einen bestimmten Datentyp und umgekehrt. Je nach Algorithmus, den Sie beim Erstellen eines Miningmodells verwenden, müssen Sie unter Umständen einen bestimmten Datentyp angeben. Informationen zu den Inhalts- und Datentypen in Miningmodellen und -strukturen finden Sie unter [Inhaltstypen &#40;Data Mining&#41;](data-mining/content-types-data-mining.md).  
  
 **Weitere Informationen:** [Miningstrukturen &#40;Analysis Services – Data Mining&#41;](data-mining/mining-structures-analysis-services-data-mining.md), [Miningmodellspalten](data-mining/mining-model-columns.md), [Data Mining-Assistent &#40;Analysis Services – Data Mining&#41;](data-mining/data-mining-wizard-analysis-services-data-mining.md), [Erstellen einer relationalen Miningstruktur](data-mining/create-a-relational-mining-structure.md)  
  
## <a name="options"></a>Tastatur  
 **Miningmodellstruktur**  
 Zeigt die Spalten aus den Ansichten und geschachtelte Tabellen an, die Sie auf der vorherigen Seite des Assistenten ausgewählt haben.  
  
 **Spalten**  
 Listet die Spalten auf.  
  
 **Inhaltstyp**  
 Geben Sie den Inhaltstyp für die Spalte an. Wenn Sie auf der vorherigen Seite des Assistenten angegeben haben, dass die Spalte ein Schlüssel ist, sind die folgenden Werte verfügbar:  
  
|Option|Description|  
|------------|-----------------|  
|Key|Geben Sie an, dass die Spalte einen eindeutigen Bezeichner für die Fallreihe enthält.|  
|Key Sequence|Geben Sie an, dass die Spalte einen Sequenzbezeichner enthält.|  
|Key Time|Geben Sie an, dass die Spalte ein Datum oder eine andere eindeutige fortlaufende Nummer enthält, die zum Bezeichnen einer Datums- oder Zeitreihe verwendet wird.|  
  
 Wenn Sie die Spalte als Nicht-Schlüsselspalte ausgewählt haben, sind je nach Datentyp die folgenden Werte verfügbar:  
  
|Option|Description|  
|------------|-----------------|  
|Continuous|Geben Sie an, dass die Spalte fortlaufende numerische Werte enthält.|  
|Discretized|Geben Sie an, dass die Spalte numerische Werte enthält, die diskretisiert wurden oder als diskrete Werte behandelt werden können.|  
|Discrete|Geben Sie an, dass die Spalte Text oder andere nicht numerische Werte enthält.|  
  
 **Data type**  
 Geben Sie den Datentyp für die Spalte an.  
  
 Die folgenden Werte sind verfügbar:  
  
-   `Boolean`  
  
-   `Date`  
  
-   `Double`  
  
-   `Long`  
  
-   `Text`  
  
 **Erkennen**  
 Analysieren Sie ein Datenbeispiel in allen numerischen Spalten. Ersetzt angegebene Werte für den **Inhaltstyp** durch einen empfohlenen Inhaltstyp.  
  
## <a name="see-also"></a>Siehe auch  
 [Data Mining-Assistent F1-Hilfe &#40;Analysis Services – Datamining&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md)   
 [Verbundene Spalten vorschlagen &#40;Datamining-Assistent&#41;](suggest-related-columns-data-mining-wizard.md)   
 [Tabellentypen angeben &#40;Datamining-Assistent&#41;](specify-table-types-data-mining-wizard.md)   
 [Geben Sie Inhalt und Datentyp der Spaltenwerts &#40;Datamining-Assistent&#41;](specify-the-column-s-content-and-data-type-data-mining-wizard.md)  
  
  
