---
title: Unterschlüssel für ODBC-Konvertierungsprogramme | Microsoft-Dokumentation
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68093941"
---
# <a name="odbc-translators-subkey"></a>Unterschlüssel für ODBC-Konvertierungsprogramme
Die Werte unter dem Unterschlüssel für ODBC-Konvertierungsprogramme Auflisten der installierten Übersetzer. Das Format dieser Werte wird in der folgenden Tabelle dargestellt.  
  
|Name|Datentyp|Daten|  
|----------|---------------|----------|  
|*translator-desc*|REG_SZ|**installiert**|  
  
 Die *Translator-Desc* Name wird von der Translator-Entwickler definiert.  
  
 Nehmen wir beispielsweise an, dass ein Benutzer die Microsoft® Code Seite Translator und eine benutzerdefinierte ASCII zu EBCDIC-Konvertierer installiert ist. Die Werte unter dem Unterschlüssel für ODBC-Konvertierungsprogramme könnte folgendermaßen aussehen:  
  
```  
MS Code Page Translator: REG_SZ : Installed  
ASCII to EBCDIC: REG_SZ : Installed.  
```
