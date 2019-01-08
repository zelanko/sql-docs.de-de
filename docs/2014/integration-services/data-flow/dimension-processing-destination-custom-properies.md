---
title: Benutzerdefinierte Eigenschaften des Ziels für Dimensionsverarbeitung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 9700f663-53f2-49b6-b1ef-92c7b752d6a1
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 2723231bb6200252a8c809214bd82826ce9b6e25
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52790502"
---
# <a name="dimension-processing-destination-custom-properies"></a>Benutzerdefinierte Eigenschaften des Ziels für Dimensionsverarbeitung
  Das Ziel für Dimensionsverarbeitung verfügt sowohl über benutzerdefinierte Eigenschaften als auch über die Eigenschaften, die allen Datenflusskomponenten gemeinsam sind.  
  
 Die folgende Tabelle beschreibt die benutzerdefinierten Eigenschaften des Ziels für Dimensionsverarbeitung. Alle Eigenschaften weisen Lese-/Schreibzugriff auf.  
  
|Eigenschaft|Datentyp|Description|  
|--------------|---------------|-----------------|  
|ASConnectionString|Zeichenfolge|Die Verbindungszeichenfolge zu einer Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] oder einem [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekt.|  
|KeyDuplicate|Ganze Zahl (Enumeration)|Wenn usedefaultconfiguration `False`, ein Wert, wie Fehler aufgrund doppelter Schlüssel behandelt werden soll. Die möglichen Werte sind `IgnoreError` (0), `ReportAndContinue` (1) und `ReportAndStop` (2). Der Standardwert dieser Eigenschaft ist `IgnoreError` (0).|  
|KeyErrorAction|Ganze Zahl (Enumeration)|Wenn usedefaultconfiguration `False`, ein Wert, der wie Schlüsselfehler behandelt werden sollen. Die möglichen Werte sind `ConvertToUnknown` (0) und `DiscardRecord` (1). Der Standardwert dieser Eigenschaft ist `ConvertToUnknown` (0).|  
|KeyErrorLimit|Integer|Wenn usedefaultconfiguration `False`, die Obergrenze von Schlüsselfehlern, die aktiviert sind.|  
|KeyErrorLimitAction|Ganze Zahl (Enumeration)|Wenn usedefaultconfiguration `False`, einen Wert an die Aktion beim `KeyErrorLimit` erreicht ist. Die möglichen Werte sind `StopLogging` (1) und `StopProcessing` (0). Der Standardwert dieser Eigenschaft ist `StopProcessing` (0).|  
|KeyErrorLogFile|Zeichenfolge|Wenn usedefaultconfiguration `False`, der Pfad und Dateiname der Fehlerprotokolldatei.|  
|KeyNotFound|Ganze Zahl (Enumeration)|Wenn usedefaultconfiguration `False`, ein Wert, wie Fehler aufgrund fehlender Schlüssel behandelt werden soll. Die möglichen Werte sind `IgnoreError` (0), `ReportAndContinue` (1) und `ReportAndStop` (2). Der Standardwert dieser Eigenschaft ist `IgnoreError` (0).|  
|NullKeyConvertedToUnknown|Ganze Zahl (Enumeration)|Wenn usedefaultconfiguration `False`, ein Wert, der wie null-Schlüssel behandelt werden sollen, die in den unbekannten Wert konvertiert. Die möglichen Werte sind `IgnoreError` (0), `ReportAndContinue` (1) und `ReportAndStop` (2). Der Standardwert dieser Eigenschaft ist `IgnoreError` (0).|  
|NullKeyNotAllowed|Ganze Zahl (Enumeration)|Wenn usedefaultconfiguration `False`, ein Wert, der wie nicht erlaubte Nullwerte behandelt werden sollen. Die möglichen Werte sind `IgnoreError` (0), `ReportAndContinue` (1) und `ReportAndStop` (2). Der Standardwert dieser Eigenschaft ist `IgnoreError` (0).|  
|ProcessType|Ganze Zahl (Enumeration)|Der Typ der von der Transformation verwendeten Dimensionsverarbeitung. Die Werte sind `ProcessAdd` (1) (inkrementell), `ProcessFull` (0) und `ProcessUpdate` (2).|  
|UseDefaultConfiguration|Boolean|Ein Wert, der angibt, ob die Transformation die Standardfehlerkonfiguration verwendet. Wenn diese Eigenschaft `False` ist, schließt die Transformation Informationen über Fehlerverarbeitung ein.|  
  
 Die Eingabe und die Eingabespalten des Ziels für Dimensionsverarbeitung verfügen nicht über benutzerdefinierte Eigenschaften.  
  
 Weitere Informationen finden Sie unter [Dimension Processing Destination](dimension-processing-destination.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Common Properties](../common-properties.md)  
  
  
