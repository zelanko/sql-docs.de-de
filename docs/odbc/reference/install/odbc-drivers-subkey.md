---
description: Unterschlüssel für ODBC-Treiber
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b950a352c3da69a2a8de9a89f7bbebf87e0a597a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88448920"
---
# <a name="odbc-drivers-subkey"></a>Unterschlüssel für ODBC-Treiber
Mit den Werten unter dem Unterschlüssel ODBC-Treiber werden die installierten Treiber aufgelistet. Das Format dieser Werte wird in der folgenden Tabelle dargestellt.  
  
|Name|Datentyp|Daten|  
|----------|---------------|----------|  
|*Treiber Beschreibung*|REG_SZ|**Installiert**|  
  
 Der *Treiber Beschreibungs* Name wird vom Treiber Entwickler definiert. Dies ist normalerweise der Name des DBMS, das dem Treiber zugeordnet ist.  
  
 Nehmen wir beispielsweise an, dass Treiber für formatierte Textdateien und SQL Server installiert wurden. Die Werte unter dem Unterschlüssel ODBC-Treiber können wie folgt lauten:  
  
```  
Text : REG_SZ : Installed  
SQL Server : REG_SZ : Installed  
```
