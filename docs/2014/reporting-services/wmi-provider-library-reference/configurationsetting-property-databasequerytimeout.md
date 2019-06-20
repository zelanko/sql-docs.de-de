---
title: 'DatabaseQueryTimeout-Eigenschaft (WMI: MSReportServer_ConfigurationSetting) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- DatabaseQueryTimeout Property
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- DatabaseQueryTimeout property
ms.assetid: 96faed97-9799-4bbf-a66f-fdd532d3eace
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2e92e3e0f6752ea99fe89c962ebe96e343c0195b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66097751"
---
# <a name="databasequerytimeout-property-wmi-msreportserverconfigurationsetting"></a>DatabaseQueryTimeout-Eigenschaft (WMI: MSReportServer_ConfigurationSetting)
  Gibt die Anzahl von Sekunden an, die verstreichen müssen, ehe der Berichtsserver annimmt, dass der Befehl fehlgeschlagen ist oder die Ausführungszeit zu lang war. Der Berichtsserver nimmt die zeitliche Steuerung der Abfrage anhand des SQL-Katalogs und nicht anhand einer Datenquelle für den Bericht vor. Lese-/Schreibzugriff.  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Public Dim DatabaseQueryTimeout As UInt32  
```  
  
```csharp  
public UInt32 DatabaseQueryTimeout;  
```  
  
## <a name="property-values"></a>Eigenschaftswerte  
 Ein 32-Bit-`integer`-Objekt ohne Vorzeichen, das die Anzahl der Sekunden darstellt, die für die Ausführung der Abfrage erlaubt sind  
  
## <a name="example-code"></a>Beispielcode  
 [MSReportServer_ConfigurationSetting-Klasse](msreportserver-configurationsetting-class.md)  
  
## <a name="requirements"></a>Anforderungen  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [MSReportServer_ConfigurationSetting-Member](msreportserver-configurationsetting-members.md)  
  
  
