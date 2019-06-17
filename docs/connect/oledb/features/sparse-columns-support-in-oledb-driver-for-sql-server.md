---
title: Unterstützung von Sparsespalten im OLE DB-Treiber für SQL Server | Microsoft-Dokumentation
description: Unterstützung von Sparsespalten im OLE DB-Treiber für SQL Server
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- sparse columns, OLE DB Driver for SQL Server
- sparse columns, OLE DB
author: pmasl
ms.author: pelopes
manager: jroth
ms.openlocfilehash: 598d640362ea164673d198b0dc57b3743350673e
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66802918"
---
# <a name="sparse-columns-support-in-ole-db-driver-for-sql-server"></a>Unterstützung von Sparsespalten im OLE DB-Treiber für SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  OLE DB-Treiber für SQL Server unterstützt sparsespalten. Weitere Informationen über sparsespalten in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], finden Sie unter [Verwenden von Sparsespalten](../../../relational-databases/tables/use-sparse-columns.md) und [Verwenden von Spaltensätzen](../../../relational-databases/tables/use-column-sets.md).  
  
 Weitere Informationen zur Unterstützung von Sparsespalten im OLE DB-Treiber für SQL Server finden Sie unter [Unterstützung von Sparsespalten &#40;OLE DB&#41;](../../oledb/ole-db/sparse-columns-support-ole-db.md).  
  
 Informationen zu Beispielanwendungen, die diese Funktion veranschaulichen, finden Sie unter [Programmierbeispiele für SQL Server-Daten](https://msftdpprodsamples.codeplex.com/).  
  
## <a name="user-scenarios-for-sparse-columns-and-ole-db-driver-for-sql-server"></a>Benutzerszenarien für Spalten mit geringer Dichte und OLE DB-Treiber für SQLServer  
 In der folgende Tabelle werden die gängigen Benutzerszenarien für OLE DB-Treiber für SQL Server-Benutzer mit sparsespalten zusammengefasst:  
  
|Szenario|Verhalten|  
|--------------|--------------|  
|**Wählen Sie \* aus Tabelle** oder IOpenRowset:: OPENROWSET.|Gibt alle Spalten, die keine Elemente der Sparsespalte **column_set** sind, sowie eine XML-Spalte zurück, die die Werte aller Spalten ungleich NULL enthält, die Elemente der Sparsespalte **column_set** sind.|  
|Verweisen auf eine Spalte über den Namen|Auf die Spalte kann unabhängig von ihrem Status als Sparsespalte oder ihrer **column_set**-Zugehörigkeit verwiesen werden.|  
|Zugreifen auf **column_set**-Elementspalten über eine berechnete XML-Spalte.|Auf Spalten, die Elemente der Sparsespalte **column_set** sind, kann zugegriffen werden, indem Sie den **column_set** über den Namen auswählen und Werte durch Aktualisieren des XML-Codes in der Spalte **column_set** einfügen und aktualisieren.<br /><br /> Der Wert muss dem Schema für **column_set**-Spalten entsprechen.|  
|Abrufen von Metadaten für alle Spalten in einer Tabelle über das DBSCHEMA_COLUMNS-Schemarowset ohne spaltenbeschränkung (OLE DB).|Gibt eine Zeile für alle Spalten zurück, die nicht Elemente eines **column_set** sind. Wenn die Tabelle eine Sparsespalte **column_set** aufweist, wird eine Zeile dafür zurückgegeben.<br /><br /> Beachten Sie, dass hier keine Metadaten für Spalten zurückgegeben werden, die Elemente eines **column_set** sind.|  
|Abrufen von Metadaten für alle Spalten, unabhängig von geringer Dichte oder Zugehörigkeit in einem **column_set**. Hier könnte eine sehr große Anzahl an Zeilen zurückgegeben werden.|Rufen Sie IDBSchemaRowset:: GetRowset für das DBSCHEMA_COLUMNS_EXTENDED-Schemarowset ein.|  
|Abrufen von Metadaten nur für Spalten, die Elemente eines **column_set** sind. Hier könnte eine sehr große Anzahl an Zeilen zurückgegeben werden.|Rufen Sie IDBSchemaRowset:: GetRowset für das DBSCHEMA_SPARSE_COLUMN_SET-Schemarowset ein.|  
|Bestimmen, ob eine Spalte eine geringe Dichte aufweist|Betrachten Sie die SS_IS_SPARSE-Spalte des DBSCHEMA_COLUMNS-Schemarowsets (OLE DB).|  
|Bestimmen, ob eine Spalte ist eine **Column_set**.|Betrachten Sie die SS_IS_COLUMN_SET-Spalte des DBSCHEMA_COLUMNS-Schemarowsets. Oder wenden Sie sich an *DwFlags* IColumnsInfo:: GetColumnInfo oder DBCOLUMNFLAGS im von IColumnsRowset:: GetColumnsRowset zurückgegebenen Rowset zurückgegeben. Für **column_set**-Spalten wird DBCOLUMNFLAGS_SS_ISCOLUMNSET festgelegt.|  
|Importieren und Exportieren von Sparsespalten über BCP für eine Tabelle ohne **column_set**.|Keine Änderung im Verhalten von Vorgängerversionen von OLE DB-Treiber für SQL Server.|  
|Importieren und Exportieren von Sparsespalten über BCP für eine Tabelle mit einem **column_set**.|Die **Column_set** importiert und exportiert Sie in die gleiche Weise wie XML, also als **'varbinary(max)'** Wenn gebunden wird, als ein binärer Typ ist, oder als **nvarchar(max)** Wenn als eine gebunden**Char** oder **Wchar** Typ.<br /><br /> Spalten, die Elemente der Sparsespalte **column_set** sind, werden nicht als unterschiedliche Spalten exportiert. Sie werden nur im Wert des **column_set** exportiert.|  
|**Queryout** -Verhalten für BCP.|Keine Änderung bei der Behandlung explizit benannter Spalten aus früheren Versionen von OLE DB-Treiber für SQL Server.<br /><br /> In Szenarien, die das Importieren und Exportieren zwischen Tabellen mit unterschiedlichen Schemas umfassen, ist möglicherweise eine besondere Behandlung erforderlich.<br /><br /> Weitere Informationen über BCP finden Sie unter „Massenkopierunterstützung (BCP) für Spalten mit geringer Dichte” weiter unten in diesem Thema.|  
  
## <a name="down-level-client-behavior"></a>Downlevelclient-Verhalten  
 Downlevelclients geben Metadaten nur für Spalten zurück, die nicht Elemente der Sparsespalte **column_set** für SQLColumns und DBSCHMA_COLUMNS sind.
  
 Downlevelclients können auf Spalten, die Elemente der Sparsespalte **column_set** sind, über den Namen zugreifen. Auf die Spalte **column_set** kann als XML-Spalte für [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]-Clients zugegriffen werden.  
  
## <a name="bulk-copy-bcp-support-for-sparse-columns"></a>Massenkopierunterstützung (BCP) für Spalten mit geringer Dichte  
 In OLE DB sind keine Änderungen an der BCP-API für die Sparsespalten oder **column_set**-Funktionen vorgenommen werden.  
  
 Wenn eine Tabelle einen **column_set** aufweist, werden Sparsespalten nicht wie unterschiedliche Spalten behandelt. Die Werte aller sparsespalten sind im Wert des enthalten die **Column_set**, dem auf die gleiche Weise wie eine XML-Spalte exportiert wird, also als **'varbinary(max)'** Wenn gebunden wird, als ein binärer Typ ist, oder als  **nvarchar(max)** wenn er als ein **Char** oder **Wchar** Typ). Beim Import der **Column_set** Wert muss dem Schema der entsprechen den **Column_set**.  
  
 Bei **queryout**-Vorgängen gibt es keine Änderungen in der Behandlung von Spalten, auf die explizit verwiesen wird. **column_set**-Spalten weisen das gleiche Verhalten auf wie XML-Spalten, und die Sparseeigenschaft hat keine Auswirkungen auf die Behandlung von benannten Sparsespalten.  
  
 Wenn jedoch **queryout** für das Exportieren verwendet wird, und Sie über den Namen auf Sparsespalten verweisen, die Elemente des Sparsespaltensatzes sind, können Sie keinen direkten Import in eine Spalte mit gleicher Struktur durchführen. Dies liegt daran, dass BCP Metadaten verwendet, die konsistent mit einem **select \*** -Vorgang für den Import sind, und **column_set**-Elementspalten diesen Metadaten nicht zuordnen kann. Damit **column_set**-Elementspalten einzeln importiert werden können, müssen Sie eine Ansicht für die Tabelle definieren, die auf die gewünschten **column_set**-Spalten verweist. Darüber hinaus müssen Sie den Importvorgang über die Ansicht ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [OLE DB-Treiber für SQL-Server](../../oledb/oledb-driver-for-sql-server.md)  
  
  
