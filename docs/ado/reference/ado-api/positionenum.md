---
title: PositionEnum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- PositionEnum
helpviewer_keywords:
- PositionEnum enumeration
ms.assetid: e69af0a5-3405-4b72-9c6e-6b188ff746fd
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d5f7ca47177a953313ff983bb25f9178b73b4930
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67917603"
---
# <a name="positionenum"></a>PositionEnum
Gibt die aktuelle Position des Datensatzzeigers innerhalb einer [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|**adPosBOF**|-2|Gibt an, dass der Zeiger für den aktuellen Datensatz am Dateianfang ist (d. h. die [BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) Eigenschaft **"true"** ).|  
|**adPosEOF**|-3|Gibt an, dass der Zeiger für den aktuellen Datensatz am Ende der Datei ist (d. h. die [EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) Eigenschaft **"true"** ).|  
|**adPosUnknown**|-1|Gibt an, dass die **Recordset** ist leer, die aktuelle Position ist unbekannt, oder der Anbieter unterstützt nicht die [AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md) oder [AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md) Eigenschaft.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-äquivalent  
 Package: **com.ms.wfc.data**  
  
|Konstante|  
|--------------|  
|AdoEnums.Position.BOF|  
|AdoEnums.Position.EOF|  
|AdoEnums.Position.UNKNOWN|  
  
## <a name="applies-to"></a>Gilt für  
  
|||  
|-|-|  
|[AbsolutePage-Eigenschaft (ADO)](../../../ado/reference/ado-api/absolutepage-property-ado.md)|[AbsolutePosition-Eigenschaft (ADO)](../../../ado/reference/ado-api/absoluteposition-property-ado.md)|
