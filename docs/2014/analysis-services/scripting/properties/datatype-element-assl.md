---
title: DataType-Element (ASSL) | Microsoft Docs
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
- DataType Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DataType
helpviewer_keywords:
- DataType element
ms.assetid: efe6f717-8288-4ca2-85ed-9b63d27c02d8
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 706d13e68b21a71fa9be80bf89fc4f9cdd4c6014
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36048147"
---
# <a name="datatype-element-assl"></a>DataType-Element (ASSL)
  Definiert den Datentyp des zugeordneten Elements.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
  
<DataItem> <!-- or Measure -->  
   ...  
   <DataType>...</DataType>  
   ...  
</DataItem>  
```  
  
## <a name="element-characteristics"></a>Elementmerkmale  
  
|Merkmal|Description|  
|--------------------|-----------------|  
|Datentyp und -länge|Zeichenfolge (Enumeration)|  
|Standardwert|InclusionThresholdSetting|  
|Cardinality|0-1: Optionales Element, das nur einmal auftreten kann.|  
  
## <a name="element-relationships"></a>Elementbeziehungen  
  
|Beziehung|Element|  
|------------------|-------------|  
|Übergeordnetes Element|[DataItem](../data-type/dataitem-data-type-assl.md), [Measure](../objects/measure-element-assl.md)|  
|Untergeordnete Elemente|InclusionThresholdSetting|  
  
## <a name="remarks"></a>Hinweise  
 Die Werte für `DataType` werden in der `System.Data.OleDb.OleDbType`-Enumeration definiert. Aber nur die Enumerationswerte in der folgenden Tabelle sind im `DataType`-Element gültig.  
  
|value|Description|  
|-----------|-----------------|  
|*BigInt*|Ein 64-Bit-Integer mit Vorzeichen Dieser Datentyp wird dem `Int64` -Datentyp im [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework und dem DBTYPE_I8-Geben Sie in der OLE DB.|  
|*Bool*|Ein boolescher Wert. Dieser Datentyp wird dem `Boolean`-Datentyp in .NET Framework und dem DBTYPE_BOOL-Datentyp in der OLE DB zugeordnet.|  
|*Währung*|Ein Währungswert im Bereich von-2<sup>63</sup> (bzw. -922.337.203.685.477,5808) auf 2<sup>63</sup>-1 (bzw. + 922.337.203.685.477,5807) mit einer Genauigkeit von einem Zehntausendstel einer Währungseinheit. Dieser Datentyp wird dem `Decimal`-Datentyp in .NET Framework und dem DBTYPE_CY-Datentyp in der OLE DB zugeordnet.|  
|*Datum*|Datumdaten, gespeichert als Gleitkommazahl mit doppelter Genauigkeit. Der ganzzahlige Teil gibt die Anzahl von Tagen seit dem 30. Dezember 1899 wieder, während der Bruchteil ein Teil eines Tages ist. Dieser Datentyp wird dem `DateTime`-Datentyp in .NET Framework und dem DBTYPE_DATE-Datentyp in der OLE DB zugeordnet.|  
|*Double*|Eine Gleitkommazahl mit doppelter Genauigkeit Zahl innerhalb des Bereichs von - 1,79E + 308 bis 1,79E + 308. Dieser Datentyp wird dem `Double`-Datentyp in .NET Framework und dem DBTYPE_R8-Datentyp in der OLE DB zugeordnet.|  
|*Integer*|Ein 32-Bit-Integer mit Vorzeichen Dieser Datentyp wird dem `Int32`-Datentyp in .NET Framework und dem DBTYPE_I4-Datentyp in der OLE DB zugeordnet.|  
|*Single*|Eine Gleitkommazahl mit einfacher Genauigkeit Zahl innerhalb des Bereichs von - 3,40E + 38 bis 3,40E + 38. Dieser Datentyp wird dem `Single`-Datentyp in .NET Framework und dem DBTYPE_R4-Datentyp in der OLE DB zugeordnet.|  
|*"Smallint"*|Eine 16-Bit-Ganzzahl mit Vorzeichen. Dieser Datentyp wird dem `Int16`-Datentyp in .NET Framework und dem DBTYPE_I2-Datentyp in der OLE DB zugeordnet.|  
|*"Tinyint"*|Eine 8-Bit-Ganzzahl mit Vorzeichen. Dieser Datentyp wird dem `SByte`-Datentyp in .NET Framework und dem DBTYPE_I1-Datentyp in der OLE DB zugeordnet.|  
|*UnsignedBigInt*|Eine 64-Bit-Ganzzahl ohne Vorzeichen. Dieser Datentyp wird dem `UInt64`-Datentyp in .NET Framework und dem DBTYPE_UI8-Datentyp in der OLE DB zugeordnet.|  
|*UnsignedInt*|Eine 32-Bit-Ganzzahl ohne Vorzeichen. Dieser Datentyp wird dem `UInt32`-Datentyp in .NET Framework und dem DBTYPE_UI4-Datentyp in der OLE DB zugeordnet.|  
|*UnsignedSmallInt*|Eine 16-Bit-Ganzzahl ohne Vorzeichen. Dieser Datentyp wird dem `UInt16`-Datentyp in .NET Framework und dem DBTYPE_UI2-Datentyp in der OLE DB zugeordnet.|  
|*WChar*|Ein mit NULL endender Datenstrom von Unicode-Zeichen. Dieser Datentyp wird dem `String`-Datentyp in .NET Framework und dem DBTYPE_WSTR-Datentyp in der OLE DB zugeordnet.|  
|*Geerbt*|Der Datentyp des der `DataItem` enthalten sind, der [Quelle](source-element-measure-assl.md) Element von der `Measure` Element. **Hinweis:** gilt nur für `Measure` Elemente.|  
  
## <a name="see-also"></a>Siehe auch  
 [Eigenschaften &#40;ASSL&#41;](properties-assl.md)  
  
  