---
title: Benutzerdefinierte Eigenschaften des Ziels für Dimensionsverarbeitung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 9700f663-53f2-49b6-b1ef-92c7b752d6a1
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 9713bbf35f3271dd0ae7168dac838d37621ec5c8
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84915960"
---
# <a name="dimension-processing-destination-custom-properies"></a>Benutzerdefinierte Eigenschaften des Ziels für Dimensionsverarbeitung
  Das Ziel für Dimensionsverarbeitung verfügt sowohl über benutzerdefinierte Eigenschaften als auch über die Eigenschaften, die allen Datenflusskomponenten gemeinsam sind.  
  
 Die folgende Tabelle beschreibt die benutzerdefinierten Eigenschaften des Ziels für Dimensionsverarbeitung. Alle Eigenschaften weisen Lese-/Schreibzugriff auf.  
  
|Eigenschaft|Datentyp|BESCHREIBUNG|  
|--------------|---------------|-----------------|  
|ASConnectionString|String|Die Verbindungszeichenfolge zu einer Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] oder einem [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekt.|  
|KeyDuplicate|Ganze Zahl (Enumeration)|Wenn UseDefaultConfiguration `False` den Wert hat, ein Wert, der angibt, wie doppelte Schlüsselfehler behandelt werden. Die möglichen Werte sind `IgnoreError` (0), `ReportAndContinue` (1) und `ReportAndStop` (2). Der Standardwert dieser Eigenschaft ist `IgnoreError` (0).|  
|KeyErrorAction|Ganze Zahl (Enumeration)|Wenn UseDefaultConfiguration der `False` Wert ist, ein Wert, der angibt, wie der Schlüsselfehler behandelt werden soll. Die möglichen Werte sind `ConvertToUnknown` (0) und `DiscardRecord` (1). Der Standardwert dieser Eigenschaft ist `ConvertToUnknown` (0).|  
|KeyErrorLimit|Integer|Wenn UseDefaultConfiguration `False` den Wert hat, wird die obere Grenze von Schlüsselfehlern aktiviert.|  
|KeyErrorLimitAction|Ganze Zahl (Enumeration)|Wenn UseDefaultConfiguration `False` den Wert hat, ein Wert, der die Aktion angibt, die ausgeführt werden soll, wenn `KeyErrorLimit` erreicht wird. Die möglichen Werte sind `StopLogging` (1) und `StopProcessing` (0). Der Standardwert dieser Eigenschaft ist `StopProcessing` (0).|  
|KeyErrorLogFile|String|Wenn UseDefaultConfiguration `False` den Wert hat, der Pfad und der Dateiname der Fehlerprotokoll Datei.|  
|KeyNotFound|Ganze Zahl (Enumeration)|Wenn UseDefaultConfiguration `False` den Wert hat, ein Wert, der angibt, wie Fehler aufgrund fehlender Schlüssel behandelt werden. Die möglichen Werte sind `IgnoreError` (0), `ReportAndContinue` (1) und `ReportAndStop` (2). Der Standardwert dieser Eigenschaft ist `IgnoreError` (0).|  
|NullKeyConvertedToUnknown|Ganze Zahl (Enumeration)|Wenn UseDefaultConfiguration `False` den Wert hat, ein Wert, der angibt, wie NULL-Schlüssel behandelt werden, die in den unbekannten Wert konvertiert wurden. Die möglichen Werte sind `IgnoreError` (0), `ReportAndContinue` (1) und `ReportAndStop` (2). Der Standardwert dieser Eigenschaft ist `IgnoreError` (0).|  
|NullKeyNotAllowed|Ganze Zahl (Enumeration)|Wenn UseDefaultConfiguration der `False` Wert ist, ein Wert, der angibt, wie unzulässige Nullen behandelt werden. Die möglichen Werte sind `IgnoreError` (0), `ReportAndContinue` (1) und `ReportAndStop` (2). Der Standardwert dieser Eigenschaft ist `IgnoreError` (0).|  
|ProcessType|Ganze Zahl (Enumeration)|Der Typ der von der Transformation verwendeten Dimensionsverarbeitung. Die Werte sind `ProcessAdd` (1) (inkrementell), `ProcessFull` (0) und `ProcessUpdate` (2).|  
|UseDefaultConfiguration|Boolean|Ein Wert, der angibt, ob die Transformation die Standardfehlerkonfiguration verwendet. Wenn diese Eigenschaft `False` ist, schließt die Transformation Informationen über Fehlerverarbeitung ein.|  
  
 Die Eingabe und die Eingabespalten des Ziels für Dimensionsverarbeitung verfügen nicht über benutzerdefinierte Eigenschaften.  
  
 Weitere Informationen finden Sie unter [Dimension Processing Destination](dimension-processing-destination.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Common Properties](../common-properties.md)  
  
  
