---
title: Transformation für Prozentwert-Stichproben | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.percentagesamplingtrans.f1
helpviewer_keywords:
- testing mining models
- sampling seeds [Integration Services]
- data mining [Analysis Services], sample data sets
- Percentage Sampling transformation
- sample data sets [Integration Services]
- datasets [Integration Services], sample
- training mining models
ms.assetid: 59767e52-f732-4b3f-8602-be50d0a64ef2
author: janinezhang
ms.author: janinez
ms.openlocfilehash: e7f68e2a6affcdeb7970b457786d91c69967c72b
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84939363"
---
# <a name="percentage-sampling-transformation"></a>Transformation für Prozentwert-Stichproben
  Die Transformation für Prozentwert-Stichproben erstellt ein Stichprobendataset, indem ein Prozentwert der Transformationseingabezeilen ausgewählt wird. Das Stichprobendataset ist eine zufällige Auswahl von Zeilen aus der Transformationseingabe, damit die Stichprobe für die Eingabe repräsentativ ist.  
  
> [!NOTE]  
>  Neben dem angegeben Prozentwert verwendet die Transformation für Prozentwert-Stichproben einen Algorithmus, um zu ermitteln, ob eine Zeile in die Stichprobenausgabe eingeschlossen werden soll. Dies bedeutet, dass die Anzahl von Zeilen in der Stichprobenausgabe möglicherweise nicht genau den angegebenen Prozentwert widerspiegelt. Wenn Sie z. B. 10 % für ein Eingabedataset mit 25.000 Zeilen angeben, kann es sein, dass keine Stichprobe mit 2.500 Zeilen generiert wird. Die Stichprobe hat möglicherweise ein paar mehr oder weniger Zeilen.  
  
 Die Transformation für Prozentwert-Stichproben ist besonders für das Data Mining hilfreich. Mit dieser Transformation können Sie ein Dataset nach dem Zufallsprinzip in zwei Datasets aufteilen: eines zum Trainieren des Data Mining-Modells und ein anderes zum Testen des Modells.  
  
 Die Transformation für Prozentwert-Stichproben ist außerdem zum Erstellen von Stichprobendatasets für die Paketentwicklung hilfreich. Wenn Sie die Transformation für Prozentwert-Stichproben auf einen Datenfluss anwenden, können Sie die Größe des Datasets gleichmäßig reduzieren und zugleich die Datenmerkmale beibehalten. Das Testpaket kann dann schneller ausgeführt werden, weil ein kleines, aber repräsentatives Dataset verwendet wird.  
  
## <a name="configuration-the-percentage-sampling-transformation"></a>Konfiguration der Transformation für Prozentwert-Stichproben  
 Sie können einen Stichproben-Ausgangswert angeben, um das Verhalten des Zufallszahlen-Generators zu ändern, mit dem die Transformation Zeilen auswählt. Wenn der gleiche Stichproben-Ausgangswert verwendet wird, erstellt die Transformation immer die gleiche Stichprobenausgabe. Wenn kein Ausgangswert angegeben ist, erstellt die Transformation die Zufallszahl mithilfe der Taktanzahl des Betriebssystems. Deshalb sollten Sie einen Standardausgangswert wählen, wenn Sie die Transformationsergebnisse beim Entwickeln und Testen eines Pakets überprüfen möchten. Anschließend verwenden Sie dann einen zufälligen Ausgangswert, wenn das Paket auf den Produktionsserver verschoben wird.  
  
 Diese Transformation ist mit der Transformation für Zeilenstichproben vergleichbar, die ein Stichprobendataset erstellt, indem eine angegebene Anzahl von Eingabezeilen ausgewählt wird. Weitere Informationen finden Sie unter [Row Sampling Transformation](row-sampling-transformation.md).  
  
 Die Transformation für Prozentwert-Stichproben schließt die benutzerdefinierte Eigenschaft `SamplingValue` ein. Diese Eigenschaft kann beim Laden des Pakets mithilfe eines Eigenschaftsausdrucks aktualisiert werden. Weitere Informationen finden Sie unter [Integration Services-Ausdrücke &#40;SSIS&#41;](../../expressions/integration-services-ssis-expressions.md), [Verwenden von Eigenschaftsausdrücken in Paketen](../../expressions/use-property-expressions-in-packages.md) und [Benutzerdefinierte Eigenschaften von Transformationen](transformation-custom-properties.md).  
  
 Diese Transformation weist eine Eingabe und zwei Ausgaben auf. Eine Fehlerausgabe wird nicht unterstützt.  
  
 Sie können Eigenschaften mit dem [!INCLUDE[ssIS](../../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen.  
  
 Weitere Informationen zu den Eigenschaften, die Sie im Dialogfeld **Transformations-Editor für Prozentwertstichprobe** festlegen können, finden Sie unter [Percentage Sampling Transformation Editor](../../percentage-sampling-transformation-editor.md).  
  
 Das Dialogfeld **Erweiterter Editor** enthält die Eigenschaften, die programmgesteuert festgelegt werden können. Klicken Sie auf eines der folgenden Themen, um weitere Informationen zu den Eigenschaften zu erhalten, die Sie im Dialogfeld **Erweiterter Editor** oder programmgesteuert festlegen können:  
  
-   [Allgemeine Eigenschaften](../../common-properties.md)  
  
-   [Transformation Custom Properties](transformation-custom-properties.md)  
  
 Weitere Informationen zum Festlegen der Eigenschaften finden Sie unter [Festlegen der Eigenschaften einer Datenflusskomponente](../set-the-properties-of-a-data-flow-component.md).  
  
  
