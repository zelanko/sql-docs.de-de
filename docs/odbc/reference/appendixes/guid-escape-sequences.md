---
title: GUID Escape Sequenzen | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC escape sequences [ODBC], GUID
- escape sequences [ODBC], guid
- guid escape sequence [ODBC]
ms.assetid: 71d43ef9-4a31-493e-b9e0-f864e9ef3ce6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 44907bfbd884bf361ce5f2ab8b3f6d8a247aba44
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306971"
---
# <a name="guid-escape-sequences"></a>GUID-Escapesequenzen
ODBC verwendet Escapesequenzen für GUID-Literale. Die Syntax dieser Escapesequenz ist wie folgt:  
  
```  
{guid 'nnnnnnnn-nnnn-nnnn-nnnn-nnnnnnnnnnnn'}  
```  
  
## <a name="remarks"></a>Bemerkungen  
 In der BNF-Notation ist die Syntax wie folgt:  
  
 *ODBC-guid-escape* ::=  
     *ODBC-esc-Initiator guid* '*guid-value*' *ODBC-esc-terminator*  
  
 *ODBC-esc-Initiator* ::=  
  
 *ODBC-esc-Terminator* ::=  
  
 *guid-wert* ::= *clock-low-value guid-separator clock-middle-value guid-separator clock-high-value guid-separator clock-seq-value guid-separator node-value*  
  
 *guid-separator* ::= -  
  
 *Takt-Niedrigwert* ::= hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit *hex_digit hex_digit hex_digit*  
  
 *Takt-Mittelwert* ::= *hex_digit hex_digit hex_digit hex_digit*  
  
 *Uhr-High-Value* ::= *hex_digit hex_digit hex_digit hex_digit*  
  
 *clock-seq-wert* ::= *hex_digit hex_digit hex_digit hex_digit hex_digit*  
  
 *clock-node-value* ::= hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit *hex_digit hex_digit*  
  
 *hex_digit* ::= 0 &#124; 1 &#124; 2 &#124; 3 &#124; 4 &#124; 5 &#124; &#124; 7 7 &#124; 8 &#124; 9 &#124; A &#124; &#124; B &#124; C &#124; D &#124; E &#124; F  
  
 Die GUID-Literal-Escapesequenz wird unterstützt, wenn der GUID-Datentyp von der Datenquelle unterstützt wird. Eine Anwendung sollte **SQLGetTypeInfo** aufrufen, um zu bestimmen, ob dieser Datentyp unterstützt wird.
