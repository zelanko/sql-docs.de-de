---
title: AssociationSet-Element (CSDLBI) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 93e5ac4d-d7e8-490e-b775-28263a48cfcc
caps.latest.revision: 8
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: d28f903b4e501f648329a65824292256bca7520b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36163201"
---
# <a name="associationset-element-csdlbi"></a>AssociationSet-Element (CSDLBI)
  Die `AssociationSet` Element ist ein komplexer Typ, der eine Zuordnung definiert. In einem CSDLBI-Datenmodell stellt eine Zuordnung eine Beziehung zwischen zwei Tabellen dar.  
  
 Für jede eindeutige Beziehung in einem Modell muss `AssociationSet` angegeben werden. `AssociationSet` definiert die Endpunkte mithilfe des `Association`-Elements. Die `AssociationSet` -Element definiert zusätzlich Metadaten für die Beziehung und ihre Verwendung im Datenmodell.  
  
## <a name="applicable-attributes"></a>Anwendbare Attribute  
 Die folgende Tabelle enthält die Elemente und Attribute, die definieren, die `AssociationSet` Element.  
  
|Name|Ist erforderlich|Description|  
|----------|-----------------|-----------------|  
|Status|ja|Eine Zeichenfolge, die angibt, ob die Zuordnung aktiv ist. Der Wert wird durch das State-Element definiert.|  
|Ausgeblendet|nein|Ein boolescher Wert der angibt, ob die Beziehung sichtbar ist. Standardmäßig weist Hidden den Wert `false` auf; dies bedeutet, dass alle Beziehungen im Modell sichtbar sind.|  
  
## <a name="state-element"></a>State-Element  
 Das `State`-Element ist ein einfacher Typ, der angibt, ob eine Zuordnung aktiv oder inaktiv ist. Aktive Zuordnungen sollten in Berechnungen verwendet werden, auf inaktive Zuordnungen muss in Berechungen explizit verwiesen werden.  
  
 Wenn mehrere Zuordnungssätze vorhanden sind, die zwei Entitäten verbinden, kann nur ein Zuordnungssatz als aktiv gekennzeichnet werden. Wenn zwei Beziehungen zwischen den zwei gleichen Tabellen vorhanden sind, kann also nur eine Verbindung aktiv sein.  
  
 Die folgende Tabelle enthält die Werte der `State` Element.  
  
|value|Description|  
|-----------|-----------------|  
|Active|Die Zuordnung ist aktiv.|  
|Inaktiv|Die Zuordnung ist aktiv.|  
  
## <a name="example"></a>Beispiel  
 **Tabellarisch**  
  
 Im folgenden Beispiel wird eine Beziehung im tabellarischen AdventureWorks-Modell (in CSDLBI 1.1) veranschaulicht. Die Zuordnung ist als inaktiv gekennzeichnet, weil bereits eine Beziehung (zwischen OrderKey und Date) besteht.  
  
```  
<AssociationSet   
    Name="InternetSales_Date_Date_Date"  
    Association="Sandbox.InternetSales_Date_Date_Date">  
    <End EntitySet="InternetSales" />  
    <End EntitySet="DimDate" />  
<bi:AssociationSet State="Inactive" />  
</AssociationSet>  
  
```  
  
## <a name="example"></a>Beispiel  
 **Multidimensional**  
  
 Im folgenden Beispiel wird die Beziehung zwischen der Tabelle Sales und der Tabelle Currency im Contoso-Vorgangscube veranschaulicht.  
  
```  
<AssociationSet   
    Name ="Sales_Currency_Currency_Currency_Name2"  
    Association ="Sandbox.Sales_Currency_Currency_Currency_Name2">  
    <End EntitySet ="Sales" />  
    <End EntitySet ="Currency" />  
<bi:AssociationSet />  
</AssociationSet>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Technische Referenz für BI-Anmerkungen zu CSDL](technical-reference-for-bi-annotations-to-csdl.md)  
  
  