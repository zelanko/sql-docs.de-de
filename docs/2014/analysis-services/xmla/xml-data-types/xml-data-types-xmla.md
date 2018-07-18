---
title: XML-Datentypen (XMLA) | Microsoft-Dokumentation
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9ccba3c69101362d1a384320808a30066ae572b3
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37297090"
---
# <a name="xml-data-types-xmla"></a>XML-Datentypen (XMLA)
  Zusätzlich zu den von der XML 1.0-Empfehlung definierten standardmäßigen Grundtypen und abgeleiteten Typen definiert die XMLA 1.1-Spezifikation (XML for Analysis) zusätzliche Datentypen, um die Darstellung von mehrdimensionalen und tabellarischen Daten zu unterstützen.  
  
 XMLA verwendet die in der folgenden Tabelle aufgelisteten Datentypen.  
  
|Datentypen|Description|  
|----------------|-----------------|  
|Boolean|Die standard-XML- `boolean` -Datentyp.|  
|Decimal|Die standard-XML- `decimal` -Datentyp.|  
|[EmptyResult](emptyresult-data-type-xmla.md)|Ein Namespace auf dem `root`-Element. Dieser Namespace wird zurückgegeben, wenn ein XMLA-Befehl kein Ergebnis zurückgibt, weil der XMLA-Befehl nicht normalerweise kein Ergebnis zurückgibt, oder aufgrund eines Fehlers auf das [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Instanz während der Ausführung des XMLA-Befehls.|  
|[EnumString](enumstring-data-type-xmla.md)|Ein Satz genannter Zeichenfolgenkonstanten für einen gegebenen Enumerator.|  
|Integer|Die standard-XML- `int` -Datentyp.|  
|[MDDataSet](mddataset-data-type-xmla.md)|Mehrdimensionale Daten, die zurückgegeben werden, indem die *Ergebnis* Parameter der [Execute](../xml-elements-methods-execute.md) Methode.|  
|[Resultset](resultset-data-type-xmla.md)|Ein selbstbeschreibendes XML-Resultset zurückgegebenes der `Execute` Methode.|  
|[Rowset](rowset-data-type-xmla.md)|Zeilen aus einer Datenquelle, die von einem eingebetteten XML-Schema strukturiert wurden zurückgegeben, indem die [Discover](../xml-elements-methods-discover.md) Methode.|  
|Zeichenfolge|Der XML-Code `string` -Datentyp.|  
|UnsignedInt|Der `unsignedInt`-XML-Schematyp.|  
  
 Vollständige Beschreibungen der XML-Standarddatentypen finden Sie in den Kandidatenempfehlungen des World Wide Web Consortium (WC3).  
  
## <a name="see-also"></a>Siehe auch  
 [XML-Elemente &#40;XMLA&#41;](../../dev-guide/xml-elements-xmla.md)   
 [XML for Analysis &#40;XMLA&#41; Verweis](../xml-for-analysis-xmla-reference.md)  
  
  
