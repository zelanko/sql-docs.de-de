---
title: SortDirection-Eigenschaft (RDS) | Microsoft-Dokumentation
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- SortDirection property [RDS]
ms.assetid: 1d9d8715-e4ad-4ff3-bf7f-f1dc0532d8c2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9ef187cd2ae291413fccf10e2af51642c50e06e5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62670876"
---
# <a name="sortdirection-property-rds"></a>SortDirection-Eigenschaft (RDS)
Gibt an, ob eine Sortierreihenfolge aufsteigend oder absteigend sortiert wird.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DataControl.SortDirection = value  
```  
  
#### <a name="parameters"></a>Parameter  
 *DataControl*  
 Eine Objektvariable, steht ein [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) Objekt.  
  
 *Wert*  
 Ein **booleschen** Wert, der bei Festlegung auf **"true"**, gibt an, die Sortierreihenfolge ist Aufsteigend. **"False"** gibt eine absteigende Reihenfolge.  
  
## <a name="remarks"></a>Hinweise  
 Die [SortColumn](../../../ado/reference/rds-api/sortcolumn-property-rds.md), **Sortierreihenfolge**, [FilterValue](../../../ado/reference/rds-api/filtervalue-property-rds.md), [FilterCriterion](../../../ado/reference/rds-api/filtercriterion-property-rds.md), und [FilterColumn](../../../ado/reference/rds-api/filtercolumn-property-rds.md)Eigenschaften bereitstellen, Sortier- und Filterfunktionen für den clientseitigen Cache. Die Funktion zum Sortieren sortiert die Datensätze mithilfe von Werten aus einer Spalte. Die Funktion zum Filtern wird eine Teilmenge der Datensätze auf Grundlage von Suchkriterien, während die vollständige [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) wird im Cache beibehalten. Die [zurücksetzen](../../../ado/reference/rds-api/reset-method-rds.md) Methode führen Sie die Kriterien und Ersetzen Sie die aktuelle **Recordset** mit einen aktualisierbaren **Recordset**.  
  
## <a name="applies-to"></a>Gilt für  
 [DataControl-Objekt (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Siehe auch  
 [FilterColumn, FilterCriterion, FilterValue, SortColumn- und SortDirection-Eigenschaften und Reset-Methode – Beispiel (VBScript)](../../../ado/reference/rds-api/filter-column-criterion-value-sortcolumn-sortdirection-example-vbscript.md)   
 [Sort-Eigenschaft](../../../ado/reference/ado-api/sort-property.md)   
 [SortColumn-Eigenschaft (RDS)](../../../ado/reference/rds-api/sortcolumn-property-rds.md)


