---
description: Benutzerdefinierte Eigenschaften des Ziels für Dimensionsverarbeitung
title: Benutzerdefinierte Eigenschaften des Ziels für Dimensionsverarbeitung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 9700f663-53f2-49b6-b1ef-92c7b752d6a1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7e6959edde524e2219573793b5becb34f5d63f1c
ms.sourcegitcommit: cfa04a73b26312bf18d8f6296891679166e2754d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2020
ms.locfileid: "92192721"
---
# <a name="dimension-processing-destination-custom-properies"></a>Benutzerdefinierte Eigenschaften des Ziels für Dimensionsverarbeitung

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  Das Ziel für Dimensionsverarbeitung verfügt sowohl über benutzerdefinierte Eigenschaften als auch über die Eigenschaften, die allen Datenflusskomponenten gemeinsam sind.  
  
 Die folgende Tabelle beschreibt die benutzerdefinierten Eigenschaften des Ziels für Dimensionsverarbeitung. Alle Eigenschaften weisen Lese-/Schreibzugriff auf.  
  
|Eigenschaft|Datentyp|BESCHREIBUNG|  
|--------------|---------------|-----------------|  
|ASConnectionString|String|Die Verbindungszeichenfolge zu einer Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] oder einem [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekt.|  
|KeyDuplicate|Ganze Zahl (Enumeration)|Wenn UseDefaultConfiguration **FALSE**ist; ein Wert, der angibt, wie Fehler aufgrund doppelter Schlüssel behandelt werden. Die möglichen Werte sind **IgnoreError** (0), **ReportAndContinue** (1) und **ReportAndStop** (2). Der Standardwert dieser Eigenschaft ist **IgnoreError** (0).|  
|KeyErrorAction|Ganze Zahl (Enumeration)|Wenn UseDefaultConfiguration **FALSE**ist; ein Wert, der angibt, wie Fehler aufgrund von Schlüsseln behandelt werden sollen. Die möglichen Werte sind **ConvertToUnknown** (0) und **DiscardRecord** (1). Der Standardwert dieser Eigenschaft ist **ConvertToUnknown** (0).|  
|KeyErrorLimit|Integer|Wenn UseDefaultConfiguration **FALSE**ist; die Obergrenze von aktivierten Schlüsselfehlern.|  
|KeyErrorLimitAction|Ganze Zahl (Enumeration)|Wenn UseDefaultConfiguration **FALSE**ist; ein Wert, der angibt, welche Aktion aufgeführt werden soll, wenn **KeyErrorLimit** erreicht wird. Die möglichen Werte sind **StopLogging** (1) und **StopProcessing** (0). Der Standardwert dieser Eigenschaft ist **StopProcessing** (0).|  
|KeyErrorLogFile|String|Wenn UseDefaultConfiguration **FALSE**ist; der Pfad und Dateiname der Fehlerprotokolldatei.|  
|KeyNotFound|Ganze Zahl (Enumeration)|Wenn UseDefaultConfiguration **FALSE**ist; ein Wert, der angibt, wie Fehler aufgrund fehlender Schlüssel behandelt werden sollen. Die möglichen Werte sind **IgnoreError** (0), **ReportAndContinue** (1) und **ReportAndStop** (2). Der Standardwert dieser Eigenschaft ist **IgnoreError** (0).|  
|NullKeyConvertedToUnknown|Ganze Zahl (Enumeration)|Wenn UseDefaultConfiguration **FALSE**ist; ein Wert, der angibt, wie NULL-Schlüssel behandelt werden sollen, die in den unbekannten Wert konvertiert wurden. Die möglichen Werte sind **IgnoreError** (0), **ReportAndContinue** (1) und **ReportAndStop** (2). Der Standardwert dieser Eigenschaft ist **IgnoreError** (0).|  
|NullKeyNotAllowed|Ganze Zahl (Enumeration)|Wenn UseDefaultConfiguration **FALSE**ist; ein Wert, der angibt, wie nicht erlaubte Nullwerte behandelt werden sollen. Die möglichen Werte sind **IgnoreError** (0), **ReportAndContinue** (1) und **ReportAndStop** (2). Der Standardwert dieser Eigenschaft ist **IgnoreError** (0).|  
|ProcessType|Ganze Zahl (Enumeration)|Der Typ der von der Transformation verwendeten Dimensionsverarbeitung. Die Werte sind **ProcessAdd** (1) (inkrementell), **ProcessFull** (0) und **ProcessUpdate** (2).|  
|UseDefaultConfiguration|Boolean|Ein Wert, der angibt, ob die Transformation die Standardfehlerkonfiguration verwendet. Wenn diese Eigenschaft **False**ist, schließt die Transformation Informationen über Fehlerverarbeitung ein.|  
  
 Die Eingabe und die Eingabespalten des Ziels für Dimensionsverarbeitung verfügen nicht über benutzerdefinierte Eigenschaften.  
  
 Weitere Informationen finden Sie unter [Dimension Processing Destination](../../integration-services/data-flow/dimension-processing-destination.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Common Properties](./set-the-properties-of-a-data-flow-component.md)  
  
