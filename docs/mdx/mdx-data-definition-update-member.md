---
title: Update Member-Anweisung (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 73a2bf2973d8c4f8f9bf9ac886728fb45250343f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68038143"
---
# <a name="mdx-data-definition---update-member"></a>MDX-Datendefinition – UPDATE MEMBER


  Aktualisiert ein vorhandenes berechnetes Element.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
UPDATE MEMBER Cube_Name.Member_Name   
   AS MDX_Expression  
      [,Property_Name = Property_Value, ...n]  
......[,SCOPE_ISOLATION = CUBE]  
```  
  
## <a name="arguments"></a>Argumente  
 *Cube_Name*  
 Eine gültige Zeichenfolge, die den Namen des Cubes bereitstellt, in dem das Element enthalten ist.  
  
 *Member_Name*  
 Eine gültige Zeichenfolge, die den Namen eines vorhandenen Elements bereitstellt.  
  
 *MDX_Expression*  
 Ein gültiger MDX-Ausdruck (Multidimensional Expressions), auf den das Element aktualisiert wird.  
  
 *Property_Name*  
 Eine gültige Zeichenfolge, die den Namen einer Eigenschaft eines berechneten Elements bereitstellt.  
  
 *Property_Value*  
 Ein gültiger Skalarausdruck, der den Eigenschaftswert des berechneten Elements bereitstellt.  
  
## <a name="remarks"></a>Bemerkungen  
 Mit der UPDATE MEMBER-Anweisung wird ein vorhandenes berechnetes Element aktualisiert und gleichzeitig die relative Rangfolge des Elements in Bezug auf andere Berechnungen beibehalten. Deshalb können Sie die Lösungsreihenfolge (SOLVEORDER) mithilfe der UPDATE MEMBER-Anweisung nicht ändern.  
  
 Eine UPDATE MEMBER-Anweisung kann nicht im MDX-Skript für einen Cube angegeben werden.  
  
 Die Angabe eines anderen als des aktuell verbundenen Cubes verursacht einen Fehler. Daher sollten Sie den aktuellen Cube mithilfe von CURRENTCUBE statt mit dem Cubenamen angeben.  
  
 Weitere Informationen zu Elementeigenschaften, die durch OLE DB definiert sind, finden Sie in der OLE DB-Dokumentation.  
  
## <a name="standard-properties"></a>Standardeigenschaften  
 Jedes Element verfügt über Standardeigenschaften. In der folgenden Tabelle werden diese Standardeigenschaften aufgeführt.  
  
|Eigenschaftsbezeichner|Bedeutung|  
|-------------------------|-------------|  
|FORMAT_STRING|Eine Format Zeichenfolge im Office-Stil, die die Client Anwendung zum Anzeigen von Zellwerten verwenden kann.|  
|VISIBLE|Ein Wert, der bestimmt, ob das berechnete Element in einem Schemarowset sichtbar ist. Sichtbare berechnete Elemente können einer Menge mit der [AddCalculatedMembers](../mdx/addcalculatedmembers-mdx.md) -Funktion hinzugefügt werden. Ein Wert ungleich 0 zeigt an, dass das berechnete Element sichtbar ist. Der Standardwert für diese Eigenschaft ist *sichtbar*.<br /><br /> Berechnete Elemente, die nicht sichtbar sind, werden üblicherweise als Zwischenschritte in komplexeren berechneten Elementen verwendet. Auf diese berechneten Elemente können auch andere Arten von Elementen (z. B. Measures) verweisen.|  
|NON_EMPTY_BEHAVIOR|Das Measure oder die Menge, mit dem oder der MDX beim Auflösen leerer Zellen das Verhalten berechneter Elemente bestimmt.|  
|CAPTION|Ein Zeichenfolgenwert, der die Beschriftung angibt, die von der Clientanwendung zum Anzeigen des Elements verwendet wird.|  
|DISPLAY_FOLDER|Ein Zeichenfolgenwert, der den Pfad des Anzeigeordners angibt, in dem das Element von der Clientanwendung angezeigt wird. Das Trennzeichen für Ordnerebenen wird von der Clientanwendung definiert. Für die von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]bereitgestellten Tools und Clients wird der umgekehrte schräg\\Strich () als Ebenentrennzeichen verwendet. Um mehrere Anzeigeordner für ein definiertes Element bereitzustellen, verwenden Sie ein Semikolon (;) als Trennzeichen für die Ordner.|  
|ASSOCIATED_MEASURE_GROUP|Der Name der Measuregruppe, der dieses Element zugeordnet wird.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Drop Member-Anweisung &#40;MDX-&#41;](../mdx/mdx-data-definition-drop-member.md)   
 [Create Member-Anweisung &#40;MDX-&#41;](../mdx/mdx-data-definition-create-member.md)   
 [MDX-Daten Definitions Anweisungen &#40;MDX-&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
