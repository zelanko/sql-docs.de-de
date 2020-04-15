---
title: Standardtreiber-Unterschlüssel | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- default subkey [ODBC]
- registry entries for components [ODBC], default subkey
- subkeys [ODBC], default subkey
- drivers subkey [ODBC]
ms.assetid: 9e58b24f-ebfc-4286-a272-0843b4d6f2d5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bb134d670964e352d94c13474d8a72fa4bd494ba
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301053"
---
# <a name="default-driver-subkey"></a>Unterschlüssel für Standardtreiber
Der Standardunterschlüssel enthält einen einzelnen Wert, der den treiber beschreibt, der von der Standarddatenquelle verwendet wird. Das Format dieses Werts wird in der folgenden Tabelle angezeigt.  
  
|Name|Datentyp|Daten|  
|----------|---------------|----------|  
|**Treiber**|REG_SZ|*Default-Driver-Beschreibung*|  
  
 Der Name der *Standardtreiberbeschreibung* entspricht dem Namen des Werts unter dem Unterschlüssel ODBC-Treiber, der den Treiber beschreibt.  
  
 Wenn die Standarddatenquelle beispielsweise den SQL Server-Treiber verwendet, könnte der Wert unter dem Standardunterschlüssel wie:  
  
```  
Driver : REG_SZ : SQL Server  
```  
  
> [!NOTE]  
>  Der im Standardunterschlüssel enthaltene Standardtreiber kann sich entweder auf einen Standardbenutzer-DSN oder auf ein Standardsystem-DSN beziehen. Wenn sowohl ein Standardbenutzer-DSN als auch ein Standardsystem-DSN erstellt wurden, wird der Standardtreiber durch den zuletzt erstellten DSN bestimmt, sodass es sich möglicherweise nicht um einen gültigen Eintrag für den Zuersterstellten DSN handelt.
