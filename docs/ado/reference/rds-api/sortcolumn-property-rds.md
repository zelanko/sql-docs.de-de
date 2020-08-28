---
description: SortColumn-Eigenschaft (RDS)
title: SortColumn-Eigenschaft (RDS) | Microsoft-Dokumentation
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 555ad28129e0a2868f0c1b9bc8c338e40022caa0
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88981201"
---
# <a name="sortcolumn-property-rds"></a>SortColumn-Eigenschaft (RDS)
Gibt an, in welcher Spalte die Datensätze sortiert werden sollen.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DataControl.SortColumn = String  
```  
  
#### <a name="parameters"></a>Parameter  
 *DataControl*  
 Eine Objekt Variable, die einen [RDS darstellt. DataControl](./datacontrol-object-rds.md) -Objekt.  
  
 *String*  
 Ein **Zeichen** folgen Wert, der den Namen oder Alias der Spalte darstellt, nach der die Datensätze sortiert werden sollen.  
  
## <a name="remarks"></a>Bemerkungen  
 Die Eigenschaften **SortColumn**, [SortDirection](./sortdirection-property-rds.md), [FilterValue](./filtervalue-property-rds.md), [Filterkriterium](./filtercriterion-property-rds.md)und [FilterColumn](./filtercolumn-property-rds.md) stellen Sortier-und Filterfunktionen für den Client seitigen Cache bereit. Die Sortierfunktion ordnet Datensätze nach Werten aus einer Spalte an. Die Filterfunktion zeigt eine Teilmenge der Datensätze basierend auf den Suchkriterien an, während das vollständige [Recordset](../ado-api/recordset-object-ado.md) im Cache beibehalten wird. Die [Reset](./reset-method-rds.md) -Methode führt die Kriterien aus und ersetzt das aktuelle **Recordset** durch ein Aktualisier bares **Recordset**.  
  
 Um nach einem **Recordset**zu sortieren, müssen Sie zunächst alle ausstehenden Änderungen speichern. Wenn Sie das RDS verwenden **. DataControl**, Sie können die [SubmitChanges](./submitchanges-method-rds.md) -Methode verwenden. Beispielsweise, wenn Ihr **RDS. DataControl** hat den Namen ADC1, der Code ist `ADC1.SubmitChanges` . Wenn Sie ein ADO- **Recordset**verwenden, können Sie die zugehörige [UpdateBatch](../ado-api/updatebatch-method.md) -Methode verwenden. Die Verwendung von **UpdateBatch** ist die empfohlene Methode für **Recordset** -Objekte [, die mit der Methode](./createrecordset-method-rds.md) "-Methode" erstellt werden. Der Code könnte z `myRS.UpdateBatch` . b. oder lauten `ADC1.Recordset.UpdateBatch` .  
  
## <a name="applies-to"></a>Gilt für  
 [DataControl-Objekt (RDS)](./datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Filter Column, Filterkriterium, FilterValue, SortColumn und SortDirection Properties und Reset Method example (VBScript)](./filter-column-criterion-value-sortcolumn-sortdirection-example-vbscript.md)   
 [Sort-Eigenschaft](../ado-api/sort-property.md)   
 [SortDirection-Eigenschaft (RDS)](./sortdirection-property-rds.md)