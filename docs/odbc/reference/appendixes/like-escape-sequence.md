---
title: LIKE-Escapesequenz | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 629ceaf666ae732d0838a216272c308dcb5b5658
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68041714"
---
# <a name="like-escape-sequence"></a>LIKE-Escapesequenz
ODBC verwendet Escapesequenzen für die LIKE-Klausel. Die Syntax dieser Escapesequenz lautet wie folgt:  
  
```  
{'escape-character'}  
```  
  
## <a name="remarks"></a>Bemerkungen  
 In der BNF-Notation lautet die Syntax wie folgt:  
  
 *ODBC-like-Escape* :: =  
  
 *ODBC-ESC-Initiator-* *Escapezeichen*' *ODBC-ESC-Terminator* '  
  
 *Escape-Zeichen* :: =- *Zeichen*  
  
 *ODBC-ESC-Initiator* :: = {  
  
 *ODBC-ESC-Terminator* :: =}  
  
 Um zu ermitteln, ob der Treiber die like-Escapesequenz unterstützt, kann eine Anwendung **SQLGetInfo** mit dem SQL_LIKE_ESCAPE_CLAUSE Informationstyp aufrufen.
