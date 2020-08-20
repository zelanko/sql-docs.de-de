---
description: Operatorenrangfolge und -assoziativität
title: Operatorenrangfolge und -assoziativität | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- associativity [Integration Services]
- precedence [Integration Services]
ms.assetid: 5094164f-dabc-45b5-b611-384feb2b3fe3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cda01c12856bff3e28b06c9cfddccb368e6a3e6b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88477497"
---
# <a name="operator-precedence-and-associativity"></a>Operatorenrangfolge und -assoziativität

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  Jeder Operator, der von der Ausdrucksauswertung unterstützt wird, weist eine zugewiesene Rangfolge in der Rangfolgenhierarchie auf und enthält eine bestimmte Auswertungsrichtung. Die Auswertungsrichtung für einen Operator ist die Operatorassoziativität. Operatoren mit einer höheren Position in der Rangfolge werden vor Operatoren mit einer niedrigeren Position in der Rangfolge ausgewertet. Besitzt ein komplexer Ausdruck mehrere Operatoren, bestimmt die Operatorenrangfolge die Reihenfolge, in der die einzelnen Operationen ausgeführt werden. Die Ausführungsreihenfolge kann sich entscheidend auf das Ergebnis auswirken. Manche Operatoren weisen die gleiche Rangfolge auf. Falls ein Ausdruck mehrere Operatoren mit gleicher Rangfolge enthält, werden die Operatoren von links nach rechts bzw. von rechts nach links ausgewertet.  
  
 In der folgenden Tabelle ist die Rangfolge von Operatoren aufgeführt, wobei Operatoren mit einer hohen Position in der Rangfolge zuerst aufgeführt sind. Operatoren auf derselben Ebene haben die gleiche Rangfolge.  
  
|Operatorsymbol|Vorgangstyp|Assoziativität|  
|---------------------|-----------------------|-------------------|  
|( )|expression|Von links nach rechts|  
|-, !, ~|Unär|Von rechts nach links|  
|Umwandlungen|Unär|Von rechts nach links|  
|*, / ,%|Multiplikativ|Von links nach rechts|  
|+, -|Additiv|Von links nach rechts|  
|\<, >, \<=, >=|Relational|Von links nach rechts|  
|==, !=|Gleichheit|Von links nach rechts|  
|&|Bitweises AND|Von links nach rechts|  
|^|Bitweises exklusives OR|Von links nach rechts|  
|&#124;|Bitweises inklusives OR|Von links nach rechts|  
|&&|Logisches AND|Von links nach rechts|  
|&#124;&#124;|Logisches OR|Von links nach rechts|  
|? :|Bedingter Ausdruck|Von rechts nach links|  
  
## <a name="see-also"></a>Siehe auch  
 [Operatoren &#40;SSIS-Ausdruck&#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  
