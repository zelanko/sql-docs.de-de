---
title: Unterschlüssel für ODBC-Treiber | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- subkeys [ODBC], drivers subkey
- registry entries for components [ODBC], drivers subkey
- drivers subkey [ODBC]
ms.assetid: 8edbf68f-d05d-4d77-92f6-e9500008f520
author: MightyPen
ms.author: genemi
ms.openlocfilehash: eb54ba7becad42d8d9d2c2870c02db37a3c7d89f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68093980"
---
# <a name="odbc-drivers-subkey"></a>Unterschlüssel für ODBC-Treiber
Mit den Werten unter dem Unterschlüssel ODBC-Treiber werden die installierten Treiber aufgelistet. Das Format dieser Werte wird in der folgenden Tabelle dargestellt.  
  
|Name|Datentyp|Data|  
|----------|---------------|----------|  
|*Treiber Beschreibung*|REG_SZ|**Lierter**|  
  
 Der *Treiber Beschreibungs* Name wird vom Treiber Entwickler definiert. Dies ist normalerweise der Name des DBMS, das dem Treiber zugeordnet ist.  
  
 Nehmen wir beispielsweise an, dass Treiber für formatierte Textdateien und SQL Server installiert wurden. Die Werte unter dem Unterschlüssel ODBC-Treiber können wie folgt lauten:  
  
```  
Text : REG_SZ : Installed  
SQL Server : REG_SZ : Installed  
```
