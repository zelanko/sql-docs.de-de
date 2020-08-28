---
description: FilterColumn-Eigenschaft (RDS)
title: FilterColumn-Eigenschaft (RDS) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- FilterColumn property [ADO]
ms.assetid: 0a5473e8-8ce6-4518-83fb-4920b827e285
author: rothja
ms.author: jroth
ms.openlocfilehash: 1af2eb386f3d61387158a3a654ff900f6b6ad43a
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88982201"
---
# <a name="filtercolumn-property-rds"></a>FilterColumn-Eigenschaft (RDS)
Gibt die Spalte an, für die die Filterkriterien ausgewertet werden sollen.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DataControl.FilterColumn = String  
```  
  
#### <a name="parameters"></a>Parameter  
 *DataControl*  
 Eine Objekt Variable, die einen [RDS darstellt. DataControl](./datacontrol-object-rds.md) -Objekt.  
  
 *String*  
 Ein **Zeichen** folgen Wert, der die Spalte angibt, für die die Filterkriterien ausgewertet werden sollen. Die Filterkriterien werden in der [filterCriteria](./filtercriterion-property-rds.md) -Eigenschaft angegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Die Eigenschaften [SortColumn](./sortcolumn-property-rds.md), [SortDirection](./sortdirection-property-rds.md), [FilterValue](./filtervalue-property-rds.md), [Filterkriterium](./filtercriterion-property-rds.md)und **FilterColumn** stellen Sortier-und Filterfunktionen für den Client seitigen Cache bereit. Die Sortierfunktion ordnet Datensätze nach Werten aus einer Spalte an. Die Filterfunktion zeigt eine Teilmenge der Datensätze basierend auf den Suchkriterien an, während das vollständige [Recordset](../ado-api/recordset-object-ado.md) im Cache beibehalten wird. Die [Reset](./reset-method-rds.md) -Methode führt die Kriterien aus und ersetzt das aktuelle **Recordset** durch ein Aktualisier bares **Recordset**.  
  
## <a name="applies-to"></a>Gilt für  
 [DataControl-Objekt (RDS)](./datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Filter Column, Filterkriterium, FilterValue, SortColumn und SortDirection Properties und Reset Method example (VBScript)](./filter-column-criterion-value-sortcolumn-sortdirection-example-vbscript.md)   
 [Filterkriterium-Eigenschaft (RDS)](./filtercriterion-property-rds.md)   
 [FilterValue-Eigenschaft (RDS)](./filtervalue-property-rds.md)   
 [SortColumn-Eigenschaft (RDS)](./sortcolumn-property-rds.md)   
 [SortDirection-Eigenschaft (RDS)](./sortdirection-property-rds.md)