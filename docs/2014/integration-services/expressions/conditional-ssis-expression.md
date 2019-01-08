---
title: '? decodiert werden: (Bedingung) (SSIS-Ausdruck) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- conditional operator (?:)
- '?: (conditional operator)'
ms.assetid: d38e6890-7338-4ce0-a837-2dbb41823a37
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f644dc95d5c137c8ee1cdb5ecf8b0e2659e28e40
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52811192"
---
# <a name="--conditional-ssis-expression"></a>? decodiert werden: (Bedingung) (SSIS-Ausdruck)
  Gibt einen von zwei Ausdrücken basierend auf der Auswertung eines booleschen Ausdrucks zurück. Falls der boolesche Ausdruck zu TRUE ausgewertet wird, wird der erste Ausdruck ausgewertet, und das Ergebnis ist das Ausdrucksergebnis. Falls der boolesche Ausdruck zu FALSE ausgewertet wird, wird der zweite Ausdruck ausgewertet, und das Ergebnis ist das Ausdrucksergebnis.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
boolean_expression?expression1:expression2  
  
```  
  
## <a name="arguments"></a>Argumente  
 *boolean_expression*  
 Ein gültiger Ausdruck, der zu TRUE, FALSE oder NULL ausgewertet wird.  
  
 *expression1*  
 Ein gültiger Ausdruck.  
  
 *expression2*  
 Ein gültiger Ausdruck.  
  
## <a name="result-types"></a>Ergebnistypen  
 Der Datentyp von *expression1* oder *expression2*.  
  
## <a name="remarks"></a>Hinweise  
 Falls *boolean_expression* zu NULL ausgewertet wird, lautet das Ergebnis des Ausdrucks NULL. Wenn ein ausgewählter Ausdruck, *expression1* oder *expression2* , NULL ist, lautet das Ergebnis NULL. Wenn ein ausgewählter Ausdruck ungleich NULL ist, aber der nicht ausgewählte Ausdruck NULL ist, besitzt das Ergebnis den Wert des ausgewählten Ausdrucks.  
  
 Falls *expression1* und *expression2* vom gleichen Datentyp sind, gehört auch das Ergebnis zu diesem Datentyp. Die folgenden zusätzlichen Regeln sind auch auf Ergebnistypen anwendbar:  
  
-   Für den DT_TEXT-Datentyp müssen *expression1* und *expression2* die gleiche Codepage aufweisen.  
  
-   Die Länge eines Ergebnisses mit dem DT_BYTES-Datentyp ist die Länge des längeren Arguments.  
  
 Die Ausdrucksgruppe, *expression1* und *expression2*, muss zu gültigen Datentypen ausgewertet werden und eine der folgenden Regeln einhalten:  
  
-   **Numerisch**   *expression1* und *expression2* müssen einen numerischen Datentyp aufweisen. Die Schnittmenge der Datentypen muss ein numerischer Datentyp gemäß den Regeln zu den impliziten numerischen Konvertierungen sein, die die Ausdrucksauswertung ausführt. Die Schnittmenge der beiden numerischen Datentypen darf nicht NULL sein. Weitere Informationen finden Sie unter [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).  
  
-   **Zeichenfolge** sowohl *expression1* und *expression2* müssen ein Zeichenfolgen-Datentyp sein: DT_STR oder DT_WSTR. Die beiden Ausdrücke können zu verschiedenen Zeichenfolgen-Datentypen ausgewertet werden. Das Ergebnis weist den DT_WSTR-Datentyp und die Länge des längeren Arguments auf.  
  
-   **Datum, Uhrzeit oder Datum/Uhrzeit** sowohl *expression1* und *expression2* muss auf einen der folgenden Datentypen ausgewertet werden: DT_DBDATE, DT_DATE, DT_DBTIME, DT_DBTIME2, DT_DBTIMESTAMP, DT_DBTIMESTAMP2, DT_DBTIMESTAPMOFFSET oder DT_FILETIME.  
  
    > [!NOTE]  
    >  Das System unterstützt keine Vergleiche zwischen einem Ausdruck, der zu einem Uhrzeitdatentyp ausgewertet wird, und einem Ausdruck, der entweder zu einem Datums- oder zu einem Datums-/Uhrzeitdatentyp ausgewertet wird. In diesem Fall wird ein Fehler generiert.  
  
     Beim Vergleich der Ausdrücke werden die folgenden Konvertierungsregeln in der angegebenen Reihenfolge angewendet:  
  
    -   Wenn zwei Ausdrücke zu dem gleichen Datentyp ausgewertet werden, wird der Datentyp verglichen.  
  
    -   Wenn ein Ausdruck den DT_DBTIMESTAMPOFFSET-Datentyp aufweist, wird der andere Ausdruck implizit in DT_DBTIMESTAMPOFFSET konvertiert, und ein DT_DBTIMESTAMPOFFSET-Vergleich wird ausgeführt. Weitere Informationen finden Sie unter [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).  
  
    -   Wenn ein Ausdruck den DT_DBTIMESTAMP2-Datentyp aufweist, wird der andere Ausdruck implizit in DT_DBTIMESTAMP2 konvertiert, und ein DT_DBTIMESTAMP2-Vergleich wird ausgeführt.  
  
    -   Wenn ein Ausdruck den DT_DBTIME2-Datentyp aufweist, wird der andere Ausdruck implizit in DT_DBTIME2 konvertiert, und ein DT_DBTIME2-Vergleich wird ausgeführt.  
  
    -   Wenn ein Ausdruck einen anderen Datentyp als DT_DBTIMESTAMPOFFSET, DT_DBTIMESTAMP2 oder DT_DBTIME2 aufweist, werden die Ausdrücke vor dem Vergleichen in den DT_DBTIMESTAMP-Datentyp konvertiert.  
  
     Beim Vergleichen der Ausdrücke gelten folgende Annahmen:  
  
    -   Wenn jeder Ausdruck einen Datentyp aufweist, der Millisekunden umfasst, wird angenommen, dass bei dem Datentyp mit der geringsten Anzahl von Ziffern für Millisekunden die verbleibenden Ziffern Nullen sind.  
  
    -   Wenn jeder Ausdruck einen Datumsdatentyp aufweist, jedoch nur ein Ausdruck einen Zeitzonenoffset umfasst, wird angenommen, dass der Datumsdatentyp ohne Zeitzonenoffset in koordinierter Weltzeit (Coordinated Universal Time; UTC) ausgedrückt ist.  
  
 Weitere Informationen zu Datentypen finden Sie unter [Integration Services Data Types](../data-flow/integration-services-data-types.md).  
  
## <a name="expression-examples"></a>Beispiele für Ausdrücke  
 In diesem Beispiel wird ein Ausdruck gezeigt, der bedingt zu `savannah` oder `unknown`ausgewertet wird.  
  
```  
@AnimalName == "Elephant"? "savannah": "unknown"  
```  
  
 Dieses Beispiel zeigt einen Ausdruck, der auf eine **ListPrice** -Spalte verweist. **ListPrice** weist den DT_CY-Datentyp auf. Der Ausdruck multipliziert **ListPrice** bedingt mit 0,2 oder 0,1.  
  
```  
ListPrice < 350.00 ? ListPrice * .2 : ListPrice * .1  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Operatorenrangfolge und -assoziativität](operator-precedence-and-associativity.md)   
 [Operatoren &#40;SSIS-Ausdruck&#41;](operators-ssis-expression.md)  
  
  
