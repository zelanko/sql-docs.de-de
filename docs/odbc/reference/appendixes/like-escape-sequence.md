---
description: LIKE-Escapesequenz
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 19d20f80f9fea4df2c508ec4ec4bcc2ee6718986
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429642"
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
