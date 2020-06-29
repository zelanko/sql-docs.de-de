---
title: Transformations-Editor für Fuzzysuche (Registerkarte Erweitert) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fuzzylookuptransformation.advanced.f1
helpviewer_keywords:
- Fuzzy Lookup Transformation Editor
ms.assetid: 0a2919be-2ea7-4c06-82b8-0ffad5f0dd83
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 68f53eb2735dc07656fc8ff2b81c3259caa4847b
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85425257"
---
# <a name="fuzzy-lookup-transformation-editor-advanced-tab"></a>Transformations-Editor für Fuzzysuche (Registerkarte Erweitert)
  Auf der Registerkarte **Erweitert** des Dialogfelds **Transformations-Editor für Fuzzysuche** können Sie die Parameter für die Fuzzysuche festlegen.  
  
 Weitere Informationen zur Transformation für Fuzzysuche finden Sie unter [Fuzzy Lookup Transformation](data-flow/transformations/lookup-transformation.md).  
  
## <a name="options"></a>Optionen  
 **Maximale Anzahl von Übereinstimmungen, die pro Suche ausgegeben werden**  
 Geben Sie die maximale Anzahl der Übereinstimmungen an, die pro Eingabezeile von der Transformation zurückgegeben werden können. Der Standardwert lautet **1**.  
  
 **Schwellenwert für Ähnlichkeit**  
 Legen Sie mithilfe des Schiebereglers den Schwellenwert für Ähnlichkeit auf Komponentenebene fest. Je näher der Wert an 1 liegt, desto stärker muss die Ähnlichkeit zwischen Suchwert und Quellwert sein, um als Übereinstimmung zu gelten. Durch eine Erhöhung des Schwellenwertes kann die Geschwindigkeit beim Abgleich erhöht werden, weil als Kandidaten dann weniger Datensätze berücksichtigt werden müssen.  
  
 **Tokentrennzeichen**  
 Geben Sie die Trennzeichen an, die von der Transformation verwendet werden, um Spaltenwerte mit Token zu versehen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler-und Meldungs Referenz für Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Transformations-Editor für Fuzzysuche &#40;Registerkarte Verweis Tabelle&#41;](../../2014/integration-services/fuzzy-lookup-transformation-editor-reference-table-tab.md)   
 [Transformations-Editor für Fuzzysuche &#40;Registerkarte Spalten&#41;](../../2014/integration-services/fuzzy-lookup-transformation-editor-columns-tab.md)  
  
  
