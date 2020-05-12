---
title: OPENDATASOURCE (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/26/2019
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- OPENDATASOURCE
- OPENDATASOURCE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- data sources [SQL Server]
- OPENDATASOURCE function
- remote data access [SQL Server], OPENDATASOURCE
- ad hoc distributed queries
- OLE DB data sources [SQL Server]
- ad hoc connection information
ms.assetid: 5510b846-9cde-4687-8798-be9a273aad31
author: julieMSFT
ms.author: jrasnick
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: ec0e71eaf4c5f92ddd196435a78c3824d98e9d76
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82826809"
---
# <a name="opendatasource-transact-sql"></a>OPENDATASOURCE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  Stellt Ad-hoc-Verbindungsinformationen als Teil eines vierteiligen Objektnamens ohne Verwendung eines Verbindungsservernamens bereit.  

 ![Linksymbol](../../database-engine/configure-windows/media/topic-link.gif "Linksymbol") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
OPENDATASOURCE ( 'provider_name', 'init_string' )  
```  
  
## <a name="arguments"></a>Argumente  
 '*provider_name*'  
 Der Namen, der als PROGID des OLE DB-Anbieters für den Zugriff auf die Datenquelle registriert ist. *provider_name* ist vom Datentyp **char** und verfügt über keinen Standardwert.  

 > [!IMPORTANT]
 > Der vorherige Microsoft OLE DB-Anbieter für SQL Server (SQLOLEDB) und SQL Server Native Client OLE DB-Anbieter (SQLNCLI) bleiben als veraltet markiert und sollten nicht mehr für neue Bereitstellungen verwendet werden. Verwenden Sie stattdessen den neuen [Microsoft OLE DB-Treiber für SQL Server](../../connect/oledb/oledb-driver-for-sql-server.md) (MSOLEDBSQL), der mit den aktuellsten Serverfeatures aktualisiert wird.
 
 '*init_string*'  
 Die Verbindungszeichenfolge, die an die IDataInitialize-Schnittstelle des Zielanbieters übergeben wird. Die Syntax der Anbieterzeichenfolge basiert auf durch Semikolons getrennten Schlüssel-Wert-Paaren im folgenden Format: **'** _keyword1_=_value_ **;** _keyword2_=_value_ **'** .  
  
 Informationen zu bestimmten, vom Anbieter unterstützten Paaren aus Schlüsselwort und Wert finden Sie im MDAC SDK ([!INCLUDE[msCoName](../../includes/msconame-md.md)] Data Access Components Software Development Kit). In dieser Dokumentation wird die grundlegende Syntax definiert. In der folgenden Tabelle werden die am häufigsten im *init_string*-Argument verwendeten Schlüsselwörter aufgelistet.  
  
|Schlüsselwort|OLE DB-Eigenschaft|Gültige Werte und Beschreibung|  
|-------------|---------------------|----------------------------------|  
|Data source|DBPROP_INIT_DATASOURCE|Name der Datenquelle, mit der eine Verbindung hergestellt werden soll. Unterschiedliche Anbieter interpretieren diesen Namen auf unterschiedliche Arten. Für den OLE DB-Anbieter von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client gibt er den Servernamen an. Für den OLE DB-Anbieter von Jet gibt er den vollständigen Pfad der MDB- oder XLS-Datei an.|  
|Location|DBPROP_INIT_LOCATION|Speicherort der Datenbank, mit der eine Verbindung hergestellt werden soll.|  
|Extended Properties|DBPROP_INIT_PROVIDERSTRING|Anbieterspezifische Verbindungszeichenfolge.|  
|Connect timeout|DBPROP_INIT_TIMEOUT|Timeoutwert, bei dessen Erreichen der Verbindungsversuch einen Fehler verursacht.|  
|Benutzer-ID|DBPROP_AUTH_USERID|Für die Verbindung zu verwendende Benutzer-ID.|  
|Kennwort|DBPROP_AUTH_PASSWORD|Für die Verbindung zu verwendendes Kennwort.|  
|Katalog|DBPROP_INIT_CATALOG|Name des Anfangs- oder Standardkatalogs beim Herstellen einer Verbindung mit der Datenquelle.|  
|Integrierte Sicherheit|DBPROP_AUTH_INTEGRATED|SSPI, zur Angabe der Windows-Authentifizierung|  
  
## <a name="remarks"></a>Bemerkungen  
`OPENROWSET` erbt immer die Sortierung der Instanz, unabhängig von der für Spalten festgelegten Sortierung.

Mit `OPENDATASOURCE` kann nur auf Remotedaten von OLE DB-Datenquellen zugegriffen werden, wenn für den angegebenen Anbieter die Registrierungsoption DisallowAdhocAccess explizit auf 0 festgelegt wird und wenn die erweiterte Konfigurationsoption „Ad Hoc Distributed Queries“ aktiviert ist. Wenn diese Optionen nicht festgelegt sind, ermöglicht das Standardverhalten keinen Ad-hoc-Zugriff.  
  
Die `OPENDATASOURCE`-Funktion kann in der [!INCLUDE[tsql](../../includes/tsql-md.md)]-Syntax an denselben Stellen verwendet werden wie ein Verbindungsservername. Deshalb kann `OPENDATASOURCE` als erster Teil eines vierteiligen Namens verwendet werden, der in einer SELECT-, INSERT-, UPDATE-, oder DELETE-Anweisung auf einen Tabellen- oder Sichtnamen bzw. in einer EXECUTE-Anweisung auf eine remote gespeicherte Prozedur verweist. Beim Ausführen von remote gespeicherten Prozeduren muss `OPENDATASOURCE` auf eine andere [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz verweisen. Für die Argumente von OPENDATASOURCE können keine Variablen verwendet werden.  
  
Wie die `OPENROWSET`-Funktion sollte `OPENDATASOURCE` nur auf OLE DB-Datenquellen verweisen, auf die selten zugegriffen wird. Definieren Sie Verbindungsserver für Datenquellen, auf die nicht nur ein paar Mal zugegriffen wird. Weder OPENDATASOURCE noch OPENROWSET stellt die gesamte Funktionalität einer Verbindungsserverdefinition bereit, wie die Sicherheitsverwaltung und die Möglichkeit, Kataloginformationen abzufragen. Alle Verbindungsinformationen, einschließlich Kennwörtern, müssen bei jedem Aufruf von OPENDATASOURCE bereitgestellt werden.  
  
> [!IMPORTANT]  
> Die Windows-Authentifizierung bietet deutlich mehr Sicherheit als die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung. Verwenden Sie nach Möglichkeit die Windows-Authentifizierung. `OPENDATASOURCE` sollte nicht mit expliziten Kennwörtern in der Verbindungszeichenfolge verwendet werden.  
  
Die Verbindungsanforderungen für jeden Anbieter sind vergleichbar mit den Anforderungen an die Parameter, die zum Erstellen von Verbindungsservern verwendet werden. Details für viele gängige Anbieter sind im Artikel [sp_addlinkedserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md) aufgeführt.  
  
Jeder Aufruf von `OPENDATASOURCE`, `OPENQUERY` oder `OPENROWSET` in der `FROM`-Klausel wird einzeln und unabhängig von anderen Aufrufen dieser Funktionen ausgewertet, die als Ziel des Updates verwendet werden, auch wenn für die beiden Aufrufe identische Argumente angegeben werden. Insbesondere haben Filter- oder Joinbedingungen, die auf das Ergebnis eines dieser Aufrufe angewendet werden, keine Auswirkungen auf die Ergebnisse des jeweils anderen.  
  
## <a name="permissions"></a>Berechtigungen  
 Jeder Benutzer kann OPENDATASOURCE ausführen. Die Berechtigungen, die zum Herstellen einer Verbindung mit dem Remoteserver verwendet werden, werden anhand der Verbindungszeichenfolge bestimmt.  
  
## <a name="examples"></a>Beispiele  

### <a name="a-using-opendatasource-with-select-and-the-sql-server-ole-db-driver"></a>A. Verwenden von OPENDATASOURCE mit SELECT und dem SQL Server OLE DB-Treiber  
 Im folgenden Beispiel wird der [Microsoft OLE DB-Treiber für SQL Server](../../connect/oledb/oledb-driver-for-sql-server.md) für den Zugriff auf die `HumanResources.Department`-Tabelle in der [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]-Datenbank auf dem Remoteserver `Seattle1` verwendet. Mithilfe einer `SELECT`-Anweisung wird das zurückgegebene Rowset definiert. Die Anbieterzeichenfolge enthält die Schlüsselwörter `Server` und `Trusted_Connection`. Diese Schlüsselwörter werden vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB-Treiber erkannt.  
  
```sql  
SELECT GroupName, Name, DepartmentID  
FROM OPENDATASOURCE('MSOLEDBSQL', 'Server=Seattle1;Database=AdventureWorks2016;TrustServerCertificate=Yes;Trusted_Connection=Yes;').HumanResources.Department  
ORDER BY GroupName, Name;  
``` 

### <a name="b-using-opendatasource-with-select-and-the-sql-server-ole-db-provider"></a>B. Verwenden von OPENDATASOURCE mit SELECT und dem SQL Server OLE DB-Anbieter  
Im folgenden Beispiel wird eine Ad-hoc-Verbindung mit der `Payroll`-Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf dem Server `London` erstellt und die `AdventureWorks2012.HumanResources.Employee`-Tabelle abgefragt. 

> [!NOTE] 
> Die Verwendung von SQLNCLI bewirkt eine Umleitung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zur neuesten Version des SQL Server Native Client OLE DB-Anbieters. Es wird vorausgesetzt, dass der OLE DB-Anbieter mit der angegebenen PROGID in der Registrierung registriert ist. 

> [!IMPORTANT]  
> Der SQL Server Native Client OLE DB-Anbieter (SQLNCLI) bleibt als veraltet markiert und sollte nicht mehr für neue Bereitstellungen verwendet werden. Verwenden Sie stattdessen den neuen [Microsoft OLE DB-Treiber für SQL Server](../../connect/oledb/oledb-driver-for-sql-server.md) (MSOLEDBSQL), der mit den aktuellsten Serverfeatures aktualisiert wird.
  
```sql  
SELECT *  
FROM OPENDATASOURCE('SQLNCLI',  
    'Data Source=London\Payroll;Integrated Security=SSPI')  
    .AdventureWorks2012.HumanResources.Employee;  
```  

### <a name="c-using-the-microsoft-ole-db-provider-for-jet"></a>C. Verwenden des Microsoft OLE DB-Anbieters für Jet   
 Im folgenden Beispiel wird eine Ad-hoc-Verbindung zu einem Excel-Arbeitsblatt im Format 1997 – 2003 hergestellt.  
  
```sql  
SELECT * FROM OPENDATASOURCE('Microsoft.Jet.OLEDB.4.0',  
    'Data Source=C:\DataFolder\Documents\TestExcel.xls;Extended Properties=EXCEL 5.0')...[Sheet1$] ;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [OPENROWSET &#40;Transact-SQL&#41;](../../t-sql/functions/openrowset-transact-sql.md)   
 [sp_addlinkedserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)  
  
