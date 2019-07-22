---
title: LEN (SSIS-Ausdruck) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- LEN function
- number of characters
ms.assetid: d961398b-e4d0-4936-be17-8f4c5882a640
author: janinezhang
ms.author: janinez
ms.openlocfilehash: fe71d2e914d665392b9728fdeb55c4ddd53431c1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68027537"
---
# <a name="len-ssis-expression"></a>LEN (SSIS-Ausdruck)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Gibt die Anzahl von Zeichen in einem Zeichenausdruck zurück. Wenn die Zeichenfolge führende und nachfolgende Leerzeichen enthält, werden sie von der Funktion für die Anzahl berücksichtigt. LEN gibt identische Werte für dieselbe Zeichenfolge mit Einzelbyte- und Doppelbytezeichen zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
LEN(character_expression)  
```  
  
## <a name="arguments"></a>Argumente  
 *character_expression*  
 Der auszuwertende Ausdruck.  
  
## <a name="result-types"></a>Ergebnistypen  
 DT_I4  
  
## <a name="remarks"></a>Remarks  
 Das *character_expression* -Argument kann den Datentyp DT_WSTR, DT_TEXT, DT_NTEXT oder DT_IMAGE aufweisen. Weitere Informationen finden Sie unter [Integration Services Datentypen](../../integration-services/data-flow/integration-services-data-types.md).  
  
 Wenn *character_expression* ein Zeichenfolgenliteral oder eine Datenspalte mit dem DT_STR-Datentyp ist, wird dieses bzw. diese implizit in den DT_WSTR-Datentyp umgewandelt, bevor LEN ausgeführt wird. Andere Datentypen müssen explizit in den DT_WSTR-Datentyp umgewandelt werden. Weitere Informationen finden Sie unter [Umwandlung &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/cast-ssis-expression.md).  
  
 Falls das an die LEN-Funktion übergebene Argument einen BLOB-Datentyp (Binary Large Object Block) aufweist, wie z. B. DT_TEXT, DT_NTEXT oder DT_IMAGE, gibt die Funktion die Anzahl der Bytes zurück.  
  
 LEN gibt ein NULL-Ergebnis zurück, wenn das Argument NULL ist.  
  
## <a name="expression-examples"></a>Beispiele für Ausdrücke  
 In diesem Beispiel wird die Länge eines Zeichenfolgenliterals zurückgegeben. Als Ergebnis wird 12 zurückgegeben.  
  
```  
LEN("Ball Bearing")  
```  
  
 In diesem Beispiel wird die Differenz zwischen der Länge von Werten in den Spalten **FirstName** und **LastName** zurückgegeben.  
  
```  
LEN(FirstName) - LEN(LastName)  
```  
  
 Gibt die Länge eines Computernamens mithilfe der **MachineName**-Systemvariablen zurück.  
  
```  
LEN(@MachineName)  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Funktionen &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
