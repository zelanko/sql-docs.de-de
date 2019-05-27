---
title: Editor für Fuzzygruppierung Transformation (Registerkarte Erweitert) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fuzzygroupingtransformation.advanced.f1
helpviewer_keywords:
- Fuzzy Grouping Transformation Editor
ms.assetid: dd820d75-b8a7-4515-aea4-3553ba5b442e
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: dcebe499eb80fbe01b9aa36a4e07785846eaf621
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66058369"
---
# <a name="fuzzy-grouping-transformation-editor-advanced-tab"></a>Transformations-Editor für Fuzzygruppierung (Registerkarte Erweitert)
  Geben Sie mithilfe der Registerkarte **Erweitert** von **Transformations-Editor für Fuzzygruppierung** die Ein- und Ausgabespalten an, legen Sie Schwellenwerte für die Ähnlichkeit fest, und definieren Sie Begrenzungszeichen.  
  
> [!NOTE]  
>  Die `Exhaustive` und die `MaxMemoryUsage` Eigenschaften der Transformation für Fuzzygruppierung sind nicht verfügbar, in der **Transformation Editor für Fuzzygruppierung**, aber kann festgelegt werden, mithilfe der **Erweiterter Editor**. Weitere Informationen zu diesen Eigenschaften finden Sie im Abschnitt Transformation für Fuzzgruppierung von [Transformation Custom Properties](data-flow/transformations/transformation-custom-properties.md).  
  
 Weitere Informationen zur Transformation für Fuzzygruppierung finden Sie unter [Fuzzy Grouping Transformation](data-flow/transformations/fuzzy-grouping-transformation.md).  
  
## <a name="options"></a>Optionen  
 **Name der Eingabeschlüsselspalte**  
 Geben Sie den Namen einer Ausgabespalte an, die den eindeutigen Bezeichner für jede Eingabezeile enthält. Die `_key_in`-Spalte enthält einen für jede Zeile eindeutigen Wert.  
  
 **Name der Ausgabeschlüsselspalte**  
 Geben Sie den Namen einer Ausgabespalte an, die den eindeutigen Bezeichner für die kanonische Zeile einer Gruppe doppelter Zeilen enthält. Die `_key_out`-Spalte entspricht dem `_key_in`-Wert der kanonischen Datenzeile.  
  
 **Name der Ähnlichkeitsergebnisspalte**  
 Geben Sie einen Namen für die Spalte an, die das Ähnlichkeitsergebnis enthält. Das Ähnlichkeitsergebnis ist ein Wert zwischen 0 und 1, der die Ähnlichkeit zwischen der Eingabezeile und der kanonischen Zeile anzeigt. Je näher das Ergebnis an 1 liegt, desto genauer stimmt die Zeile mit der kanonischen Zeile überein.  
  
 **Schwellenwert für Ähnlichkeit**  
 Legen Sie den Schwellenwert für die Ähnlichkeit mithilfe des Schiebereglers fest. Je näher der Schwellenwert an 1 kommt, desto mehr müssen die Zeilen einander ähneln, um als Duplikate angesehen zu werden. Durch eine Erhöhung des Schwellenwertes kann die Geschwindigkeit beim Abgleich erhöht werden, weil als Kandidaten dann weniger Datensätze berücksichtigt werden müssen.  
  
 **Tokentrennzeichen**  
 Die Transformation bietet einen Standardsatz von Trennzeichen, um Daten mit Tokens zu versehen. Sie können durch Bearbeiten der Liste aber ggf. Trennzeichen hinzufügen oder entfernen.  
  
## <a name="see-also"></a>Siehe auch  
 [Fehler- und Meldungsreferenz von Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Identifizieren ähnlicher Datenzeilen mithilfe der Transformation für Fuzzygruppierung](data-flow/transformations/identify-similar-data-rows-by-using-the-fuzzy-grouping-transformation.md)  
  
  
