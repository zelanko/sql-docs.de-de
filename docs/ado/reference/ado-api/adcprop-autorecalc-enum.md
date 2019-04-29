---
title: ADCPROP_AUTORECALC_ENUM | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADCPROP_AUTORECALC_ENUM
helpviewer_keywords:
- ADCPROP_AUTORECALC_ENUM [ADO]
ms.assetid: ded4f087-87b9-4efa-8026-bde53d3e9e8a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bb10b3f4fb563275a8f27a92e41c265336c3cb55
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63065398"
---
# <a name="adcpropautorecalcenum"></a>ADCPROP_AUTORECALC_ENUM
Gibt an, wann die [MSDataShape](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) -Anbieter erneut berechnet aggregate und berechnete Spalten in einem hierarchischen Recordset.  
  
 Diese Konstanten werden nur verwendet, mit der **MSDataShape** Anbieter und die **Recordset** "**automatische Neuberechnung**" dynamische Eigenschaft, die in verwiesen wird die [ADO Dynamische Property-Index](../../../ado/reference/ado-api/ado-dynamic-property-index.md) und die in der [Microsoft Cursor Service für OLE DB](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md) oder [Microsoft Data Shaping Service für OLE DB](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) Dokumentation.  
  
|Konstante|Wert|Description|  
|--------------|-----------|-----------------|  
|**adRecalcAlways**|1|Standard. Jedes Mal, wenn berechnet die **MSDataShape** Anbieter bestimmt die Werte, die die berechneten Spalten abhängig geändert haben.|  
|**adRecalcUpFront**|0|Berechnet nur beim Erstellen zunächst die hierarchische **Recordset**.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-äquivalent  
 Diese Konstanten keine ADO/WFC-Entsprechungen.
