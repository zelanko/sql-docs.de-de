---
description: Große benutzerdefinierte CLR-Typen in SQL Server Native Client (OLE DB)
title: Große CLR-benutzerdefinierte Typen (OLE DB) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- large CLR user-defined types [OLE DB]
ms.assetid: 4bf12058-0534-42ca-a5ba-b1c23b24d90f
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b5342dcab8dee628f074963a7ddc56a0ecc1d940
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88328286"
---
# <a name="large-clr-user-defined-types-in-sql-server-native-client-ole-db"></a>Große benutzerdefinierte CLR-Typen in SQL Server Native Client (OLE DB)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  In diesem Abschnitt werden Änderungen an OLE DB in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client erläutert, durch die große benutzerdefinierte Common Language Runtime-Typen (CLR-UDTs) unterstützt werden.  
  
 Weitere Informationen zur Unterstützung großer CLR-UDTs in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client finden Sie unter [große CLR-benutzerdefinierte Typen](../../../relational-databases/native-client/features/large-clr-user-defined-types.md). Ein Beispiel finden Sie unter [Große CLR-benutzerdefinierte Typen &#40;OLE DB&#41;](../../../relational-databases/native-client-ole-db-how-to/use-large-clr-udts-ole-db.md).  
  
## <a name="data-format"></a>Datenformat  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client verwendet ~0 zur Darstellung der Länge von Werten, die für große Objekttypen (Large Object Types, LOB) keine Größenbeschränkung aufweisen. ~0 stellt auch die Größe von CLR-UDTs dar, die größer als 8.000 Byte sind.  
  
 In der folgenden Tabelle wird die Datentypzuordnung in Parametern und Rowsets dargestellt:  
  
|SQL Server-Datentyp|OLE DB-Datentyp|Speicherlayout|value|  
|--------------------------|----------------------|-------------------|-----------|  
|CLR-UDT|DBTYPE_UDT|BYTE[]\(Bytearray)\)|132 (oledb.h)|  
  
 UDT-Werte werden als Bytearrays dargestellt. Konvertierungen zu und von hexadezimalen Zeichenfolgen werden unterstützt. Literalwerte werden mit dem Präfix 0x als hexadezimale Zeichenfolgen dargestellt. Eine Hexadezimalzeichenfolge ist die Textdarstellung der Binärdaten zur Basis 16. Ein Beispiel dafür ist eine Konvertierung vom Servertyp **varbinary(10)** in DBTYPE_STR, die zu einer hexadezimalen Darstellung von 20 Zeichen führt, wobei jedes Zeichenpaar ein einzelnes Byte repräsentiert.  
  
## <a name="parameter-properties"></a>Parametereigenschaften  
 Der DBPROPSET_SQLSERVERPARAMETER-Eigenschaftensatz unterstützt UDTs durch OLE DB. Weitere Informationen finden Sie unter [Verwenden von benutzerdefinierten Typen](~/relational-databases/native-client/features/using-user-defined-types.md).  
  
## <a name="column-properties"></a>Spalteneigenschaften  
 Der DBPROPSET_SQLSERVERCOLUMN-Eigenschaftensatz unterstützt die Erstellung von Tabellen durch OLE DB. Weitere Informationen finden Sie unter [Verwenden von benutzerdefinierten Typen](~/relational-databases/native-client/features/using-user-defined-types.md).  
  
## <a name="data-type-mapping-in-itabledefinitioncreatetable"></a>Datentypzuordnung zu ITableDefinition::CreateTable  
 Die folgenden Informationen werden von **DBCOLUMNDESC**-Strukturen verwendet, die von ITableDefinition::CreateTable verwendet werden, wenn UDT-Spalten erforderlich sind:  
  
|OLE DB-Datentyp (*wType*)|*pwszTypeName*|SQL Server-Datentyp|*rgPropertySets*|  
|----------------------------------|--------------------|--------------------------|----------------------|  
|DBTYPE_UDT|Wird ignoriert.|UDT|Muss einen DBPROPSET_SQLSERVERCOLUMN-Eigenschaftensatz einschließen.|  
  
## <a name="icommandwithparametersgetparameterinfo"></a>ICommandWithParameters::GetParameterInfo  
 Die folgenden Informationen werden in der DBPARAMINFO-Struktur durch **prgParamInfo** zurückgegeben:  
  
|Parametertyp|*wType*|*ulParamSize*|*bPrecision*|*bScale*|*dwFlags* DBPARAMFLAGS_ISLONG|  
|--------------------|-------------|-------------------|------------------|--------------|------------------------------------|  
|DBTYPE_UDT<br /><br /> (Länge kleiner oder gleich 8.000 Bytes)|"DBTYPE_UDT"|*n*|nicht definiert|nicht definiert|clear|  
|DBTYPE_UDT<br /><br /> (Länge größer als 8.000 Bytes)|"DBTYPE_UDT"|~0|nicht definiert|nicht definiert|set|  
  
## <a name="icommandwithparameterssetparameterinfo"></a>ICommandWithParameters::SetParameterInfo  
 Die in der DBPARAMBINDINFO-Struktur bereitgestellten Informationen müssen Folgendem entsprechen:  
  
|Parametertyp|*pwszDataSourceType*|*ulParamSize*|*bPrecision*|*bScale*|*dwFlags* DBPARAMFLAGS_ISLONG|  
|--------------------|--------------------------|-------------------|------------------|--------------|------------------------------------|  
|DBTYPE_UDT<br /><br /> (Länge kleiner oder gleich 8.000 Bytes)|DBTYPE_UDT|*n*|wird ignoriert.|wird ignoriert.|Muss festgelegt werden, wenn der Parameter mit DBTYPE_IUNKNOWN übergeben werden soll.|  
|DBTYPE_UDT<br /><br /> (Länge größer als 8.000 Bytes)|DBTYPE_UDT|~0|wird ignoriert.|wird ignoriert.|wird ignoriert.|  
  
## <a name="isscommandwithparameters"></a>ISSCommandWithParameters  
 Anwendungen verwenden **ISSCommandWithParameters**, um die im Abschnitt „Parametereigenschaften“ definierten Parametereigenschaften abzurufen und festzulegen.  
  
## <a name="icolumnsrowsetgetcolumnsrowset"></a>IColumnsRowset::GetColumnsRowset  
 Die folgenden Spalten werden zurückgegeben:  
  
|Spaltentyp|DBCOLUMN_TYPE|DBCOLUMN_COLUMNSIZE|DBCOLUMN_PRECISION|DBCOLUMN_SCALE|DBCOLUMN_FLAGS_ISLONG|DBCOLUMNS_ISSEARCHABLE|DBCOLUMN_OCTETLENGTH|  
|-----------------|--------------------|--------------------------|-------------------------|---------------------|-----------------------------|-----------------------------|---------------------------|  
|DBTYPE_UDT<br /><br /> (Länge kleiner oder gleich 8.000 Bytes)|DBTYPE_UDT|*n*|NULL|NULL|Löschen|DB_ALL_EXCEPT_LIKE|n|  
|DBTYPE_UDT<br /><br /> (Länge größer als 8.000 Bytes)|DBTYPE_UDT|~0|NULL|NULL|Set|DB_ALL_EXCEPT_LIKE|0|  
  
 Die folgenden Spalten werden ebenfalls für UDTs definiert:  
  
|Spalten-ID|type|BESCHREIBUNG|  
|-----------------------|----------|-----------------|  
|DBCOLUMN_UDT_CATALOGNAME|DBTYPE_WSTR|Für UDT-Spalten der Name des Katalogs, in dem der UDT definiert ist.|  
|DBCOLUMN_UDT_SCHEMANAME|DBTYPE_WSTR|Für UDT-Spalten der Name des Schemas, in dem der UDT definiert ist.|  
|DBCOLUMN_UDT_NAME|DBTYPE_WSTR|Für UDT-Spalten der einteilige Name des UDT.|  
|DBCOLUMN_ASSEMBLY_TYPENAME|DBTYPE_WSTR|Für UDT-Spalten der vollständige Typname des UDT. Mit dem vollqualifizierten Namen des Assemblytyps können Sie ein Objekt dieses Typs mit der Type.GetType-Methode instanziieren.|  
  
## <a name="icolumnsinfogetcolumninfo"></a>IColumnsInfo::GetColumnInfo  
 Die in der DBCOLUMNINFO-Struktur zurückgegebenen Informationen lauten wie folgt:  
  
|Parametertyp|*wType*|*ulColumnSize*|*bPrecision*|*bScale*|*dwFlags*<br /><br /> DBCOLUMNFLAGS_ISLONG|  
|--------------------|-------------|--------------------|------------------|--------------|-----------------------------------------|  
|DBTYPE_UDT<br /><br /> (Länge kleiner oder gleich 8.000 Bytes)|DBTYPE_UDT|*n*|~0|~0|Löschen|  
|DBTYPE_UDT<br /><br /> (Länge größer als 8.000 Bytes)|DBTYPE_UDT|~0|~0|~0|Set|  
  
## <a name="columns-rowset-schema-rowsets"></a>COLUMNS-Rowset (Schemarowsets)  
 Die folgenden Spaltenwerte werden für UDT-Typen zurückgegeben:  
  
|Spaltentyp|DATA_TYPE|COLUMN_FLAGS, DBCOLUMFLAGS_ISLONG|CHARACTER_OCTET_LENGTH|  
|-----------------|----------------|-----------------------------------------|------------------------------|  
|DBTYPE_UDT<br /><br /> (Länge kleiner oder gleich 8.000 Bytes)|DBTYPE_UDT|Löschen|*n*|  
|DBTYPE_UDT<br /><br /> (Länge größer als 8.000 Bytes)|DBTYPE_UDT|Set|0|  
  
 Die folgenden zusätzlichen Spalten werden für UDTs definiert:  
  
|Spaltenbezeichner|type|BESCHREIBUNG|  
|-----------------------|----------|-----------------|  
|SS_UDT_CATALOGNAME|DBTYPE_WSTR|Für UDT-Spalten der Name des Katalogs, in dem der UDT definiert ist.|  
|SS_UDT_SCHEMANAME|DBTYPE_WSTR|Für UDT-Spalten der Name des Schemas, in dem der UDT definiert ist.|  
|SS_UDT_NAME|DBTYPE_WSTR|Für UDT-Spalten der einteilige Name des UDT.|  
|SS_ASSEMBLY_TYPENAME|DBTYPE_WSTR|Für UDT-Spalten ist dies der vollständige Typname des UDT. Mit dem vollqualifizierten Namen des Assemblytyps können Sie ein Objekt dieses Typs mit der Type.GetType-Methode instanziieren.|  
  
 Im Hinblick auf das PROCEDURE_PARAMETERS-Rowset enthält DATA_TYPE die gleichen Werte wie das COLUMNS-Schemarowset, und TYPE_NAME enthält den UDT. Es werden die gleichen zusätzlichen Spalten definiert.  
  
 UDTs werden nicht im PROVIDER_TYPES-Schemarowset angezeigt.  
  
## <a name="bindings-and-conversions"></a>Bindungen und Konvertierungen  
  
|Binding-Datentyp|UDT zu Server|Nicht-UDT zu Server|UDT von Server|Nicht-UDT von Server|  
|----------------------|-------------------|------------------------|---------------------|--------------------------|  
|DBTYPE_UDT|Unterstützt (5)|Fehler (1)|Unterstützt (5)|Fehler (4)|  
|DBTYPE_BYTES|Unterstützt (5)|–|Unterstützt (5)|–|  
|DBTYPE_WSTR|Unterstützt (2), (5)|–|Unterstützt (3), (5), (6)|–|  
|DBTYPE_BSTR|Unterstützt (2), (5)|–|Unterstützt (3), (5)|–|  
|DBTYPE_STR|Unterstützt (2), (5)|–|Unterstützt (3), (5)|–|  
|DBTYPE_IUNKNOWN|Unterstützt (6)|–|Unterstützt (6)|–|  
|DBTYPE_VARIANT (VT_UI1 &#124; VT_ARRAY)|Unterstützt (5)|–|Unterstützt (3), (5)|–|  
|DBTYPE_VARIANT (VT_BSTR)|Unterstützt (2), (5)|–|–|–|  
  
### <a name="key-to-symbols"></a>Aufschlüsselung der Symbole  
  
|Symbol|Bedeutung|  
|------------|-------------|  
|1|Wird ein anderer Servertyp als DBTYPE_UDT mit **ICommandWithParameters::SetParameterInfo** angegeben, und ist der Accessortyp DBTYPE_UDT, tritt bei Ausführung der Anweisung ein Fehler auf.  Der Fehler lautet DB_E_ERRORSOCCURRED, und der Parameterstatus lautet DBSTATUS_E_BADACCESSOR.<br /><br /> Es tritt ein Fehler auf, wenn ein Parameter des Typs UDT für einen Serverparameter angegeben wird, bei dem es sich nicht um einen UDT handelt.|  
|2|Daten werden von einer hexadezimalen Zeichenfolge in binäre Daten konvertiert.|  
|3|Daten werden von binären Daten in eine hexadezimale Zeichenfolge konvertiert.|  
|4|Beim Verwenden von **CreateAccessor** oder **GetNextRows** kann eine Überprüfung stattfinden. Der Fehler lautet DB_E_ERRORSOCCURRED. Der Bindungsstatus wird auf DBBINDSTATUS_UNSUPPORTEDCONVERSION festgelegt.|  
|5|BY_REF kann verwendet werden.|  
|6|UDT-Parameter können als DBTYPE_IUNKNOWN im DBBINDING gebunden werden. Durch das Binden an DBTYPE_IUNKNOWN wird angezeigt, dass die Daten von der Anwendung mit der ISequentialStream-Schnittstelle als Stream verarbeitet werden sollen. Wenn ein Consumer *wType* in einer Bindung als Typ DBTYPE_IUNKNOWN angibt und der entsprechende Spalten-oder Ausgabeparameter der gespeicherten Prozedur ein UDT ist, wird von SQL Server Native Client ISequentialStream zurückgegeben. Bei einem Eingabeparameter wird von SQL Server Native Client der für die ISequentialStream-Schnittstelle abgefragt.<br /><br /> Sie können auswählen, ob die Länge der UDT-Daten bei Verwendung der DBTYPE_IUNKNOWN-Bindung im Falle großer UDTs gebunden werden soll. Die Länge muss für kleine UDTs jedoch gebunden sein. Ein DBTYPE_UDT-Parameter kann als großer UDT angegeben werden, wenn mindestens eine der folgenden Bedingungen zutrifft:<br />*ulParamParamSize* entspricht ~0.<br />DBPARAMFLAGS_ISLONG ist in der DBPARAMBINDINFO-Struktur festgelegt.<br /><br /> Für Zeilendaten ist die DBTYPE_IUNKNOWN-Bindung nur für große UDTs zulässig. Mit der IColumnsInfo::GetColumnInfo-Methode in einem Rowset oder der IColumnsInfo-Schnittstelle eines Befehlsobjekts können Sie ermitteln, ob eine Spalte einen großen benutzerdefinierten Typ aufweist. Eine DBTYPE_UDT-Spalte ist eine große UDT-Spalte, wenn mindestens eine der folgenden Bedingungen zutrifft:<br />Das DBCOLUMNFLAGS_ISLONG-Flag ist auf das Element *dwFlags* der DBCOLUMNINFO-Struktur festgelegt. <br />Das *ulColumnSize*-Element von DBCOLUMNINFO entspricht ~ 0.|  
  
 DBTYPE_NULL und DBTYPE_EMPTY können für Eingabeparameter gebunden werden, jedoch nicht für Ausgabeparameter oder Ergebnisse. Ist der Status für Eingabeparameter gebunden, muss er auf DBSTATUS_S_ISNULL für DBTYPE_NUL oder DBSTATUS_S_DEFAULT für DBTYPE_EMPTY festgelegt werden. DBTYPE_BYREF kann nicht mit DBTYPE_NULL oder DBTYPE_EMPTY verwendet werden.  
  
 DBTYPE_UDT kann auch in DBTYPE_EMPTY und DBTYPE_NULL konvertiert werden. DBTYPE_NULL und DBTYPE_EMPTY können jedoch nicht in DBTYPE_UDT konvertiert werden. Dies stimmt mit DBTYPE_BYTES überein. **ISSCommandWithParameters** wird verwendet, um UDTs als Parameter zu verarbeiten.  
  
 Datenkonvertierungen durch OLE DB-Basisdienste (**IDataConvert**) sind nicht auf DBTYPE_UDT anwendbar.  
  
 Es werden keine weiteren Bindungen unterstützt.  
  
## <a name="comparability-for-irowsetfind"></a>Vergleichbarkeit für 'IRowsetFind'  
 Für UDT-Typen werden lediglich die folgenden Vergleiche unterstützt:  
  
-   EQ  
  
-   NE  
  
-   IGNORE  
  
 Beim Versuch eines anderen Vergleichs wird DB_E_BADCOMPAREOP zurückgegeben.  
  
## <a name="bcp-support-for-udts"></a>BCP-Unterstützung für UDTs  
 UDT-Werte können nur als Zeichen oder Binärwerte importiert und exportiert werden.  
  
## <a name="down-level-client-behavior-for-udts"></a>Verhalten von Downlevelclients für UDTs  
 Für UDTs gilt die folgende Typzuordnung zu Clients der unteren Ebene:  
  
|Clientversion|DBTYPE_UDT<br /><br /> (Länge kleiner oder gleich 8.000 Bytes)|DBTYPE_UDT<br /><br /> (Länge größer als 8.000 Bytes)|  
|--------------------|------------------------------------------------------------------|---------------------------------------------------------|  
|SQL Server 2005|UDT|varbinary(max)|  
|SQL Server 2008 und höher|UDT|UDT|  
  
 Wenn **DataTypeCompatibility** (SSPROP_INIT_DATATYPECOMPATIBILITY) auf „80“ festgelegt ist, werden UDT-Typen für Clients ebenso angezeigt wie für Downlevelclients.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Große benutzerdefinierte CLR-Typen](~/relational-databases/native-client/features/large-clr-user-defined-types.md)  
  
  

