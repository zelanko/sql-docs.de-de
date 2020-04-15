---
title: ODBC Übersetzer Subkey | Microsoft Docs
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
ms.openlocfilehash: 617416adfcddfbf041c48acbf83cb9589e34ae27
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81296220"
---
# <a name="odbc-translators-subkey"></a>Unterschlüssel für ODBC-Konvertierungsprogramme
Die Werte unter dem Unterschlüssel ODBC Translators listen die installierten Übersetzer auf. Das Format dieser Werte wird in der folgenden Tabelle angezeigt.  
  
|Name|Datentyp|Daten|  
|----------|---------------|----------|  
|*übersetzer-desc*|REG_SZ|**Installiert**|  
  
 Der *Name translator-desc* wird vom Übersetzerentwickler definiert.  
  
 Angenommen, ein Benutzer hat den Microsoft® Codepage Translator und einen benutzerdefinierten ASCII-zu-EBCDIC-Übersetzer installiert. Die Werte unter dem Unterschlüssel ODBC Translators können wie folgt lauten:  
  
```  
MS Code Page Translator: REG_SZ : Installed  
ASCII to EBCDIC: REG_SZ : Installed.  
```
