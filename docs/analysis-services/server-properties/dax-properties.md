---
title: DAX-Eigenschaften | Microsoft-Dokumentation
ms.date: 10/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 794caf245e0cc3494713991159c5a911a187afae
ms.sourcegitcommit: 448106b618fe243e418bbfc3daae7aee8d8553d2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2018
ms.locfileid: "48264863"
---
# <a name="dax-properties"></a>DAX-Eigenschaften
[!INCLUDE[ssas-appliesto-sqlas-all](../../includes/ssas-appliesto-sqlas-all.md)]

   Die DAX-Abschnitt der Datei "Msmdsrv.ini" enthält Einstellungen zur Steuerung bestimmter Verhaltensweisen von Abfragen in Analysis Services verwendet werden, z. B. die Obergrenze für die Anzahl der Zeilen in einer DAX-Abfrageresultset zurückgegeben.

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

Einstellung |value |Description
--------|-------|-----------
MaxIntermediateRowsetSize | 1000000 | Maximale Anzahl von in einer DAX-Abfrage zurückgegebenen Zeilen. Fügen Sie diesen Eintrag manuell zur Datei „msmdsrv.ini“ hinzu, und erhöhen Sie den Wert, wenn die Standardeinstellung zu niedrig ist.
PredicateCheckSpoolCardinalityThreshold| 5000 | Eine erweiterte Eigenschaft, die nur unter Anleitung des Microsoft-Supports geändert werden sollte.

Weitere Informationen zu zusätzlichen Servereigenschaften und zum Festlegen dieser Eigenschaften finden Sie unter [Servereigenschaften in Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md).
