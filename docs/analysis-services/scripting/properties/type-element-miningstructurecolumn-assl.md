---
title: Geben Sie-Element (MiningStructureColumn) (ASSL) | Microsoft Docs
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: bcb7cec0d968e1320bdafc4bf53d25d6efdabc6f
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="type-element-miningstructurecolumn-assl"></a>Type-Element (MiningStructureColumn) (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Enthält den Typ des der [MiningStructureColumn](../../../analysis-services/scripting/data-type/miningstructurecolumn-data-type-assl.md) Element.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<MiningStructureColumn>  
   ...  
   <Type>...</Type>  
   ...  
</MiningStructureColumn>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Beschreibung|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|Keine|  
|Kardinalität|1-1: Erforderliches Element, das nur einmal auftritt.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[Miningstructurecolumn-Objekt](../../../analysis-services/scripting/data-type/miningstructurecolumn-data-type-assl.md)|  
|Untergeordnete Elemente|Keine|  
  
## <a name="remarks"></a>Hinweise  
 Der Wert dieses Elements ist auf eine der in der folgenden Tabelle aufgelisteten Zeichenfolgen beschränkt.  
  
|Wert|Description|  
|-----------|-----------------|  
|*Long*|Ein 64-Bit-Integer mit Vorzeichen Dieser Datentyp wird dem **Int64** -Datentyp in der [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework und dem DBTYPE_I8-Geben Sie in der OLE DB.|  
|*Boolean*|Ein boolescher Wert. Dieser Datentyp wird dem **booleschen** -Datentyp in .NET Framework und dem DBTYPE_BOOL-Datentyp in OLE DB.|  
|*Text*|Ein mit NULL endender Datenstrom von Unicode-Zeichen. Dieser Datentyp wird dem **Zeichenfolge** in .NET Framework und dem DBTYPE_WSTR-Datentyp in OLE DB-Datentyp.|  
|*Double*|Eine Gleitkommazahl mit doppelter Genauigkeit innerhalb des Bereichs-1, 79E + 308 bis 1,79E + 308. Dieser Datentyp wird dem **doppelte** -Datentyp in .NET Framework und dem DBTYPE_R8-Datentyp in OLE DB.|  
|*Datum*|Datumdaten, gespeichert als Gleitkommazahl mit doppelter Genauigkeit. Der ganzzahlige Teil gibt die Anzahl von Tagen seit dem 30. Dezember 1899 wieder, während der Bruchteil ein Teil eines Tages ist. Dieser Datentyp wird dem **"DateTime"** in .NET Framework und dem DBTYPE_DATE-Datentyp in OLE DB-Datentyp.|  
|*Tabelle*|Eine geschachtelte Tabelle. Dieser Datentyp wird dem DBTYPE_HCHAPTER-Datentyp in der OLE DB zugeordnet.<br /><br /> Hinweis: Tabellenspalten in .NET Framework verfügen nicht über einen äquivalenten integrierten Datentyp, jedoch werden stattdessen von unterstützt die **DataReader** Klasse.|  
  
 Die Enumeration, die den zulässigen Werten für entspricht **Typ** im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.MiningStructureColumnTypes>.  
  
 Das Element, das das übergeordnete Element des entspricht **Typ** im Objekt Analysis Management Objects (AMO) Modell ist <xref:Microsoft.AnalysisServices.MiningStructureColumn>.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbankeigenschaften & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
