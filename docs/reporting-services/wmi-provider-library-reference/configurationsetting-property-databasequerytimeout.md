---
title: 'DatabaseQueryTimeout-Eigenschaft (WMI: MSReportServer_ConfigurationSetting) | Microsoft-Dokumentation'
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: wmi-provider-library-reference
ms.topic: conceptual
apiname:
- DatabaseQueryTimeout Property
apilocation:
- reportingservices.mof
apitype: MOFDef
helpviewer_keywords:
- DatabaseQueryTimeout property
ms.assetid: 96faed97-9799-4bbf-a66f-fdd532d3eace
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 8149c0954195796ce71a48e022a2f7bc83471601
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65573584"
---
# <a name="configurationsetting-property---databasequerytimeout"></a>ConfigurationSetting-Eigenschaft: DatabaseQueryTimeout
  Gibt die Anzahl von Sekunden an, die verstreichen müssen, ehe der Berichtsserver annimmt, dass der Befehl fehlgeschlagen ist oder die Ausführungszeit zu lang war. Der Berichtsserver nimmt die zeitliche Steuerung der Abfrage anhand des SQL-Katalogs und nicht anhand einer Datenquelle für den Bericht vor. Lese-/Schreibzugriff.  
  
## <a name="syntax"></a>Syntax  
  
```vb  
Public Dim DatabaseQueryTimeout As UInt32  
```  
  
```csharp  
public UInt32 DatabaseQueryTimeout;  
```  
  
## <a name="property-values"></a>Eigenschaftswerte  
 Ein 32-Bit- **Integer** -Objekt ohne Vorzeichen, das die Anzahl der Sekunden darstellt, die für die Ausführung der Abfrage erlaubt sind.  
  
## <a name="example-code"></a>Beispielcode  
 [MSReportServer_ConfigurationSetting-Klasse](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
  
## <a name="requirements"></a>Anforderungen  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen  
 [MSReportServer_ConfigurationSetting-Member](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
