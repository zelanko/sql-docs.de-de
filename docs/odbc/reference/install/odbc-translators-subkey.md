---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7d26f2d33d81e08cfe4bddff9b2260bd2f098f00
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68093941"
---
# <a name="odbc-translators-subkey"></a>Unterschlüssel für ODBC-Konvertierungsprogramme
Mit den Werten unter dem Unterschlüssel ODBC-Übersetzer werden die installierten Konvertierer aufgelistet. Das Format dieser Werte wird in der folgenden Tabelle dargestellt.  
  
|Name|Datentyp|Data|  
|----------|---------------|----------|  
|*Übersetzer*|REG_SZ|**Lierter**|  
  
 Der Name des Konvertierungs Programms wird vom Entwickler des *Konvertierers* definiert.  
  
 Nehmen wir beispielsweise an, dass ein Benutzer den Microsoft® Codepage Translator und einen benutzerdefinierten ASCII-Code für den EBCDIC-Konvertierer installiert hat. Die Werte unter dem Unterschlüssel ODBC-Übersetzer können wie folgt lauten:  
  
```  
MS Code Page Translator: REG_SZ : Installed  
ASCII to EBCDIC: REG_SZ : Installed.  
```
