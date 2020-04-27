---
title: Verweise auf Parameterauflistungen (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: c4b47e15-0484-4c13-9182-898db825f01f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c3c9452a9be55c71431a0ed3012769b1f5f6d8eb
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66106413"
---
# <a name="parameters-collection-references-report-builder-and-ssrs"></a>Verweise auf Parameters-Auflistungen (Berichts-Generator und SSRS)
  Berichtsparameter gehören zu den integrierten Auflistungen, auf die Sie aus einem Ausdruck heraus verweisen können. Indem Sie Parameter in einen Ausdruck einschließen, können Sie die Berichtsdaten und die Darstellung von Berichten anhand der Auswahlen eines Benutzers anpassen. Ausdrücke können für jede Eigenschaft eines Berichtselements oder Textfelds verwendet werden, das die Optionen (*Fx*) oder \<**Ausdruck**> bereitstellt. Ausdrücke werden auch zum Steuern des Berichtsinhalts und der Darstellung eines Berichts auf andere Weise verwendet. Weitere Informationen finden Sie unter [Beispiele für Ausdrücke (Berichts-Generator und SSRS)](expression-examples-report-builder-and-ssrs.md).  
  
 Wenn Sie Parameterwerte mit Dataset-Feldwerten zur Laufzeit vergleichen, müssen die Datentypen der beiden verglichenen Elemente identisch sein. Berichtsparameter können einen der folgenden Typen aufweisen: Boolean, DateTime, Integer, Float oder Text (steht für den zugrunde liegenden Datentyp String). Es kann erforderlich sein, dass Sie den Datentyp des Parameterwerts konvertieren, damit er dem Datasetwert entspricht. Weitere Informationen finden Sie unter [Datentypen in Ausdrücken &#40;Berichts-Generator und SSRS&#41;](expressions-report-builder-and-ssrs.md).  
  
 Wenn Sie einen Parameterverweis in einen Ausdruck einfügen möchten, müssen Sie wissen, wie die korrekte Syntax für den Parameterverweis angegeben wird. Diese variiert je nachdem, ob der Parameter ein ein- oder mehrwertiger Parameter ist.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="using-a-single-valued-parameter-in-an-expression"></a><a name="Single"></a> Verwenden von einwertigen Parametern in Ausdrücken  
 Die folgende Tabelle enthält Beispiele für die zu verwendende Syntax zum Verweisen auf einwertige Parameter beliebigen Datentyps in einem Ausdruck.  
  
|Beispiel|BESCHREIBUNG|  
|-------------|-----------------|  
|`=Parameters!` *\<ParameterName>* `.IsMultiValue`|Gibt `False` zurück.<br /><br /> Überprüft, ob ein Parameter mehrwertig ist. Wenn `True`der Wert ist, ist der Parameter mehr prozentig und eine Auflistung von-Objekten. Wenn `False`der Wert ist, ist der Parameter einwertig und stellt ein einzelnes Objekt dar.|  
|`=Parameters!` *\<ParameterName>* `.Count`|Gibt den Ganzzahlwert 1 zurück. Für einwertige Parameter ist der Wert stets 1.|  
|`=Parameters!` *\<ParameterName>* `.Label`|Gibt die Parameterbezeichnung zurück, die häufig als Anzeigename in einer Dropdownliste der verfügbaren Werte verwendet wird.|  
|`=Parameters!` *\<ParameterName>* `.Value`|Gibt den Parameterwert zurück. Wenn die Label-Eigenschaft nicht festgelegt ist, wird dieser Wert in der Dropdownliste der verfügbaren Werte angezeigt.|  
|`=CStr(Parameters!`  *\<ParameterName>* `.Value)`|Gibt den Parameterwert als Zeichenfolge zurück.|  
|`=Fields(Parameters!` *\<ParameterName>* `.Value).Value`|Gibt den Wert für das Feld zurück, das den gleichen Namen wie der Parameter besitzt.|  
  
 Weitere Informationen zum Verwenden von Parametern in einem Filter finden Sie unter [Hinzufügen von Datasetfiltern, Datenbereichsfiltern und Gruppenfiltern &#40;Berichts-Generator und SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md).  
  
##  <a name="using-a-multivalue-parameter-in-an-expression"></a><a name="Multi"></a> Verwenden eines mehrwertigen Parameters in einem Ausdruck  
 Die folgende Tabelle enthält Beispiele für die zu verwendende Syntax zum Verweisen auf mehrwertige Parameter beliebigen Datentyps in einem Ausdruck.  
  
|Beispiel|BESCHREIBUNG|  
|-------------|-----------------|  
|`=Parameters!` *\<MultivalueParameterName>* `.IsMultiValue`|Gibt `True` oder `False` zurück.<br /><br /> Überprüft, ob ein Parameter mehrwertig ist. Wenn `True` zurückgegeben wird, ist der Parameter mehrwertig und stellt eine Auflistung von Objekten dar. Wenn `False` zurückgegeben wird, ist der Parameter einwertig und stellt ein einzelnes Objekt dar.|  
|`=Parameters!` *\<MultivalueParameterName>* `.Count`|Gibt eine ganze Zahl zurück.<br /><br /> Bezieht sich auf die Anzahl der Werte. Für einwertige Parameter ist der Wert stets 1. Für mehrwertige Parameter ist der Wert 0 oder höher.|  
|`=Parameters!` *\<MultivalueParameterName>* `.Value(0)`|Gibt den ersten Wert eines mehrwertigen Parameters zurück.|  
|`=Parameters!` *\<MultivalueParameterName>* `.Value(Parameters!` *\<MultivalueParameterName>* `.Count-1)`|Gibt den letzten Wert eines mehrwertigen Parameters zurück.|  
|`=Split("Value1,Value2,Value3",",")`|Gibt ein Array von Werten zurück.<br /><br /> Erstellt ein Array von Werten für einen mehrwertigen `String`-Parameter. Sie können ein beliebiges Trennzeichen im zweiten Parameter von Split verwenden. Mit diesem Ausdruck können Standardwerte für einen mehrwertigen Parameter festgelegt werden oder ein mehrwertiger Parameter zum Senden an einen Unterbericht oder Drillthroughbericht erstellt werden.|  
|`=Join(Parameters!` *\<MultivalueParameterName>* `.Value,", ")`|Gibt eine `String` zurück, die eine Liste von durch Trennzeichen getrennten Werten in einem mehrwertigen Parameter enthält. Sie können ein beliebiges Trennzeichen im zweiten Parameter von Join verwenden.|  
  
 Weitere Informationen zum Verwenden von Parametern in einem Filter finden Sie unter [Berichtsparameter (Berichts-Generator und Berichts-Designer)](report-parameters-report-builder-and-report-designer.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausdrücke &#40;Berichts-Generator und SSRS&#41;](expressions-report-builder-and-ssrs.md)   
 [Häufig verwendete Filter (Berichts-Generator und SSRS)](commonly-used-filters-report-builder-and-ssrs.md)   
 [Hinzufügen, Ändern oder Löschen von Berichtsparametern &#40;Berichts-Generator und SSRS&#41;](add-change-or-delete-a-report-parameter-report-builder-and-ssrs.md)   
 [Tutorial: Add a Parameter to Your Report (Report Builder) (Tutorial: Hinzufügen eines Parameters zu einem Bericht (Berichts-Generator))](../tutorial-add-a-parameter-to-your-report-report-builder.md)   
 [Lernprogramme &#40;Berichts-Generator&#41;](../report-builder-tutorials.md)   
 [Integrierte Sammlungen in Ausdrücken &#40;Berichts-Generator und SSRS&#41;](built-in-collections-in-expressions-report-builder.md)  
  
  
