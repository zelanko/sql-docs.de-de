---
description: Unterschlüssel für Datenquellenspezifikationen
title: Unterschlüssel der Datenquellen Spezifikation | Microsoft-Dokumentation
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
ms.openlocfilehash: 8fabfd07779f74945bf647d20075de0cc057710b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88494565"
---
# <a name="data-source-specification-subkeys"></a>Unterschlüssel für Datenquellenspezifikationen
Jede Datenquelle, die im Unterschlüssel für ODBC-Datenquellen aufgelistet ist, verfügt über einen eigenen Unterschlüssel. Dieser Unterschlüssel hat denselben Namen wie der entsprechende Wert unter dem Unterschlüssel für ODBC-Datenquellen. Die Werte unter diesem Unterschlüssel müssen die Treiber-DLL auflisten und eine Beschreibung der Datenquelle auflisten. Wenn der Treiber Konvertierer unterstützt, können die Werte den Namen eines Standard Konvertierers, die standardmäßige Übersetzungs-DLL und die Standard Übersetzungs Option auflisten. Die Werte können auch andere Informationen auflisten, die der Treiber zum Herstellen einer Verbindung mit der Datenquelle benötigt. Beispielsweise ist für den Treiber möglicherweise ein Servername, ein Datenbankname oder ein Schema Name erforderlich.  
  
 Die Formate der Werte sind wie in der folgenden Tabelle dargestellt. Nur der Treiber Wert ist erforderlich.  
  
|Name|Datentyp|Daten|  
|----------|---------------|----------|  
|BESCHREIBUNG|REG_SZ|*Beschreibung*|  
|Treiber|REG_SZ|*Treiber-DLL-Pfad*|  
|TranslationDLL|REG_SZ|*Translator-dll-Pfad*|  
|TranslationName|REG_SZ|*Translator-Name*|  
|"TranslationOption"|REG_SZ|*Translation-Option*|  
|*Name des Opt-Werts*|*Opt-Value-Type*|*Opt-Value-Data*|  
  
 Nehmen wir beispielsweise an, dass der SQL Server Treiber den Servernamen und ein Flag für die Konvertierung von OEM zu ANSI benötigt und die Server-und OemToAnsi-Werte für diese definiert. Angenommen, die Inventur Datenquelle verwendet den Microsoft® Codepage Translator, um zwischen den Codepages für Windows® Latin 1 (1250) und mehrsprachige (850) zu übersetzen. Die Werte unter dem Inventur Unterschlüssel können wie folgt lauten:  
  
```  
Description : REG_SZ : Inventory database on server InvServ  
Driver : REG_SZ : C:\WINDOWS\SYSTEM32\SQLSRV32.DLL  
OEMTOANSI : REG_SZ : Yes  
Server : REG_SZ : InvServ  
TranslationDLL : REG_SZ : C:\WINDOWS\SYSTEM32\MSCPXL32.DLL  
TranslationName : REG_SZ : MS Code Page Translator  
TranslationOption : REG_SZ : 12500850  
```
