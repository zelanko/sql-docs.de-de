---
title: Unterschlüssel für Standardtreiber default | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e82644d3bddab5d4f6fde6f7103bd9731872bab9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68094191"
---
# <a name="default-driver-subkey"></a>Unterschlüssel für Standardtreiber
Der Standard-Unterschlüssel enthält einen einzelnen Wert, der den Treiber, die von der Standarddatenquelle verwendete beschreibt. Das Format dieses Werts wird in der folgenden Tabelle dargestellt.  
  
|Name|Datentyp|Daten|  
|----------|---------------|----------|  
|**Treiber**|REG_SZ|*Standard-Treiber-Beschreibung*|  
  
 Die *Treiber standardbeschreibung* Name ist identisch mit den Namen des Werts unter der ODBC-Treiber-Unterschlüssel, die den Treiber beschreibt.  
  
 Beispielsweise, wenn die Standarddatenquelle SQL Server-Treiber verwendet, der Wert unter dem Unterschlüssel Standardwert möglicherweise:  
  
```  
Driver : REG_SZ : SQL Server  
```  
  
> [!NOTE]  
>  Der Standardtreiber, die innerhalb des Unterschlüssels "Standard" kann entweder ein Standardbenutzer DSN oder einen Standardsystem-DSN verweisen. Wenn sowohl ein Standardsystem als auch eine Standardbenutzer-DSN DSN erstellt wurden, der Standardtreiber richtet sich nach der DSN, der zuletzt erstellt wurde, damit es ein gültiger Eintrag für den DSN möglicherweise nicht, die zuerst erstellt wurde.
