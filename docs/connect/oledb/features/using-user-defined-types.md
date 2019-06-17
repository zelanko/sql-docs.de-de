---
title: Verwenden von benutzerdefinierten Typen | Microsoft-Dokumentation
description: Verwenden von benutzerdefinierten Typen mit dem OLE DB-Treiber für SQLServer
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- DBPROPSET_DATASOURCEINFO property set
- UDTs [OLE DB Driver for SQL Server]
- user-defined types [SQL Server], OLE DB Driver for SQL Server
- OLE DB Driver for SQL Server, user-defined types
- DBPROPSET_SQLSERVERPARAMETER property set
- IColumnsRowset interface
- MSOLEDBSQL, user-defined types
- OLE DB Driver for SQL Server, user-defined types
- data access [OLE DB Driver for SQL Server], user-defined types
- ISSCommandWithParameters interface
author: pmasl
ms.author: pelopes
manager: jroth
ms.openlocfilehash: efc2c82f047beca82f1daeda6318f16803499f86
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66802862"
---
# <a name="using-user-defined-types"></a>Verwenden von benutzerdefinierten Typen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  In [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] wurden benutzerdefinierte Typen (User-Defined Types, UDTs) eingeführt. UDTs erweitern das SQL-Typsystem, indem sie es ermöglichen, Objekte und benutzerdefinierte Datenstrukturen in einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenbank zu speichern. UDTs können mehrere Datentypen enthalten und Verhalten zeigen, das sie von den herkömmlichen Aliasdatentypen aus einem einzelnen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Systemdatentyp unterscheidet. UDTs werden in einer beliebigen, von .NET CLR (Common Language Runtime) unterstützten Sprache definiert, die überprüfbaren Code generiert. Dies schließt Microsoft Visual C#<sup>®</sup> und Visual Basic<sup>®</sup> .NET ein. Die Daten werden in Feldern und Eigenschaften einer .NET-Klasse oder -Struktur verfügbar gemacht. Das Verhalten wird durch die Methoden der Klasse oder Struktur definiert.  
  
 Ein UDT kann als Spaltendefinition einer Tabelle, als Variable in einem [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Batch oder als Argument einer [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Funktion oder gespeicherten Prozedur verwendet werden.  
  
## <a name="ole-db-driver-for-sql-server"></a>OLE DB-Treiber für SQL Server  
 Der OLE DB-Treiber für SQL Server unterstützt UDTs als Binärtypen mit Metadateninformationen, so dass UDTs als Objekte verwaltet werden können. UDT-Spalten werden als DBTYPE_UDT verfügbar gemacht, und ihre Metadaten werden über die OLE DB-Kernschnittstelle **IColumnRowset** und die neue [ISSCommandWithParameters](../../oledb/ole-db-interfaces/isscommandwithparameters-ole-db.md)-Schnittstelle bereitgestellt.  
  
> [!NOTE]  
>  Die **IRowsetFind::FindNextRow**-Methode funktioniert nicht mit dem UDT-Datentyp. DB_E_BADCOMPAREOP wird zurückgegeben, wenn der UDT als Suchspaltentyp verwendet wird.  
  
### <a name="data-bindings-and-coercions"></a>Datenbindungen und -umwandlungen  
 Die folgende Tabelle veranschaulicht die Bindung und Umwandlung bei Verwendung der aufgeführten Datentypen mit einem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-UDT. UDT-Spalten werden über den OLE DB-Treiber für SQL Server als DBTYPE_UDT verfügbar gemacht. Die Metadaten können Sie über die entsprechenden Schemarowsets abrufen und so Ihre benutzerdefinierten Typen als Objekte verwalten.  
  
|Datentyp|Zu Server<br /><br /> **UDT**|Zu Server<br /><br /> **non-UDT**|Von Server<br /><br /> **UDT**|Von Server<br /><br /> **non-UDT**|  
|---------------|---------------------------|--------------------------------|-----------------------------|----------------------------------|  
|DBTYPE_UDT|Unterstützt<sup>6</sup>|Fehler<sup>1</sup>|Unterstützt<sup>6</sup>|Fehler<sup>5</sup>|  
|DBTYPE_BYTES|Unterstützt<sup>6</sup>|Nicht zutreffend<sup>2</sup>|Unterstützt<sup>6</sup>|Nicht zutreffend<sup>2</sup>|  
|DBTYPE_WSTR|Unterstützt<sup>3,6</sup>|Nicht zutreffend<sup>2</sup>|Unterstützt<sup>4,6</sup>|Nicht zutreffend<sup>2</sup>|  
|DBTYPE_BSTR|Unterstützt<sup>3,6</sup>|Nicht zutreffend<sup>2</sup>|Unterstützt<sup>4</sup>|Nicht zutreffend<sup>2</sup>|  
|DBTYPE_STR|Unterstützt<sup>3,6</sup>|Nicht zutreffend<sup>2</sup>|Unterstützt<sup>4,6</sup>|Nicht zutreffend<sup>2</sup>|  
|DBTYPE_IUNKNOWN|Nicht unterstützt|Nicht zutreffend<sup>2</sup>|Nicht unterstützt|Nicht zutreffend<sup>2</sup>|  
|DBTYPE_VARIANT (VT_UI1 &#124; VT_ARRAY)|Unterstützt<sup>6</sup>|Nicht zutreffend<sup>2</sup>|Unterstützt<sup>4</sup>|Nicht zutreffend<sup>2</sup>|  
|DBTYPE_VARIANT (VT_BSTR)|Unterstützt<sup>3,6</sup>|Nicht zutreffend<sup>2</sup>|–|Nicht zutreffend<sup>2</sup>|  
  
 <sup>1</sup>Wird ein anderer Servertyp als DBTYPE_UDT mit **ICommandWithParameters::SetParameterInfo** angegeben, und ist der Accessortyp DBTYPE_UDT, tritt bei Ausführung der Anweisung ein Fehler auf (DB_E_ERRORSOCCURRED; der Parameterstatus lautet DBSTATUS_E_BADACCESSOR). Andernfalls werden die Daten an den Server gesendet, der Server gibt jedoch einen Fehler zurück und zeigt an, dass keine implizite Umwandlung des UDT in den Parameterdatentyp erfolgt.  
  
 <sup>2</sup>Nicht Bestandteil dieses Artikels.  
  
 <sup>3</sup>Es erfolgt eine Datenkonvertierung einer hexadezimalen Zeichenfolge in Binärdaten.  
  
 <sup>4</sup>Es erfolgt eine Datenkonvertierung von Binärdaten in eine hexadezimale Zeichenfolge.  
  
 <sup>5</sup>Die Überprüfung kann zum Zeitpunkt der Accessorerstellung oder zum Zeitpunkt des Abrufens vorgenommen werden. Der Fehler ist DB_E_ERRORSOCCURRED, der Bindungsstatus ist auf DBBINDSTATUS_UNSUPPORTEDCONVERSION festgelegt.  
  
 <sup>6</sup>BY_REF wird möglicherweise verwendet.  
  
 DBTYPE_NULL und DBTYPE_EMPTY können für Eingabeparameter gebunden werden, aber nicht für Ausgabeparameter oder Ergebnisse. Ist der Status für Eingabeparameter gebunden, muss er auf DBSTATUS_S_ISNULL oder DBSTATUS_S_DEFAULT festgelegt werden.  
  
 DBTYPE_UDT kann auch in DBTYPE_EMPTY und DBTYPE_NULL umgewandelt werden, DBTYPE_NULL und DBTYPE_EMPTY können jedoch nicht in DBTYPE_UDT umgewandelt werden. Dies stimmt mit DBTYPE_BYTES überein.  
  
> [!NOTE]  
>  Für den Umgang mit UDTs als Parametern wird eine neue Schnittstelle, **ISSCommandWithParameters**, verwendet, die von **ICommandWithParameters** erbt. Anwendungen müssen diese Schnittstelle verwenden, um mindestens SSPROP_PARAM_UDT_NAME der DBPROPSET_SQLSERVERPARAMETER-Eigenschaftengruppe für UDT-Parameter festzulegen. Andernfalls gibt **ICommand::Execute** DB_E_ERRORSOCCURRED zurück. Diese Schnittstelle und Eigenschaftengruppe werden im weiteren Verlauf dieses Artikels erläutert.  
  
 Wird ein UDT in eine Spalte eingefügt, die nicht groß genug für alle Daten ist, gibt **ICommand::Execute** S_OK mit dem Status DB_E_ERRORSOCCURRED zurück.  
  
 Datenkonvertierungen durch OLE DB-Basisdienste (**IDataConvert**) sind nicht auf DBTYPE_UDT anwendbar. Es werden keine weiteren Bindungen unterstützt.  
  
### <a name="ole-db-rowset-additions-and-changes"></a>Hinzufügungen und Änderungen am OLE DB-Rowset  
 OLE DB-Treiber für SQL Server fügt neue Werte oder Änderungen in zahlreichen Core-OLE DB-Schemarowsets.  
  
#### <a name="the-procedureparameters-schema-rowset"></a>Das PROCEDURE_PARAMETERS-Schemarowset  
 Die folgenden Hinzufügungen wurden am PROCEDURE_PARAMETERS-Schemarowset vorgenommen.  
  
|Spaltenname|Typ|und Beschreibung|  
|-----------------|----------|-----------------|  
|SS_UDT_CATALOGNAME|DBTYPE_WSTR|Der dreiteilige Namensbezeichner.|  
|SS_UDT_SCHEMANAME|DBTYPE_WSTR|Der dreiteilige Namensbezeichner.|  
|SS_UDT_NAME|DBTYPE_WSTR|Der dreiteilige Namensbezeichner.|  
|SS_UDT_ASSEMBLY_TYPENAME|DBTYPE_WSTR|Der qualifizierte Name der Assembly mit dem Typnamen und allen zur CLR-Referenzierung erforderlichen Angaben zur Assembly-ID.|  
  
#### <a name="the-sqlassemblies-schema-rowset"></a>Das SQL_ASSEMBLIES-Schemarowset  
 Der OLE DB-Treiber für SQL Server macht ein neues anbieterspezifisches Schemarowset verfügbar, das die registrierten UDTs beschreibt. Der ASSEMBLY-Server wird möglicherweise als DBTYPE_WSTR angegeben, ist aber nicht im Rowset vorhanden. Ohne Angabe wird das Rowset standardmäßig für den aktuellen Server festgelegt. Das SQL_ASSEMBLIES-Schemarowset wird in der folgenden Tabelle definiert:  
  
|Spaltenname|Typ|und Beschreibung|  
|-----------------|----------|-----------------|  
|ASSEMBLY_CATALOG|DBTYPE_WSTR|Der Katalogname der Assembly, die den Typ enthält.|  
|ASSEMBLY_SCHEMA|DBTYPE_WSTR|Der Name des Schemas oder der Eigentümername der Assembly, die den Typ enthält. Obwohl der Bereich einer Assembly durch die Datenbank und nicht durch ein Schema definiert wird, hat sie einen Eigentümer, der hier angegeben wird.|  
|ASSEMBLY_NAME|DBTYPE_WSTR|Der Name der Assembly, die den Typ enthält.|  
|ASSEMBLY_ID|DBTYPE_UI4|Die Objekt-ID der Assembly, die den Typ enthält.|  
|PERMISSION_SET|DBTYPE_WSTR|Ein Wert, der den Zugriffsbereich für die Assembly angibt. Zulässige Werten sind "SAFE", "EXTERNAL_ACCESS" und "UNSAFE".|  
|ASSEMBLY_BINARY|DBTYPE_BYTES|Die Binärdarstellung der Assembly.|  
  
#### <a name="the-sqlassemblies-dependencies-schema-rowset"></a>Das SQL_ASSEMBLIES_ DEPENDENCIES-Schemarowset  
 Der OLE DB-Treiber für SQL Server macht ein neues anbieterspezifisches Schemarowset verfügbar, das die Assemblyabhängigkeiten für einen bestimmten Server beschreibt. ASSEMBLY_SERVER wird möglicherweise vom Aufrufer als DBTYPE_WSTR angegeben, ist aber nicht im Rowset vorhanden. Ohne Angabe wird das Rowset standardmäßig für den aktuellen Server festgelegt. Das SQL_ASSEMBLY_DEPENDENCIES-Schemarowset wird in der folgenden Tabelle definiert:  
  
|Spaltenname|Typ|und Beschreibung|  
|-----------------|----------|-----------------|  
|ASSEMBLY_CATALOG|DBTYPE_WSTR|Der Katalogname der Assembly, die den Typ enthält.|  
|ASSEMBLY_SCHEMA|DBTYPE_WSTR|Der Name des Schemas oder der Eigentümername der Assembly, die den Typ enthält. Obwohl der Bereich einer Assembly durch die Datenbank und nicht durch ein Schema definiert wird, hat sie einen Eigentümer, der hier angegeben wird.|  
|ASSEMBLY_ID|DBTYPE_UI4|Die Objekt-ID der Assembly.|  
|REFERENCED_ASSEMBLY_ID|DBTYPE_UI4|Die Objekt-ID der referenzierten Assembly.|  
  
#### <a name="the-sqlusertypes-schema-rowset"></a>Das SQL_USER_TYPES-Schemarowset  
 Der OLE DB-Treiber für SQL Server macht ein neues Schemarowset, SQL_USER_TYPES, verfügbar, das beschreibt, wann die registrierten UDTs für einen bestimmten Server hinzugefügt werden. UDT_SERVER muss vom Aufrufer als DBTYPE_WSTR angegeben werden, ist aber nicht im Rowset vorhanden. Das SQL_USER_TYPES-Schemarowset wird in der folgenden Tabelle definiert.  
  
|Spaltenname|Typ|und Beschreibung|  
|-----------------|----------|-----------------|  
|UDT_CATALOGNAME|DBTYPE_WSTR|Bei UDT-Spalten ist diese Eigenschaft eine Zeichenfolge, die den Namen des Katalogs angibt, in dem der UDT definiert ist.|  
|UDT_SCHEMANAME|DBTYPE_WSTR|Bei UDT-Spalten ist diese Eigenschaft eine Zeichenfolge, die den Namen des Schemas angibt, in dem der UDT definiert ist.|  
|UDT_NAME|DBTYPE_WSTR|Der Name der Assembly, die die UDT-Klasse enthält.|  
|UDT_ASSEMBLY_TYPENAME|DBTYPE_WSTR|Vollständiger Typname (AQN) einschließlich Typname mit Namespace als Präfix (falls zutreffend).|  
  
#### <a name="the-columns-schema-rowset"></a>Das COLUMNS-Schemarowset  
 Dem COLUMNS-Schemarowset wurden unter anderem die folgenden Spalten hinzugefügt:  
  
|Spaltenname|Typ|und Beschreibung|  
|-----------------|----------|-----------------|  
|SS_UDT_CATALOGNAME|DBTYPE_WSTR|Bei UDT-Spalten ist diese Eigenschaft eine Zeichenfolge, die den Namen des Katalogs angibt, in dem der UDT definiert ist.|  
|SS_UDT_SCHEMANAME|DBTYPE_WSTR|Bei UDT-Spalten ist diese Eigenschaft eine Zeichenfolge, die den Namen des Schemas angibt, in dem der UDT definiert ist.|  
|SS_UDT_NAME|DBTYPE_WSTR|Der Name des UDT.|  
|SS_UDT_ASSEMBLY_TYPENAME|DBTYPE_WSTR|Vollständiger Typname (AQN) einschließlich Typname mit Namespace als Präfix (falls zutreffend).|  
  
### <a name="ole-db-property-set-additions-and-changes"></a>Hinzufügungen und Änderungen an der OLE DB-Eigenschaftengruppe  
 OLE DB-Treiber für SQL Server fügt neue Werte oder Änderungen in zahlreichen Core-OLE DB-Eigenschaft legt.  
  
#### <a name="the-dbpropsetsqlserverparameter-property-set"></a>Die DBPROPSET_SQLSERVERPARAMETER-Eigenschaftengruppe  
 Um UDTs mit OLE DB zu unterstützen, implementiert der OLE DB-Treiber für SQL Server die neue DBPROPSET_SQLSERVERPARAMETER-Eigenschaftengruppe mit folgenden Werten:  
  
|Name|Typ|und Beschreibung|  
|----------|----------|-----------------|  
|SSPROP_PARAM_UDT_CATALOGNAME|DBTYPE_WSTR|Der dreiteilige Namensbezeichner.<br /><br /> Bei UDT-Parametern ist diese Eigenschaft eine Zeichenfolge, die den Namen des Katalogs angibt, in dem der UDT definiert ist.|  
|SSPROP_PARAM_UDT_SCHEMANAME|DBTYPE_WSTR|Der dreiteilige Namensbezeichner.<br /><br /> Bei UDT-Parametern ist diese Eigenschaft eine Zeichenfolge, die den Namen des Schemas angibt, in dem der UDT definiert ist.|  
|SSPROP_PARAM_UDT_NAME|DBTYPE_WSTR|Der dreiteilige Namensbezeichner.<br /><br /> Bei UDT-Spalten ist diese Eigenschaft eine Zeichenfolge, die den einteiligen Namen des UDT angibt.|  
  
 SSPROP_PARAM_UDT_NAME ist erforderlich. SSPROP_PARAM_UDT_CATALOGNAME und SSPROP_PARAM_UDT_SCHEMANAME sind optional. Wenn Eigenschaften falsch angegeben werden, wird DB_E_ERRORSINCOMMAND zurückgegeben. Werden weder SSPROP_PARAM_UDT_CATALOGNAME noch SSPROP_PARAM_UDT_SCHEMANAME angegeben, muss der UDT in derselben Datenbank und im selben Schema definiert werden wie die Tabelle. Befindet sich der UDT nicht im selben Schema wie die Tabelle (aber in derselben Datenbank), muss SSPROP_PARAM_UDT_SCHEMANAME angegeben werden. Befindet sich die UDT-Definition in einer anderen Datenbank, müssen SSPROP_PARAM_UDT_CATALOGNAME und SSPROP_PARAM_UDT_SCHEMANAME angegeben werden.  
  
#### <a name="the-dbpropsetsqlservercolumn-property-set"></a>Die DBPROPSET_SQLSERVERCOLUMN-Eigenschaftengruppe  
 Um die Tabellenerstellung in der **ITableDefinition**-Schnittstelle zu unterstützen, fügt der OLE DB-Treiber für SQL Server zur DBPROPSET_SQLSERVERCOLUMN-Eigenschaftengruppe die folgenden drei neuen Spalten hinzu.  
  
|Name|und Beschreibung|Typ|und Beschreibung|  
|----------|-----------------|----------|-----------------|  
|SSPROP_COL_UDT_CATALOGNAME|UDT_CATALOGNAME|VT_BSTR|Bei Spalten vom Typ DBTYPE_UDT ist diese Eigenschaft eine Zeichenfolge, die den Namen des Katalogs angibt, in dem der UDT definiert ist.|  
|SSPROP_COL_UDT_SCHEMANAME|UDT_SCHEMANAME|VT_BSTR|Bei Spalten vom Typ DBTYPE_UDT ist diese Eigenschaft eine Zeichenfolge, die den Namen des Schemas angibt, in dem der UDT definiert ist.|  
|SSPROP_COL_UDT_NAME|UDT_NAME|VT_BSTR|Bei Spalten vom Typ DBTYPE_UDT ist diese Eigenschaft eine Zeichenfolge, die den einteiligen Namen des UDT angibt. Für andere Spaltentypen gibt diese Eigenschaft eine leere Zeichenfolge zurück.|  
  
> [!NOTE]  
>  UDTs werden nicht im PROVIDER_TYPES-Schemarowset angezeigt. Alle Spalten haben Lese- und Schreibzugriff.  
  
 ADO verweist mit dem entsprechenden Eintrag aus der Beschreibungsspalte auf diese Eigenschaften.  
  
 SSPROP_COL_UDTNAME ist erforderlich. SSPROP_COL_UDT_CATALOGNAME und SSPROP_COL_UDT_SCHEMANAME sind optional. Wenn Eigenschaften falsch angegeben werden, wird **DB_E_ERRORSINCOMMAND** zurückgegeben.  
  
 Werden weder SSPROP_COL_UDT_CATALOGNAME noch SSPROP_COL_UDT_SCHEMANAME angegeben, muss der UDT in derselben Datenbank und im selben Schema definiert werden wie die Tabelle.  
  
 Befindet sich der UDT nicht im selben Schema wie die Tabelle (aber in derselben Datenbank), muss SSPROP_COL_UDT_SCHEMANAME angegeben werden.  
  
 Befindet sich die UDT-Definition in einer anderen Datenbank, müssen SSPROP_COL_UDT_CATALOGNAME und SSPROP_COL_UDT_SCHEMANAME angegeben werden.  
  
### <a name="ole-db-interface-additions-and-changes"></a>Hinzufügungen und Änderungen an der OLE DB-Schnittstelle  
 OLE DB-Treiber für SQL Server fügt neue Werte oder Änderungen in zahlreichen Core-OLE DB-Schnittstellen.  
  
#### <a name="the-isscommandwithparameters-interface"></a>Die ISSCommandWithParameters-Schnittstelle  
 Zur Unterstützung von UDTs durch OLE DB implementiert der OLE DB-Treiber für SQL Server eine Reihe von Änderungen, darunter die neue **ISSCommandWithParameters**-Schnittstelle. Diese neue Schnittstelle erbt von der OLE DB-Kernschnittstelle **ICommandWithParameters**. Zusätzlich zu den drei von **ICommandWithParameters** geerbten Methoden (**GetParameterInfo**, **MapParameterNames** und **SetParameterInfo**) stellt **ISSCommandWithParameters** zur Verarbeitung serverspezifischer Datentypen die Methoden **GetParameterProperties** und **SetParameterProperties** bereit.  
  
> [!NOTE]  
>  Die **ISSCommandWithParameters**-Schnittstelle nutzt auch die neue SSPARAMPROPS-Struktur.  
  
#### <a name="the-icolumnsrowset-interface"></a>Die IDBColumnsRowset-Schnittstelle  
 Neben der **ISSCommandWithParameters**-Schnittstelle fügt der OLE DB-Treiber für SQL Server auch zu dem nach Aufruf der **IColumnsRowset::GetColumnRowset**-Methode zurückgegebenen Rowset neue Werte hinzu, darunter:  
  
|Spaltenname|Typ|und Beschreibung|  
|-----------------|----------|-----------------|  
|DBCOLUMN_SS_UDT_CATALOGNAME|DBTYPE_WSTR|Ein UDT-Katalognamensbezeichner.|  
|DBCOLUMN_SS_UDT_SCHEMANAME|DBTYPE_WSTR|Ein UDT-Schemanamensbezeichner.|  
|DBCOLUMN_SS_UDT_NAME|DBTYPE_WSTR|Ein UDT-Namensbezeichner.|  
|DBCOLUMN_SS_ASSEMBLY_TYPENAME|DBTYPE_WSTR|Der qualifizierte Name der Assembly mit dem Typnamen und allen zur CLR-Referenzierung erforderlichen Angaben zur Assembly-ID.|  
  
 Ist DBCOLUMN_TYPE auf DBTYPE_UDT festgelegt, können Sie eine Server-UDT-Spalte von anderen Binärtypen unterscheiden, indem Sie die hinzugefügten UDT-Metadaten betrachten, die in der vorherigen Tabelle angegeben sind. Sind diese Daten teilweise vollständig, handelt es sich bei dem Servertyp um einen UDT. Für Nicht-UDT-Servertypen werden diese Spalten immer als NULL zurückgegeben.  
 
  
## <a name="see-also"></a>Weitere Informationen  
 [OLE DB-Treiber für SQL Server-Features](../../oledb/features/oledb-driver-for-sql-server-features.md)    
 [ISSCommandWithParameters &#40;OLE-DB&#41;](../../oledb/ole-db-interfaces/isscommandwithparameters-ole-db.md)  
  
  
