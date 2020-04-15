---
title: Äußere Join Escape Sequenz | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- outer join escape sequence [ODBC]
- escape sequences [ODBC], outer join
- ODBC escape sequences [ODBC], outer join
ms.assetid: 2cfd1525-6677-4d36-9b9e-730496853750
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 37ce446328d263f492cdfd369f6e8f9f64fe6dfc
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303611"
---
# <a name="outer-join-escape-sequence"></a>Escapesequenz für äußere Verknüpfungen
ODBC verwendet Escapesequenzen für äußere Verknüpfungen. Die Syntax dieser Escapesequenz ist wie folgt:  
  
```  
{oj outer-join}  
```  
  
## <a name="remarks"></a>Bemerkungen  
 In der BNF-Notation ist die Syntax wie folgt:  
  
 *ODBC-outer-join-escape* ::=  
  
 *ODBC-esc-Initiator* oj *outer-join ODBC-esc-terminator*  
  
 *äußere Verknüpfung* ::= *Tabellenname* [*Korrelationsname*] "LEFT &#124; RECHTS &#124; FULL"  
  
 OUTER*JOIN- Tabellenname* [*Korrelationsname*] *&#124;-Außenverbindung*  
  
 *Suche-*  
  
 *Zustand*  
  
 *Korrelationsname* ::= *benutzerdefinierter Name*  
  
 *ODBC-esc-Initiator* ::=  
  
 *ODBC-esc-Terminator* ::=  
  
 Um zu bestimmen, welche Teile dieser Anweisung unterstützt werden, ruft eine Anwendung **SQLGetInfo** mit dem SQL_OJ_CAPABILITIES-Informationstyp auf. Für äußere Verknüpfungen darf die Suchbedingung nur die *Join-Bedingung* zwischen den angegebenen *Tabellennamen*enthalten.
