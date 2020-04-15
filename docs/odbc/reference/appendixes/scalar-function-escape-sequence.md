---
title: Skalar Funktion Escape-Sequenz | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- escape sequences [ODBC], scalar function
- scalar functions [ODBC], escape sequences
- ODBC escape sequences [ODBC], scalar function
ms.assetid: aaf5d516-e090-445f-8839-9e39581c69c7
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8347b8e6f0fab6dffc5295fb3b8260a6a56ed123
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305073"
---
# <a name="scalar-function-escape-sequence"></a>Skalarfunktion-Escapesequenz
ODBC verwendet Escape-Sequenzen für Skalarfunktionen. Die Syntax dieser Escapesequenz ist wie folgt:  
  
```  
{fn scalar-function}  
```  
  
## <a name="remarks"></a>Bemerkungen  
 In der BNF-Notation ist die Syntax wie folgt:  
  
 *ODBC-scalar-function-escape* ::=  
  
 *ODBC-esc-Initiator* fn *scalar-Funktion ODBC-esc-terminator*  
  
 *scalar-Funktion* ::= *Funktionsname* (*Argument-Liste*)  
  
 (Die Definitionen für den *Nicht-Terminals-Funktionsnamen* und *Funktionsnamen* (*Argument-Liste*) werden aus der Liste der skalaren Funktionen in [Anhang E: Skalarfunktionen](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md)abgeleitet.)  
  
 *ODBC-esc-Initiator* ::=  
  
 *ODBC-esc-Terminator* ::=  
  
 Um zu bestimmen, ob die Datenquelle Prozeduren und der Treiber die ODBC-Prozeduraufrufsyntax unterstützt, kann eine Anwendung **SQLGetInfo**aufrufen. Weitere Informationen finden Sie in [Anhang E: Skalarfunktionen](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md).
