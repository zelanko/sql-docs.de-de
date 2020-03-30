---
title: Anzeigen von Datenunterschieden
ms.prod: sql
ms.technology: ssdt
ms.topic: conceptual
f1_keywords:
- sql.data.tools.datacompare.f1
ms.assetid: f88d3350-2eaf-44cc-96a8-84008b6cd071
author: markingmyname
ms.author: maghan
manager: jroth
ms.reviewer: “”
ms.custom: seo-lt-2019
ms.date: 02/09/2017
ms.openlocfilehash: 5c9e80f6289ff3313a3eeb7cec0601fb2c651aa2
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "75226752"
---
# <a name="how-to-view-data-differences"></a>Gewusst wie: Anzeigen von Datenunterschieden

Nach dem Vergleich der Daten in zwei Datenbanken werden alle verglichenen *Datenbankobjekte* sowie deren Status aufgeführt. Sie können auch Ergebnisse für die Datensätze in den einzelnen Objekten (gruppiert nach Status) anzeigen.  
  
Nachdem Sie sich die Unterschiede angesehen haben, können Sie einige oder alle unterschiedlichen, fehlenden oder neuen Objekte oder Datensätze des *Ziels* aktualisieren, sodass sie der *Quelle* entsprechen.  
  
### <a name="to-view-data-differences"></a>So zeigen Sie Datenunterschiede an  
  
1.  Vergleichen Sie die Daten einer Quelle und eines Ziels.  
  
2.  (Optional) Führen Sie einen oder beide der folgenden Schritte aus:  
  
    -   Standardmäßig werden die Ergebnisse für alle Objekte (unabhängig vom jeweiligen Status) angezeigt. Wenn nur Objekte mit einem bestimmten Status angezeigt werden sollen, klicken Sie auf eine Option in der Liste **Filter**.  
  
    -   Wenn Sie Ergebnisse für Datensätze innerhalb eines bestimmten Objekts anzeigen möchten, klicken Sie im Hauptergebnisbereich auf das gewünschte Objekt, und klicken Sie anschließend im Bereich mit der Datensatzansicht auf eine Registerkarte. Jede Registerkarte zeigt sämtliche Datensätze innerhalb des Objekts, die einen bestimmten Status besitzen: Unterschiedliche Datensätze, Nur in der Quelle, Nur im Ziel oder Identische Datensätze. Die Daten sind nach Datensatz und Spalte sortiert.  
  
## <a name="see-also"></a>Weitere Informationen  
[Gewusst wie: Vergleichen von verschiedenen Datenbankdefinitionen mithilfe des Schemavergleichs](../ssdt/how-to-use-schema-compare-to-compare-different-database-definitions.md)  
  
