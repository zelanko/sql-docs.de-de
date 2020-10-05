---
description: FilterValue-Eigenschaft (RDS)
title: FilterValue-Eigenschaft (RDS) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- FilterValue property [ADO]
ms.assetid: 28f17186-b842-4cf9-b320-a9bb941c481b
author: rothja
ms.author: jroth
ms.openlocfilehash: 2f2731f86983f6e2c61f5626970e4fbbb3f09590
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2020
ms.locfileid: "91720671"
---
# <a name="filtervalue-property-rds"></a>FilterValue-Eigenschaft (RDS)
Gibt den Wert an, mit dem Datensätze gefiltert werden.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](/dotnet/framework/wcf/)migriert werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DataControl.FilterValue = String  
```  
  
#### <a name="parameters"></a>Parameter  
 *DataControl*  
 Eine Objekt Variable, die einen [RDS darstellt. DataControl](./datacontrol-object-rds.md) -Objekt.  
  
 *String*  
 Ein **Zeichen** folgen Wert, der einen Datenwert darstellt, mit dem Datensätze gefiltert werden (z `'Programmer'` `125` . b. oder).  
  
## <a name="remarks"></a>Bemerkungen  
 Die Eigenschaften [SortColumn](./sortcolumn-property-rds.md), [SortDirection](./sortdirection-property-rds.md), **FilterValue**, [Filterkriterium](./filtercriterion-property-rds.md)und [FilterColumn](./filtercolumn-property-rds.md) stellen Sortier-und Filterfunktionen für den Client seitigen Cache bereit. Die Sortierfunktion ordnet Datensätze nach Werten aus einer Spalte an. Die Filterfunktion zeigt eine Teilmenge der Datensätze basierend auf den Suchkriterien an, während das vollständige [Recordset](../ado-api/recordset-object-ado.md) im Cache beibehalten wird. Die [Reset](./reset-method-rds.md) -Methode führt die Kriterien aus und ersetzt das aktuelle **Recordset** durch ein Aktualisier bares **Recordset**.  
  
 NULL-Werte führen zu einem Typen Konflikt Fehler.  
  
## <a name="applies-to"></a>Gilt für  
 [DataControl-Objekt (RDS)](./datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Filter Column, Filterkriterium, FilterValue, SortColumn und SortDirection Properties und Reset Method example (VBScript)](./filter-column-criterion-value-sortcolumn-sortdirection-example-vbscript.md)   
 [FilterColumn-Eigenschaft (RDS)](./filtercolumn-property-rds.md)   
 [Filterkriterium-Eigenschaft (RDS)](./filtercriterion-property-rds.md)   
 [SortColumn-Eigenschaft (RDS)](./sortcolumn-property-rds.md)   
 [SortDirection-Eigenschaft (RDS)](./sortdirection-property-rds.md)