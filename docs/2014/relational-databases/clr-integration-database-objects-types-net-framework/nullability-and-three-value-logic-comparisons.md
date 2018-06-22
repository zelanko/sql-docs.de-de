---
title: NULL-Zulässigkeit und Vergleiche mit Dreiwertiger Logik | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- precision [CLR integration]
- overflow detections [CLR integration]
- null values [CLR integration]
- three-value logic comparisons [CLR integration]
- data types [CLR integration]
- SqlBoolean data type
ms.assetid: 13da4c7f-1010-4b2d-a63c-c69b6bfd96f1
caps.latest.revision: 39
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 07a0076cadc805b3534d778070b7b61b28e1bf3d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36150378"
---
# <a name="nullability-and-three-value-logic-comparisons"></a>Zulässigkeit von NULL-Werten und Vergleiche mit dreiwertiger Logik
  Wenn Sie mit den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentypen vertraut sind, finden Sie eine ähnliche Semantik und Genauigkeit im `System.Data.SqlTypes`-Namespace in [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]. Es gibt jedoch einige Unterschiede, und die wichtigsten dieser Unterschiede werden in diesem Thema behandelt.  
  
## <a name="null-values"></a>NULL-Werte  
 Ein Hauptunterschied zwischen den systemeigenen CLR (Common Language Runtime)-Datentypen und den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentypen besteht darin, dass Erstere keine NULL-Werte zulassen, Letztere dagegen die uneingeschränkte NULL-Semantik bereitstellen.  
  
 Vergleiche werden durch NULL-Werte beeinflusst. Wenn die beiden Werte x und y verglichen werden und x oder y NULL ist, dann ergeben einige logische Vergleiche den Wert UNKNOWN statt true oder false.  
  
## <a name="sqlboolean-data-type"></a>SqlBoolean-Datentyp  
 Die `System.Data.SqlTypes` Namespace führt eine `SqlBoolean` Typ zur Darstellung dieser Logik 3-Wert. Vergleiche zwischen beliebigen Werten des Typs `SqlTypes` ergeben einen Wert des `SqlBoolean`-Typs. Der UNKNOWN-Wert wird durch den NULL-Wert des `SqlBoolean`-Typs dargestellt. Die Eigenschaften `IsTrue`, `IsFalse`, und `IsNull` dienen zur Überprüfung des Werts einer `SqlBoolean` Typ.  
  
## <a name="operations-functions-and-null-values"></a>Vorgänge, Funktionen und NULL-Werte  
 Alle arithmetischen Operatoren (+, -, \*, /, %), bitweisen Operatoren (~, & und |), und die meisten Funktionen NULL zurück, wenn einer der Operanden oder Argumente des `SqlTypes` NULL sind. Die `IsNull` Eigenschaft gibt immer einen Wert "true" oder "false" zurück.  
  
## <a name="precision"></a>Genauigkeit  
 Dezimaldatentypen in der [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] CLR gelten andere Maximalwerte als für die numerischen Datentypen und dezimaldatentypen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Außerdem wird bei den Dezimaldatentypen der [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]-CLR die maximale Genauigkeit angenommen. In der CLR für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], allerdings `SqlDecimal` bietet die gleiche maximale Genauigkeit und Dezimalstellenanzahl sowie die gleiche Semantik wie die decimal-Datentyp in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="overflow-detection"></a>Überlauferkennung  
 In der [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]-CLR wird durch die Addition von zwei sehr großen Zahlen möglicherweise keine Ausnahme ausgelöst. Wenn kein Prüfvorgang verwendet wurde, dann wird das zurückgegebene Ergebnis möglicherweise als negative Ganzzahl dargestellt. In `System.Data.SqlTypes` werden Ausnahmen für alle Überlauf- und Unterlauffehler sowie Fehler aufgrund einer Division durch 0 ausgelöst.  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server-Datentypen in .NET Framework](sql-server-data-types-in-the-net-framework.md)  
  
  