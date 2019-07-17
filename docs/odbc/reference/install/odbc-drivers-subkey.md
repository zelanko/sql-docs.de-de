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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68093980"
---
# <a name="odbc-drivers-subkey"></a>Unterschlüssel für ODBC-Treiber
Die Werte unter dem Unterschlüssel für ODBC-Treiber Listen die installierten Treiber. Das Format dieser Werte wird in der folgenden Tabelle dargestellt.  
  
|Name|Datentyp|Daten|  
|----------|---------------|----------|  
|*Treiber-Beschreibung*|REG_SZ|**installiert**|  
  
 Die *treiberbeschreibung* Name wird vom Treiber Entwickler definiert. Es ist in der Regel der Name des DBMS mit dem Treiber verknüpft ist.  
  
 Nehmen wir beispielsweise an, dass die Treiber für formatierten Text-Dateien und SQL Server installiert wurden. Die Werte unter dem Unterschlüssel für ODBC-Treiber können Folgendes sein:  
  
```  
Text : REG_SZ : Installed  
SQL Server : REG_SZ : Installed  
```
