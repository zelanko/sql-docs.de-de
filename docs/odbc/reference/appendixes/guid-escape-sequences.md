---
title: GUID-Escapesequenzen | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bf41671abc6393a18fad06e1debd297fed1f04c5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63188957"
---
# <a name="guid-escape-sequences"></a>GUID-Escapesequenzen
ODBC verwendet Escapesequenzen für GUID-Literale. Die Syntax dieser Escape-Sequenz lautet wie folgt aus:  
  
```  
{guid 'nnnnnnnn-nnnn-nnnn-nnnn-nnnnnnnnnnnn'}  
```  
  
## <a name="remarks"></a>Hinweise  
 In BNF-Schreibweise lautet die Syntax:  
  
 *ODBC-guid-escape* ::=  
     *Initiator-ODBC-esc-Guid* "*Guid-Wert*" *ODBC-esc-Terminator*  
  
 *ODBC-esc-initiator* ::= {  
  
 *ODBC-esc-terminator* ::= }  
  
 *GUID-Wert* :: = *Uhr mit geringem Wert Guid-Trennzeichen-Uhr-Middle-Guid-Trennzeichen-Uhr-High-Value-Guid-Trennzeichen-Uhr-Seq-Guid-Trennzeichen Knotenwert*  
  
 *guid-separator* ::= -  
  
 *Clock-mit geringem Wert* :: = *Hex_digit Hex_digit Hex_digit Hex_digit Hex_digit Hex_digit Hex_digit Hex_digit*  
  
 *Clock-Middle-Value* :: = *Hex_digit Hex_digit Hex_digit Hex_digit*  
  
 *Clock-High-Value* :: = *Hex_digit Hex_digit Hex_digit Hex_digit*  
  
 *clock-seq-value* ::= *hex_digit hex_digit hex_digit hex_digit*  
  
 *Clock-Knotenwert* :: = *Hex_digit Hex_digit Hex_digit Hex_digit Hex_digit Hex_digit Hex_digit Hex_digit Hex_digit Hex_digit Hex_digit Hex_digit*  
  
 *hex_digit* ::= 0 &#124; 1 &#124; 2 &#124; 3 &#124; 4 &#124; 5 &#124; 6 &#124; 7 &#124; 8 &#124; 9 &#124; A &#124; B &#124; C &#124; D &#124; E &#124; F  
  
 Die GUID-literal Escape-Sequenz wird unterstützt, wenn der GUID-Datentyp, die von der Datenquelle unterstützt wird. Es sollte eine Anwendung aufrufen **SQLGetTypeInfo** zu bestimmen, ob dieser Datentyp unterstützt wird.
