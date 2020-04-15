---
title: ODBC-Treiber-Subkey | Microsoft Docs
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
ms.openlocfilehash: dd1f8d3293e35a543cce6b5079d9c6e10a331a88
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304031"
---
# <a name="odbc-drivers-subkey"></a>Unterschlüssel für ODBC-Treiber
Die Werte unter dem Unterschlüssel ODBC-Treiber listen die installierten Treiber auf. Das Format dieser Werte wird in der folgenden Tabelle angezeigt.  
  
|Name|Datentyp|Daten|  
|----------|---------------|----------|  
|*Treiberbeschreibung*|REG_SZ|**Installiert**|  
  
 Der Name der *Treiberbeschreibung* wird vom Treiberentwickler definiert. Es ist in der Regel der Name des DBMS, das dem Treiber zugeordnet ist.  
  
 Angenommen, es wurden Treiber für formatierte Textdateien und SQL Server installiert. Die Werte unter dem Unterschlüssel ODBC-Treiber können wie:  
  
```  
Text : REG_SZ : Installed  
SQL Server : REG_SZ : Installed  
```
