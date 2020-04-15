---
title: Prozedur Aufruf Escape Sequenz | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- escape sequences [ODBC], procedure call
- procedure call escape sequence [ODBC]
- ODBC escape sequences [ODBC], procedure call
ms.assetid: 269fbab0-e5f2-4a98-86c0-2d7b647acaae
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1194efe6a21c456a722ccd4352661c998f0316d9
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298220"
---
# <a name="procedure-call-escape-sequence"></a>Prozeduraufruf-Escapesequenz
ODBC verwendet Escapesequenzen für Prozeduraufrufe. Die Syntax dieser Escapesequenz ist wie folgt:  
  
 **•**[?=] *prozedur-name*[**(**[*parameter*][,[*parameter*]]...**call** **)**]**}**  
  
 In der BNF-Notation ist die Syntax wie folgt:  
  
 *ODBC-Prozedur-Flucht* ::=  
  
 &#124; *ODBC-esc-Initiator* [?=] *Aufrufprozedur ODBC-esc-terminator*  
  
 *Prozedur* ::= *prozedur-name* &#124; *procedure-name* (*procedure-parameter-list*)  
  
 *Prozedur-Bezeichner* ::= *benutzerdefinierter Name*  
  
 *prozedur-name* ::= *procedure-identifier*  
  
 &#124; *Besitzername*. *Prozedur-Bezeichner*  
  
 &#124; *Katalogname Katalog-Trennzeichen-Prozedur-Bezeichner* *procedure-identifier*  
  
 &#124; *Katalognamen-Katalogtrennzeichen* [*Besitzername*]. *Prozedur-Bezeichner*  
  
 (Die dritte Syntax ist nur gültig, wenn die Datenquelle keine Besitzer unterstützt.)  
  
 *Besitzername* ::= *benutzerdefinierter Name*  
  
 *Katalogname* ::= *benutzerdefinierter Name*  
  
 *Katalogtrennzeichen* ::= -*Implementierungsdefiniert*  
  
 (Das Katalogtrennzeichen wird über **SQLGetInfo** mit der Option SQL_CATALOG_NAME_SEPARATOR Informationen zurückgegeben.)  
  
 *procedure-parameter-list* ::= *procedure-parameter*  
  
 &#124; *Procedure-Parameter*, *procedure-parameter-list*  
  
 *procedure-parameter* ::= *dynamic-parameter* &#124; *literal* &#124; *empty-string*  
  
 *empty-string* ::=  
  
 *ODBC-esc-Initiator* ::=  
  
 *ODBC-esc-Terminator* ::=  
  
 (Wenn ein Prozedurparameter eine leere Zeichenfolge ist, verwendet die Prozedur den Standardwert für diesen Parameter.)  
  
 Um zu bestimmen, ob die Datenquelle Prozeduren und der Treiber die ODBC-Prozeduraufrufsyntax unterstützt, kann eine Anwendung **SQLGetInfo** mit dem SQL_PROCEDURES-Informationstyp aufrufen.
