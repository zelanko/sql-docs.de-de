---
title: Procedure Call Escape Sequence | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 914bd4759552680a57c345dc3a7c3bc1bcc103a6
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63188497"
---
# <a name="procedure-call-escape-sequence"></a>Prozeduraufruf-Escapesequenz
ODBC verwendet Escapesequenzen für Prozeduraufrufe an. Die Syntax dieser Escape-Sequenz lautet wie folgt aus:  
  
 **{**[? =]**Aufrufen** *Prozedurname*[**(**[*Parameter*] [, [*Parameter*]]... **)**]**}**  
  
 In BNF-Schreibweise lautet die Syntax:  
  
 *ODBC-procedure-escape* ::=  
  
 &#124;*Initiator der ODBC-esc* [? =] aufrufen *Prozedur ODBC-esc-Terminator*  
  
 *procedure* ::= *procedure-name* &#124; *procedure-name* (*procedure-parameter-list*)  
  
 *procedure-identifier* ::= *user-defined-name*  
  
 *procedure-name* ::= *procedure-identifier*  
  
 &#124; *owner-name*.*procedure-identifier*  
  
 &#124;*Katalognamen Katalogtrennzeichen* *Prozedur-ID*  
  
 &#124;*Katalognamen Katalogtrennzeichen* [*Besitzernamen*]. *Prozedur-ID*  
  
 (Die dritte Syntax ist nur gültig, wenn die Datenquelle Besitzer nicht unterstützt.)  
  
 *owner-name* ::= *user-defined-name*  
  
 *catalog-name* ::= *user-defined-name*  
  
 *catalog-separator* ::= {*implementation-defined*}  
  
 (Das Katalogtrennzeichen zurückgegeben wurde **SQLGetInfo** mit der Option SQL_CATALOG_NAME_SEPARATOR Informationen.)  
  
 *procedure-parameter-list* ::= *procedure-parameter*  
  
 &#124; *procedure-parameter*, *procedure-parameter-list*  
  
 *procedure-parameter* ::= *dynamic-parameter* &#124; *literal* &#124; *empty-string*  
  
 *empty-string* ::=  
  
 *ODBC-esc-initiator* ::= {  
  
 *ODBC-esc-terminator* ::= }  
  
 (Wenn Parameter einer Prozedur eine leere Zeichenfolge ist, verwendet die Prozedur den Standardwert für diesen Parameter.)  
  
 Um zu bestimmen, ob die Datenquelle, Verfahren unterstützt und der Treiber die Aufrufsyntax des ODBC-Prozedur unterstützt, eine Anwendung aufrufen kann **SQLGetInfo** mit dem Typ der SQL_PROCEDURES-Informationen.
