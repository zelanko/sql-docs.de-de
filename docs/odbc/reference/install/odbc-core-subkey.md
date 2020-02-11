---
title: Unterschlüssel für ODBC-Kern | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 98c9380083eb5a0ad796f436af271564676b757d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68094012"
---
# <a name="odbc-core-subkey"></a>Unterschlüssel für ODBC-Kernkomponenten
Der Wert unter dem ODBC Core-Unterschlüssel gibt die Verwendungs Anzahl für die Kernkomponenten an (Treiber-Manager, Cursor Bibliothek, Installer-DLL usw.). Das Format dieses Werts ist in der folgenden Tabelle dargestellt.  
  
|Name|Datentyp|Data|  
|----------|---------------|----------|  
|Usagecount|REG_DWORD|*count*|  
  
 Nehmen wir beispielsweise an, dass die ODBC-Kernkomponenten von den Setup Programmen für drei verschiedene Anwendungen und zwei unterschiedliche Treiber installiert wurden. Der Wert unter dem ODBC Core-Unterschlüssel lautet wie folgt:  
  
```  
UsageCount : REG_DWORD : 0x5  
```
