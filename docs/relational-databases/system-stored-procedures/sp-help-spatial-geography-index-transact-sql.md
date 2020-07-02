---
title: sp_help_spatial_geography_index (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_spatial_geography_index
- sp_help_spatial_geography_index_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_spatial_geography_index procedure
ms.assetid: c9bf5675-eafc-4d71-bfdb-da963384fa0c
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 1864aec83a60c83a1ff10bb0c5e3f814631c27fc
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85733262"
---
# <a name="sp_help_spatial_geography_index-transact-sql"></a>sp_help_spatial_geography_index (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Gibt die Namen und Werte für einen angegebenen Satz von Eigenschaften über einen räumlichen **geography** -Index zurück. Das Ergebnis wird in einem Tabellenformat zurückgegeben. Sie können wählen, ob ein Kernsatz von Eigenschaften oder alle Eigenschaften des Indexes zurückgegeben werden sollen.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_help_spatial_geography_index [ @tabname =] 'tabname'   
     [ , [ @indexname = ] 'indexname' ]   
     [ , [ @verboseoutput = ] 'verboseoutput' ]   
     [ , [ @query_sample = ] 'query_sample' ]   
```  
  
## <a name="arguments"></a>Argumente  
 Siehe [Arguments and Properties of Spatial Index Stored Procedures](../../relational-databases/system-stored-procedures/spatial-index-stored-procedures-arguments-and-properties.md).  
  
## <a name="properties"></a>Eigenschaften  
 Siehe [Arguments and Properties of Spatial Index Stored Procedures](../../relational-databases/system-stored-procedures/spatial-index-stored-procedures-arguments-and-properties.md).  
  
## <a name="permissions"></a>Berechtigungen  
 Dem Benutzer muss eine PUBLIC-Rolle zugewiesen werden, um auf die Prozedur zuzugreifen. Erfordert die READ ACCESS-Berechtigung für den Server und das Objekt.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird verwendet `sp_help_spatial_geography_index` , um den räumlichen **geografieindex** **SIndx_SpatialTable_geography_col2** , der für die-Tabelle **geography_col** für das angegebene Abfrage Beispiel in ** \@ QS**definiert ist Dieses Beispiel gibt nur die Kerneigenschaften des angegebenen Indexes zurück.  
  
```  
declare @qs geography  
        ='POLYGON((-90.0 -180, -90 180.0, 90 180.0, 90 -180, -90 -180.0))';  
exec sp_help_spatial_geography_index 'geography_col', 'SIndx_SpatialTable_geography_col2', 0, @qs;  
```  
  
 Das umgebende Feld einer **geography** -Instanz ist die gesamte Erde.  
  
## <a name="requirements"></a>Anforderungen  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Prozeduren für räumliche Indizes](https://msdn.microsoft.com/library/1be0f34e-3d5a-4a1f-9299-bd482362ec7a)   
 [sp_help_spatial_geography_index](../../relational-databases/system-stored-procedures/sp-help-spatial-geography-index-transact-sql.md)   
 [Übersicht über räumliche Indizes](../../relational-databases/spatial/spatial-indexes-overview.md)   
 [Räumliche Daten &#40;SQL Server&#41;](../../relational-databases/spatial/spatial-data-sql-server.md)  
  
  
