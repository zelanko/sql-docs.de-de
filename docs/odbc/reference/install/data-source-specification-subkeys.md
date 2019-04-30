---
title: Datenquellen-Spezifikation Unterschlüssel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data source specification subkeys [ODBC]
- registry entries for data sources [ODBC], data source specification subkeys
- subkeys [ODBC], data source specification subkeys
ms.assetid: d7e88a07-e6ab-4258-a45d-1ca21234fbec
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ad210f91d00f9e692c8ee20fef01a808a01501c3
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63198207"
---
# <a name="data-source-specification-subkeys"></a>Unterschlüssel für Datenquellenspezifikationen
Jede Datenquelle, die in der ODBC-Datenquellen-Unterschlüssel aufgeführt verfügt über einen Unterschlüssel selbst. Dieser Unterschlüssel hat den gleichen Namen wie der entsprechende Wert unter dem Unterschlüssel für ODBC-Datenquellen. Die Werte unter diesem Unterschlüssel müssen die Treiber-DLL "auflisten" und listet möglicherweise eine Beschreibung der Datenquelle. Der Treiber Übersetzer unterstützt, können die Werte der Name der standardmäßigen Übersetzer, die Standard-Konvertierungs-DLL und die Standardoption für die Übersetzung auflisten. Die Werteliste möglicherweise auch andere Informationen, die vom Treiber bei der Herstellung einer Verbindung mit der Datenquelle erforderlich sind. Der Treiber möglicherweise z. B. einen Servernamen, Datenbanknamen oder Schemaname.  
  
 Die Formate der-Werte sind wie in der folgenden Tabelle gezeigt. Nur der Treiber-Wert ist erforderlich.  
  
|Name|Datentyp|Daten|  
|----------|---------------|----------|  
|Description|REG_SZ|*description*|  
|Treiber|REG_SZ|*driver-DLL-path*|  
|TranslationDLL|REG_SZ|*translator-DLL-path*|  
|TranslationName|REG_SZ|*translator-name*|  
|TranslationOption|REG_SZ|*translation-option*|  
|*opt-value-name*|*opt-value-type*|*opt-value-data*|  
  
 Nehmen wir beispielsweise an der SQL Server-Treiber erfordert den Namen des Servers und ein Flag für OEM-ANSI-Konvertierung und definiert die Werte für Server und OEMTOANSI für diese. Angenommen Sie auch, dass die Datenquelle für die Inventur der Microsoft® Code Seite Translator verwendet, um zwischen dem Windows® Latin 1 (1250) und Codepages Mehrsprachig (850) zu übersetzen. Die Werte unter dem Unterschlüssel Inventur könnte folgendermaßen aussehen:  
  
```  
Description : REG_SZ : Inventory database on server InvServ  
Driver : REG_SZ : C:\WINDOWS\SYSTEM32\SQLSRV32.DLL  
OEMTOANSI : REG_SZ : Yes  
Server : REG_SZ : InvServ  
TranslationDLL : REG_SZ : C:\WINDOWS\SYSTEM32\MSCPXL32.DLL  
TranslationName : REG_SZ : MS Code Page Translator  
TranslationOption : REG_SZ : 12500850  
```
