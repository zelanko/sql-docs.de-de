---
title: Unterstützung für Sparsespalten in SQL Server Native Client | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- sparse columns, ODBC
- sparse columns, SQL Server Native Client
- sparse columns, OLE DB
ms.assetid: aee5ed81-7e23-42e4-92d3-2da7844d9bc3
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0e21bd33bd181dc4075b74256047336562d11fb4
ms.sourcegitcommit: 78e32562f9c1fbf2e50d3be645941d4aa457e31f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54100578"
---
# <a name="sparse-columns-support-in-sql-server-native-client"></a>Unterstützung für Spalten mit geringer Dichte in SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client unterstützt Sparsespalten. Weitere Informationen über sparsespalten in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], finden Sie unter [Verwenden von Sparsespalten](../../../relational-databases/tables/use-sparse-columns.md) und [Verwenden von Spaltensätzen](../../../relational-databases/tables/use-column-sets.md).  
  
 Weitere Informationen zu Spalten mit geringer Dichte-Unterstützung in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client finden Sie unter [Sparse-Spalten unterstützt &#40;ODBC&#41; ](../../../relational-databases/native-client/odbc/sparse-columns-support-odbc.md) und [Sparse-Spalten unterstützt &#40;OLE DB&#41; ](../../../relational-databases/native-client/ole-db/sparse-columns-support-ole-db.md) .  
  
 Informationen zu Beispielanwendungen, die diese Funktion veranschaulichen, finden Sie unter [Programmierbeispiele für SQL Server-Daten](https://msftdpprodsamples.codeplex.com/).  
  
## <a name="user-scenarios-for-sparse-columns-and-sql-server-native-client"></a>Benutzerszenarien für Spalten mit geringer Dichte und SQL Server Native Client  
 In der folgenden Tabelle sind die gängigen Benutzerszenarien für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-Benutzer mit Sparsespalten zusammengefasst:  
  
|Szenario|Verhalten|  
|--------------|--------------|  
|**Wählen Sie \* aus Tabelle** oder IOpenRowset:: OPENROWSET.|Gibt alle Spalten, die keine Elemente der Sparsespalte **column_set** sind, sowie eine XML-Spalte zurück, die die Werte aller Spalten ungleich NULL enthält, die Elemente der Sparsespalte **column_set** sind.|  
|Verweisen auf eine Spalte über den Namen|Auf die Spalte kann unabhängig von ihrem Status als Sparsespalte oder ihrer **column_set**-Zugehörigkeit verwiesen werden.|  
|Zugreifen auf **column_set**-Elementspalten über eine berechnete XML-Spalte.|Auf Spalten, die Elemente der Sparsespalte **column_set** sind, kann zugegriffen werden, indem Sie den **column_set** über den Namen auswählen und Werte durch Aktualisieren des XML-Codes in der Spalte **column_set** einfügen und aktualisieren.<br /><br /> Der Wert muss dem Schema für **column_set**-Spalten entsprechen.|  
|Abrufen von Metadaten für alle Spalten in einer Tabelle über SQLColumns mit einem spaltensuchmuster NULL oder "%" (ODBC) oder über das DBSCHEMA_COLUMNS-Schemarowset ohne spaltenbeschränkung (OLE DB).|Gibt eine Zeile für alle Spalten zurück, die nicht Elemente eines **column_set** sind. Wenn die Tabelle eine Sparsespalte **column_set** aufweist, wird eine Zeile dafür zurückgegeben.<br /><br /> Beachten Sie, dass hier keine Metadaten für Spalten zurückgegeben werden, die Elemente eines **column_set** sind.|  
|Abrufen von Metadaten für alle Spalten, unabhängig von geringer Dichte oder Zugehörigkeit in einem **column_set**. Hier könnte eine sehr große Anzahl an Zeilen zurückgegeben werden.|Legen Sie das Deskriptorfeld SQL_SOPT_SS_NAME_SCOPE auf SQL_SS_NAME_SCOPE_EXTENDED und rufen [SQLColumns](../../../relational-databases/native-client-odbc-api/sqlcolumns.md) (ODBC).<br /><br /> Rufen Sie IDBSchemaRowset:: GetRowset für das DBSCHEMA_COLUMNS_EXTENDED-Schemarowset (OLE DB).<br /><br /> Dieses Szenario ist in einer Anwendung, die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client einer früheren Version als [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] verwendet, nicht möglich. Eine solche Anwendung könnte jedoch Systemsichten direkt Abfragen.|  
|Abrufen von Metadaten nur für Spalten, die Elemente eines **column_set** sind. Hier könnte eine sehr große Anzahl an Zeilen zurückgegeben werden.|Legen Sie das Deskriptorfeld SQL_SOPT_SS_NAME_SCOPE auf SQL_SS_NAME_SCOPE_SPARSE_COLUMN_SET und Aufrufen von SQLColumns (ODBC).<br /><br /> Rufen Sie IDBSchemaRowset:: GetRowset für das DBSCHEMA_SPARSE_COLUMN_SET-Schemarowset (OLE DB).<br /><br /> Dieses Szenario ist in einer Anwendung, die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client einer früheren Version als [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] verwendet, nicht möglich. Eine solche Anwendung könnte jedoch Systemsichten abfragen.|  
|Bestimmen, ob eine Spalte eine geringe Dichte aufweist|Wenden Sie sich an die SS_IS_SPARSE-Spalte der SQLColumns-Resultsets (ODBC).<br /><br /> Betrachten Sie die SS_IS_SPARSE-Spalte des DBSCHEMA_COLUMNS-Schemarowsets (OLE DB).<br /><br /> Dieses Szenario ist in einer Anwendung, die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client einer früheren Version als [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] verwendet, nicht möglich. Eine solche Anwendung könnte jedoch Systemsichten abfragen.|  
|Bestimmen, ob eine Spalte ist eine **Column_set**.|Prüfen Sie die SS_IS_COLUMN_SET-Spalte des Resultsets SQLColumns aus. Oder sehen Sie sich das [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-spezifische SQL_CA_SS_IS_COLUMN_SET-Spaltenattribut (ODBC) an.<br /><br /> Betrachten Sie die SS_IS_COLUMN_SET-Spalte des DBSCHEMA_COLUMNS-Schemarowsets. Oder wenden Sie sich an *DwFlags* IColumnsInfo:: GetColumnInfo oder DBCOLUMNFLAGS im von IColumnsRowset:: GetColumnsRowset zurückgegebenen Rowset zurückgegeben. Für **Column_set** Spalten DBCOLUMNFLAGS_SS_ISCOLUMNSET festgelegt (OLE DB).<br /><br /> Dieses Szenario ist in einer Anwendung, die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client einer früheren Version als [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] verwendet, nicht möglich. Eine solche Anwendung könnte jedoch Systemsichten abfragen.|  
|Importieren und Exportieren von Sparsespalten über BCP für eine Tabelle ohne **column_set**.|Keine Änderung im Verhalten im Vergleich zu vorherigen Versionen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.|  
|Importieren und Exportieren von Sparsespalten über BCP für eine Tabelle mit einem **column_set**.|Die **Column_set** importiert und exportiert Sie in die gleiche Weise wie XML, also als **'varbinary(max)'** Wenn gebunden wird, als ein binärer Typ ist, oder als **nvarchar(max)** Wenn als eine gebunden**Char** oder **Wchar** Typ.<br /><br /> Spalten, die Elemente der Sparsespalte **column_set** sind, werden nicht als unterschiedliche Spalten exportiert. Sie werden nur im Wert des **column_set** exportiert.|  
|**Queryout** -Verhalten für BCP.|Keine Änderung in der Behandlung explizit benannter Spalten im Vergleich zu vorherigen Versionen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.<br /><br /> In Szenarien, die das Importieren und Exportieren zwischen Tabellen mit unterschiedlichen Schemas umfassen, ist möglicherweise eine besondere Behandlung erforderlich.<br /><br /> Weitere Informationen über BCP finden Sie unter „Massenkopierunterstützung (BCP) für Spalten mit geringer Dichte” weiter unten in diesem Thema.|  
  
## <a name="down-level-client-behavior"></a>Downlevelclient-Verhalten  
 Downlevelclients geben Metadaten nur für Spalten zurück, die nicht Elemente der Sparsespalte **column_set** für SQLColumns und DBSCHMA_COLUMNS sind. Der in eingeführte zusätzliche OLE DB-Schemarowsets [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] Native Client nicht zur Verfügung, auch die Änderungen SQLColumns in ODBC über SQL_SOPT_SS_NAME_SCOPE.  
  
 Downlevelclients können auf Spalten, die Elemente der Sparsespalte **column_set** sind, über den Namen zugreifen. Auf die Spalte **column_set** kann als XML-Spalte für [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]-Clients zugegriffen werden.  
  
## <a name="bulk-copy-bcp-support-for-sparse-columns"></a>Massenkopierunterstützung (BCP) für Spalten mit geringer Dichte  
 Es sind keine Änderungen an die BCP-API in entweder ODBC oder OLE DB für die Spalten mit geringer Dichte oder **Column_set** Funktionen.  
  
 Wenn eine Tabelle einen **column_set** aufweist, werden Sparsespalten nicht wie unterschiedliche Spalten behandelt. Die Werte aller sparsespalten sind im Wert des enthalten die **Column_set**, dem auf die gleiche Weise wie eine XML-Spalte exportiert wird, also als **'varbinary(max)'** Wenn gebunden wird, als ein binärer Typ ist, oder als  **nvarchar(max)** wenn er als ein **Char** oder **Wchar** Typ). Beim Import der **Column_set** Wert muss dem Schema der entsprechen den **Column_set**.  
  
 Bei **queryout**-Vorgängen gibt es keine Änderungen in der Behandlung von Spalten, auf die explizit verwiesen wird. **column_set**-Spalten weisen das gleiche Verhalten auf wie XML-Spalten, und die Sparseeigenschaft hat keine Auswirkungen auf die Behandlung von benannten Sparsespalten.  
  
 Wenn jedoch **queryout** für das Exportieren verwendet wird, und Sie über den Namen auf Sparsespalten verweisen, die Elemente des Sparsespaltensatzes sind, können Sie keinen direkten Import in eine Spalte mit gleicher Struktur durchführen. Dies ist, da BCP Metadaten konsistent mit verwendet eine **wählen &#42;**  Vorgang für den Import und kann nicht entsprechend **Column_set** -Elementspalten diesen Metadaten. Damit **column_set**-Elementspalten einzeln importiert werden können, müssen Sie eine Ansicht für die Tabelle definieren, die auf die gewünschten **column_set**-Spalten verweist. Darüber hinaus müssen Sie den Importvorgang über die Ansicht ausführen.  
  
## <a name="see-also"></a>Siehe auch  
 [Programmierung für SQL Server Native Client](../../../relational-databases/native-client/sql-server-native-client-programming.md)  
  
  
