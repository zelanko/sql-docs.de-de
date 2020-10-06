---
description: Reset-Methode (RDS)
title: Reset-Methode (RDS) | Microsoft-Dokumentation
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: fcebd112b389fe98b69b25852ef0504e88890261
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2020
ms.locfileid: "91724259"
---
# <a name="reset-method-rds"></a>Reset-Methode (RDS)
Führt die Sortierung oder den Filter für ein Client seitiges **Recordset** basierend auf den angegebenen Sortier-und Filtereigenschaften aus.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](/dotnet/framework/wcf/)migriert werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DataControl.Reset(value)  
```  
  
#### <a name="parameters"></a>Parameter  
 *DataControl*  
 Eine Objekt Variable, die einen [RDS darstellt. DataControl](./datacontrol-object-rds.md) -Objekt.  
  
 *value*  
 Optional. Ein **boolescher** Wert, der **true** (Standard) ist, wenn Sie nach dem aktuellen "gefilterten" Rowset filtern möchten. **False** gibt an, dass Sie nach dem ursprünglichen Rowset filtern, indem Sie alle vorherigen Filteroptionen entfernen.  
  
## <a name="remarks"></a>Bemerkungen  
 Die Eigenschaften [SortColumn](./sortcolumn-property-rds.md), [SortDirection](./sortdirection-property-rds.md), [FilterValue](./filtervalue-property-rds.md), [Filterkriterium](./filtercriterion-property-rds.md)und [FilterColumn](./filtercolumn-property-rds.md) stellen Sortier-und Filterfunktionen für den Client seitigen Cache bereit. Die Sortierfunktion ordnet Datensätze nach Werten aus einer Spalte an. Die Filterfunktion zeigt eine Teilmenge der Datensätze basierend auf einem Suchkriterium an, während das vollständige [Recordset](../ado-api/recordset-object-ado.md) im Cache beibehalten wird. Die **Reset** -Methode führt die Kriterien aus und ersetzt das aktuelle **Recordset** durch ein Aktualisier bares **Recordset**.  
  
 Wenn Änderungen an den ursprünglichen Daten vorgenommen wurden, die noch nicht übermittelt wurden, tritt bei der **Reset** -Methode ein Fehler auf. Verwenden Sie zunächst die [SubmitChanges](./submitchanges-method-rds.md) -Methode, um Änderungen in einem Lese-/schreibrecordset zu speichern, und verwenden Sie dann die **Reset** -Methode, um die Datensätze zu sortieren oder zu filtern. **Recordset**  
  
 Wenn Sie mehr als einen Filter für das Rowset ausführen möchten, können Sie das optionale *boolesche* Argument mit der **Reset** -Methode verwenden. Dies wird anhand des folgenden Beispiels veranschaulicht:  
  
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
 [DataControl-Objekt (RDS)](./datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Filter Column, Filterkriterium, FilterValue, SortColumn und SortDirection Properties und Reset Method example (VBScript)](./filter-column-criterion-value-sortcolumn-sortdirection-example-vbscript.md)   
 [SubmitChanges-Methode (RDS)](./submitchanges-method-rds.md)