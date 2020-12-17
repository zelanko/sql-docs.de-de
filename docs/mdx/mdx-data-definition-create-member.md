---
description: MDX-Datendefinition – CREATE MEMBER
title: Create Member-Anweisung (MDX) | Microsoft-Dokumentation
ms.date: 07/22/2020
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 878d189aba259e5b69f5c27dbbc8b80b3f7f880b
ms.sourcegitcommit: 370cab80fba17c15fb0bceed9f80cb099017e000
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/17/2020
ms.locfileid: "97642977"
---
# <a name="mdx-data-definition---create-member"></a>MDX-Datendefinition – CREATE MEMBER


  Erstellt ein berechnetes Element.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
CREATE [ SESSION ] [HIDDDEN] [ CALCULATED ] MEMBER CURRENTCUBE | Cube_Name.Member_Name   
   AS MDX_Expression  
      [,Property_Name = Property_Value, ...n]  
......[,SCOPE_ISOLATION = CUBE]  
```  
  
## <a name="arguments"></a>Argumente  
 *Cube_Name*  
 Ein gültiger Zeichenfolgenausdruck, der den Namen des Cubes bereitstellt, in dem das Element erstellt wird.  
  
 *Member_Name*  
 Ein gültiger Zeichenfolgenausdruck, der einen Elementnamen bereitstellt. Geben Sie einen vollqualifizierten Namen an, um ein Element in einer anderen Dimension als der Measures-Dimension zu erstellen. Wenn Sie keinen vollqualifizierten Elementnamen angeben, wird das Element in der Measures-Dimension erstellt.  
  
 *MDX_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions).  
  
 *Property_Name*  
 Eine gültige Zeichenfolge, die den Namen der Eigenschaft eines berechneten Elements bereitstellt.  
  
 *Property_Value*  
 Ein gültiger Skalarausdruck, der den Wert der Eigenschaft eines berechneten Elements definiert.  
  
## <a name="remarks"></a>Hinweise  
 Die CREATE MEMBER-Anweisung definiert berechnete Elemente, die während der gesamten Sitzung verfügbar sind und somit in mehreren Abfragen im Verlauf der Sitzung verwendet werden können. Weitere Informationen finden Sie unter [erstellen Session-Scoped berechneter Elemente &#40;MDX&#41;](/analysis-services/multidimensional-models/mdx/mdx-calculated-members-session-scoped-calculated-members).  
  
 Sie können auch ein berechnetes Element definieren, das in einer einzelnen Abfrage verwendet wird. Wenn Sie ein berechnetes Element definieren möchten, das auf eine einzelne Abfrage beschränkt ist, verwenden Sie die WITH-Klausel in der SELECT-Anweisung. Weitere Informationen finden Sie unter [erstellen Query-Scoped berechneter Elemente &#40;MDX&#41;](/analysis-services/multidimensional-models/mdx/mdx-calculated-members-query-scoped-calculated-members).  
  
 *Property_name* kann entweder auf Standardeigenschaften oder optionale Eigenschaften berechneter Elemente verweisen. Standardelementeigenschaften sind in diesem Thema weiter unten aufgelistet. Berechnete Elemente, die mit CREATE Member ohne einen **Sitzungs** Wert erstellt wurden, haben einen Sitzungs Bereich. Außerdem müssen Zeichenfolgen, die in der Definition eines berechneten Elements stehen, in doppelte Anführungszeichen gesetzt werden. Dies unterscheidet sich von der für OLE DB definierten Methode, die angibt, dass Zeichenfolgen in einfachen Anführungszeichen stehen müssen.  
  
 Die Angabe eines anderen als des aktuell verbundenen Cubes verursacht einen Fehler. Daher sollten Sie den aktuellen Cube mithilfe von CURRENTCUBE statt mit dem Cubenamen angeben.  
  
 Weitere Informationen zu Elementeigenschaften, die durch OLE DB definiert sind, finden Sie in der OLE DB-Dokumentation.  
  
## <a name="scope"></a>`Scope`  
 Ein berechnetes Element kann in einem der Gültigkeitsbereiche auftreten, die in der folgenden Tabelle aufgeführt sind.  
  
 Abfragebereich  
 Die Sichtbarkeit und Lebensdauer des berechneten Elements ist auf die Abfrage beschränkt. Das berechnete Element ist in einer einzelnen Abfrage definiert. Der Abfragebereich hat Vorrang vor dem Sitzungsbereich. Weitere Informationen finden Sie unter [erstellen Query-Scoped berechneter Elemente &#40;MDX&#41;](/analysis-services/multidimensional-models/mdx/mdx-calculated-members-query-scoped-calculated-members).  
  
 Bereich einer Sitzung  
 Die Sichtbarkeit und Lebensdauer des berechneten Elements ist auf die Sitzung beschränkt, in der das Element erstellt wurde. (Die Lebensdauer ist kleiner als die Sitzungsdauer, wenn eine Drop Member-Anweisung für das berechnete Element ausgegeben wird.) Die CREATE Member-Anweisung erstellt ein berechnetes Element mit dem Sitzungs Bereich.  
  
### <a name="scope-isolation"></a>Bereichsisolation  
 Wenn ein MDX-Cubeskript (Multidimensional Expressions) berechnete Elemente enthält, werden die berechneten Elemente standardmäßig aufgelöst, bevor Berechnungen im Sitzungsbereich aufgelöst werden und bevor abfragedefinierte Berechnungen aufgelöst werden.  
  
> [!NOTE]  
>  In bestimmten Szenarien zeigen die [Aggregatfunktion (MDX)](../mdx/aggregate-mdx.md) und die [visualtotal (MDX)](../mdx/visualtotals-mdx.md) -Funktion dieses Verhalten nicht an.  
  
 Durch das Verhalten können in generischen Clientanwendungen Cubes mit komplexen Berechnungen verwendet werden, ohne dass die spezielle Implementierung der Berechnungen berücksichtigt werden muss. In bestimmten Szenarien ist es jedoch möglicherweise sinnvoll, berechnete Elemente im Sitzungs-oder Abfrage Bereich vor bestimmten Berechnungen im Cube auszuführen, und weder die **Aggregat** Funktion noch die **visualtotal** -Funktion sind anwendbar. Um das zu erreichen, verwenden Sie die SCOPE_ISOLATION-Berechnungseigenschaft.  
  
#### <a name="example"></a>Beispiel  
 Das folgende Skript stellt ein Beispiel für ein Szenario dar, in dem die SCOPE_ISOLATION-Berechnungseigenschaft erforderlich ist, damit das richtige Ergebnis entsteht.  
  
 **MDX-Skript des Cubes:**  
  
```  
CREATE MEMBER CURRENTCUBE.Measures.ProfitRatio AS 'Measures.[Store Sales]/Measures.[Store Cost]', SOLVE_ORDER = 10  
```  
  
 **MDX-Abfrage:**  
  
```  
WITH MEMBER [Customer].[Customers].[USA]. USAWithoutWA AS  
[Customer].[Customers].[Country].&[USA] - [Customer].[Customers].[State Province.&[WA], SOLVE_ORDER=5  
SELECT {USAWithoutWA} ON 0 FROM SALES  
WHERE ProfitRatio  
```  
  
 Das gewünschte Ergebnis der vorherigen Abfrage entspricht dem Verhältnis für die Verkäufe der USA ohne WA, damit die Kosten für die USA ohne WA gespeichert werden können. Die vorherige Abfrage gibt nicht das gewünschte Ergebnis zurück, sondern das Verhältnis für die USA abzüglich des Verhältnisses für WA. Dies stellt ein bedeutungsloses Ergebnis dar. Wenn das gewünschte Ergebnis erzielt werden soll, können Sie die SCOPE_ISOLATION-Berechnungseigenschaft verwenden.  
  
 **MDX-Abfrage mit SCOPE_ISOLATION-Berechnungseigenschaft:**  
  
```  
WITH MEMBER [Customer].[Customers].[USA]. USAWithoutWA AS  
[Customer].[Customers].[Country].&[USA] - [Customer].[Customers].[State Province.&[WA], SOLVE_ORDER=5  
,SCOPE_ISOLATION=CUBE  
SELECT {USAWithoutWA} ON 0 FROM SALES  
WHERE ProfitRatio  
```  
  
## <a name="standard-properties"></a>Standardeigenschaften  
 Jedes berechnete Element hat eine Reihe von Standardeigenschaften. Wenn eine Client Anwendung mit verbunden ist [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , werden die Standardeigenschaften entweder unterstützt, oder Sie können unterstützt werden, wenn der Administrator dies auswählt.  
  
 Abhängig von der Cubedefinition sind möglicherweise weitere Elementeigenschaften verfügbar. Die folgenden Eigenschaften enthalten Informationen, die für die Dimensionsebene im Cube relevant sind.  
  
|Eigenschaftsbezeichner|Bedeutung|  
|-------------------------|-------------|  
|SOLVE_ORDER|Die Reihenfolge, in der das berechnete Element in Fällen gelöst wird, in denen ein berechnetes Element auf ein anderes berechnetes Element verweist (also in Fällen, in denen berechnete Elemente sich überschneiden).|  
|FORMAT_STRING|Eine Format Zeichenfolge im Office-Stil, die die Client Anwendung beim Anzeigen von Zellwerten verwenden kann.|  
|VISIBLE|Ein Wert, der bestimmt, ob das berechnete Element in einem Schemarowset sichtbar ist. Sichtbare berechnete Elemente können einer Menge mit der [AddCalculatedMembers](../mdx/addcalculatedmembers-mdx.md) -Funktion hinzugefügt werden. Ein Wert ungleich 0 zeigt an, dass das berechnete Element sichtbar ist. Der Standardwert für diese Eigenschaft ist *sichtbar*.<br /><br /> Berechnete Elemente, die nicht sichtbar sind (für die dieser Wert auf 0 festgelegt ist), werden üblicherweise als Zwischenschritte in komplexeren berechneten Elementen verwendet. Auf diese berechneten Elemente können auch andere Arten von Elementen (z. B. Measures) verweisen.|  
|NON_EMPTY_BEHAVIOR|Das Measure oder die Menge, mit dem oder der beim Auflösen leerer Zellen das Verhalten berechneter Elemente bestimmt wird.<br /><br /> Warnung: Diese Eigenschaft ist veraltet. **\* \* \* \*** Vermeiden Sie es, sie festzulegen. Weitere Informationen finden Sie [unter Veraltete Analysis Services Features in SQL Server 2014](/previous-versions/sql/2014/analysis-services/deprecated-analysis-services-features-in-sql-server-2014?view=sql-server-2014&preserve-view=true) .|  
|CAPTION|Eine Zeichenfolge, die von der Clientanwendung als Beschriftung für das Element verwendet wird.|  
|DISPLAY_FOLDER|Eine Zeichenfolge, die den Pfad des Anzeigeordners angibt, der von der Clientanwendung zum Anzeigen des Elements verwendet wird. Das Trennzeichen für Ordnerebenen wird von der Clientanwendung definiert. Bei den von bereitgestellten Tools und Clients [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ist der umgekehrte Schrägstrich ( \\ ) das ebenendtrennzeichen. Um mehrere Anzeigeordner für ein definiertes Element bereitzustellen, verwenden Sie ein Semikolon (;) als Trennzeichen für die Ordner.|  
|ASSOCIATED_MEASURE_GROUP|Der Name der Measuregruppe, der dieses Element zugeordnet wird.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Drop Member-Anweisung &#40;MDX-&#41;](../mdx/mdx-data-definition-drop-member.md)   
 [Aktualisieren der Member-Anweisung &#40;MDX-&#41;](../mdx/mdx-data-definition-update-member.md)   
 [MDX-Daten Definitions Anweisungen &#40;MDX-&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
