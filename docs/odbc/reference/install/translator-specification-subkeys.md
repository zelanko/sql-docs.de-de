---
description: Unterschlüssel für Konvertierungsprogrammspezifikationen
title: Unterschlüssel der Konvertierungsspezifikation | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- translator subkey [ODBC]
- registry entries for components [ODBC], translator specification subkeys
- translator specification subkeys [ODBC]
- subkeys [ODBC], translator specification subkeys
ms.assetid: 3c0edeee-d43a-4466-a177-bf2d2435707a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c02317c8abe12dbc693cdf7b715b6de84e5bc631
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88461292"
---
# <a name="translator-specification-subkeys"></a>Unterschlüssel für Konvertierungsprogrammspezifikationen
Jeder im Unterschlüssel für ODBC-Übersetzer aufgelistete Konvertierer hat seinen eigenen Unterschlüssel. Dieser Unterschlüssel hat denselben Namen wie der entsprechende Wert unter dem ODBC-Übersetzer-Unterschlüssel. Die Werte unter diesem Unterschlüssel Listen die vollständigen Pfade der Konvertierungs-und Konvertierungs-DLLs und der Verwendungs Anzahl auf. Die Formate der Werte sind wie in der folgenden Tabelle dargestellt.  
  
|Name|Datentyp|Daten|  
|----------|---------------|----------|  
|Translator|REG_SZ|*Translator-dll-Pfad*|  
|Einrichten|REG_SZ|*Setup-DLL-Pfad*|  
|Usagecount|REG_DWORD|*count*|  
  
 Weitere Informationen zu Verwendungs Anzahlen finden Sie unter [Nutzungs Zählung](../../../odbc/reference/install/usage-counting.md) weiter oben in diesem Abschnitt.  
  
 Anwendungen sollten die Verwendungs Anzahl nicht festlegen. Diese Anzahl wird von ODBC beibehalten.  
  
 Nehmen wir beispielsweise an, dass der Microsoft-Codepage-Konvertierer über eine Translation-DLL namens Mscpxl32.dll verfügt, dass sich die Konvertierungs Funktionen des Konvertierungs Programms in derselben DLL befinden und dass der Konvertierer dreimal installiert wurde. Die Werte unter dem Unterschlüssel Microsoft Code Page Translator können wie folgt lauten:  
  
```  
Translator : REG_SZ : C:\WINDOWS\SYSTEM32\MSCPXL32.DLL  
Setup : REG_SZ : C:\WINDOWS\SYSTEM32\MSCPXL32.DLL  
UsageCount : REG_DWORD : 0x3  
```
