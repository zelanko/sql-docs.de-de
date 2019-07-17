---
title: Sp_help_spatial_geography_histogram (Transact-SQL) | Microsoft-Dokumentation
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68085193"
---
# <a name="sphelpspatialgeographyhistogram-transact-sql"></a>sp_help_spatial_geography_histogram (Transact-SQL)
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
`[ @tabname = ] 'tabname'` Ist der qualifizierte oder nicht qualifizierte Name der Tabelle für die der räumlichkeitsindex angegeben wurde.  
  
 Anführungszeichen sind nur dann erforderlich, wenn eine qualifizierte Tabelle angegeben wird. Bei Angabe eines vollqualifizierten Namens, einschließlich eines Datenbanknamens, muss es sich bei dem Datenbanknamen um den Namen der aktuellen Datenbank handeln. *Tabname* ist **Sysname**, hat keinen Standardwert.  
  
`[ @colname = ] 'columnname'` Ist der Name der angegebenen räumlichen Spalte. *ColumnName* ist eine **Sysname**, hat keinen Standardwert.  
  
`[ @resolution = ] 'resolution'` Ist die Auflösung des Begrenzungsrahmens. Werte zwischen 10 und 5000 sind gültig. *Auflösung* ist eine **Tinyint**, hat keinen Standardwert.  
  
`[ @sample = ] 'sample'` Ist der Prozentsatz der Tabelle, die verwendet wird. Gültige Werte liegen zwischen 0 und 100. *TABLESAMPLE* ist eine **"float"** . Standardwert ist 100.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein Tabellenwert wird zurückgegeben. In der folgenden Tabelle wird der Spalteninhalt der Tabelle beschrieben.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**cellid**|**int**|Stellt die eindeutige ID jeder Zelle, mit der Anzahl von 1 ab.|  
|**cell**|**geography**|Ist ein rechteckiges Polygon, das die einzelnen Zellen darstellt. Die Zellenform ist mit der für die räumliche Indizierung verwendeten Zellenform identisch.|  
|**row_count**|**bigint**|Gibt die Anzahl räumlicher Objekte an, die die Zelle berühren oder enthalten.|  
  
## <a name="permissions"></a>Berechtigungen  
 Der Benutzer muss ein Mitglied der Datenbankrolle **public** sein. Erfordert die READ ACCESS-Berechtigung für den Server und das Objekt.  
  
## <a name="remarks"></a>Hinweise  
 Auf der räumlichen SSMS-Registerkarte wird eine grafische Darstellung der Ergebnisse angezeigt. Sie können die Ergebnisse für das räumliche Fenster abfragen, um die ungefähre Anzahl von Ergebniselementen abzurufen.  
  
> [!NOTE]  
>  Objekte in der Tabelle decken möglicherweise mehrere Zellen ab, daher ist die Summe der Zellen in der Tabelle möglicherweise größer als die Anzahl der tatsächlichen Objekte.  
  
 Das umgebende Feld für die **Geography** Typ ist die gesamte Kugel.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird **Sp_help_spatial_geography_histogram** auf die `Person.Address` -Tabelle in der [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] Datenbank.  
  
```  
EXEC sp_help_spatial_geography_histogram @tabname = Person.Address, @colname = SpatialLocation, @resolution = 64, @sample = 30;  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Prozeduren für Räumlichkeitsindizes &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/1be0f34e-3d5a-4a1f-9299-bd482362ec7a)  
  
  
