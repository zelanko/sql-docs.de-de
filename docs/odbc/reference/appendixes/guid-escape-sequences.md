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
ms.openlocfilehash: a74ed9d4dfe0afb8bf59abb11220a0677d000bfb
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67947587"
---
# <a name="guid-escape-sequences"></a>GUID-Escapesequenzen
ODBC verwendet Escapesequenzen für GUID-Literale. Die Syntax dieser Escape-Sequenz lautet wie folgt aus:  
  
```  
{guid 'nnnnnnnn-nnnn-nnnn-nnnn-nnnnnnnnnnnn'}  
```  
  
## <a name="remarks"></a>Hinweise  
 In BNF-Schreibweise lautet die Syntax:  
  
 *ODBC-Guid-Escapesequenz* :: =  
     *Initiator-ODBC-esc-Guid* "*Guid-Wert*" *ODBC-esc-Terminator*  
  
 *Initiator der ODBC-esc* :: = {  
  
 *ODBC-esc-Terminator* :: =}  
  
 *GUID-Wert* :: = *Uhr mit geringem Wert Guid-Trennzeichen-Uhr-Middle-Guid-Trennzeichen-Uhr-High-Value-Guid-Trennzeichen-Uhr-Seq-Guid-Trennzeichen Knotenwert*  
  
 *GUID-Trennzeichen* :: = -  
  
 *Clock-mit geringem Wert* :: = *Hex_digit Hex_digit Hex_digit Hex_digit Hex_digit Hex_digit Hex_digit Hex_digit*  
  
 *Clock-Middle-Value* :: = *Hex_digit Hex_digit Hex_digit Hex_digit*  
  
 *Clock-High-Value* :: = *Hex_digit Hex_digit Hex_digit Hex_digit*  
  
 *Clock-Seq-Value* :: = *Hex_digit Hex_digit Hex_digit Hex_digit*  
  
 *Clock-Knotenwert* :: = *Hex_digit Hex_digit Hex_digit Hex_digit Hex_digit Hex_digit Hex_digit Hex_digit Hex_digit Hex_digit Hex_digit Hex_digit*  
  
 *hex_digit* ::= 0 &#124; 1 &#124; 2 &#124; 3 &#124; 4 &#124; 5 &#124; 6 &#124; 7 &#124; 8 &#124; 9 &#124; A &#124; B &#124; C &#124; D &#124; E &#124; F  
  
 Die GUID-literal Escape-Sequenz wird unterstützt, wenn der GUID-Datentyp, die von der Datenquelle unterstützt wird. Es sollte eine Anwendung aufrufen **SQLGetTypeInfo** zu bestimmen, ob dieser Datentyp unterstützt wird.
