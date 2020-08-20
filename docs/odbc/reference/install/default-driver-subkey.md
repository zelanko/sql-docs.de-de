---
description: Unterschlüssel für Standardtreiber
title: Standardtreiber-Unterschlüssel | Microsoft-Dokumentation
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
ms.openlocfilehash: d78cc54253d002c54510fdc47f46f10de9281b65
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88494553"
---
# <a name="default-driver-subkey"></a>Unterschlüssel für Standardtreiber
Der Standard Unterschlüssel enthält einen einzelnen Wert, der den von der Standarddaten Quelle verwendeten Treiber beschreibt. Das Format dieses Werts ist in der folgenden Tabelle dargestellt.  
  
|Name|Datentyp|Daten|  
|----------|---------------|----------|  
|**Treiber**|REG_SZ|*Default-Driver-Description*|  
  
 Der Name der *Standardtreiber Beschreibung* ist mit dem Namen des Werts unter dem Unterschlüssel ODBC-Treiber identisch, der den Treiber beschreibt.  
  
 Wenn die Standarddaten Quelle z. b. den SQL Server-Treiber verwendet, kann der Wert unter dem Standard Unterschlüssel wie folgt lauten:  
  
```  
Driver : REG_SZ : SQL Server  
```  
  
> [!NOTE]  
>  Der Standardtreiber, der im Standard Unterschlüssel enthalten ist, kann entweder auf einen Standardbenutzer-DSN oder auf einen standardmäßigen System-DSN verweisen. Wenn sowohl ein Standardbenutzer-DSN als auch ein standardmäßiger System-DSN erstellt wurde, wird der Standardtreiber von dem zuletzt erstellten DSN festgelegt, sodass es sich möglicherweise nicht um einen gültigen Eintrag für den DSN handelt, der zuerst erstellt wurde.
