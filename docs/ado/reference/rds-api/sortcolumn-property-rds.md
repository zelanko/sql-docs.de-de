---
title: SortColumn-Eigenschaft (RDS) | Microsoft-Dokumentation
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- SortColumn property [RDS]
ms.assetid: f6f80f67-f0fb-4e63-a5f5-8fdf312aac63
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 370bec12ac65e78c2eb104c3e5fe25d4fc8b434a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47763358"
---
# <a name="sortcolumn-property-rds"></a>SortColumn-Eigenschaft (RDS)
Gibt an, nach welcher Spalte die Datensätze sortiert.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/en-us/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DataControl.SortColumn = String  
```  
  
#### <a name="parameters"></a>Parameter  
 *DataControl*  
 Eine Objektvariable, steht ein [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) Objekt.  
  
 *String*  
 Ein **Zeichenfolge** Wert, der den Namen oder Alias der Spalte, um die Datensätze sortiert darstellt.  
  
## <a name="remarks"></a>Hinweise  
 Die **SortColumn**, [Sortierreihenfolge](../../../ado/reference/rds-api/sortdirection-property-rds.md), [FilterValue](../../../ado/reference/rds-api/filtervalue-property-rds.md), [FilterCriterion](../../../ado/reference/rds-api/filtercriterion-property-rds.md), und [FilterColumn](../../../ado/reference/rds-api/filtercolumn-property-rds.md)Eigenschaften bereitstellen, Sortier- und Filterfunktionen für den clientseitigen Cache. Die Funktion zum Sortieren sortiert die Datensätze durch Werte aus einer Spalte. Die Funktion zum Filtern wird eine Teilmenge der Datensätze auf Grundlage von Suchkriterien, während die vollständige [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) wird im Cache beibehalten. Die [zurücksetzen](../../../ado/reference/rds-api/reset-method-rds.md) Methode führen Sie die Kriterien und Ersetzen Sie die aktuelle **Recordset** mit einen aktualisierbaren **Recordset**.  
  
 Nach dem sortiert eine **Recordset**, müssen Sie zunächst alle ausstehenden Änderungen speichern. Bei Verwendung der **RDS. DataControl**, können Sie die [SubmitChanges](../../../ado/reference/rds-api/submitchanges-method-rds.md) Methode. Beispielsweise wenn Ihre **RDS. DataControl** ist mit dem Namen ADC1, ist Ihr Code wäre `ADC1.SubmitChanges`. Wenn Sie ein ADO verwenden **Recordset**, können Sie die [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) Methode. Mithilfe von **UpdateBatch** ist die empfohlene Methode für **Recordset** Objekte erstellt, mit der [CreateRecordset](../../../ado/reference/rds-api/createrecordset-method-rds.md) Methode. Angenommen, Ihr Code möglicherweise `myRS.UpdateBatch` oder `ADC1.Recordset.UpdateBatch`.  
  
## <a name="applies-to"></a>Gilt für  
 [DataControl-Objekt (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Siehe auch  
 [FilterColumn, FilterCriterion, FilterValue, SortColumn- und SortDirection-Eigenschaften und Reset-Methode – Beispiel (VBScript)](../../../ado/reference/rds-api/filter-column-criterion-value-sortcolumn-sortdirection-example-vbscript.md)   
 [Sort-Eigenschaft](../../../ado/reference/ado-api/sort-property.md)   
 [SortDirection-Eigenschaft (RDS)](../../../ado/reference/rds-api/sortdirection-property-rds.md)





