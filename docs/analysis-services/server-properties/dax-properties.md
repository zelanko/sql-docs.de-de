---
title: DAX-Eigenschaften | Microsoft Docs
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3960c3c2b98b26ce7508d5f11d1eafbdc486dca3
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="dax-properties"></a>DAX-Eigenschaften
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
   Der DAX-Abschnitt von „msmdsrv.ini“ enthält Einstellungen zur Steuerung bestimmter Verhaltensweisen von Abfragen in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], wie z.B. die maximale Anzahl von Zeilen, die in einem DAX-Abfrageresultset zurückgegeben werden.

  Bei sehr großen Rowsets – etwa den in DirectQuery-Modellen zurückgegebenen – ist der Standardwert von einer Million Zeilen möglicherweise nicht ausreichend. Wissen Sie, ob die Grenze anpassen benötigt, wenn Sie diesen Fehler erhalten: Das Resultset einer Abfrage einer externen Datenquelle hat die maximal zulässige Größe von ‚1000000' Zeilen überschritten.

Um die Obergrenze zu erhöhen, legen Sie die Konfigurationseinstellung **MaxIntermediateRowSize** fest. Sie müssen das gesamte Element manuell in den DAX-Abschnitt der Konfigurationsdatei einfügen. Die Einstellung ist in der Datei erst dann vorhanden, wenn Sie sie hinzufügen.

## <a name="configuration-snippet"></a>Konfigurationscodeausschnitt

```
<ConfigurationSettings>
. . .
<DAX>
  <PredicateCheckSpoolCardinalityThreshold>5000
  </PredicateCheckSpoolCardinalityThreshold>
  <DQ>
     <MaxIntermediateRowsetSize>1000000
     </MaxIntermediateRowsetSize>
  </DQ>
</DAX>
. . .
```

## <a name="property-descriptions"></a>Eigenschaftsbeschreibungen

Einstellung |Wert |Description
--------|-------|-----------
MaxIntermediateRowsetSize | 1000000 | Maximale Anzahl von in einer DAX-Abfrage zurückgegebenen Zeilen. Fügen Sie diesen Eintrag manuell zur Datei „msmdsrv.ini“ hinzu, und erhöhen Sie den Wert, wenn die Standardeinstellung zu niedrig ist.
PredicateCheckSpoolCardinalityThreshold| 5000 | Eine erweiterte Eigenschaft, die nur unter Anleitung des Microsoft-Supports geändert werden sollte.

Weitere Informationen zu zusätzlichen Servereigenschaften und zum Festlegen dieser Eigenschaften finden Sie unter [Servereigenschaften in Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md).
