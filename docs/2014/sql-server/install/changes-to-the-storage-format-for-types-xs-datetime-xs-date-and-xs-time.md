---
title: 'Änderungen am Speicherformat für die Typen xs: DateTime, xs: Date und xs: Time | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- xs:date
- xs:time
- storage format
- DateTime
ms.assetid: b9f758df-030c-4aec-8ade-1bf904aa2c61
caps.latest.revision: 10
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 56342ff7c7754fb8ef1619fdb1b71e37600192b3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36060434"
---
# <a name="changes-to-the-storage-format-for-types-xsdatetime-xsdate-and-xstime"></a>Änderungen am Speicherformat für die Typen 'xs:dateTime', 'xs:date' und 'xs:time'
  Die XMLDATETIME-Regel gibt an, ob Ihre Datenbanken typisierte XML-Daten enthalten, die nach dem Upgrade auf [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ungültig werden.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Das Speicherformat in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] für Typen xs: DateTime, xs: Date und xs: Time wurde geändert zur Unterstützung von Werten mit oder ohne Zeitzoneninformationen und zur Beibehaltung der Zeitzone zu ermöglichen.  
  
 Wenn eine XML-Schemaauflistung auf einen dieser Typen verweist, werden die XML-Indizes aller Spalten, die der Auflistung zugeordnet sind, nach dem Upgrade auf [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] deaktiviert. Sie können sie mit SELECT und/oder XQUERIES abfragen, der XML-Index wird jedoch nicht verwendet. Bei einem negativen Wert für das Jahr kommt es zu einem Laufzeitfehler.  
  
 Darüber hinaus unterstützt [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] keine Werte mit negativen Jahren.  
  
 Die XMLDATETIME-Regel prüft, ob eine der XML-Schemaauflistungen auf einen der betroffenen Typen verweist und ob XML-Spalten vorhanden sind, die durch solche Auflistungen typisiert werden.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Wenn die XMLDATETIME-Regel feststellt, dass XML-Spalten entsprechend einer Schemaauflistung typisiert sind, die auf xs:date, xs:time oder xs:dateTime verweist, müssen Sie zunächst herausfinden, ob Ihre Daten Werte mit negativen Jahren enthalten. Das Vorhandensein solcher Werte würde die Neuerstellung der XML-Indizes nach dem Upgrade verhindern.  
  
 Die folgende Abfrage sucht nach XML-Schemaauflistungen, die auf die entsprechenden Typen verweisen, und nach den typisierten XML-Spalten. Damit erfahren Sie, ob es Instanzen mit negativen Werten für das Jahr gibt.  
  
```  
CREATE PROCEDURE DateTimeInvestigation(@withdata bit)  
-- @withdata = 0: only get the affected meta data information  
-- @withdata = 1: get the affected meta data and instance information  
AS  
BEGIN  
-- First get XML containing all schema collections containing affected element and attributes  
-- components (model groups????)   
-- and columns that are affected by the schema collections.   
CREATE table #_dt_collector(x xml);   
;with dttypes as  
  (SELECT * FROM sys.xml_schema_components   
   where base_xml_component_id IN   
      (SELECT xml_component_id   
       FROM sys.xml_schema_types   
       where (name='dateTime' or name='date') and kind='P'  
      )   
   union all  
   SELECT * FROM sys.xml_schema_components  
   where xml_component_id IN   
      (SELECT xml_component_id   
       FROM sys.xml_schema_types   
       where (name='dateTime' or name='date') and kind='P'  
       or kind='N' or kind='Z')   
   ),   
dtplaced as  
  (SELECT scp.*   
   FROM sys.xml_schema_component_placements scp   
   JOIN dttypes on scp.placed_xml_component_id=dttypes.xml_component_id  
  )   
insert into #_dt_collector SELECT x FROM (SELECT  
  xsc.xml_collection_id as "@collid"  
, s.name as "@schema"  
, xscol.name as "@name"  
, count(xsc.xml_component_id) as "@affected_elems_and_attrs"  
, (SELECT S.Name as "@schema", T.Name as "@table"  
        , C.Name as "@column"   
   FROM sys.columns C   
   JOIN sys.tables T ON C.object_id = T.object_id  
   JOIN sys.schemas S ON S.schema_id = T.schema_id  
   WHERE C.xml_collection_id = xsc.xml_collection_id  
   FOR XML PATH('Columns'), TYPE  
  )   
FROM sys.xml_schema_components xsc  
JOIN dtplaced on xsc.xml_component_id=dtplaced.xml_component_id  
JOIN sys.xml_schema_collections xscol on xsc.xml_collection_id =xscol.xml_collection_id  
JOIN sys.schemas s on xscol.schema_id=s.schema_id  
group by xsc.xml_collection_id, s.name, xscol.name  
FOR XML PATH('XML_Schema_Collections'), TYPE) as T(x);   
if (@withdata = 0)    
  BEGIN  
  SELECT x as "*" FROM #_dt_collector for xml path(''), root('data');   
  drop table #_dt_collector;   
  return;   
  END;   
-- Declare cursor to find all columns bound to the schema collections  
DECLARE C CURSOR FOR  
SELECT S.Name, T.Name, C.Name   
FROM sys.columns C   
JOIN sys.tables T ON C.object_id = T.object_id  
JOIN sys.schemas S ON S.schema_id = T.schema_id  
WHERE C.xml_collection_id  
IN (SELECT distinct xsc.xml_collection_id  
    FROM sys.xml_schema_components xsc  
    JOIN (SELECT scp.*   
          FROM sys.xml_schema_component_placements scp   
          JOIN (SELECT * FROM sys.xml_schema_components   
                where base_xml_component_id    
                in (SELECT xml_component_id   
                    FROM sys.xml_schema_types   
                    where (name='dateTime' or name='date') and kind='P'  
                   )   
                union all  
                SELECT * FROM sys.xml_schema_components  
                where xml_component_id   
                in (SELECT xml_component_id   
                    FROM sys.xml_schema_types   
                    where (name='dateTime' or name='date') and kind='P'  
                    or kind='N' or kind='Z')   
               ) dttypes on scp.placed_xml_component_id=dttypes.xml_component_id  
          ) dtplaced on xsc.xml_component_id=dtplaced.xml_component_id);   
DECLARE @SchemaName nvarchar(max);   
DECLARE @TableName nvarchar(max);   
DECLARE @ColumnName nvarchar(max);   
DECLARE @strSQL nvarchar(MAX);   
OPEN C;   
FETCH NEXT FROM C INTO @SchemaName, @TableName, @ColumnName;   
WHILE (@@FETCH_STATUS = 0)   
BEGIN  
      SET @strSQL = 'INSERT INTO #_dt_collector SELECT x FROM ( ';   
      SET @strSQL = @strSQL +    
                    'SELECT ''' + @SchemaName + '.' + @TableName + '.' + @ColumnName   
                  + ''' as "@Column", ';   
      SET @strSQL = @strSQL +    
      'sum(' + @ColumnName + '.value(''count(//*[. instance of element(*,xs:dateTime?)])'', ''bigint'')) as "@dT_elements"  
     , sum(' + @ColumnName + '.value(''count(//*[. instance of element(*,xs:dateTime?)][substring(string(.),1,1) ="-"])'', ''bigint'')) as "@neg_dT_elements"  
     , sum(' + @ColumnName + '.value(''count(//*[. instance of element(*,xs:date?)])'', ''bigint'')) as "@date_elements"  
     , sum(' + @ColumnName + '.value(''count(//*[. instance of element(*,xs:date?)][substring(string(.),1,1) ="-"])'', ''bigint'')) as "@neg_date_elements"   
     , sum(' + @ColumnName + '.value(''count(for $d in //@*, $v in data($d)  
                      where $v instance of xs:dateTime?   
                      return 1)'', ''bigint'')) as "@dT_attributes"   
     , sum(' + @ColumnName + '.value(''count(for $d in //@*, $v in data($d)   
                      where $v instance of xs:dateTime?   
                      and substring(string($v),1,1)= "-"  
                      return 1)'', ''bigint'')) as "@neg_dt_attributes"  
     , sum(' + @ColumnName + '.value(''count(for $d in //@*, $v in data($d)   
                      where $v instance of xs:date?   
                      return 1)'', ''bigint'')) as "@date_attributes"   
     , sum('+ @ColumnName + '.value(''count(for $d in //@*, $v in data($d)   
                      where $v instance of xs:date?   
                      and substring(string($v),1,1)= "-"  
                      return 1)'', ''bigint'')) as "@neg_date_attributes"'  
      + ' FROM ' + @SchemaName + '.' + @TableName  
      + ' FOR XML PATH(''data''), type) T(x)';   
      --SELECT @strSQL;   
      EXEC sp_executesql @strSQL;   
      FETCH NEXT FROM C INTO @SchemaName, @TableName, @ColumnName;   
END;   
CLOSE C;   
DEALLOCATE C;   
SELECT x as "*" FROM #_dt_collector for xml path(''), root('data');   
drop table #_dt_collector;   
END;   
go  
-- Get the dependent columns per affected XML Schema Collection and the  
-- number of affected values  
EXECUTE DateTimeInvestigation 1;   
```  
  
 Wenn negative Werte für das Jahr gefunden werden, stehen mehrere Lösungen zur Verfügung:  
  
-   Zeilen löschen.  
  
-   Diese Werte aktualisieren.  
  
-   Die ganze XML-Spalte löschen.  
  
-   Die XML-Spalte mit einer Schemaauflistung erneut eingeben, die xs:date oder xs:dateTime nicht verwendet (verwenden Sie z. B. xs:string).  
  
 Nachdem Sie die Probleme mit negativen Jahren gelöst haben, können Sie auf [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] aktualisieren.  
  
 Um XML-Indizes nach dem Upgrade in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] verwenden zu können, müssen Sie die XML-Indizes erneut erstellen oder XML-Spalten für alle Spalten erneut eingeben, die xs:date, xs:time oder xs:dateTime verwenden.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Engine-Upgradeprobleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)  
  
  