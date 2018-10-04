---
title: AssociationSet-Element (CSDLBI) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: 93e5ac4d-d7e8-490e-b775-28263a48cfcc
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7a7e165afc901b82d73f11f04fbb2c2cbb5402ac
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48224890"
---
# <a name="associationset-element-csdlbi"></a>AssociationSet-Element (CSDLBI)
  Die `AssociationSet` Element ist ein komplexer Typ, der eine Zuordnung definiert. In einem CSDLBI-Datenmodell stellt eine Zuordnung eine Beziehung zwischen zwei Tabellen dar.  
  
 Für jede eindeutige Beziehung in einem Modell muss `AssociationSet` angegeben werden. `AssociationSet` definiert die Endpunkte mithilfe des `Association`-Elements. Die `AssociationSet` -Element definiert zusätzlich Metadaten für die Beziehung und ihre Verwendung im Datenmodell.  
  
## <a name="applicable-attributes"></a>Anwendbare Attribute  
 Die folgende Tabelle enthält die Elemente und Attribute, die definieren, die `AssociationSet` Element.  
  
|Name|Ist erforderlich|Description|  
|----------|-----------------|-----------------|  
|Status|Benutzerkontensteuerung|Eine Zeichenfolge, die angibt, ob die Zuordnung aktiv ist. Der Wert wird durch das State-Element definiert.|  
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
  
  
