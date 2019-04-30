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
manager: craigg
ms.openlocfilehash: 43be1c5e75998903ff4e64fc5f4230818a873ffc
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63281124"
---
# <a name="odbc-drivers-subkey"></a>Unterschlüssel für ODBC-Treiber
Die Werte unter dem Unterschlüssel für ODBC-Treiber Listen die installierten Treiber. Das Format dieser Werte wird in der folgenden Tabelle dargestellt.  
  
|Name|Datentyp|Daten|  
|----------|---------------|----------|  
|*driver-description*|REG_SZ|**installiert**|  
  
 Die *treiberbeschreibung* Name wird vom Treiber Entwickler definiert. Es ist in der Regel der Name des DBMS mit dem Treiber verknüpft ist.  
  
 Nehmen wir beispielsweise an, dass die Treiber für formatierten Text-Dateien und SQL Server installiert wurden. Die Werte unter dem Unterschlüssel für ODBC-Treiber können Folgendes sein:  
  
```  
Text : REG_SZ : Installed  
SQL Server : REG_SZ : Installed  
```
