---
title: FilterColumn-Eigenschaft (RDS) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- FilterColumn property [ADO]
ms.assetid: 0a5473e8-8ce6-4518-83fb-4920b827e285
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: eed6a3f1ad03ae9cfb09695cfc7152df726c8244
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66712654"
---
# <a name="filtercolumn-property-rds"></a>FilterColumn-Eigenschaft (RDS)
Gibt die Spalte auf dem die Filterkriterien ausgewertet werden soll.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DataControl.FilterColumn = String  
```  
  
#### <a name="parameters"></a>Parameter  
 *DataControl*  
 Eine Objektvariable, steht ein [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) Objekt.  
  
 *String*  
 Ein **Zeichenfolge** Wert, der angibt, die Spalte auf dem die Filterkriterien ausgewertet werden soll. Die Filterkriterien werden angegeben, der [FilterCriterion](../../../ado/reference/rds-api/filtercriterion-property-rds.md) Eigenschaft.  
  
## <a name="remarks"></a>Hinweise  
 Die [SortColumn](../../../ado/reference/rds-api/sortcolumn-property-rds.md), [Sortierreihenfolge](../../../ado/reference/rds-api/sortdirection-property-rds.md), [FilterValue](../../../ado/reference/rds-api/filtervalue-property-rds.md), [FilterCriterion](../../../ado/reference/rds-api/filtercriterion-property-rds.md), und **FilterColumn**Eigenschaften bereitstellen, Sortier- und Filterfunktionen für den clientseitigen Cache. Die Funktion zum Sortieren sortiert die Datensätze durch Werte aus einer Spalte. Die Funktion zum Filtern wird eine Teilmenge der Datensätze auf Grundlage von Suchkriterien, während die vollständige [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) wird im Cache beibehalten. Die [zurücksetzen](../../../ado/reference/rds-api/reset-method-rds.md) Methode führen Sie die Kriterien und Ersetzen Sie die aktuelle **Recordset** mit einen aktualisierbaren **Recordset**.  
  
## <a name="applies-to"></a>Gilt für  
 [DataControl-Objekt (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Siehe auch  
 [FilterColumn, FilterCriterion, FilterValue, SortColumn- und SortDirection-Eigenschaften und Reset-Methode – Beispiel (VBScript)](../../../ado/reference/rds-api/filter-column-criterion-value-sortcolumn-sortdirection-example-vbscript.md)   
 [FilterCriterion-Eigenschaft (RDS)](../../../ado/reference/rds-api/filtercriterion-property-rds.md)   
 [FilterValue-Eigenschaft (RDS)](../../../ado/reference/rds-api/filtervalue-property-rds.md)   
 [SortColumn-Eigenschaft (RDS)](../../../ado/reference/rds-api/sortcolumn-property-rds.md)   
 [SortDirection-Eigenschaft (RDS)](../../../ado/reference/rds-api/sortdirection-property-rds.md)


