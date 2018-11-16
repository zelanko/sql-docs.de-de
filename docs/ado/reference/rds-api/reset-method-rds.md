---
title: Reset-Methode (RDS) | Microsoft-Dokumentation
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Reset method [ADO]
ms.assetid: 3957197a-f543-4d6b-9e11-67a77c2063b7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7fc769436a919a4d522fb48699c6fc6faa0d6e5c
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "51600050"
---
# <a name="reset-method-rds"></a>Reset-Methode (RDS)
Führt Sie die Sortierung und Filterung für eine clientseitige **Recordset** basierend auf den angegebenen Eigenschaften der sortieren und filtern.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DataControl.Reset(value)  
```  
  
#### <a name="parameters"></a>Parameter  
 *DataControl*  
 Eine Objektvariable, steht ein [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) Objekt.  
  
 *value*  
 Optional. Ein **booleschen** Wert, der **"true"** (Standard), wenn Sie für das aktuelle "gefiltert" Rowset filtern möchten. **"False"** gibt an, dass Sie auf das ursprüngliche Rowset filtern, entfernen alle vorherigen Filteroptionen.  
  
## <a name="remarks"></a>Hinweise  
 Die [SortColumn](../../../ado/reference/rds-api/sortcolumn-property-rds.md), [Sortierreihenfolge](../../../ado/reference/rds-api/sortdirection-property-rds.md), [FilterValue](../../../ado/reference/rds-api/filtervalue-property-rds.md), [FilterCriterion](../../../ado/reference/rds-api/filtercriterion-property-rds.md), und [FilterColumn](../../../ado/reference/rds-api/filtercolumn-property-rds.md)Eigenschaften bereitstellen, Sortier- und Filterfunktionen für den clientseitigen Cache. Die Funktion zum Sortieren sortiert die Datensätze durch Werte aus einer Spalte. Die Funktion zum Filtern wird eine Teilmenge der Datensätze auf Grundlage einer Suchkriterien angezeigt, während das vollständige [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) wird im Cache beibehalten. Die **zurücksetzen** Methode führen Sie die Kriterien und Ersetzen Sie die aktuelle **Recordset** mit einen aktualisierbaren **Recordset**.  
  
 Wenn Änderungen auf die ursprünglichen Daten, die nicht übermittelt wurden, werden die **zurücksetzen** Methode fehl. Verwenden Sie zunächst die [SubmitChanges](../../../ado/reference/rds-api/submitchanges-method-rds.md) Methode zum Speichern von Änderungen in einer Lese-/Schreibzugriff **Recordset**, und verwenden Sie dann die **zurücksetzen** Methode sortieren oder Filtern der Datensätze.  
  
 Wenn Sie mehr als ein Filter für Ihr Rowset ausführen möchten, können Sie die optionale *booleschen* Argument mit den **zurücksetzen** Methode. Das folgende Beispiel zeigt, wie Sie dies durchführen:  
  
```  
ADC.SQL = "Select au_lname from authors"  
ADC.Refresh    ' Get the new rowset.  
  
ADC.FilterColumn = "au_lname"  
ADC.FilterCriterion = "<"  
ADC.FilterValue = "'M'"  
ADC.Reset         ' Rowset now has all Last Names < "M".  
  
ADC.FilterCriterion = ">"  
ADC.FilterValue = "'F'"  
' Passing True is not necessary, because it is the   
' default filter on the current "filtered" rowset.  
ADC.Reset(TRUE)     ' Rowset now has all Last   
                    ' Names < "M" and > "F".  
  
ADC.FilterCriterion = ">"  
ADC.FilterValue = "'T'"  
' Filter on the original rowset, throwing out the  
' previous filter options.  
ADC.Reset(FALSE)   ' Rowset now has all Last Names > "T".  
```  
  
## <a name="applies-to"></a>Gilt für  
 [DataControl-Objekt (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Siehe auch  
 [FilterColumn, FilterCriterion, FilterValue, SortColumn- und SortDirection-Eigenschaften und Reset-Methode – Beispiel (VBScript)](../../../ado/reference/rds-api/filter-column-criterion-value-sortcolumn-sortdirection-example-vbscript.md)   
 [SubmitChanges-Methode (RDS)](../../../ado/reference/rds-api/submitchanges-method-rds.md)



