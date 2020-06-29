---
title: Benutzerdefinierte Eigenschaften des Ziels für Partitionsverarbeitung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 3eac4413-0c90-4b06-8f7e-d0d72f4d869d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 04d5f9a669fbccc798698914c919e63d90e04591
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85431597"
---
# <a name="partition-processing-destination-custom-properties"></a>Benutzerdefinierte Eigenschaften des Ziels für Partitionsverarbeitung
  Das Ziel für Partitionsverarbeitung verfügt sowohl über benutzerdefinierte Eigenschaften als auch über die Eigenschaften, die allen Datenflusskomponenten gemeinsam sind.  
  
 Die folgende Tabelle beschreibt die benutzerdefinierten Eigenschaften des Ziels für Partitionsverarbeitung. Alle Eigenschaften weisen Lese-/Schreibzugriff auf.  
  
|Eigenschaft|Datentyp|BESCHREIBUNG|  
|--------------|---------------|-----------------|  
|ASConnectionString|String|Die Verbindungszeichenfolge zu einem [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekt oder einer Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|KeyDuplicate|Ganze Zahl (Enumeration)|Wenn UseDefaultConfiguration `False` den Wert hat, ein Wert, der angibt, wie doppelte Schlüsselfehler behandelt werden. Die möglichen Werte sind `IgnoreError` (0), `ReportAndContinue` (1) und `ReportAndStop` (2). Der Standardwert dieser Eigenschaft ist `IgnoreError` (0).|  
|KeyErrorAction|Ganze Zahl (Enumeration)|Wenn UseDefaultConfiguration der `False` Wert ist, ein Wert, der angibt, wie Schlüsselfehler behandelt werden. Die möglichen Werte sind `ConvertToUnknown` (0) und `DiscardRecord` (1). Der Standardwert dieser Eigenschaft ist `ConvertToUnknown` (0).|  
|KeyErrorLimit|Integer|Wenn UseDefaultConfiguration `False` den Wert hat, ist die Obergrenze von zulässigen Schlüsselfehlern.|  
|KeyErrorLimitAction|Ganze Zahl (Enumeration)|Wenn UseDefaultConfiguration `False` den Wert hat, ein Wert, der die Aktion angibt, die ausgeführt werden soll, wenn `KeyErrorLimit` erreicht wird. Die möglichen Werte sind `StopLogging` (1) und `StopProcessing` (0). Der Standardwert dieser Eigenschaft ist `StopProcessing` (0).|  
|KeyErrorLogFile|String|Wenn UseDefaultConfiguration `False` den Wert hat, der Pfad und der Dateiname der Fehlerprotokoll Datei.|  
|KeyNotFound|Ganze Zahl (Enumeration)|Wenn UseDefaultConfiguration `False` den Wert hat, ein Wert, der angibt, wie Fehler aufgrund fehlender Schlüssel behandelt werden. Die möglichen Werte sind `IgnoreError` (0), `ReportAndContinue` (1) und `ReportAndStop` (2). Der Standardwert dieser Eigenschaft ist `ReportAndContinue` (1).|  
|NullKeyConvertedToUnknown|Ganze Zahl (Enumeration)|Wenn UseDefaultConfiguration `False` den Wert hat, ein Wert, der angibt, wie NULL-Schlüssel behandelt werden, die in den unbekannten Wert konvertiert wurden. Die möglichen Werte sind `IgnoreError` (0), `ReportAndContinue` (1) und `ReportAndStop` (2). Der Standardwert dieser Eigenschaft ist `IgnoreError` (0).|  
|NullKeyNotAllowed|Ganze Zahl (Enumeration)|Wenn UseDefaultConfiguration der `False` Wert ist, ein Wert, der angibt, wie unzulässige Nullen behandelt werden. Die möglichen Werte sind `IgnoreError` (0), `ReportAndContinue` (1) und `ReportAndStop` (2). Der Standardwert dieser Eigenschaft ist `ReportAndContinue` (1).|  
|ProcessType|Ganze Zahl (Enumeration)|Der Typ der von der Transformation verwendeten Partitionsverarbeitung. Die möglichen Werte sind `ProcessAdd` (1) (inkrementell), `ProcessFull` (0) und `ProcessUpdate` (2).|  
|UseDefaultConfiguration|Boolean|Ein Wert, der angibt, ob die Transformation die Standardfehlerkonfiguration verwendet. Wenn diese Eigenschaft ist `False` , verwendet die Transformation die Werte der benutzerdefinierten Fehler Behandlungs Eigenschaften, die in dieser Tabelle aufgeführt sind, einschließlich KeyDuplicate, KeyErrorAction und so weiter.|  
  
 Die Eingabe und die Eingabespalten des Ziels für Partitionsverarbeitung verfügen nicht über benutzerdefinierte Eigenschaften.  
  
 Weitere Informationen finden Sie unter [Partition Processing Destination](partition-processing-destination.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Common Properties](../common-properties.md)  
  
  
