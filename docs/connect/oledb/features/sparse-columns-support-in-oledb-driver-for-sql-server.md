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
ms.openlocfilehash: 786adbde3519ef859e316a82cdb66af199dbf139
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2020
ms.locfileid: "86006873"
---
# <a name="sparse-columns-support-in-ole-db-driver-for-sql-server"></a>Unterstützung von Sparsespalten im OLE DB-Treiber für SQL Server
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Der OLE DB-Treiber für SQL Server unterstützt Sparsespalten. Weitere Informationen zu Sparsespalten in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] finden Sie unter [Verwenden von Spalten mit geringer Dichte](../../../relational-databases/tables/use-sparse-columns.md) und [Verwenden von Spaltensätzen](../../../relational-databases/tables/use-column-sets.md).  
  
 Weitere Informationen zur Unterstützung von Sparsespalten im OLE DB-Treiber für SQL Server finden Sie unter [Unterstützung von Sparsespalten &#40;OLE DB&#41;](../../oledb/ole-db/sparse-columns-support-ole-db.md).  
  
 Informationen zu Beispielanwendungen, die diese Funktion veranschaulichen, finden Sie unter [Programmierbeispiele für SQL Server-Daten](https://msftdpprodsamples.codeplex.com/).  
  
## <a name="user-scenarios-for-sparse-columns-and-ole-db-driver-for-sql-server"></a>Benutzerszenarien für Spalten mit geringer Dichte und dem OLE DB-Treiber für SQL Server  
 In der folgenden Tabelle sind die gängigen Benutzerszenarien für Benutzer des OLE DB-Treibers für SQL Server mit Sparsespalten zusammengefasst:  
  
|Szenario|Verhalten|  
|--------------|--------------|  
|**select \* from table** oder IOpenRowset::OpenRowset.|Gibt alle Spalten, die keine Elemente der Sparsespalte **column_set** sind, sowie eine XML-Spalte zurück, die die Werte aller Spalten ungleich NULL enthält, die Elemente der Sparsespalte **column_set** sind.|  
|Verweisen auf eine Spalte über den Namen|Auf die Spalte kann unabhängig von ihrem Status als Sparsespalte oder ihrer **column_set**-Zugehörigkeit verwiesen werden.|  
|Zugreifen auf **column_set**-Elementspalten über eine berechnete XML-Spalte.|Auf Spalten, die Elemente der Sparsespalte **column_set** sind, kann zugegriffen werden, indem Sie den **column_set** über den Namen auswählen und Werte durch Aktualisieren des XML-Codes in der Spalte **column_set** einfügen und aktualisieren.<br /><br /> Der Wert muss dem Schema für **column_set**-Spalten entsprechen.|  
|Abrufen von Metadaten für alle Spalten in einer Tabelle über das DBSCHEMA_COLUMNS-Schemarowset ohne Spaltenbeschränkung (OLE DB).|Gibt eine Zeile für alle Spalten zurück, die nicht Elemente eines **column_set** sind. Wenn die Tabelle eine Sparsespalte **column_set** aufweist, wird eine Zeile dafür zurückgegeben.<br /><br /> Beachten Sie, dass hier keine Metadaten für Spalten zurückgegeben werden, die Elemente eines **column_set** sind.|  
|Abrufen von Metadaten für alle Spalten, unabhängig von geringer Dichte oder Zugehörigkeit in einem **column_set**. Hier könnte eine sehr große Anzahl an Zeilen zurückgegeben werden.|Abrufen von IDBSchemaRowset::GetRowset für das DBSCHEMA_COLUMNS_EXTENDED-Schemarowset.|  
|Abrufen von Metadaten nur für Spalten, die Elemente eines **column_set** sind. Hier könnte eine sehr große Anzahl an Zeilen zurückgegeben werden.|Abrufen von IDBSchemaRowset::GetRowset für das DBSCHEMA_SPARSE_COLUMN_SET-Schemarowset.|  
|Bestimmen, ob eine Spalte eine geringe Dichte aufweist|Betrachten Sie die SS_IS_SPARSE-Spalte des DBSCHEMA_COLUMNS-Schemarowsets (OLE DB).|  
|Bestimmen, ob eine Spalte ein **column_set** ist.|Betrachten Sie die SS_IS_COLUMN_SET-Spalte des DBSCHEMA_COLUMNS-Schemarowsets. Betrachten Sie alternativ *dwFlags*, das von IColumnsInfo::GetColumnInfo zurückgegeben wird, oder DBCOLUMNFLAGS in dem von IColumnsRowset::GetColumnsRowset zurückgegebenen Rowset. Für **column_set**-Spalten wird DBCOLUMNFLAGS_SS_ISCOLUMNSET festgelegt.|  
|Importieren und Exportieren von Sparsespalten über BCP für eine Tabelle ohne **column_set**.|Keine Änderung im Verhalten im Vergleich zu vorherigen Versionen des OLE DB-Treibers für SQL Server.|  
|Importieren und Exportieren von Sparsespalten über BCP für eine Tabelle mit einem **column_set**.|Der **column_set** wird auf die gleiche Weise wie XML importiert und exportiert, d. h. wie **varbinary(max)** bei Bindung als Binärtyp oder **nvarchar(max)** bei Bindung als **char**- oder **wchar**-Typ.<br /><br /> Spalten, die Elemente der Sparsespalte **column_set** sind, werden nicht als unterschiedliche Spalten exportiert. Sie werden nur im Wert des **column_set** exportiert.|  
|**queryout**-Verhalten für BCP.|Keine Änderung in der Behandlung explizit benannter Spalten im Vergleich zu vorherigen Versionen des OLE DB-Treibers für SQL Server.<br /><br /> In Szenarien, die das Importieren und Exportieren zwischen Tabellen mit unterschiedlichen Schemas umfassen, ist möglicherweise eine besondere Behandlung erforderlich.<br /><br /> Weitere Informationen über BCP finden Sie unter „Massenkopierunterstützung (BCP) für Spalten mit geringer Dichte” weiter unten in diesem Thema.|  
  
## <a name="down-level-client-behavior"></a>Downlevelclient-Verhalten  
 Downlevelclients geben Metadaten nur für Spalten zurück, die nicht Elemente der Sparsespalte **column_set** für SQLColumns und DBSCHMA_COLUMNS sind.
  
 Downlevelclients können auf Spalten, die Elemente der Sparsespalte **column_set** sind, über den Namen zugreifen. Auf die Spalte **column_set** kann als XML-Spalte für [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]-Clients zugegriffen werden.  
  
## <a name="bulk-copy-bcp-support-for-sparse-columns"></a>Massenkopierunterstützung (BCP) für Spalten mit geringer Dichte  
 In OLE DB sind keine Änderungen an der BCP-API für die Sparsespalten oder **column_set**-Funktionen vorgenommen werden.  
  
 Wenn eine Tabelle einen **column_set** aufweist, werden Sparsespalten nicht wie unterschiedliche Spalten behandelt. Die Werte aller Sparsespalten sind im Wert des **column_set** enthalten, der auf dieselbe Art und Weise wie eine XML-Spalte exportiert wird, d. h. als **varbinary(max)** , wenn er als Binärtyp gebunden ist, oder als **nvarchar(max)** , wenn er als **char**-Typ oder **wchar**-Typ gebunden ist. Beim Importieren muss der **column_set**-Wert dem Schema des **column_set** entsprechen.  
  
 Bei **queryout**-Vorgängen gibt es keine Änderungen in der Behandlung von Spalten, auf die explizit verwiesen wird. **column_set**-Spalten weisen das gleiche Verhalten auf wie XML-Spalten, und die Sparseeigenschaft hat keine Auswirkungen auf die Behandlung von benannten Sparsespalten.  
  
 Wenn jedoch **queryout** für das Exportieren verwendet wird, und Sie über den Namen auf Sparsespalten verweisen, die Elemente des Sparsespaltensatzes sind, können Sie keinen direkten Import in eine Spalte mit gleicher Struktur durchführen. Dies liegt daran, dass BCP Metadaten verwendet, die konsistent mit einem **select \*** -Vorgang für den Import sind, und **column_set**-Elementspalten diesen Metadaten nicht zuordnen kann. Damit **column_set**-Elementspalten einzeln importiert werden können, müssen Sie eine Ansicht für die Tabelle definieren, die auf die gewünschten **column_set**-Spalten verweist. Darüber hinaus müssen Sie den Importvorgang über die Ansicht ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [OLE DB-Treiber für SQL-Server](../../oledb/oledb-driver-for-sql-server.md)  
  
  
