---
title: sp_help_spatial_geography_histogram (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_spatial_geography_histogram_TSQL
- sp_help_spatial_geography_histogram
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_spatial_geography_histogram
ms.assetid: 5c5bd319-055d-4cd6-8c5a-06354cc056cc
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 3c2b94b4c76054fb1e9ce6e078f3490ad263a52c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68085193"
---
# <a name="sp_help_spatial_geography_histogram-transact-sql"></a>sp_help_spatial_geography_histogram (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Ermöglicht es, Rasterparameter für einen räumlichen Index mit Schlüsseln zu versehen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_help_spatial_geography_histogram [ @tabname =] 'tabname'   
     [ , [ @colname = ] 'columnname' ]   
     [ , [ @resolution = ] 'resolution' ]  
     [ , [ @sample = ] 'tablesample' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @tabname = ] 'tabname'`Der qualifizierte oder nicht qualifizierte Name der Tabelle, für die der räumliche Index angegeben wurde.  
  
 Anführungszeichen sind nur dann erforderlich, wenn eine qualifizierte Tabelle angegeben wird. Bei Angabe eines vollqualifizierten Namens, einschließlich eines Datenbanknamens, muss es sich bei dem Datenbanknamen um den Namen der aktuellen Datenbank handeln. *tabname* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @colname = ] 'columnname'`Der Name der angegebenen räumlichen Spalte. *ColumnName* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @resolution = ] 'resolution'`Die Auflösung des umgebenden Felds. Werte zwischen 10 und 5000 sind gültig. *Auflösung* ist vom Datentyp **tinyint**und hat keinen Standardwert.  
  
`[ @sample = ] 'sample'`Der Prozentsatz der verwendeten Tabelle. Gültige Werte sind 0 bis 100. *TABLESAMPLE* ist ein **float**-Wert. Der Standardwert ist 100.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein Tabellenwert wird zurückgegeben. In der folgenden Tabelle wird der Spalteninhalt der Tabelle beschrieben.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**cellid**|**int**|Stellt die eindeutige ID jeder Zelle mit einer Anfangs Anzahl von 1 dar.|  
|**Kern**|**geography**|Ist ein rechteckiges Polygon, das die einzelnen Zellen darstellt. Die Zellenform ist mit der für die räumliche Indizierung verwendeten Zellenform identisch.|  
|**row_count**|**bigint**|Gibt die Anzahl räumlicher Objekte an, die die Zelle berühren oder enthalten.|  
  
## <a name="permissions"></a>Berechtigungen  
 Der Benutzer muss ein Mitglied der Datenbankrolle **public** sein. Erfordert die READ ACCESS-Berechtigung für den Server und das Objekt.  
  
## <a name="remarks"></a>Bemerkungen  
 Auf der räumlichen SSMS-Registerkarte wird eine grafische Darstellung der Ergebnisse angezeigt. Sie können die Ergebnisse für das räumliche Fenster abfragen, um die ungefähre Anzahl von Ergebniselementen abzurufen.  
  
> [!NOTE]  
>  Objekte in der Tabelle decken möglicherweise mehrere Zellen ab, daher ist die Summe der Zellen in der Tabelle möglicherweise größer als die Anzahl der tatsächlichen Objekte.  
  
 Das umgebende Feld für den **geography** -Typ ist der gesamte Globus.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird **sp_help_spatial_geography_histogram** für die `Person.Address` -Tabelle in [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] der-Datenbank aufgerufen.  
  
```  
EXEC sp_help_spatial_geography_histogram @tabname = Person.Address, @colname = SpatialLocation, @resolution = 64, @sample = 30;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Prozeduren für räumliche Indizes &#40;Transact-SQL-&#41;](https://msdn.microsoft.com/library/1be0f34e-3d5a-4a1f-9299-bd482362ec7a)  
  
  
