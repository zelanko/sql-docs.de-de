---
description: Unterschlüssel für ODBC-Konvertierungsprogramme
title: Unterschlüssel für ODBC-Übersetzer | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- translator subkey [ODBC]
- subkeys [ODBC], translator subkey
- registry entries for components [ODBC], translator subkey
ms.assetid: 6b170f1f-e263-4aac-9d49-8d0ca0470ca2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 46308518f1f806cea21bbb824312d5269f8b61e4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88499713"
---
# <a name="odbc-translators-subkey"></a>Unterschlüssel für ODBC-Konvertierungsprogramme
Mit den Werten unter dem Unterschlüssel ODBC-Übersetzer werden die installierten Konvertierer aufgelistet. Das Format dieser Werte wird in der folgenden Tabelle dargestellt.  
  
|Name|Datentyp|Daten|  
|----------|---------------|----------|  
|*Übersetzer*|REG_SZ|**Installiert**|  
  
 Der Name des Konvertierungs Programms wird vom Entwickler des *Konvertierers* definiert.  
  
 Nehmen wir beispielsweise an, dass ein Benutzer den Microsoft® Codepage Translator und einen benutzerdefinierten ASCII-Code für den EBCDIC-Konvertierer installiert hat. Die Werte unter dem Unterschlüssel ODBC-Übersetzer können wie folgt lauten:  
  
```  
MS Code Page Translator: REG_SZ : Installed  
ASCII to EBCDIC: REG_SZ : Installed.  
```
