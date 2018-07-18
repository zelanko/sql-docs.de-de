---
title: CoalesceEmpty (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 78e4f59ab1e994e34a7f0b1a0c519f34e20a2bd4
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34740289"
---
# <a name="coalesceempty-mdx"></a>CoalesceEmpty (MDX)


  Konvertiert einen leeren Zellenwert in einen angegebenen nicht leeren Zellenwert, bei dem es sich um eine Zahl oder eine Zeichenfolge handeln kann.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Numeric syntax  
CoalesceEmpty( Numeric_Expression1 [ ,Numeric_Expression2,...n] )  
  
String syntax  
CoalesceEmpty(String_Expression1 [ ,String_Expression2,...n] )  
```  
  
## <a name="arguments"></a>Argumente  
 *Numeric_Expression1*  
 Ein gültiger numerischer Ausdruck, bei dem es sich in der Regel um einen MDX-Ausdruck (Multidimensional Expressions) für Zellenkoordinaten handelt, die eine Zahl zurückgeben.  
  
 *Numeric_Expression2 dar*  
 Ein gültiger numerischer Ausdruck, bei dem es sich in der Regel um einen angegebenen numerischen Wert handelt.  
  
 *String_Expression1*  
 Ein gültiger Zeichenfolgenausdruck, bei dem es sich in der Regel um einen MDX-Ausdruck (Multidimensional Expressions) für Zellenkoordinaten handelt, der eine Zeichenfolge zurückgibt.  
  
 *String_Expression2*  
 Ein gültiger Zeichenfolgenausdruck, bei dem es sich in der Regel um einen angegebenen Zeichenfolgenwert handelt, der einen vom ersten Zeichenfolgenausdruck zurückgegebenen NULL-Wert ersetzt.  
  
## <a name="remarks"></a>Hinweise  
 Wenn eine oder mehrere numerische Ausdrücke angegeben werden, die **CoalesceEmpty** Funktion gibt den numerischen Wert des ersten numerischen Ausdrucks (von links nach rechts), die in einen nicht leeren Wert aufgelöst werden kann. Kann keiner der angegebenen numerischen Ausdrücke in einen nicht leeren Wert aufgelöst werden, gibt die Funktion den leeren Zellenwert zurück. Der Wert für den zweiten numerischen Ausdruck ist in der Regel der numerische Wert, der den vom ersten numerischen Ausdruck zurückgegebenen NULL-Wert ersetzt.  
  
 Wenn ein oder mehrere Zeichenfolgenausdrücke angegeben werden, gibt die Funktion den Zeichenfolgenwert des ersten Zeichenfolgenausdrucks (von links nach rechts) zurück, der in einen nicht leeren Wert aufgelöst werden kann. Kann keiner der angegebenen Zeichenfolgenausdrücke in einen nicht leeren Wert aufgelöst werden, gibt die Funktion den leeren Zellenwert zurück. Der Wert für den zweiten Zeichenfolgenausdruck ist in der Regel der Zeichenfolgenwert, der den vom ersten Zeichenfolgenausdruck zurückgegebenen NULL-Wert ersetzt.  
  
 Die **CoalesceEmpty** -Funktion kann nur Werte desselben Typs akzeptiert. Das heißt, alle angegebenen Wertausdrücke müssen entweder zu numerischen Datentypen oder dem leeren Zellenwert ausgewertet werden, oder alle angegebenen Wertausdrücke müssen zu Zeichenfolgen-Datentypen oder dem leeren Zellenwert ausgewertet werden. Ein einzelner Aufruf dieser Funktion kann nicht sowohl numerische Ausdrücke als auch Zeichenfolgenausdrücke enthalten.  
  
 Weitere Informationen zu leeren Zellen finden Sie in der OLE DB-Dokumentation.  
  
## <a name="example"></a>Beispiel  
 Die folgende Beispielabfrage die **Adventure Works** Cube. In diesem Beispiel wird die Bestellmenge jedes Produkts sowie den Prozentsatz der Bestellmengen nach Kategorie zurückgegeben. Die **CoalesceEmpty** Funktion wird sichergestellt, dass null-Werte als null (0) dargestellt werden, wenn die berechneten Elemente formatiert.  
  
```  
WITH   
   MEMBER [Measures].[Order Percent by Category] AS  
   CoalesceEmpty(   
      ([Product].[Product Categories].CurrentMember,  
        Measures.[Order Quantity]) /   
          (  
           Ancestor  
           ( [Product].[Product Categories].CurrentMember,   
             [Product].[Product Categories].[Category]  
           ), Measures.[Order Quantity]  
       ), 0  
   ), FORMAT_STRING='Percent'  
SELECT   
   {Measures.[Order Quantity],  
      [Measures].[Order Percent by Category]} ON COLUMNS,  
{[Product].[Product].Members} ON ROWS  
FROM [Adventure Works]  
WHERE {[Date].[Calendar Year].[Calendar Year].&[2003]}  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
