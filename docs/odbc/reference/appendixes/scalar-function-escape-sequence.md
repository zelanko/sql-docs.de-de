---
title: Escapesequenz für Skalarfunktionen | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305073"
---
# <a name="scalar-function-escape-sequence"></a>Skalarfunktion-Escapesequenz
ODBC verwendet Escapesequenzen für Skalarfunktionen. Die Syntax dieser Escapesequenz lautet wie folgt:  
  
```  
{fn scalar-function}  
```  
  
## <a name="remarks"></a>Bemerkungen  
 In der BNF-Notation lautet die Syntax wie folgt:  
  
 *ODBC-Scalar-Function-Escape* :: =  
  
 *ODBC-ESC-Initiator* FN *Scalar-Funktion ODBC-ESC-Terminator*  
  
 *Skalarfunktion* :: = *Funktionsname* (*Argument-List*)  
  
 (Die Definitionen für den nicht terminale *-Funktionsnamen* und den *Funktionsnamen* (*Argument-List*) werden aus der Liste der Skalarfunktionen in [Anhang E: skalare Funktionen](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md)abgeleitet.)  
  
 *ODBC-ESC-Initiator* :: = {  
  
 *ODBC-ESC-Terminator* :: =}  
  
 Um zu ermitteln, ob die Datenquelle Prozeduren unterstützt und der Treiber die ODBC-Prozedur Aufruf Syntax unterstützt, kann eine Anwendung **SQLGetInfo**aufrufen. Weitere Informationen finden Sie unter [Anhang E: Skalarfunktionen](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md).
