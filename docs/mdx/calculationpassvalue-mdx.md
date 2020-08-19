---
description: CalculationPassValue (MDX)
title: CalculationPassValue (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 98d30326b709f7bd651b7941e48d412a7b875ffd
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88425042"
---
# <a name="calculationpassvalue-mdx"></a>CalculationPassValue (MDX)


  Gibt entweder den numerischen oder den Zeichenfolgenwert eines MDX-Ausdrucks (Multidimensional Expressions) zurück, der über den angegebenen Berechnungsdurchlauf eines Cubes ausgewertet wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
      Numeric syntax  
CalculationPassValue(Numeric_Expression,Pass_Value [, ABSOLUTE | RELATIVE [,ALL]])  
String syntax  
CalculationPassValue(String_Expression ,Pass_Value [, ABSOLUTE | RELATIVE [,ALL]])  
```  
  
## <a name="arguments"></a>Argumente  
 *Numeric_Expression*  
 Ein gültiger numerischer Ausdruck, bei dem es sich in der Regel um einen MDX-Ausdruck (Multidimensional Expressions) für Zellenkoordinaten handelt, die eine Zahl zurückgeben.  
  
 *String_Expression*  
 Ein gültiger Zeichenfolgenausdruck, bei dem es sich in der Regel um einen gültigen MDX-Ausdruck (Multidimensional Expressions) für Zellenkoordinaten handelt, der eine als Zeichenfolge ausgedrückte Zahl zurückgibt.  
  
 *Pass_Value*  
 Ein gültiger numerischer Ausdruck, der die Berechnungsdurchlaufnummer angibt.  
  
 ABSOLUTE  
 Ein-Zugriffsflagwert, der angibt, dass der *Pass_Value* -Parameter den NULL basierten Index des Berechnungs Durchlaufs enthält. ABSOLUTE ist der Standard-Zugriffsflagwert, der verwendet wird, wenn kein Zugriffsflagwert angegeben ist.  
  
 RELATIVE  
 Ein-Zugriffsflagwert, der angibt, dass der *Pass_Value* -Parameter einen relativen Offset vom Berechnungs Durchlauf der auslösenden Berechnung enthält. Wenn der Offset in einen Berechnungsdurchlaufindex kleiner als null (0) aufgelöst wird, wird Berechnungsdurchlauf 0 verwendet, und es tritt kein Fehler auf.  
  
 ALL  
 Wenn dieses Flag festgelegt wird, sind alle Werte NULL, die nicht von der Speicher-Engine geladen werden. Wenn das Flag nicht festgelegt wird, werden die Werte ohne jegliche Berechnungen aggregiert.  
  
## <a name="remarks"></a>Bemerkungen  
 Bei einem numerischer Ausdruck gibt die Funktion einen numerischen Wert zurück, indem sie den angegebenen numerischen MDX-Ausdruck im angegebenen Berechnungsdurchlauf auswertet, optional geändert durch ein Zugriffsflag und einen Zugriffsflagmodifizierer.  
  
 Wenn ein Zeichen folgen Ausdruck bereitgestellt wird, gibt die Funktion einen Zeichen folgen Wert zurück, indem der angegebene MDX-Zeichen folgen Ausdruck im angegebenen Berechnungs Durchlauf ausgewertet und optional durch ein Zugriffsflag und einen Zugriffsflagmodifizierer geändert wird *.*  
  
 Bei der automatischen Rekursions Auflösung in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] hat diese Funktion wenig praktische Verwendung.  
  
> [!NOTE]  
>  Nur Administratoren können die **CalculationPassValue** -Funktion innerhalb eines MDX-Skripts verwenden. Wenn ein MDX-Skript mit dieser Funktion im Kontext einer Rolle ausgeführt wird, die nicht über Administratorprivilegien verfügt, tritt ein Fehler auf.  
  
## <a name="see-also"></a>Weitere Informationen  
 [CalculationCurrentPass-&#40;MDX-&#41;](../mdx/calculationcurrentpass-mdx.md)   
 [IIf-&#40;MDX-&#41;](../mdx/iif-mdx.md)   
 [MDX-Funktionsreferenz &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
