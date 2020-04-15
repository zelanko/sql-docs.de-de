---
title: Zuordnen der Cursorattribute1 Informationstypen | Microsoft Docs
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
ms.openlocfilehash: d70cf0a93a6c6160faeb0afe991b2adfff11b8f1
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301043"
---
# <a name="mapping-the-cursor-attributes1-information-types"></a>Zuordnen der Informationstypen „Cursor Attributes1“
Wenn ein ODBC 3. *x-Anwendung* ruft **SQLGetInfo** in einem ODBC 2 *.x-Treiber* mit dem SQL_XXXX_CURSOR_ATTRIBUTES1-Informationstyp auf (für dynamische, reine Vorwärts-, Keyset-Treiber- oder statische Cursor) hängt die Einstellung der vom Treiber-Manager zurückgegebenen Bits davon ab, was der ODBC 2. *x-Treiber* kehrt für den entsprechenden ODBC 2 zurück. *x* x-Informationstypen. Die Bits werden wie in der folgenden Tabelle dargestellt festgelegt.  
  
|Bit in<br /><br /> SQL_XXXX_CURSOR_ATTRIBUTES1|Cursortyp|ODBC 2. *x* Informationen<br /><br /> type|  
|-----------------------------------------------|-----------------|-------------------------------------|  
|SQL_CA1_NEXT|All|SQL_FETCH_DIRECTION|  
|SQL_CA1_ABSOLUTE SQL_CA1_RELATIVE SQL_CA1_BOOKMARK|Dynamisch, Keyset-Treiber, statisch|SQL_FETCH_DIRECTION|  
|SQL_CA1_LOCK_NO_CHANGE SQL_CA1_LOCK_UNLOCK SQL_CA1_LOCK_EXCLUSIVE|Dynamisch, Keyset-Treiber, statisch|SQL_LOCK_TYPES|  
|SQL_CA1_POSITIONED_UPDATE SQL_CA1_POSITIONED_DELETE SQL_CA1_SELECT_FOR_UPDATE|All|SQL_POSITIONED_STATEMENTS|  
|SQL_CA1_POS_POSITION SQL_CA1_POS_DELETE SQL_CA1_POS_REFRESH SQL_CA1_POS_BULK_ADD|Dynamisch, Keyset-Treiber, statisch|SQL_POS_OPERATIONS|
