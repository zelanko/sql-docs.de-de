---
title: WIE Sie die Escape-Sequenz | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: 65447904f32b7e0457ed807f18e942b334ddc236
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47626618"
---
# <a name="like-escape-sequence"></a>LIKE-Escapesequenz
ODBC verwendet Escape-Sequenzen, für die LIKE-Klausel. Die Syntax dieser Escape-Sequenz lautet wie folgt aus:  
  
```  
{'escape-character'}  
```  
  
## <a name="remarks"></a>Hinweise  
 In BNF-Schreibweise lautet die Syntax:  
  
 *ODBC-ähnliche-Escapesequenz* :: =  
  
 *Initiator der ODBC-esc* Escape "*Escapezeichen*" *ODBC-esc-Terminator*  
  
 *Escape-Zeichen* :: = *Zeichen*  
  
 *Initiator der ODBC-esc* :: = {  
  
 *ODBC-esc-Terminator* :: =}  
  
 Um festzustellen, ob der Treiber die LIKE Escape unterstützt Sequenz, die eine Anwendung aufrufen kann **SQLGetInfo** mit dem Typ der SQL_LIKE_ESCAPE_CLAUSE-Informationen.
