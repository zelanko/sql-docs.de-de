---
title: Sp_help_spatial_geography_index_xml (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_spatial_geography_index_xml_TSQL
- sp_help_spatial_geography_index_xml
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_spatial_geography_index_xml procedure
ms.assetid: 821d4127-3ce5-4474-8561-043404a20d81
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: ed44f70a49c1cf221a9ef74b19030512273b1480
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51671539"
---
# <a name="sphelpspatialgeographyindexxml-transact-sql"></a>sp_help_spatial_geography_index_xml (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Gibt den Namen und den Wert für einen angegebenen Eigenschaftssatz über einen räumlichen **geography** -Index zurück. Sie können wählen, ob ein Kernsatz von Eigenschaften oder alle Eigenschaften des Indexes zurückgegeben werden sollen.  
  
 Ergebnisse werden in einem XML-Fragment zurückgegeben, das den Namen und den Wert der ausgewählten Eigenschaften anzeigt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_help_spatial_geography_index_xml [ @tabname =] 'tabname'   
     [ , [ @indexname = ] 'indexname' ]   
     [ , [ @verboseoutput = ] 'verboseoutput' ]   
     [ , [ @query_sample = ] 'query_sample' ]   
     [ ,.[ @xml_output = ] 'xml_output' ]   
```  
  
## <a name="arguments"></a>Argumente  
 Siehe [Arguments and Properties of Spatial Index Stored Procedures](../../relational-databases/system-stored-procedures/spatial-index-stored-procedures-arguments-and-properties.md).  
  
## <a name="properties"></a>Eigenschaften  
 Siehe [Arguments and Properties of Spatial Index Stored Procedures](../../relational-databases/system-stored-procedures/spatial-index-stored-procedures-arguments-and-properties.md).  
  
## <a name="permissions"></a>Berechtigungen  
 Dem Benutzer muss eine PUBLIC-Rolle zugewiesen werden, um auf die Prozedur zuzugreifen. Erfordert die READ ACCESS-Berechtigung für den Server und das Objekt.  
  
## <a name="remarks"></a>Hinweise  
 Eigenschaften, die NULL-Werte enthalten sind, sind nicht in der zurückgegebenen Menge enthalten.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird `sp_help_spatial_geography_index_xml` um den räumlichkeitsindex **SIndx_SpatialTable_geography_col2** für Tabelle definierten **Geography_col** für das angegebene Abfragebeispiel in  **@qs**. Dieses Beispiel gibt die Kerneigenschaften des angegebenen Index in einem XML-Fragment zurück, das den Namen und den Wert der ausgewählten Eigenschaften anzeigt.  
  
 Anschließend wird eine [XQuery](../../xquery/xquery-basics.md) für das Resultset ausgeführt, die eine bestimmte Eigenschaft zurückgibt.  
  
```  
declare @qs geography  
        ='POLYGON((-90.0 -180, -90 180.0, 90 180.0, 90 -180, -90 -180.0))';  
declare @x xml;  
exec sp_help_spatial_geography_index_xml 'geography_col', 'SIndx_SpatialTable_geography_col2', 0, @qs, @x output;  
select @x.value('(/Primary_Filter_Efficiency/text())[1]', 'float');  
```  
  
 Ähnlich wie [sp_help_spatial_geography_index](../../relational-databases/system-stored-procedures/sp-help-spatial-geography-index-transact-sql.md)ermöglicht diese gespeicherte Prozedur einen vereinfachten programmgesteuerten Zugriff auf die Eigenschaften eines **geography** -Räumlichkeitsindex und dokumentiert das Resultset in XML.  
  
 Das umgebende Feld einer **geography** ist die gesamte Erde.  
  
## <a name="requirements"></a>Anforderungen  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Prozeduren für Räumlichkeitsindizes](https://msdn.microsoft.com/library/1be0f34e-3d5a-4a1f-9299-bd482362ec7a)   
 [sp_help_spatial_geography_index](../../relational-databases/system-stored-procedures/sp-help-spatial-geography-index-transact-sql.md)   
 [Übersicht über räumliche Indizes](../../relational-databases/spatial/spatial-indexes-overview.md)   
 [Räumliche Daten &#40;SQL Server&#41;](../../relational-databases/spatial/spatial-data-sql-server.md)   
 [XQuery-Grundlagen](../../xquery/xquery-basics.md)   
 [XQuery-Sprachreferenz](../../xquery/xquery-language-reference-sql-server.md)  
  
  
