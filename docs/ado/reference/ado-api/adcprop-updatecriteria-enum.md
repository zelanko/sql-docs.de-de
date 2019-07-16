---
title: ADCPROP_UPDATECRITERIA_ENUM | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADCPROP_UPDATECRITERIA_ENUM
helpviewer_keywords:
- ADCPROP_UPDATECRITERIA_ENUM [ADO]
ms.assetid: 33fd7b65-2ec8-4f62-91a7-630b5dab1aa2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 12d960e8fcd5e1f27ea8198ce52e080f6fddf7c2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67921416"
---
# <a name="adcpropupdatecriteriaenum"></a>ADCPROP_UPDATECRITERIA_ENUM
Gibt an, welche Felder verwendet werden können, zum Erkennen von Konflikten während einer vollständigen Aktualisierung einer Zeile mit der Datenquelle mit einem [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt.  
  
 Verwenden Sie diese Konstanten mit dem **Recordset** "**Updatekriterium**" dynamische Eigenschaft, die in verwiesen wird die [ADO dynamische Property-Index](../../../ado/reference/ado-api/ado-dynamic-property-index.md) und in der dokumentiert[ Microsoft Cursor Service für OLE DB](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md) Dokumentation.  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|**adCriteriaAllCols**|1|Erkennt Konflikte, wenn jede Spalte der Quelle Datenzeile geändert wurde.|  
|**adCriteriaKey**|0|Erkennt Konflikte, wenn die Schlüsselspalte des ausgewählten Zeile Datenquelle geändert wurde, was bedeutet, dass die Zeile gelöscht wurde.|  
|**adCriteriaTimeStamp**|3|Erkennt Konflikte, wenn der Zeitstempel des ausgewählten Zeile Datenquelle geändert wurde, d. h., die die Zeile wurde auf die zugegriffen wurde nach der **Recordset** abgerufen wurde.|  
|**adCriteriaUpdCols**|2|Erkennt Konflikte, wenn eine der Spalten der Datenquelle, die Zeile auf aktualisierte Felder entsprechen den **Recordset** geändert wurden.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-äquivalent  
 Package: **com.ms.wfc.data**  
  
|Konstante|  
|--------------|  
|AdoEnums.AdcPropUpdateCriteria.ALLCOLS|  
|AdoEnums.AdcPropUpdateCriteria.KEY|  
|AdoEnums.AdcPropUpdateCriteria.TIMESTAMP|  
|AdoEnums.AdcPropUpdateCriteria.UPDCOLS|
