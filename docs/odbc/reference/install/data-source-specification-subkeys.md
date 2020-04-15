---
title: Unterschlüssel für die Datenquellenspezifikation | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 281377c307f3f3750e87bf5dc988beb7660067af
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300340"
---
# <a name="data-source-specification-subkeys"></a>Unterschlüssel für Datenquellenspezifikationen
Jede Datenquelle, die im Unterschlüssel ODBC-Datenquellen aufgeführt ist, verfügt über einen eigenen Unterschlüssel. Dieser Unterschlüssel hat denselben Namen wie der entsprechende Wert unter dem Unterschlüssel ODBC-Datenquellen. Die Werte unter diesem Unterschlüssel müssen die Treiber-DLL auflisten und möglicherweise eine Beschreibung der Datenquelle auflisten. Wenn der Treiber Übersetzer unterstützt, können die Werte den Namen eines Standardübersetzers, die Standardübersetzungs-DLL und die Standardübersetzungsoption auflisten. Die Werte können auch andere Informationen auflisten, die vom Treiber benötigt werden, um eine Verbindung mit der Datenquelle herzustellen. Der Treiber kann z. B. einen Servernamen, einen Datenbanknamen oder einen Schemanamen erfordern.  
  
 Die Formate der Werte sind wie in der folgenden Tabelle dargestellt. Es ist nur der Treiberwert erforderlich.  
  
|Name|Datentyp|Daten|  
|----------|---------------|----------|  
|BESCHREIBUNG|REG_SZ|*Beschreibung*|  
|Treiber|REG_SZ|*treiber-DLL-Pfad*|  
|ÜbersetzungDLL|REG_SZ|*Übersetzer-DLL-Pfad*|  
|TranslationName|REG_SZ|*Übersetzername*|  
|TranslationOption|REG_SZ|*Übersetzungsoption*|  
|*opt-value-name*|*opt-value-Typ*|*opt-value-daten*|  
  
 Angenommen, der SQL Server-Treiber benötigt den Servernamen und ein Flag für die OEM-in-ANSI-Konvertierung und definiert die Server- und OEMTOANSI-Werte für diese. Angenommen, die Datenquelle "Inventar" verwendet den Microsoft® Codepage-Übersetzer, um zwischen den Codepages Windows® Latin 1 (1250) und Multilingual (850) zu übersetzen. Die Werte unter dem Unterschlüssel "Inventar" können wie folgt lauten:  
  
```  
Description : REG_SZ : Inventory database on server InvServ  
Driver : REG_SZ : C:\WINDOWS\SYSTEM32\SQLSRV32.DLL  
OEMTOANSI : REG_SZ : Yes  
Server : REG_SZ : InvServ  
TranslationDLL : REG_SZ : C:\WINDOWS\SYSTEM32\MSCPXL32.DLL  
TranslationName : REG_SZ : MS Code Page Translator  
TranslationOption : REG_SZ : 12500850  
```
