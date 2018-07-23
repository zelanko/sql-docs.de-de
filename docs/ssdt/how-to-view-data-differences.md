---
title: 'Gewusst wie: Anzeigen von Datenunterschieden | Microsoft-Dokumentation'
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql.data.tools.datacompare.f1
ms.assetid: f88d3350-2eaf-44cc-96a8-84008b6cd071
caps.latest.revision: 6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d1276c84091513c06a2febcb215cf3bffa23cdd7
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39088292"
---
# <a name="how-to-view-data-differences"></a>Gewusst wie: Anzeigen von Datenunterschieden
Nach dem Vergleich der Daten in zwei Datenbanken werden alle verglichenen *Datenbankobjekte* sowie deren Status aufgeführt. Sie können auch Ergebnisse für die Datensätze in den einzelnen Objekten (gruppiert nach Status) anzeigen.  
  
Nachdem Sie sich die Unterschiede angesehen haben, können Sie einige oder alle unterschiedlichen, fehlenden oder neuen Objekte oder Datensätze des *Ziels* aktualisieren, sodass sie der *Quelle* entsprechen.  
  
### <a name="to-view-data-differences"></a>So zeigen Sie Datenunterschiede an  
  
1.  Vergleichen Sie die Daten einer Quelle und eines Ziels.  
  
2.  (Optional) Führen Sie einen oder beide der folgenden Schritte aus:  
  
    -   Standardmäßig werden die Ergebnisse für alle Objekte (unabhängig vom jeweiligen Status) angezeigt. Wenn nur Objekte mit einem bestimmten Status angezeigt werden sollen, klicken Sie auf eine Option in der Liste **Filter**.  
  
    -   Wenn Sie Ergebnisse für Datensätze innerhalb eines bestimmten Objekts anzeigen möchten, klicken Sie im Hauptergebnisbereich auf das gewünschte Objekt, und klicken Sie anschließend im Bereich mit der Datensatzansicht auf eine Registerkarte. Jede Registerkarte zeigt sämtliche Datensätze innerhalb des Objekts, die einen bestimmten Status besitzen: Unterschiedliche Datensätze, Nur in der Quelle, Nur im Ziel oder Identische Datensätze. Die Daten sind nach Datensatz und Spalte sortiert.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[Gewusst wie: Vergleichen von verschiedenen Datenbankdefinitionen mithilfe des Schemavergleichs](../ssdt/how-to-use-schema-compare-to-compare-different-database-definitions.md)  
  
