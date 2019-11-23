---
title: sp_help_spatial_geometry_index (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_spatial_geometry_index
- sp_help_spatial_geometry_index_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_spatial_geometry_index procedure
ms.assetid: f1bcefb1-09c8-4b49-8c51-5d471065849f
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: e2e5d935fc3d6db5d243ec4b76841f13a60e5a11
ms.sourcegitcommit: 43c3d8939f6f7b0ddc493d8e7a643eb7db634535
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/14/2019
ms.locfileid: "72304855"
---
# <a name="sp_help_spatial_geometry_index-transact-sql"></a>sp_help_spatial_geometry_index (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Gibt die Namen und Werte für einen angegebenen Satz von Eigenschaften über einen **geometry** -Räumlichkeitsindex zurück. Das Ergebnis wird in einem Tabellenformat zurückgegeben. Sie können wählen, ob ein Kernsatz von Eigenschaften oder alle Eigenschaften des Indexes zurückgegeben werden sollen.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_help_spatial_geometry_index [ @tabname =] 'tabname'   
     [ , [ @indexname = ] 'indexname' ]   
     [ , [ @verboseoutput = ] 'verboseoutput'   
     [ , [ @query_sample = ] 'query_sample']   
```  
  
## <a name="arguments"></a>Argumente  
 Siehe [Arguments and Properties of Spatial Index Stored Procedures](../../relational-databases/system-stored-procedures/spatial-index-stored-procedures-arguments-and-properties.md).  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Siehe [Arguments and Properties of Spatial Index Stored Procedures](../../relational-databases/system-stored-procedures/spatial-index-stored-procedures-arguments-and-properties.md).  
  
## <a name="permissions"></a>Berechtigungen  
 Dem Benutzer muss eine PUBLIC-Rolle zugewiesen werden, um auf die Prozedur zuzugreifen. Erfordert die READ ACCESS-Berechtigung für den Server und das Objekt.  
  
## <a name="remarks"></a>Remarks  
 Eigenschaften, die NULL-Werte enthalten sind, sind nicht in der zurückgegebenen Menge enthalten.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird `sp_help_spatial_geometry_index` verwendet, um den räumlichen Index **SIndx_SpatialTable_geometry_col2** zu untersuchen, der für die Tabelle **geometry_col** für das angegebene Abfrage Beispiel in **\@QS**definiert wurde. Dieses Beispiel gibt nur die Kerneigenschaften des angegebenen Indexes zurück.  
  
```  
declare @qs geometry  
        ='POLYGON((-90.0 -180.0, -90.0 180.0, 90.0 180.0, 90.0 -180.0, -90.0 -180.0))';  
exec sp_help_spatial_geometry_index 'geometry_col', 'SIndx_SpatialTable_geometry_col2', 0, @qs;  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Prozeduren für räumliche Indizes](https://msdn.microsoft.com/library/1be0f34e-3d5a-4a1f-9299-bd482362ec7a)   
 [sp_help_spatial_geometry_index_xml](../../relational-databases/system-stored-procedures/sp-help-spatial-geometry-index-xml-transact-sql.md)   
 [Übersicht über räumliche Indizes](../../relational-databases/spatial/spatial-indexes-overview.md)   
 [Räumliche Daten &#40;SQL Server&#41;](../../relational-databases/spatial/spatial-data-sql-server.md)  
  
  
