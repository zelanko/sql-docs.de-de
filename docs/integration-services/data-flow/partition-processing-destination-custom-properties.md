---
description: Benutzerdefinierte Eigenschaften des Ziels für Partitionsverarbeitung
title: Benutzerdefinierte Eigenschaften des Ziels für Partitionsverarbeitung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 3eac4413-0c90-4b06-8f7e-d0d72f4d869d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 87f70b54a0f43252bd6ebc2f28b32371715760cd
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88457329"
---
# <a name="partition-processing-destination-custom-properties"></a>Benutzerdefinierte Eigenschaften des Ziels für Partitionsverarbeitung

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  Das Ziel für Partitionsverarbeitung verfügt sowohl über benutzerdefinierte Eigenschaften als auch über die Eigenschaften, die allen Datenflusskomponenten gemeinsam sind.  
  
 Die folgende Tabelle beschreibt die benutzerdefinierten Eigenschaften des Ziels für Partitionsverarbeitung. Alle Eigenschaften weisen Lese-/Schreibzugriff auf.  
  
|Eigenschaft|Datentyp|BESCHREIBUNG|  
|--------------|---------------|-----------------|  
|ASConnectionString|String|Die Verbindungszeichenfolge zu einem [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekt oder einer Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].|  
|KeyDuplicate|Ganze Zahl (Enumeration)|Wenn UseDefaultConfiguration **FALSE**ist; ein Wert, der angibt, wie Fehler aufgrund doppelter Schlüssel behandelt werden. Die möglichen Werte sind **IgnoreError** (0), **ReportAndContinue** (1) und **ReportAndStop** (2). Der Standardwert dieser Eigenschaft ist **IgnoreError** (0).|  
|KeyErrorAction|Ganze Zahl (Enumeration)|Wenn UseDefaultConfiguration **FALSE**ist; ein Wert, der angibt, wie Fehler aufgrund von Schlüsseln behandelt werden sollen. Die möglichen Werte sind **ConvertToUnknown** (0) und **DiscardRecord** (1). Der Standardwert dieser Eigenschaft ist **ConvertToUnknown** (0).|  
|KeyErrorLimit|Integer|Wenn UseDefaultConfiguration **FALSE**ist; die Obergrenze von erlaubten Schlüsselfehlern.|  
|KeyErrorLimitAction|Ganze Zahl (Enumeration)|Wenn UseDefaultConfiguration **FALSE**ist; ein Wert, der angibt, welche Aktion aufgeführt werden soll, wenn **KeyErrorLimit** erreicht wird. Die möglichen Werte sind **StopLogging** (1) und **StopProcessing** (0). Der Standardwert dieser Eigenschaft ist **StopProcessing** (0).|  
|KeyErrorLogFile|String|Wenn UseDefaultConfiguration **FALSE**ist; der Pfad und Dateiname der Fehlerprotokolldatei.|  
|KeyNotFound|Ganze Zahl (Enumeration)|Wenn UseDefaultConfiguration **FALSE**ist; ein Wert, der angibt, wie Fehler aufgrund fehlender Schlüssel behandelt werden sollen. Die möglichen Werte sind **IgnoreError** (0), **ReportAndContinue** (1) und **ReportAndStop** (2). Der Standardwert dieser Eigenschaft ist der **ReportAndContinue** (1).|  
|NullKeyConvertedToUnknown|Ganze Zahl (Enumeration)|Wenn UseDefaultConfiguration **FALSE**ist; ein Wert, der angibt, wie NULL-Schlüssel behandelt werden sollen, die in den unbekannten Wert konvertiert wurden. Die möglichen Werte sind **IgnoreError** (0), **ReportAndContinue** (1) und **ReportAndStop** (2). Der Standardwert dieser Eigenschaft ist **IgnoreError** (0).|  
|NullKeyNotAllowed|Ganze Zahl (Enumeration)|Wenn UseDefaultConfiguration **FALSE**ist; ein Wert, der angibt, wie nicht erlaubte Nullwerte behandelt werden sollen. Die möglichen Werte sind **IgnoreError** (0), **ReportAndContinue** (1) und **ReportAndStop** (2). Der Standardwert dieser Eigenschaft ist der **ReportAndContinue** (1).|  
|ProcessType|Ganze Zahl (Enumeration)|Der Typ der von der Transformation verwendeten Partitionsverarbeitung. Die möglichen Werte sind **ProcessAdd** (1) (inkrementell), **ProcessFull** (0) und **ProcessUpdate** (2).|  
|UseDefaultConfiguration|Boolean|Ein Wert, der angibt, ob die Transformation die Standardfehlerkonfiguration verwendet. Wenn diese Eigenschaft **FALSE**ist, verwendet die Transformation die Werte der benutzerdefinierten Fehlerbehandlungseigenschaften, die in dieser Tabelle aufgeführt sind, einschließlich KeyDuplicate, KeyErrorAction usw.|  
  
 Die Eingabe und die Eingabespalten des Ziels für Partitionsverarbeitung verfügen nicht über benutzerdefinierte Eigenschaften.  
  
 Weitere Informationen finden Sie unter [Partition Processing Destination](../../integration-services/data-flow/partition-processing-destination.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Common Properties](https://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
  
