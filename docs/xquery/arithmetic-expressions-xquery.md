---
title: Arithmetische Ausdrücke (XQuery) | Microsoft-Dokumentation
description: Erfahren Sie mehr über arithmetische Ausdrücke in XQuery und welche arithmetischen Operatoren unterstützt werden.
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
ms.openlocfilehash: a8d0f4f9286f80ad7031663eb21e8677d99e1cc3
ms.sourcegitcommit: 6593b3b6365283bb76c31102743cdccc175622fe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2020
ms.locfileid: "84305839"
---
# <a name="arithmetic-expressions-xquery"></a>Arithmetische Ausdrücke (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Alle arithmetischen Operatoren werden unterstützt, mit Ausnahme von **idiv**. Die folgenden Beispiele veranschaulichen die Grundlagen der Verwendung von arithmetischen Operatoren:  
  
```  
DECLARE @x xml  
SET @x=''  
SELECT @x.query('2 div 2')  
SELECT @x.query('2 * 2')  
```  
  
 Da **idiv** nicht unterstützt wird, besteht eine Lösung darin, den **xs: Integer ()** -Konstruktor zu verwenden:  
  
```  
DECLARE @x xml  
SET @x=''  
-- Following will not work  
-- SELECT @x.query('2 idiv 2')  
-- Workaround   
SELECT @x.query('xs:integer(2 div 3)')  
```  
  
 Der aus einem arithmetischen Operator resultierende Datentyp ist vom Datentyp des Eingabewerts abhängig. Wenn die Operanden unterschiedliche Typen aufweisen, wird entweder einer oder gegebenenfalls werden beide Typen entsprechend der Typhierarchie zu einem gemeinsamen Grundtyp umgewandelt. Weitere Informationen zur Typhierarchie finden Sie unter [Typumwandlungs Regeln in XQuery](../xquery/type-casting-rules-in-xquery.md).  
  
 Die numerische Typhöherstufung erfolgt, wenn zwei Operationen verschiedene numerische Basistypen aufweisen. Wenn Sie z. b. einen **xs: Decimal** -zu einem **xs: Double** -Wert hinzufügen, ändern Sie zuerst den Dezimalwert in einen Double-Wert Anschließend wird die Addition durchgeführt und das Ergebnis als double-Wert angezeigt.  
  
 Nicht typisierte atomare Werte werden in den numerischen Basistyp des anderen Operanden oder in **xs: Double** umgewandelt, wenn der andere Operand ebenfalls nicht typisiert ist.  
  
## <a name="implementation-limitations"></a>Implementierungseinschränkungen  
 Die folgenden Einschränkungen sind zu beachten:  
  
-   Die Argumente für die arithmetischen Operatoren müssen vom Typ "numeric" oder " **untypedAtomic**" sein.  
  
-   Vorgänge für **xs: Integer** -Werte führen zu einem Wert vom Typ **xs: Decimal** anstelle von **xs: Integer**.  
  
  
