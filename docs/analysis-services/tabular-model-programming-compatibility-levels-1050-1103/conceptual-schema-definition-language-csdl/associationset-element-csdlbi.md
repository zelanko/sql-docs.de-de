---
title: AssociationSet-Element (CSDLBI) | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c2ae4f565a2383284421bb433ed5cc98371196d3
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="associationset-element-csdlbi"></a>AssociationSet-Element (CSDLBI)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Das **AssociationSet** -Element ist ein komplexer Typ, mit dem eine Zuordnung definiert wird. In einem CSDLBI-Datenmodell stellt eine Zuordnung eine Beziehung zwischen zwei Tabellen dar.  
  
 Für jede eindeutige Beziehung in einem Modell muss **AssociationSet** angegeben werden. **AssociationSet** definiert die Endpunkte mithilfe des **Association** -Elements. Das **AssociationSet** -Element definiert zusätzlich Metadaten für die Beziehung und ihre Verwendung im Datenmodell.  
  
## <a name="applicable-attributes"></a>Anwendbare Attribute  
 In der folgenden Tabelle sind die Elemente und Attribute aufgeführt, durch die das **AssociationSet** -Element definiert wird.  
  
|Name|Ist erforderlich|Beschreibung|  
|----------|-----------------|-----------------|  
|Status|ja|Eine Zeichenfolge, die angibt, ob die Zuordnung aktiv ist. Der Wert wird durch das State-Element definiert.|  
|Hidden|Nein|Ein boolescher Wert der angibt, ob die Beziehung sichtbar ist. Standardmäßig weist Hidden den Wert **false**auf; dies bedeutet, dass alle Beziehungen im Modell sichtbar sind.|  
  
## <a name="state-element"></a>State-Element  
 Das **State** -Element ist ein einfacher Typ, der angibt, ob eine Zuordnung aktiv oder inaktiv ist. Aktive Zuordnungen sollten in Berechnungen verwendet werden, auf inaktive Zuordnungen muss in Berechungen explizit verwiesen werden.  
  
 Wenn mehrere Zuordnungssätze vorhanden sind, die zwei Entitäten verbinden, kann nur ein Zuordnungssatz als aktiv gekennzeichnet werden. Wenn zwei Beziehungen zwischen den zwei gleichen Tabellen vorhanden sind, kann also nur eine Verbindung aktiv sein.  
  
 In der folgenden Tabelle sind die Werte des **State** -Elements aufgeführt.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|Active|Die Zuordnung ist aktiv.|  
|Inaktiv|Die Zuordnung ist aktiv.|  
  
## <a name="example"></a>Beispiel  
 **Tabellarische**  
  
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
 **Mehrdimensionale**  
  
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
 [Technische Referenz für BI-Anmerkungen zu CSDL](../../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/conceptual-schema-definition-language-csdl/technical-reference-for-bi-annotations-to-csdl.md)  
  
  
