---
title: ODBC Core Subkey | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- subkeys [ODBC], core subkey
- registry entries for components [ODBC], core subkey
- core subkey [ODBC]
ms.assetid: 055b31fc-f96c-450b-a596-d4570079fbf2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9e6bfcf3c1efa87076e6d3e27a438cde6f794157
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304054"
---
# <a name="odbc-core-subkey"></a>Unterschlüssel für ODBC-Kernkomponenten
Der Wert unter dem Unterschlüssel ODBC Core gibt die Verwendungsanzahl für die Kernkomponenten an (Treiber-Manager, Cursorbibliothek, Installations-DLL usw.). Das Format dieses Werts wird in der folgenden Tabelle angezeigt.  
  
|Name|Datentyp|Daten|  
|----------|---------------|----------|  
|UsageCount|REG_DWORD|*count*|  
  
 Angenommen, die ODBC Core-Komponenten wurden von den Setup-Programmen für drei verschiedene Anwendungen und zwei verschiedene Treiber installiert. Der Wert unter dem Unterschlüssel ODBC Core wäre:  
  
```  
UsageCount : REG_DWORD : 0x5  
```
