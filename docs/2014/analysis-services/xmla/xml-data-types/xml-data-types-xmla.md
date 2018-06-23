---
title: XML-Datentypen (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
- apinav
helpviewer_keywords:
- XML data types [XMLA]
- data types [XML for Analysis]
- XMLA, data types
- XML for Analysis, data types
ms.assetid: 979b5384-90d9-4e09-9286-1d1eafdc4864
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: d7a21691474e890ba8614715b18e972d1353b2c6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36061225"
---
# <a name="xml-data-types-xmla"></a>XML-Datentypen (XMLA)
  Zusätzlich zu den von der XML 1.0-Empfehlung definierten standardmäßigen Grundtypen und abgeleiteten Typen definiert die XMLA 1.1-Spezifikation (XML for Analysis) zusätzliche Datentypen, um die Darstellung von mehrdimensionalen und tabellarischen Daten zu unterstützen.  
  
 XMLA verwendet die in der folgenden Tabelle aufgelisteten Datentypen.  
  
|Datentypen|Description|  
|----------------|-----------------|  
|Boolean|Der standard-XML- `boolean` -Datentyp.|  
|Decimal|Der standard-XML- `decimal` -Datentyp.|  
|[EmptyResult](emptyresult-data-type-xmla.md)|Ein Namespace auf dem `root`-Element. Dieser Namespace wird zurückgegeben, wenn ein XMLA-Befehl kein Ergebnis zurückgibt, weil der XMLA-Befehl nicht normalerweise kein Ergebnis zurückgibt, oder aufgrund eines Fehlers auf das [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Instanz beim Ausführen des XMLA-Befehls.|  
|[EnumString](enumstring-data-type-xmla.md)|Ein Satz genannter Zeichenfolgenkonstanten für einen gegebenen Enumerator.|  
|Integer|Der standard-XML- `int` -Datentyp.|  
|[MDDataSet](mddataset-data-type-xmla.md)|Mehrdimensionale Daten, die zurückgegeben werden, indem Sie die *Ergebnis* Parameter von der [Execute](../xml-elements-methods-execute.md) Methode.|  
|[Resultset](resultset-data-type-xmla.md)|Ein selbstbeschreibendes XML-Resultset zurückgegeben, durch die `Execute` Methode.|  
|[Rowset](rowset-data-type-xmla.md)|Zurückgegebene Zeilen aus einer Datenquelle, die von einem eingebetteten XML-Schema strukturiert wurden die [Discover](../xml-elements-methods-discover.md) Methode.|  
|Zeichenfolge|Der XML-Code `string` -Datentyp.|  
|UnsignedInt|Der `unsignedInt`-XML-Schematyp.|  
  
 Vollständige Beschreibungen der XML-Standarddatentypen finden Sie in den Kandidatenempfehlungen des World Wide Web Consortium (WC3).  
  
## <a name="see-also"></a>Siehe auch  
 [XML-Elemente &#40;XMLA&#41;](../../dev-guide/xml-elements-xmla.md)   
 [XML for Analysis &#40;XMLA&#41; Verweis](../xml-for-analysis-xmla-reference.md)  
  
  