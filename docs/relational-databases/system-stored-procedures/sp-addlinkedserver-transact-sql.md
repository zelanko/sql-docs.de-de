---
title: sp_addlinkedserver (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_addlinkedserver_TSQL
- sp_addlinkedserver
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addlinkedserver
ms.assetid: fed3adb0-4c15-4a1a-8acd-1b184aff558f
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ad01313933cb2e04bf22257bcdd0eb93a1a755e9
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "72313746"
---
# <a name="sp_addlinkedserver-transact-sql"></a>sp_addlinkedserver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  Erstellt einen Verbindungsserver. Ein Verbindungsserver ermöglicht den Zugriff auf verteilte, heterogene Abfragen für OLE DB-Datenquellen. Nachdem ein Verbindungs Server mithilfe von **sp_addlinkedserver**erstellt wurde, können verteilte Abfragen für diesen Server ausgeführt werden. Wenn der Verbindungsserver als Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]definiert wird, können remote gespeicherte Prozeduren ausgeführt werden.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
sp_addlinkedserver [ @server= ] 'server' [ , [ @srvproduct= ] 'product_name' ]   
     [ , [ @provider= ] 'provider_name' ]  
     [ , [ @datasrc= ] 'data_source' ]   
     [ , [ @location= ] 'location' ]   
     [ , [ @provstr= ] 'provider_string' ]   
     [ , [ @catalog= ] 'catalog' ]   
```  
  
## <a name="arguments"></a>Argumente  
[ @server = ] * \'Server\' *          
Der Name des zu erstellenden Verbindungsservers. *server* ist vom Datentyp **sysname**und hat keinen Standardwert.  
  
[ @srvproduct = ] * \'product_name\' *          
Der Produktname der OLE DB-Datenquelle, die als Verbindungsserver hinzugefügt werden soll. *product_name* ist vom Datentyp **nvarchar (** 128 **)** und hat den Standardwert NULL. Wenn **SQL Server**, *provider_name*, *data_source*, *Location*, *provider_string*und *catalog* nicht angegeben werden müssen.  
  
[ @provider = ] * \'provider_name\' *          
Der eindeutige Programmbezeichner (Programmatic Identifier, PROGID) des OLE DB-Anbieters, der dieser Datenquelle entspricht. *provider_name* muss für den angegebenen OLE DB Anbieter, der auf dem aktuellen Computer installiert ist, eindeutig sein. *provider_name* ist vom Datentyp **nvarchar (128)** und hat den Standardwert NULL. Wenn *provider_name* jedoch ausgelassen wird, wird sqlncli verwendet. 

> [!NOTE]
> Die Verwendung von SQLNCLI [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] leitet zur neuesten Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter weiter. Es wird vorausgesetzt, dass der OLE DB-Anbieter mit der angegebenen PROGID in der Registrierung registriert ist.

> [!IMPORTANT] 
> Der vorherige Microsoft OLE DB-Anbieter für SQL Server (SQLOLEDB) und SQL Server Native Client OLE DB-Anbieter (SQLNCLI) bleiben als veraltet markiert und sollten nicht mehr für neue Bereitstellungen verwendet werden. Verwenden Sie stattdessen den neuen [Microsoft OLE DB-Treiber für SQL Server](../../connect/oledb/oledb-driver-for-sql-server.md) (MSOLEDBSQL), der mit den aktuellsten Serverfeatures aktualisiert wird.
  
[ @datasrc = ] * \'data_source\' *          
 Der Name der Datenquelle, wie er vom OLE DB-Anbieter interpretiert wird. *data_source* ist vom Datentyp **nvarchar (** 4000 **)**. *data_source* wird als DBPROP_INIT_DATASOURCE Eigenschaft zum Initialisieren des OLE DB Anbieters übermittelt.  
  
[ @location = ] * \'Speicherort\' *          
 Der Speicherort der Datenbank im vom OLE DB-Anbieter unterstützten Format. *Location* ist vom Datentyp **nvarchar (** 4000 **)** und hat den Standardwert NULL. der *Speicherort* wird als DBPROP_INIT_LOCATION-Eigenschaft zum Initialisieren des OLE DB Anbieters übermittelt.  
  
[ @provstr = ] * \'provider_string\' *          
 Die für den OLE DB-Anbieter spezifische Verbindungszeichenfolge, die eine eindeutige Datenquelle identifiziert. *provider_string* ist vom Datentyp **nvarchar (** 4000 **)** und hat den Standardwert NULL. *provstr* wird entweder an IDataInitialize weitergeleitet oder als DBPROP_INIT_PROVIDERSTRING-Eigenschaft festgelegt, um den OLE DB-Anbieter zu initialisieren.  
  
 Wenn der Verbindungs Server [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] für den Native Client OLE DB-Anbieter erstellt wird, kann die Instanz mit dem Server Schlüsselwort as Server = Server*Name*\\*instanceName* angegeben werden, um eine bestimmte Instanz [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]von anzugeben. *Server* Name ist der Name des Computers, auf dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird, und *instanceName* ist der Name der spezifischen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , mit der der Benutzer verbunden wird.  
  
> [!NOTE]
> Der Zugriff auf eine gespiegelte Datenbank ist nur dann möglich, wenn eine Verbindungszeichenfolge den Datenbanknamen enthält. Dieser Name ist notwendig, um Failoverversuche des Datenzugriffsanbieters zu ermöglichen. Die Datenbank kann im ** \@provstr** -Parameter oder ** \@im Catalog** -Parameter angegeben werden. Optional kann in der Verbindungszeichenfolge auch ein Failoverpartnername angegeben werden.  
  
[ @catalog = ] * \'Katalog\' *       
 Der Katalog, der verwendet werden soll, wenn eine Verbindung mit dem OLE DB-Anbieter hergestellt wird. *catalog* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. der *Katalog* wird als DBPROP_INIT_CATALOG-Eigenschaft zum Initialisieren des OLE DB Anbieters übermittelt. Wenn der Verbindungsserver für eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] definiert wird, verweist catalog auf die Standarddatenbank, der der Verbindungsserver zugeordnet ist.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="remarks"></a>Hinweise  
 Die folgende Tabelle zeigt die Einrichtungsmöglichkeiten eines Verbindungsservers für Datenquellen, auf die über OLE DB zugegriffen werden kann. Für die Einrichtung eines Verbindungsservers für eine bestimmte Datenquelle gibt es mehrere Möglichkeiten; für die einzelnen Datenquellentypen sind möglicherweise mehrere Zeilen vorhanden. Diese Tabelle zeigt auch die **sp_addlinkedserver** Parameterwerte, die zum Einrichten des Verbindungs Servers verwendet werden sollen.  
  
|OLE DB-Remotedatenquelle|OLE DB-Anbieter|product_name|provider_name|data_source|location|provider_string|catalog|  
|-------------------------------|---------------------|-------------------|--------------------|------------------|--------------|----------------------|-------------|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-OLE DB-Anbieter|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <sup>1</sup> (Standard)||||||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-OLE DB-Anbieter||**SQLNCLI**|Netzwerkname von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (für Standardinstanz)|||Datenbankname (optional)|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-OLE DB-Anbieter||**SQLNCLI**|*Servername*\\*instanceName* (für eine bestimmte Instanz)|||Datenbankname (optional)|  
|Oracle, Version 8 und höher|Oracle-Anbieter für OLE DB|Any|**OraOLEDB.Oracle**|Alias für die Oracle-Datenbank||||  
|Access/Jet|Microsoft OLE DB-Anbieter für Jet|Any|**Microsoft.Jet.OLEDB.4.0**|Vollständiger Pfad der Jet-Datenbankdatei||||  
|ODBC-Datenquelle (ODBC data source)|Microsoft OLE DB-Anbieter für ODBC|Any|**MSDASQL**|System-DSN der ODBC-Datenquelle||||  
|ODBC-Datenquelle (ODBC data source)|[!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB-Anbieter für ODBC|Any|**MSDASQL**|||ODBC-Verbindungszeichenfolge||  
|Dateisystem|[!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB-Anbieter für den Indexdienst|Any|**MSIDXS**|Katalogname von Indexdienstleistung||||  
|[!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel-Kalkulationstabelle|[!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB-Anbieter für Jet|Any|**Microsoft.Jet.OLEDB.4.0**|Vollständiger Pfad der Excel-Datei||Excel 5,0||  
|IBM DB2-Datenbank|[!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB-Anbieter für DB2|Any|**DB2OLEDB**|||Weitere [!INCLUDE[msCoName](../../includes/msconame-md.md)] Informationen finden Sie unter OLE DB Provider für DB2-Dokumentation.|Katalogname der DB2-Datenbank|  
  
 <sup>1</sup> diese Art der Einrichtung eines Verbindungs Servers erzwingt, dass der Name des Verbindungs Servers mit dem Netzwerknamen der Remote Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]identisch ist. Verwenden Sie *data_source* , um den Server anzugeben.  
  
 <sup>2</sup> "Any" gibt an, dass der Produktname etwas sein kann.  
  
 Der [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter ist der Anbieter, der mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet wird, wenn kein Anbieter Name angegeben [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ist oder wenn als Produktname angegeben wird. Selbst wenn Sie den älteren Anbieternamen, SQLOLEDB, angeben, wird er beim persistenten Speichern im Katalog in SQLNCLI geändert.  
  
 Mit den Parametern *data_source*, *Location*, *provider_string*und *catalog* wird die Datenbank bzw. die Datenbanken identifiziert, auf die der Verbindungs Server verweist. Falls einer dieser Parameter den Wert NULL hat, wird die entsprechende OLE DB-Initialisierungseigenschaft nicht festgelegt.  
  
 Verwenden Sie in einer Clusterumgebung, wenn Sie Dateinamen angeben, um auf OLE DB-Datenquellen zu verweisen, den UNC-Namen (Universal Naming Convention) oder ein freigegebenes Laufwerk, um den Speicherort anzugeben.  
  
 **sp_addlinkedserver** kann nicht innerhalb einer benutzerdefinierten Transaktion ausgeführt werden.  
  
> [!IMPORTANT]
> Wenn ein Verbindungs Server mithilfe von **sp_addlinkedserver**erstellt wird, wird für alle lokalen Anmeldungen eine standardmäßige selbst Zuordnung hinzugefügt. Für nicht- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anbieter [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] können authentifizierte Anmeldungen möglicherweise Zugriff auf den Anbieter unter dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Dienst Konto erhalten. Administratoren sollten eventuell `sp_droplinkedsrvlogin <linkedserver_name>, NULL` verwenden, um die globale Zuordnung zu entfernen.  
  
## <a name="permissions"></a>Berechtigungen  
 Die `sp_addlinkedserver` -Anweisung erfordert `ALTER ANY LINKED SERVER` die-Berechtigung. (Das [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Dialogfeld **neuer Verbindungs Server** wird so implementiert, dass die Mitgliedschaft in der `sysadmin` Server Rolle "Fixed" erforderlich ist.)  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-using-the-microsoft-sql-server-ole-db-provider"></a>A. Verwenden des Microsoft SQL Server OLE DB-Anbieters  
 Im folgenden Beispiel wird der Verbindungsserver `SEATTLESales` erstellt. Der Produktname lautet `SQL Server`, und es wird kein Anbietername verwendet.  
  
```sql  
USE master;  
GO  
EXEC sp_addlinkedserver   
   N'SEATTLESales',  
   N'SQL Server';  
GO  
```  

 Im folgenden Beispiel wird mithilfe des `S1_instance1` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB Treibers ein Verbindungs Server für eine Instanz von erstellt.  

```sql  
EXEC sp_addlinkedserver     
   @server=N'S1_instance1',   
   @srvproduct=N'',  
   @provider=N'MSOLEDBSQL',   
   @datasrc=N'S1\instance1';  
```  

 Im folgenden Beispiel wird mithilfe des `S1_instance1` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-OLE DB Anbieters ein Verbindungs Server für eine Instanz von erstellt.  
 
> [!IMPORTANT] 
> Der SQL Server Native Client OLE DB-Anbieter (SQLNCLI) bleibt als veraltet markiert und sollte nicht mehr für neue Bereitstellungen verwendet werden. Verwenden Sie stattdessen den neuen [Microsoft OLE DB-Treiber für SQL Server](../../connect/oledb/oledb-driver-for-sql-server.md) (MSOLEDBSQL), der mit den aktuellsten Serverfeatures aktualisiert wird.
  
```sql  
EXEC sp_addlinkedserver     
   @server=N'S1_instance1',   
   @srvproduct=N'',  
   @provider=N'SQLNCLI',   
   @datasrc=N'S1\instance1';  
```  
  
### <a name="b-using-the-microsoft-ole-db-provider-for-microsoft-access"></a>B. Verwenden des Microsoft OLE DB-Anbieters für Microsoft Access  
 Der Microsoft.Jet.OLEDB.4.0-Anbieter stellt eine Verbindung mit Microsoft Access-Datenbanken her, die das 2002-2003-Format verwenden. Im folgenden Beispiel wird der Verbindungsserver `SEATTLE Mktg` erstellt.  
  
> [!NOTE]  
> In diesem Beispiel wird davon [!INCLUDE[msCoName](../../includes/msconame-md.md)] ausgegangen, dass sowohl der Zugriff als auch die **Northwind** -Beispieldatenbank installiert sind und dass sich die **Northwind** -Datenbank in c:\msoffice\access\samplesbefindet.  
  
```sql  
EXEC sp_addlinkedserver   
   @server = N'SEATTLE Mktg',   
   @provider = N'Microsoft.Jet.OLEDB.4.0',   
   @srvproduct = N'OLE DB Provider for Jet',  
   @datasrc = N'C:\MSOffice\Access\Samples\Northwind.mdb';  
GO  
```  
  
 Der Microsoft.ACE.OLEDB.12.0-Anbieter stellt eine Verbindung mit Microsoft Access-Datenbanken her, die das 2007-Format verwenden. Im folgenden Beispiel wird der Verbindungsserver `SEATTLE Mktg` erstellt.  
  
> [!NOTE]  
> In diesem Beispiel wird davon [!INCLUDE[msCoName](../../includes/msconame-md.md)] ausgegangen, dass sowohl der Zugriff als auch die **Northwind** -Beispieldatenbank installiert sind und dass sich die **Northwind** -Datenbank in c:\msoffice\access\samplesbefindet.  
  
```sql  
EXEC sp_addlinkedserver   
   @server = N'SEATTLE Mktg',   
   @provider = N'Microsoft.ACE.OLEDB.12.0',   
   @srvproduct = N'OLE DB Provider for ACE',  
   @datasrc = N'C:\MSOffice\Access\Samples\Northwind.accdb';  
GO  
```  
  
### <a name="c-using-the-microsoft-ole-db-provider-for-odbc-with-the-data_source-parameter"></a>C. Verwenden des Microsoft OLE DB-Anbieters für ODBC mit dem data_source-Parameter  
 Im folgenden Beispiel wird ein Verbindungs Server mit `SEATTLE Payroll` dem Namen erstellt [!INCLUDE[msCoName](../../includes/msconame-md.md)] , der den OLE DB Anbieter für`MSDASQL`ODBC () und den *data_source* -Parameter verwendet.  
  
> [!NOTE]  
> Der angegebene ODBC-Datenquellenname muss vor der Verwendung des Verbindungsservers auf dem Server als System-DSN definiert werden.  
  
```sql  
EXEC sp_addlinkedserver   
   @server = N'SEATTLE Payroll',   
   @srvproduct = N'',  
   @provider = N'MSDASQL',   
   @datasrc = N'LocalServer';  
GO  
```  
  
### <a name="d-using-the-microsoft-ole-db-provider-for-excel-spreadsheet"></a>D. Verwenden des Microsoft OLE DB-Anbieters für Excel-Arbeitsblätter  
 Um eine Verbindungs Server Definition mit dem [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB-Anbieter für Jet für den Zugriff auf eine Excel-Tabelle im 1997-2003-Format zu erstellen, erstellen Sie zunächst einen benannten Bereich in Excel, indem Sie die Spalten und Zeilen des Excel-Arbeitsblatts angeben, die ausgewählt werden sollen. Auf den Namen des Bereichs kann dann als Tabellenname in einer verteilten Abfrage verwiesen werden.  
  
```sql  
EXEC sp_addlinkedserver 'ExcelSource',  
   'Jet 4.0',  
   'Microsoft.Jet.OLEDB.4.0',  
   'c:\MyData\DistExcl.xls',  
   NULL,  
   'Excel 5.0';  
GO  
```  
  
 Um auf Daten zugreifen zu können, die sich in einer Excel-Kalkulationstabelle befinden, ordnen Sie einem Zellenbereich einen Namen zu. Die folgende Abfrage kann für den Zugriff auf den angegebenen benannten Bereich `SalesData` als Tabelle mithilfe des zuvor eingerichteten Verbindungsservers verwendet werden.  
  
```sql  
SELECT *  
   FROM ExcelSource...SalesData;  
GO  
```  
  
 Wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unter einem Domänenkonto ausgeführt wird, das Zugriff auf eine Remotefreigabe hat, kann ein UNC-Pfad anstelle eines zugeordneten Laufwerks verwendet werden.  
  
```sql  
EXEC sp_addlinkedserver 'ExcelShare',  
   'Jet 4.0',  
   'Microsoft.Jet.OLEDB.4.0',  
   '\\MyServer\MyShare\Spreadsheets\DistExcl.xls',  
   NULL,  
   'Excel 5.0';  
```  
  
 Verwenden Sie den ACE-Anbieter, um eine Verbindung mit einem Excel-Arbeitsblatt im Excel 2007-Format herzustellen.  
  
```sql  
EXEC sp_addlinkedserver @server = N'ExcelDataSource',   
@srvproduct=N'ExcelData', @provider=N'Microsoft.ACE.OLEDB.12.0',   
@datasrc=N'C:\DataFolder\People.xlsx',  
@provstr=N'EXCEL 12.0' ;  
  
```  
  
### <a name="e-using-the-microsoft-ole-db-provider-for-jet-to-access-a-text-file"></a>E. Verwenden des Microsoft OLE DB-Anbieters für Jet für den Zugriff auf eine Textdatei  
 Im folgenden Beispiel wird ein Verbindungsserver für den direkten Zugriff auf Textdateien erstellt, ohne die Dateien als Tabellen in einer MDB-Datei von Microsoft Access zu verknüpfen. Der Anbieter ist `Microsoft.Jet.OLEDB.4.0`, und die Anbieterzeichenfolge lautet `Text`.  
  
 Die Datenquelle ist der vollständige Pfad des Verzeichnisses mit den Textdateien. Eine Datei namens schema.ini, die die Struktur der Textdateien beschreibt, muss im selben Verzeichnis wie die Textdateien vorhanden sein. Weitere Informationen zum Erstellen der Datei Schema.ini finden Sie in der Dokumentation zur Jet-Datenbank-Engine.  
  
```sql  
--Create a linked server.  
EXEC sp_addlinkedserver txtsrv, N'Jet 4.0',   
   N'Microsoft.Jet.OLEDB.4.0',  
   N'c:\data\distqry',  
   NULL,  
   N'Text';  
GO  
  
--Set up login mappings.  
EXEC sp_addlinkedsrvlogin txtsrv, FALSE, Admin, NULL;  
GO  
  
--List the tables in the linked server.  
EXEC sp_tables_ex txtsrv;  
GO  
  
--Query one of the tables: file1#txt  
--using a four-part name.   
SELECT *   
FROM txtsrv...[file1#txt];  
```  
  
### <a name="f-using-the-microsoft-ole-db-provider-for-db2"></a>F. Verwenden des Microsoft OLE DB-Anbieters für DB2  
 Im folgenden Beispiel wird der Verbindungsserver `DB2` erstellt, der `Microsoft OLE DB Provider for DB2` verwendet.  
  
```sql  
EXEC sp_addlinkedserver  
   @server=N'DB2',  
   @srvproduct=N'Microsoft OLE DB Provider for DB2',  
   @catalog=N'DB2',  
   @provider=N'DB2OLEDB',  
   @provstr=N'Initial Catalog=PUBS;  
       Data Source=DB2;  
       HostCCSID=1252;  
       Network Address=XYZ;  
       Network Port=50000;  
       Package Collection=admin;  
       Default Schema=admin;';  
```  
  
### <a name="g-add-a-sssdsfull-as-a-linked-server-for-use-with-distributed-queries-on-cloud-and-on-premises-databases"></a>G. Hinzufügen [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] eines als Verbindungs Server für die Verwendung mit verteilten Abfragen in Cloud-und lokalen Datenbanken  
 Sie können eine [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] als Verbindungsserver hinzufügen und diesen dann für verteilte Abfragen verwenden, die lokale Datenbanken und Clouddatenbanken umfassen. Dies ist eine Komponente für Daten Bank Hybridlösungen, die lokale Unternehmensnetzwerke und die Azure-Cloud umfassen.  
  
 Das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Box-Produkt enthält das Feature für verteilte Abfragen, mit dem Sie Abfragen zum Kombinieren von Daten aus lokalen Datenquellen und Daten aus Remote Quellen (einschließlich Daten aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nicht-Datenquellen), die als Verbindungs Server definiert sind, schreiben können. Jede [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] (außer der virtuellen Masterdatenbank) kann als einzelner Verbindungsserver hinzugefügt und wie jede andere Datenbank direkt in Datenbankanwendungen verwendet werden.  
  
 Die Vorteile der Verwendung einer [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] sind: Verwaltbarkeit, Hochverfügbarkeit, Skalierbarkeit, ein vertrautes Entwicklungsmodell sowie ein relationales Datenmodell. Auf welche Weise eine [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] von Ihrer Datenbank in der Cloud verwendet wird, richtet sich nach den Anwendungsanforderungen. Sie können alle Daten gleichzeitig auf eine [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] verschieben oder einige Daten stufenweise umlagern, während die übrigen Daten in der lokalen Umgebung verbleiben. Für eine solche Hybrid Datenbankanwendung [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] kann nun als Verbindungs Server hinzugefügt werden, und die Datenbankanwendung kann verteilte Abfragen ausgeben, [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] um Daten aus und lokalen Datenquellen zu kombinieren.  
  
 Im folgenden finden Sie ein einfaches Beispiel für das Herstellen einer [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] Verbindung mit einer mithilfe von verteilten Abfragen:  
  
```sql  
-- Configure the linked server  
-- Add one Azure SQL DB as Linked Server  
EXEC sp_addlinkedserver  
  @server='myLinkedServer', -- here you can specify the name of the linked server  
  @srvproduct='',       
  @provider='sqlncli', -- using SQL Server Native Client  
  @datasrc='myServer.database.windows.net',   -- add here your server name  
  @location='',  
  @provstr='',  
  @catalog='myDatabase'  -- add here your database name as initial catalog (you cannot connect to the master database)  

-- Add credentials and options to this linked server  
EXEC sp_addlinkedsrvlogin  
  @rmtsrvname = 'myLinkedServer',  
  @useself = 'false',  
  @rmtuser = 'myLogin',             -- add here your login on Azure DB  
  @rmtpassword = 'myPassword' -- add here your password on Azure DB  

EXEC sp_serveroption 'myLinkedServer', 'rpc out', true;  

-- Now you can use the linked server to execute 4-part queries  
-- You can create a new table in the Azure DB  
EXEC ('CREATE TABLE t1tutut2(col1 int not null CONSTRAINT PK_col1 PRIMARY KEY CLUSTERED (col1) )') at myLinkedServer  
-- Insert data from your local SQL Server  
EXEC ('INSERT INTO t1tutut2 VALUES(1),(2),(3)') at myLinkedServer  
  
-- Query the data using 4-part names  
SELECT * FROM myLinkedServer.myDatabase.dbo.myTable  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Prozeduren für verteilte Abfragen &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/distributed-queries-stored-procedures-transact-sql.md)   
 [sp_addlinkedsrvlogin &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql.md)   
 [sp_addserver &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md)   
 [sp_dropserver &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-dropserver-transact-sql.md)   
 [sp_serveroption &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-serveroption-transact-sql.md)   
 [sp_setnetname &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-setnetname-transact-sql.md)   
 [Gespeicherte System Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Systemtabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
