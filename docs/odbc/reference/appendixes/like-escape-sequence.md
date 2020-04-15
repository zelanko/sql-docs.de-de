---
title: LIKE Escape Sequenz | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC escape sequences [ODBC], LIKE
- LIKE escape sequence [ODBC]
- escape sequences [ODBC], LIKE
ms.assetid: 798d75ea-be9d-4bef-b297-318bc327f1ca
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 517c21f7b64fa7ceb662af9839a9fed1a1e6eff6
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304921"
---
# <a name="like-escape-sequence"></a>LIKE-Escapesequenz
ODBC verwendet Escapesequenzen für die LIKE-Klausel. Die Syntax dieser Escapesequenz ist wie folgt:  
  
```  
{'escape-character'}  
```  
  
## <a name="remarks"></a>Bemerkungen  
 In der BNF-Notation ist die Syntax wie folgt:  
  
 *ODBC-ähnliche Flucht* ::=  
  
 *ODBC-esc-Initiator* Escape '*Escape-Zeichen*' *ODBC-esc-Terminator*  
  
 *Escape-Zeichen* ::= *Zeichen*  
  
 *ODBC-esc-Initiator* ::=  
  
 *ODBC-esc-Terminator* ::=  
  
 Um festzustellen, ob der Treiber die LIKE-Escapesequenz unterstützt, kann eine Anwendung **SQLGetInfo** mit dem SQL_LIKE_ESCAPE_CLAUSE-Informationstyp aufrufen.
