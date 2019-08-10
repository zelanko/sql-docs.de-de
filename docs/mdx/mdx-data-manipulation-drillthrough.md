---
title: Drillthrough-Anweisung (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: ee90d2c367fa289e8255a84e4eb6da19b37933e0
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68891202"
---
# <a name="mdx-data-manipulation---drillthrough"></a>MDX-Datenbearbeitung – DRILLTHROUGH


  Ruft die zugrunde liegenden Tabellenzeilen ab, die zum Erstellen einer bestimmten Zelle in einem Cube verwendet wurden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DRILLTHROUGH[MAXROWSUnsigned_Integer]   
      <MDX SELECT statement>   
      [RETURNSet_of_Attributes_and_Measures   
            [,Set_of_Attributes_and_Measures ...]  
      ]  
```  
  
## <a name="arguments"></a>Argumente  
 *Unsigned_Integer*  
 Ein positiver ganzzahliger Wert  
  
 *SELECT-Anweisung von MDX*  
 Eine gültige SELECT-Anweisung in MDX (Multidimensional Expressions)  
  
 *Set_of_Attributes_and_Measures*  
 Eine Liste mit durch Trennzeichen getrennten Dimensionsattributen und Measures  
  
## <a name="remarks"></a>Hinweise  
 Drillthrough ist ein Vorgang, bei dem ein Endbenutzer eine einzelne Zelle in einem Cube auswählt und ein Resultset aus den Quelldaten dieser Zelle abruft, um detailliertere Informationen zu erhalten. Standardmäßig wird ein Drillthrough-Resultset aus den Tabellenzellen abgeleitet, die zur Berechnung des Werts der ausgewählten Cubezelle ausgewertet wurden. Endbenutzer können einen Drillthrough nur dann durchführen, wenn die Clientanwendung diese Funktion unterstützt. In [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]werden die Ergebnisse direkt aus dem MOLAP-Speicher abgerufen, es sei denn, ROLAP-Partitionen oder-Dimensionen werden abgefragt.  
  
> [!IMPORTANT]  
>  Die Drillthrough-Sicherheit basiert auf den für den Cube definierten allgemeinen Sicherheitsoptionen. Erhält ein Benutzer auf bestimmte Daten keinen Zugriff über MDX, ist sein Zugriff über Drillthrough auf genau die gleiche Weise eingeschränkt.  
  
 Eine MDX-Anweisung gibt die betreffende Zelle an. Der durch das **MaxRows** -Argument angegebene Wert gibt die maximale Anzahl von Zeilen an, die vom resultierenden Rowset zurückgegeben werden sollen.  
  
 Standardmäßig werden maximal 10.000 Zeilen zurückgegeben. Dies bedeutet, dass Sie, wenn Sie **MaxRows** nicht angeben, mindestens 10.000 Zeilen erhalten. Wenn dieser Wert für Ihr Szenario zu niedrig ist, können Sie **MaxRows** auf eine höhere Zahl festlegen, z `MAXROWS 20000`. b. Wenn die Gesamtzahl zu niedrig ist, können Sie die Standardeinstellung erhöhen, indem Sie die Server Eigenschaft **olap\query\defaultdrillthrough MaxRows** ändern. Weitere Informationen zum Ändern dieser Eigenschaft finden Sie unter [Server Eigenschaften in Analysis Services](https://docs.microsoft.com/analysis-services/server-properties/server-properties-in-analysis-services).  
  
 Sofern nicht anders angegeben, enthalten die zurückgegebenen Spalten alle Granularitätsattribute aller Dimensionen, die mit der Measuregruppe des angegebenen Measures verbunden sind und keine m:n-Dimensionen sind. Cubedimensionen ist zur Unterscheidung von Dimensionen und Measuregruppen ein $-Zeichen vorangestellt. Die **Return** -Klausel wird verwendet, um die Spalten anzugeben, die von der Drillthrough-Abfrage zurückgegeben werden. Die folgenden Funktionen können von der **Return** -Klausel auf ein einzelnes Attribut oder Measure angewendet werden.  
  
 Name(attribute_name)  
 Gibt den Namen des angegebenen Attributelements zurück.  
  
 UniqueName(attribute_name)  
 Gibt den eindeutigen Namen des angegebenen Attributelements zurück.  
  
 Key(attribute_name[, N])  
 Gibt den Schlüssel des angegebenen Attributelements zurück, wobei N die Spalte im zusammengesetzten Schlüssel (sofern vorhanden) angibt. Der Standardwert für N ist 1.  
  
 Caption(attribute_name)  
 Gibt die Beschriftung des angegebenen Attributelements zurück.  
  
 MemberValue(attribute_name)  
 Gibt den Elementwert des angegebenen Attributelements zurück.  
  
 CustomRollup(attribute_name)  
 Gibt den benutzerdefinierte Rollupausdruck für das angegebene Attributelement zurück.  
  
 CustomRollupProperties(attribute_name)  
 Gibt die benutzerdefinierte Rollupeigenschaft für das angegebene Attributelement zurück.  
  
 UnaryOperator(attribute_name)  
 Gibt den unären Operator des angegebenen Attributelements zurück.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die Zelle für den Monat Juli 2007 für das Reseller Sales Amount-Measure (das Standardmeasure) für das Land Australien angegeben. Die RETURN-Klausel gibt an, dass die der Zelle zugrunde liegenden Werte Datum jedes Verkaufs, Produktmodellname, Mitarbeitername, Betrag der Verkäufe, Steuerbetrag sowie Produktkosten zurückgegeben werden sollen.  
  
```  
DRILLTHROUGH  
SELECT  
   ([Date].[Calendar].[Month].[July 2007])  
ON 0   
FROM [Adventure Works]  
WHERE [Geography].[Country].[Australia]  
RETURN   
  [$Date].[Date]  
  ,KEY([$Product].[Model Name])  
  ,NAME([$Employee].[Employee])  
  ,[Reseller Sales].[Reseller Sales Amount]  
  ,[Reseller Sales].[Reseller Tax Amount]  
  ,[Reseller Sales].[Reseller Standard Product Cost]  
```  
  
## <a name="see-also"></a>Siehe auch  
 [MDX für MDX &#40;-Daten Bearbeitungsanweisungen&#41;](../mdx/mdx-data-manipulation-statements-mdx.md)  
  
  
