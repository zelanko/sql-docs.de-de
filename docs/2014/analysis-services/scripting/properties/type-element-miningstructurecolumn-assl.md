---
title: Type-Element (MiningStructureColumn) (ASSL) | Microsoft-Dokumentation
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
api_name:
- Type Element (MiningStructureColumn)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- TYPE
helpviewer_keywords:
- Type element
ms.assetid: ce999716-9487-4348-bc42-270a2026a452
caps.latest.revision: 34
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 30ce9327fb28e9f452e643ded604f2a8dd72a084
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37304240"
---
# <a name="type-element-miningstructurecolumn-assl"></a>Type-Element (MiningStructureColumn) (ASSL)
  Enthält den Typ des der [MiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<MiningStructureColumn>  
   ...  
   <Type>...</Type>  
   ...  
</MiningStructureColumn>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|1-1: Erforderliches Element, das nur einmal auftritt.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[MiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|value|Description|  
|-----------|-----------------|  
|*Long*|Ein 64-Bit-Integer mit Vorzeichen Dieser Datentyp wird dem `Int64` -Datentyp in der [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework und dem DBTYPE_I8-Geben Sie in der OLE DB.|  
|*Boolean*|Ein boolescher Wert. Dieser Datentyp wird dem `Boolean`-Datentyp in .NET Framework und dem DBTYPE_BOOL-Datentyp in der OLE DB zugeordnet.|  
|*Text*|Ein mit NULL endender Datenstrom von Unicode-Zeichen. Dieser Datentyp wird dem `String`-Datentyp in .NET Framework und dem DBTYPE_WSTR-Datentyp in der OLE DB zugeordnet.|  
|*Double-Wert*|Eine Gleitkommazahl mit doppelter Genauigkeit im Bereich zwischen-1,79E + 308 bis 1,79E + 308. Dieser Datentyp wird dem `Double`-Datentyp in .NET Framework und dem DBTYPE_R8-Datentyp in der OLE DB zugeordnet.|  
|*Datum*|Datumdaten, gespeichert als Gleitkommazahl mit doppelter Genauigkeit. Der ganzzahlige Teil gibt die Anzahl von Tagen seit dem 30. Dezember 1899 wieder, während der Bruchteil ein Teil eines Tages ist. Dieser Datentyp wird dem `DateTime`-Datentyp in .NET Framework und dem DBTYPE_DATE-Datentyp in der OLE DB zugeordnet.|  
|*Tabelle*|Eine geschachtelte Tabelle. Dieser Datentyp wird dem DBTYPE_HCHAPTER-Datentyp in der OLE DB zugeordnet. **Hinweis:** Tabellenspalten in .NET Framework haben sich nicht auf einen äquivalenten integrierten Datentyp, aber werden stattdessen unterstützt der `DataReader` Klasse.|  
  
 Die Enumeration, die den zulässigen Werten für entspricht `Type` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.MiningStructureColumnTypes>.  
  
 Das Element, das dem übergeordneten entspricht `Type` im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.MiningStructureColumn>.  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  
