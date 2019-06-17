---
title: Unterschlüssel für ODBC Core | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: 5c95c4e28a5f32131307daeaa61e214af887b577
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63069699"
---
# <a name="odbc-core-subkey"></a>Unterschlüssel für ODBC-Kernkomponenten
Der Wert unter dem Unterschlüssel für ODBC Core bietet den Verwendungszähler für die Core-Komponenten (Treiber-Manager, Cursor-Bibliothek, Installationsprogramm-DLL und So weiter). Das Format dieses Werts wird in der folgenden Tabelle dargestellt.  
  
|Name|Datentyp|Daten|  
|----------|---------------|----------|  
|UsageCount|REG_DWORD|*count*|  
  
 Nehmen wir beispielsweise an, dass die ODBC-Kernkomponenten von die Setupprogramme für drei verschiedene Anwendungen und zwei verschiedenen Treiber installiert wurden. Es wäre der Wert unter dem Unterschlüssel für ODBC Core:  
  
```  
UsageCount : REG_DWORD : 0x5  
```
