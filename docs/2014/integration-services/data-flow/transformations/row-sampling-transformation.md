---
title: Transformation für Zeilenstichproben | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.rowsamplingtrans.f1
helpviewer_keywords:
- sampling seeds [Integration Services]
- random seeds
- random sampling
- sample data sets [Integration Services]
- Row Sampling transformation
- packages [Integration Services], samples
- datasets [Integration Services], sample
ms.assetid: b6caafd3-30b2-4368-82af-a44611d4cd39
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 38ad000eee18256ef5a6dda6b64e0e5afc7054ac
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84939351"
---
# <a name="row-sampling-transformation"></a>Transformation für Zeilenstichproben
  Mit der Transformation für Zeilenstichproben wird eine nach dem Zufallsprinzip ausgewählte Teilmenge eines Eingabedatasets abgerufen. Sie können die genaue Größe der Ausgabestichprobe sowie einen Ausgangswert für den Zufallszahlen-Generator angeben.  
  
 Für zufällige Stichproben gibt es viele Anwendungsmöglichkeiten. Beispielsweise könnte ein Unternehmen, das 50 Mitarbeiter nach dem Zufallsprinzip für einen Lotteriepreis auswählen möchte, die Transformation für Zeilenstichproben für die Mitarbeiterdatenbank ausführen und die genaue Anzahl von Gewinnern generieren.  
  
 Die Transformation für Zeilenstichproben ist außerdem bei der Paketentwicklung hilfreich, um ein kleines, aber repräsentatives Dataset zu erstellen. Sie können die Paketausführung und die Datentransformation mit äußerst repräsentativen Daten, aber schneller testen, weil anstelle des vollständigen Datasets eine zufällige Stichprobe verwendet wird. Das vom Testpaket verwendete Stichprobendataset besitzt immer die gleiche Größe. Deshalb können mit der Stichprobenteilmenge auch Leistungsprobleme beim Paket einfacher identifiziert werden.  
  
 Diese Transformation ist mit der Transformation für Prozentwert-Stichproben vergleichbar, die ein Stichprobendataset durch Auswählen eines Prozentwerts der Eingabezeilen erstellt. Siehe [Percentage Sampling Transformation](percentage-sampling-transformation.md).  
  
## <a name="configuring-the-row-sampling-transformation"></a>Konfigurieren der Transformation für Zeilenstichproben  
 Die Transformation für Zeilenstichproben erstellt ein Stichprobendataset durch Auswählen einer angegebene Anzahl von Transformationseingabezeilen. Da die Auswahl von Zeilen aus der Transformationseingabe nach dem Zufallsprinzip erfolgt, ist die Stichprobe für die Eingabe repräsentativ. Darüber hinaus können Sie den Ausgangswert angeben, der vom Zufallszahlen-Generator verwendet wird, um die Auswahl der Zeilen durch die Transformation zu beeinflussen.  
  
 Wenn der gleiche zufällige Ausgangswert in derselben Transformationseingabe verwendet wird, wird immer dieselbe Stichprobenausgabe generiert. Wenn kein Ausgangswert angegeben ist, erstellt die Transformation die Zufallszahl mithilfe der Taktanzahl des Betriebssystems. Deshalb können Sie beim Testen denselben Ausgangswert verwenden, um die Transformationsergebnisse beim Entwickeln und Testen des Pakets zu überprüfen. Anschließend verwenden Sie dann einen zufälligen Ausgangswert, wenn das Paket auf den Produktionsserver verschoben wird.  
  
 Die Transformation für Zeilenstichproben schließt die benutzerdefinierte Eigenschaft `SamplingValue` ein. Diese Eigenschaft kann beim Laden des Pakets mithilfe eines Eigenschaftsausdrucks aktualisiert werden. Weitere Informationen finden Sie unter [Integration Services-Ausdrücke &#40;SSIS&#41;](../../expressions/integration-services-ssis-expressions.md), [Verwenden von Eigenschaftsausdrücken in Paketen](../../expressions/use-property-expressions-in-packages.md) und [Benutzerdefinierte Eigenschaften von Transformationen](transformation-custom-properties.md).  
  
 Diese Transformation weist eine Eingabe und zwei Ausgaben auf. Es ist keine Fehlerausgabe vorhanden.  
  
 Sie können Eigenschaften mit dem [!INCLUDE[ssIS](../../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen.  
  
 Weitere Informationen zu den Eigenschaften, die Sie im Dialogfeld **Transformations-Editor für Zeilenstichprobe** festlegen können, finden Sie unter [Transformations-Editor für Zeilenstichprobe &#40;Seite „Sampling“&#41;](../../row-sampling-transformation-editor-sampling-page.md).  
  
 Das Dialogfeld **Erweiterter Editor** enthält die Eigenschaften, die programmgesteuert festgelegt werden können. Klicken Sie auf eines der folgenden Themen, um weitere Informationen zu den Eigenschaften zu erhalten, die Sie im Dialogfeld **Erweiterter Editor** oder programmgesteuert festlegen können:  
  
-   [Allgemeine Eigenschaften](../../common-properties.md)  
  
-   [Transformation Custom Properties](transformation-custom-properties.md)  
  
## <a name="related-tasks"></a>Related Tasks  
 [Festlegen der Eigenschaften einer Datenflusskomponente](../set-the-properties-of-a-data-flow-component.md)  
  
  
