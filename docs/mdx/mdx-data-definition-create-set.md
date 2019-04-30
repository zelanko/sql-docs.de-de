---
title: CREATE SET-Anweisung (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4d1e58d016649c3c21a056a82315bd0d0fb3564f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63248392"
---
# <a name="mdx-data-definition---create-set"></a>MDX-Datendefinition – CREATE SET


  Erstellt eine benannte Menge mit Sitzungsbereich für den aktuellen Cube.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
CREATE [SESSION] [ STATIC | DYNAMIC ] [HIDDEN] SET   
   CURRENTCUBE | Cube_Name  
      .Set_Name AS 'Set_Expression'  
      [,Property_Name = Property_Value, ...n]  
```  
  
## <a name="arguments"></a>Argumente  
 *Cube_Name*  
 Ein gültiger Zeichenfolgenausdruck, der den Namen des Cubes bereitstellt.  
  
 *Set_Name*  
 Ein gültiger Zeichenfolgenausdruck, der einen Namen für die zu erstellende benannte Menge bereitstellt.  
  
 *Set_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), der eine Menge zurückgibt.  
  
 *Property_name*  
 Eine gültige Zeichenfolge, die den Namen einer Mengeneigenschaft bereitstellt.  
  
 *Property_Value*  
 Ein gültiger Skalarausdruck, der den Wert der Mengeneigenschaft definiert.  
  
## <a name="remarks"></a>Hinweise  
 Eine benannte Menge ist eine Menge von Dimensionselementen (oder ein Ausdruck, der eine Menge definiert), die Sie erstellen, um sie später wieder zu verwenden. Mit einer benannten Menge können Sie beispielsweise eine Menge von Dimensionselementen definieren, die aus den 10 umsatzstärksten Geschäften besteht. Dieser Satz kann statisch oder mithilfe einer Funktion wie definiert werden, wenn [TopCount](../mdx/topcount-mdx.md). Diese benannte Menge kann dann überall verwendet werden, wo die Menge der ersten 10 Geschäfte benötigt wird.  
  
 Die CREATE SET-Anweisung erstellt eine benannte Menge, die während der gesamten Sitzung verfügbar bleibt und somit in mehreren Abfragen innerhalb einer Sitzung verwendet werden kann. Weitere Informationen finden Sie unter [mithilfe von berechneten Elementen &#40;MDX&#41;](../analysis-services/multidimensional-models/mdx/mdx-calculated-members-session-scoped-calculated-members.md).  
  
 Sie können auch eine benannte Menge zum Verwenden in einer einzelnen Abfrage definieren. Zur Definition einer solchen Menge verwenden Sie die WITH-Klausel in der SELECT-Anweisung. Weitere Informationen zu der WITH-Klausel, finden Sie unter [mithilfe von benannten Mengen &#40;MDX&#41;](../analysis-services/multidimensional-models/mdx/mdx-named-sets-creating-query-scoped-named-sets.md).  
  
 Die *Set_Expression* -Klausel kann jede Funktion, die von MDX-Syntax unterstützt enthalten. Mengen, die mit der CREATE SET-Anweisung ohne Angabe der SESSION-Klausel erstellt wurden, haben die Sitzung als Bereich. Verwenden Sie die WITH-Klausel, um eine Menge mit Abfragebereich zu erstellen.  
  
 Die Angabe eines anderen als des aktuell verbundenen Cubes verursacht einen Fehler. Daher sollten Sie den aktuellen Cube mithilfe von CURRENTCUBE statt mit dem Cubenamen angeben.  
  
## <a name="scope"></a>Bereich  
 Eine benutzerdefinierte Menge kann in einem der Bereiche auftreten, die in der folgenden Tabelle aufgeführt sind.  
  
 Bereich einer Abfrage  
 Die Sichtbarkeit und Lebensdauer der Menge ist auf die Abfrage beschränkt. Die Menge ist in einer einzelnen Abfrage definiert. Der Abfragebereich hat Vorrang vor dem Sitzungsbereich. Weitere Informationen finden Sie unter [mithilfe von benannten Mengen &#40;MDX&#41;](../analysis-services/multidimensional-models/mdx/mdx-named-sets-creating-query-scoped-named-sets.md).  
  
 Bereich einer Sitzung  
 Die Sichtbarkeit und Lebensdauer der Menge ist auf die Sitzung beschränkt, in der die Menge erstellt wurde. (Die Lebensdauer ist geringer als die Sitzungsdauer, wenn eine DROP SET-Anweisung in der Gruppe ausgegeben wird.) Die CREATE SET-Anweisung erstellt einen Satz mit Sitzungsbereich. Verwenden Sie die WITH-Klausel, um eine Menge mit Abfragebereich zu erstellen.  
  
### <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird eine Menge mit dem Namen Core Products erstellt. Die SELECT-Abfrage veranschaulicht, wie die neu erstellte Menge aufgerufen wird. Die CREATE SET-Anweisung muss vor der SELECT-Abfrage ausgeführt werden – es können nicht beide im gleichen Batch ausgeführt werden.  
  
```  
CREATE SET [Adventure Works].[Core Products] AS '{[Product].[Category].[Bikes]}'  
  
SELECT [Core Products] ON 0  
  FROM [Adventure Works]  
```  
  
## <a name="set-evaluation"></a>Mengenauswertung  
 Die Mengenauswertung kann so definiert werden, dass sie auf unterschiedliche Weise ausgeführt wird, nämlich entweder einmal bei der Mengenerstellung oder bei jeder Verwendung der Menge.  
  
 STATIC  
 Gibt an, dass die Menge nur einmal ausgewertet wird, nämlich, wenn die CREATE SET-Anweisung ausgewertet wird.  
  
 DYNAMIC  
 Gibt an, dass die Menge bei jeder Verwendung in einer Abfrage ausgewertet wird.  
  
## <a name="set-visibility"></a>Sichtbarkeit der Menge  
 Die Menge kann für andere Benutzer, die den Cube abfragen, sichtbar oder unsichtbar sein.  
  
 HIDDEN  
 Gibt an, dass die Menge für Benutzer, die den Cube abfragen, nicht sichtbar ist.  
  
## <a name="standard-properties"></a>Standardeigenschaften  
 Jede Menge verfügt über Standardeigenschaften. Wenn eine Client-Anwendung verbunden ist, um [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], die Standardeigenschaften sind entweder unterstützt oder verfügbar ist, unterstützt werden müssen, wie der Administrator wählt.  
  
|Eigenschaftsbezeichner|Bedeutung|  
|-------------------------|-------------|  
|CAPTION|Eine Zeichenfolge, die von der Clientanwendung als Beschriftung für die Menge verwendet wird.|  
|DISPLAY_FOLDER|Eine Zeichenfolge, die den Pfad des Anzeigeordners angibt, der von der Clientanwendung zum Anzeigen der Menge verwendet wird. Das Trennzeichen für Ordnerebenen wird von der Clientanwendung definiert. Für Tools und Clients, die vom [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], den umgekehrten Schrägstrich (\\) ebenentrennzeichen ist. Um mehrere Anzeigeordner für eine definierte Menge bereitzustellen, verwenden Sie ein Semikolon (;) als Trennzeichen für die Ordner.|  
  
## <a name="see-also"></a>Siehe auch  
 [DROP SET-Anweisung &#40;MDX&#41;](../mdx/mdx-data-definition-drop-set.md)   
 [MDX-Datendefinitionsanweisungen &#40;MDX&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
