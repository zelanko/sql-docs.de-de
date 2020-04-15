---
title: Übersetzer Spezifikation Unterschlüssel | Microsoft Docs
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
ms.openlocfilehash: ad21943c5313edcb09aba88d45ea21132aa9757f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81296040"
---
# <a name="translator-specification-subkeys"></a>Unterschlüssel für Konvertierungsprogrammspezifikationen
Jeder Übersetzer, der im Unterschlüssel ODBC Translators aufgeführt ist, verfügt über einen eigenen Unterschlüssel. Dieser Unterschlüssel hat denselben Namen wie der entsprechende Wert unter dem Unterschlüssel ODBC Translators. Die Werte unter diesem Unterschlüssel enthalten die vollständigen Pfade der DlLs für die Übersetzer- und Übersetzereinrichtung und die Verwendungsanzahl. Die Formate der Werte sind wie in der folgenden Tabelle dargestellt.  
  
|Name|Datentyp|Daten|  
|----------|---------------|----------|  
|Übersetzer|REG_SZ|*Übersetzer-DLL-Pfad*|  
|Einrichten|REG_SZ|*Setup-DLL-Pfad*|  
|UsageCount|REG_DWORD|*count*|  
  
 Informationen zu den Nutzungszahlen finden Sie weiter oben in diesem Abschnitt unter [Verwendungszählung.](../../../odbc/reference/install/usage-counting.md)  
  
 Anwendungen sollten die Verwendungsanzahl nicht festlegen. ODBC behält diese Anzahl bei.  
  
 Angenommen, der Microsoft Code Page Translator verfügt über eine Übersetzungs-DLL mit dem Namen Mscpxl32.dll, dass sich die Einrichtungsfunktionen des Übersetzers in derselben DLL befinden und dass der Übersetzer dreimal installiert wurde. Die Werte unter dem Unterschlüssel Microsoft Code Page Translator können wie folgt lauten:  
  
```  
Translator : REG_SZ : C:\WINDOWS\SYSTEM32\MSCPXL32.DLL  
Setup : REG_SZ : C:\WINDOWS\SYSTEM32\MSCPXL32.DLL  
UsageCount : REG_DWORD : 0x3  
```
