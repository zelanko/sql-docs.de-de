---
description: Zuordnen der Informationstypen „Cursor Attributes1“
title: Mapping der Cursor Attributes1-Informationstypen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- compatibility [ODBC], mapping cursor attributes1 information types
- application upgrades [ODBC], mapping cursor attributes1 information types
- mapping cursor attributes1 information types [ODBC]
- backward compatibility [ODBC], mapping cursor attributes1 information types
- upgrading applications [ODBC], mapping cursor attributes1 information types
ms.assetid: 9f112449-ca86-45ac-a865-e6174d67f91b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fcd4c1eaa6ddd2e6db4f2634cc22d3148e7977cf
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88461402"
---
# <a name="mapping-the-cursor-attributes1-information-types"></a>Zuordnen der Informationstypen „Cursor Attributes1“
Bei ODBC 3. die *x* -Anwendung ruft **SQLGetInfo** in einem ODBC 2 *. x* -Treiber mit dem SQL_XXXX_CURSOR_ATTRIBUTES1 Informationstyp auf (bei dynamischen, vorwärts gerichteten, keysettreibern oder statischen Cursorn), ist die Einstellung der Bits, die vom Treiber-Manager zurückgegeben werden, davon abhängig, was ODBC 2 ist. der *x* -Treiber gibt für das entsprechende ODBC 2 zurück. *x* -Informationstypen. Die Bits werden wie in der folgenden Tabelle dargestellt festgelegt.  
  
|Bit in<br /><br /> SQL_XXXX_CURSOR_ATTRIBUTES1|Cursortyp|ODBC 2. *x* -Informationen<br /><br /> type|  
|-----------------------------------------------|-----------------|-------------------------------------|  
|SQL_CA1_NEXT|All|SQL_FETCH_DIRECTION|  
|SQL_CA1_ABSOLUTE SQL_CA1_RELATIVE SQL_CA1_BOOKMARK|Dynamisch, keysettreiber, statisch|SQL_FETCH_DIRECTION|  
|SQL_CA1_LOCK_NO_CHANGE SQL_CA1_LOCK_UNLOCK SQL_CA1_LOCK_EXCLUSIVE|Dynamisch, keysettreiber, statisch|SQL_LOCK_TYPES|  
|SQL_CA1_POSITIONED_UPDATE SQL_CA1_POSITIONED_DELETE SQL_CA1_SELECT_FOR_UPDATE|All|SQL_POSITIONED_STATEMENTS|  
|SQL_CA1_POS_POSITION SQL_CA1_POS_DELETE SQL_CA1_POS_REFRESH SQL_CA1_POS_BULK_ADD|Dynamisch, keysettreiber, statisch|SQL_POS_OPERATIONS|
