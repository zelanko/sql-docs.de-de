---
title: Arithmetische Ausdrücke (XQuery) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- expressions [XQuery], arithmetic
- arithmetic expressions
ms.assetid: 90d675bf-56da-459a-9771-8cd13920a9fc
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 372ed2a1eb3ecba8f84125ae0231d2110e3966dc
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63047584"
---
# <a name="arithmetic-expressions-xquery"></a>Arithmetische Ausdrücke (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Alle arithmetische Operatoren werden unterstützt, mit Ausnahme von **Idiv**. Die folgenden Beispiele veranschaulichen die Grundlagen der Verwendung von arithmetischen Operatoren:  
  
```  
DECLARE @x xml  
SET @x=''  
SELECT @x.query('2 div 2')  
SELECT @x.query('2 * 2')  
```  
  
 Da **Idiv** wird nicht unterstützt, eine Lösung ist die Verwendung der **Xs:integer()** Konstruktor:  
  
```  
DECLARE @x xml  
SET @x=''  
-- Following will not work  
-- SELECT @x.query('2 idiv 2')  
-- Workaround   
SELECT @x.query('xs:integer(2 div 3)')  
```  
  
 Der aus einem arithmetischen Operator resultierende Datentyp ist vom Datentyp des Eingabewerts abhängig. Wenn die Operanden unterschiedliche Typen aufweisen, wird entweder einer oder gegebenenfalls werden beide Typen entsprechend der Typhierarchie zu einem gemeinsamen Grundtyp umgewandelt. Weitere Informationen zur Typhierarchie finden Sie unter [Typumwandlungsregeln in XQuery](../xquery/type-casting-rules-in-xquery.md).  
  
 Die numerische Typhöherstufung erfolgt, wenn zwei Operationen verschiedene numerische Basistypen aufweisen. Beispielsweise durch Hinzufügen einer **xs: decimal** auf eine **xs: double** ändern würden zuerst den Dezimalwert in einen Double-Wert. Anschließend wird die Addition durchgeführt und das Ergebnis als double-Wert angezeigt.  
  
 Nicht typisierte atomare Werte werden umgewandelt, der andere Operand numerischen Basistyp oder zu **xs: double** , wenn der andere Operand ebenfalls nicht typisiert ist.  
  
## <a name="implementation-limitations"></a>Implementierungseinschränkungen  
 Die folgenden Einschränkungen sind zu beachten:  
  
-   Argumente für die arithmetischen Operatoren müssen numerischen Typ aufweisen oder **UntypedAtomic**.  
  
-   Vorgänge für **xs: Integer** Werte ergeben einen Wert vom Typ **xs: decimal** anstelle von **xs: Integer**.  
  
  
