---
title: Verwenden von XML-Datentypen | Microsoft-Dokumentation
description: Verwenden von XML-Datentypen im OLE DB-Treiber für SQL Server
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- IRowsetChange interface
- IRowsetUpdate interface
- data access [OLE DB Driver for SQL Server], xml data type
- OLE DB Driver for SQL Server schema rowsets
- PROVIDER_TYPES rowset
- IColumnsInfo interface
- IRowsetFind interface
- IColumnsRowset interface
- PROCEDURE_PARAMETERS rowset
- MSOLEDBSQL, XML
- xml data type [SQL Server], OLE DB Driver for SQL Server
- OLE DB Driver for SQL Server, XML
- IRowset interface
- ISequentialStream interface
- ISSCommandWithParameters interface
- SS_XMLSCHEMA rowset
- OLE DB Driver for SQL Server OLE DB interfaces
- XML [SQL Server], OLE DB Driver for SQL Server
- COLUMNS rowset
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 0d3554363e4813dfb4b3f6cbeefec00214d5a2d6
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67988792"
---
# <a name="using-xml-data-types"></a>Verwenden von XML-Datentypen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  In [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] wurde ein **XML**-Datentyp eingeführt, der das Speichern von XML-Dokumenten und -Fragmenten in einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenbank unterstützt. Der **XML**-Datentyp ist ein integrierter Datentyp in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] und ähnelt in einigen Punkten anderen integrierten Typen wie **int** und **varchar**. Wie andere integrierte Typen können Sie den **XML**-Datentyp beim Erstellen von Tabellen als Variablen-, Parameter- oder Funktionsrückgabespaltentyp oder in CAST- und CONVERT-Funktionen verwenden.  
  
## <a name="programming-considerations"></a>Überlegungen zur Programmierung  
 XML kann selbstbeschreibend sein, da optional ein XML-Header eingefügt werden kann, der die Codierung des Dokuments angibt, zum Beispiel:  
  
 `<?xml version="1.0" encoding="windows-1252"?><doc/>`  
  
 Der XML-Standard beschreibt, wie ein XML-Prozessor die für ein Dokument verwendete Codierung durch Überprüfen der ersten Bytes des Dokuments erkennen kann. Es ist möglich, dass die von der Anwendung festgelegte Codierung einen Konflikt mit der im Dokument angegebenen Codierung auslöst. Für Dokumente, die als gebundene Parameter übergeben werden, wird XML von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] als binäre Daten behandelt, es werden also keine Konvertierungen vorgenommen, und der XML-Parser kann die im Dokument angegebene Codierung problemlos verwenden. Für XML-Daten, die als WSTR gebunden sind, muss die Anwendung jedoch sicherstellen, dass das Dokument in Unicode codiert ist. In diesem Szenario wird das Dokument möglicherweise in ein DOM geladen, die Codierung in Unicode geändert und das Dokument serialisiert. Wenn dieser Schnitt nicht ausgeführt wird, finden eventuell Datenkonvertierungen statt und führen zu ungültigem oder fehlerhaftem XML.  
  
 Konflikte können auch auftreten, wenn XML in Literalen angegeben wird. Folgendes ist beispielsweise ungültig:  
  
 `INSERT INTO xmltable(xmlcol) VALUES('<?xml version="1.0" encoding="UTF-16"?><doc/>')`  
  
 `INSERT INTO xmltable(xmlcol) VALUES(N'<?xml version="1.0" encoding="UTF-8"?><doc/>')`  
  
## <a name="ole-db-driver-for-sql-server"></a>OLE DB-Treiber für SQL Server 
 DBTYPE_XML ist ein neuer Datentyp für XML im OLE DB-Treiber für SQL Server. Zusätzlich können XML-Daten über die vorhandenen OLE DB-Typen DBTYPE_BYTES, DBTYPE_WSTR, DBTYPE_BSTR, DBTYPE_XML, DBTYPE_STR, DBTYPE_VARIANT und DBTYPE_IUNKNOWN aufgerufen werden. Daten, die in XML-Spalten gespeichert wurden, können in einem OLE DB-Treiber für SQL Server-Rowset in den folgenden Formaten aus der Spalte abgerufen werden:  
  
-   Textzeichenfolge  
  
-   **ISequentialStream**  
  
> [!NOTE]  
>  Der OLE DB-Treiber für SQL Server umfasst keinen SAX-Reader, **ISequentialStream** kann jedoch einfach mit MSXML an SAX- und DOM-Objekte übergeben werden.  
  
 **ISequentialStream** sollte zum Abrufen großer XML-Dokumente verwendet werden. Die für andere große Werttypen verwendeten Techniken gelten auch für XML. Weitere Informationen finden Sie im Abschnitt [Verwenden von Datentypen für umfangreiche Werte](../../oledb/features/using-large-value-types.md).  
  
 Daten, die in XML-Spaltentypen in einem Rowset gespeichert sind, können über die bekannten Schnittstellen wie **IRow::GetColumns**, **IRowChange::SetColumns** und **ICommand::Execute** abgerufen, eingefügt oder aktualisiert werden. Ähnlich wie beim Abrufen kann die Anwendung entweder eine Textzeichenfolge oder einen **ISequentialStream** an den OLE DB-Treiber für SQL Server übergeben.  
  
> [!NOTE]  
>  Zum Senden von XML-Daten im Zeichenfolgenformat über die **ISequentialStream**-Schnittstelle müssen Sie **ISequentialStream** durch Angabe von DBTYPE_IUNKNOWN abrufen und das Argument *pObject* in der Bindung auf NULL festlegen.  
  
 Wenn abgerufene XML-Daten abgeschnitten werden, weil der Consumerpuffer zu klein ist, wird die Länge möglicherweise als 0xffffffff zurückgegeben, was heißt, dass die Länge unbekannt ist. Dieses Verhalten ist mit der Implementierung als Datentyp, der als Datenstrom an den Client gesendet wird, ohne Längeninformationen vorab zu senden, konsistent. In einigen Fällen kann die tatsächliche Länge zurückgegeben werden, wenn der Anbieter den gesamten Wert zwischengespeichert hat (z.B. **IRowset::GetData**) und wenn eine Datenkonvertierung durchgeführt wird.  
  
 An SQL Server gesendete XML-Daten werden vom Server als Binärdaten behandelt. Durch dieses Verhalten werden Konvertierungen verhindert, und dem XML-Parser wird ermöglicht, die XML-Codierung automatisch zu erkennen. Dadurch kann ein breiteres Spektrum von XML-Dokumenten (z. B. in UTF-8 codierte Dokumente) als Eingabe für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] akzeptiert werden.  
  
 Wenn die XML-Eingabe als DBTYPE_WSTR gebunden ist, muss die Anwendung sicherstellen, dass sie bereits in Unicode codiert wurde, um mögliche Beschädigungen durch Datenkonvertierung zu verhindern.  
  
### <a name="data-bindings-and-coercions"></a>Datenbindungen und -umwandlungen  
 Die folgende Tabelle veranschaulicht die Bindung und erzwungene Umwandlung bei Verwendung der aufgeführten Datentypen mit dem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datentyp **xml**.  
  
|Datentyp|Zu Server<br /><br /> **XML**|Zu Server<br /><br /> **Nicht-XML**|Von Server<br /><br /> **XML**|Von Server<br /><br /> **Nicht-XML**|  
|---------------|---------------------------|--------------------------------|-----------------------------|----------------------------------|  
|DBTYPE_XML|Pass-Through<sup>6,7</sup>|Fehler<sup>1</sup>|OK<sup>11, 6</sup>|Error<sup>8</sup>|  
|DBTYPE_BYTES|Pass-Through<sup>6,7</sup>|Nicht zutreffend<sup>2</sup>|OK<sup>11, 6</sup>|Nicht zutreffend<sup>2</sup>|  
|DBTYPE_WSTR|Pass-Through<sup>6,10</sup>|Nicht zutreffend<sup>2</sup>|OK<sup>4, 6, 12</sup>|Nicht zutreffend<sup>2</sup>|  
|DBTYPE_BSTR|Pass-Through<sup>6,10</sup>|Nicht zutreffend<sup>2</sup>|OK<sup>3</sup>|Nicht zutreffend<sup>2</sup>|  
|DBTYPE_STR|OK<sup>6, 9, 10</sup>|Nicht zutreffend<sup>2</sup>|OK<sup>5, 6, 12</sup>|Nicht zutreffend<sup>2</sup>|  
|DBTYPE_IUNKNOWN|Bytedatenstrom über **ISequentialStream**<sup>7</sup>|Nicht zutreffend<sup>2</sup>|Bytedatenstrom über **ISequentialStream**<sup>11</sup>|Nicht zutreffend<sup>2</sup>|  
|DBTYPE_VARIANT (VT_UI1 &#124; VT_ARRAY)|Pass-Through<sup>6,7</sup>|Nicht zutreffend<sup>2</sup>|–|Nicht zutreffend<sup>2</sup>|  
|DBTYPE_VARIANT (VT_BSTR)|Pass-Through<sup>6,10</sup>|Nicht zutreffend<sup>2</sup>|OK<sup>3</sup>|Nicht zutreffend<sup>2</sup>|  
  
 <sup>1</sup>Wenn ein anderer Servertyp als DBTYPE_XML mit **ICommandWithParameters::SetParameterInfo** angegeben wird und der Accessortyp DBTYPE_XML ist, tritt beim Ausführen der Anweisung ein Fehler auf (DB_E_ERRORSOCCURRED, der Parameterstatus ist DBSTATUS_E_BADACCESSOR). Andernfalls werden die Daten an den Server gesendet, der Server gibt jedoch einen Fehler zurück und zeigt an, dass keine implizite Konvertierung von XML in den Parameterdatentyp erfolgt.  
  
 <sup>2</sup>Nicht Bestandteil dieses Artikels.  
  
 <sup>3</sup>Format ist UTF-16, keine Bytereihenfolge-Marke (Byte Order Mark, BOM), keine Codierungsspezifikation, keine NULL-Terminierung.  
  
 <sup>4</sup>Format ist UTF-16, keine BOM, keine Codierungsspezifikation, NULL-Terminierung.  
  
 <sup>5</sup>Format enthält Mehrbytezeichen, die auf der Clientcodepage mit NULL-Abschlusszeichen codiert sind. Konvertierung aus vom Server bereitgestelltem Unicode verursacht möglicherweise Datenbeschädigung, daher wird diese Bindung nicht empfohlen.  
  
 <sup>6</sup>BY_REF wird möglicherweise verwendet.  
  
 <sup>7</sup>UTF-16-Daten müssen mit einer BOM starten. Wenn nicht, wird die Codierung möglicherweise nicht ordnungsgemäß vom Server erkannt.  
  
 <sup>8</sup>Überprüfung kann beim Erstellen des Accessors oder beim Abrufen erfolgen. Der Fehler ist DB_E_ERRORSOCCURRED, Bindungsstatus ist auf DBBINDSTATUS_UNSUPPORTEDCONVERSION festgelegt.  
  
 <sup>9</sup>Daten werden über die Clientcodepage in Unicode konvertiert, bevor sie an den Server gesendet werden. Falls die Dokumentcodierung nicht mit der Clientcodepage übereinstimmt, kann es zu Datenbeschädigungen kommen, daher wird diese Bindung nicht empfohlen.  
  
 <sup>10</sup>Zum Server gesendeten Daten wird immer eine BOM hinzugefügt. Falls die Daten bereits mit einer BOM begonnen haben, stehen anschließend zwei BOMs am Beginn des Puffers. Der Server verwendet die erste BOM, um die Codierung als UTF-16 zu erkennen, und verwirft sie dann. Die zweite BOM wird als geschütztes Leerzeichenzeichen mit Nullbreite interpretiert.  
  
 <sup>11</sup>Format ist UTF-16, keine Codierungsspezifikation, zu den vom Server empfangenen Daten wird eine BOM hinzugefügt. Wenn eine leere Zeichenfolge vom Server zurückgegeben wird, wird trotzdem eine BOM an die Anwendung zurückgegeben. Wenn die Pufferlänge eine ungerade Anzahl von Bytes ist, werden die Daten ordnungsgemäß abgeschnitten. Wenn der ganze Wert in Abschnitten zurückgegeben wird, können diese verkettet werden, um wieder den richtigen Wert zusammenzusetzen.  
  
 <sup>12</sup>Falls die Pufferlänge kleiner als zwei Zeichen ist, also nicht genug Platz für eine NULL-Terminierung bietet, wird ein Überlauffehler gemeldet.  
  
> [!NOTE]  
>  Es werden keine Daten für NULL XML-Werte zurückgegeben.  
  
 Der XML-Standard erfordert, dass UTF-16-codiertes XML mit einer Bytereihenfolge-Marke (BOM), UTF-16-Zeichencode 0xFEFF beginnt. Wenn Sie mit WSTR- und BSTR-Bindungen arbeiten, benötigt der OLE DB-Treiber für SQL Server keine BOM, da die Codierung durch die Bindung impliziert ist. Bei der Verwendung von BYTES-, XML- oder IUNKNOWN-Bindungen liegt das Hauptaugenmerk auf der einfachen Zusammenarbeit mit anderen XML-Prozessoren und Speichersystemen. In diesem Fall sollte für UTF-16-codiertes XML eine BOM vorhanden sein, und die Anwendung sollte sich nicht um die eigentliche Codierung kümmern, da die Mehrheit der XML-Prozessoren (einschließlich SQL Server) die Codierung nach Überprüfen des ersten Bytes des Wertes ableitet. XML-Daten, die vom OLE DB-Treiber für SQL Server unter Verwendung von BYTES-, XML- oder IUNKNOWN-Bindungen empfangen werden, sind immer in UTF-16 mit einer BOM und ohne eingebettete Codierungsdeklaration codiert.  
  
 Datenkonvertierungen durch OLE DB-Basisdienste (**IDataConvert**) sind nicht auf DBTYPE_XML anwendbar.  
  
 Die Überprüfung erfolgt, wenn Daten an den Server gesendet werden. Die clientseitige Validierung und Codierungsänderungen müssen von Ihrer Anwendung verarbeitet werden. Es wird empfohlen, die XML-Daten nicht direkt zu verarbeiten, sondern einen DOM oder SAX-Reader zu verwenden.  
  
 DBTYPE_NULL und DBTYPE_EMPTY können für Eingabeparameter gebunden werden, aber nicht für Ausgabeparameter oder Ergebnisse. Ist der Status für Eingabeparameter gebunden, muss er auf DBSTATUS_S_ISNULL oder DBSTATUS_S_DEFAULT festgelegt werden.  
  
 DBTYPE_XML kann in DBTYPE_EMPTY und DBTYPE_NULL konvertiert werden, DBTYPE_EMPTY in DBTYPE_XML, aber DBTYPE_NULL kann nicht in DBTYPE_XML konvertiert werden. Dies stimmt mit DBTYPE_WSTR überein.  
  
 DBTYPE_IUNKNOWN ist eine unterstützte Bindung (wie in der vorherigen Tabelle gezeigt), aber es gibt keine Konvertierungen zwischen DBTYPE_XML und DBTYPE_IUNKNOWN. DBTYPE_IUNKNOWN kann nicht mit DBTYPE_BYREF verwendet werden.  
  
### <a name="ole-db-rowset-additions-and-changes"></a>Hinzufügungen und Änderungen am OLE DB-Rowset  
 Der OLE DB-Treiber für SQL Server fügt vielen der wichtigsten OLE DB-Schemarowsets neue Werte oder Änderungen hinzu.  
  
#### <a name="the-columns-and-procedure_parameters-schema-rowsets"></a>Die COLUMNS- und PROCEDURE_PARAMETERS-Schemarowsets  
 Den COLUMNS- und PROCEDURE_PARAMETERS-Schemarowsets wurden unter anderem die folgenden Spalten hinzugefügt:  
  
|Spaltenname|type|Beschreibung|  
|-----------------|----------|-----------------|  
|SS_XML_SCHEMACOLLECTION_CATALOGNAME|DBTYPE_WSTR|Der Name des Katalogs, in dem eine XML-Schemaauflistung definiert ist. NULL für eine Nicht-XML-Spalte oder nicht typisierte XML-Spalte.|  
|SS_XML_SCHEMACOLLECTION_SCHEMANAME|DBTYPE_WSTR|Der Name eines Schemas, in dem eine XML-Schemaauflistung definiert ist. NULL für eine Nicht-XML-Spalte oder nicht typisierte XML-Spalte.|  
|SS_XML_SCHEMACOLLECTIONNAME|DBTYPE_WSTR|Der Name der XML-Schemaauflistung. NULL für eine Nicht-XML-Spalte oder nicht typisierte XML-Spalte.|  
  
#### <a name="the-provider_types-schema-rowset"></a>Das PROVIDER_TYPES-Schemarowset  
 Im PROVIDER_TYPES-Schemarowset ist der COLUMN_SIZE-Wert für den **XML**-Datentyp 0, und DATA_TYPE ist DBTYPE_XML.  
  
#### <a name="the-ss_xmlschema-schema-rowset"></a>Das SS_XMLSCHEMA-Schemarowset  
 Ein neues Schemarowset SS_XMLSCHEMA wird eingeführt, mit dem Clients XML-Schema-Informationen abrufen können. Das SS_XMLSCHEMA-Rowset enthält folgende Spalten:  
  
|Spaltenname|type|Beschreibung|  
|-----------------|----------|-----------------|  
|SCHEMACOLLECTION_CATALOGNAME|DBTYPE_WSTR|Der Katalog, zu dem eine XML-Auflistung gehört.|  
|SCHEMACOLLECTION_SCHEMANAME|DBTYPE_WSTR|Das Schema, zu dem eine XML-Auflistung gehört.|  
|SCHEMACOLLECTIONNAME|DBTYPE_WSTR|Der Name einer XML-Schemaauflistung für typisierte XML-Spalten, andernfalls NULL.|  
|TARGETNAMESPACEURI|DBTYPE_WSTR|Der Zielnamespace eines XML-Schemas.|  
|SCHEMACONTENT|DBTYPE_WSTR|Der Inhalt der XML-Schemas.|  
  
 Jedes XML-Schema wird nach Katalogname, Schemaname, Schemaauflistung und Zielnamespace-URI (Uniform Resource Identifier) einem Bereich zugeordnet. Außerdem wird eine neue GUID mit dem Namen DBSCHEMA_XML_COLLECTIONS definiert. Die Anzahl von Einschränkungen und eingeschränkten Spalten für das SS_XMLSCHEMA-Schemarowset wird wie folgt definiert.  
  
|GUID|Anzahl der Einschränkungen|Eingeschränkte Spalten|  
|----------|----------------------------|------------------------|  
|DBSCHEMA_XML_COLLECTIONS|4|SCHEMACOLLECTION_CATALOGNAME<br /><br /> SCHEMACOLLECTION_SCHEMANAME<br /><br /> SCHEMACOLLECTIONNAME<br /><br /> TARGETNAMESPACEURI|  
  
### <a name="ole-db-property-set-additions-and-changes"></a>Hinzufügungen und Änderungen an der OLE DB-Eigenschaftengruppe  
 Der OLE DB-Treiber für SQL Server fügt vielen der wichtigsten OLE DB-Eigenschaftensätze neue Werte oder Änderungen hinzu.  
  
#### <a name="the-dbpropset_sqlserverparameter-property-set"></a>Die DBPROPSET_SQLSERVERPARAMETER-Eigenschaftengruppe  
 Um den **XML**-Datentyp über OLE DB zu unterstützen, implementiert der OLE DB-Treiber für SQL Server die neue DBPROPSET_SQLSERVERPARAMETER-Eigenschaftengruppe mit folgenden Werten.  
  
|Name|type|Beschreibung|  
|----------|----------|-----------------|  
|SSPROP_PARAM_XML_SCHEMACOLLECTION_CATALOGNAME|DBTYPE_WSTR|Der Name des Katalogs (Datenbank), in dem eine XML-Schemaauflistung definiert ist. Teil des dreiteiligen SQL-Namensbezeichners.|  
|SSPROP_PARAM_XML_SCHEMACOLLECTION_SCHEMANAME|DBTYPE_WSTR|Der Name eines XML-Schemas in der Schemaauflistung. Teil des dreiteiligen SQL-Namensbezeichners.|  
|SSPROP_PARAM_XML_SCHEMACOLLECTIONNAME|DBTYPE_WSTR|Der Name der XML-Schemaauflistung im Katalogteil A des dreiteiligen SQL-Namensbezeichners.|  
  
#### <a name="the-dbpropset_sqlservercolumn-property-set"></a>Die DBPROPSET_SQLSERVERCOLUMN-Eigenschaftengruppe  
 Um die Tabellenerstellung in der **ITableDefinition**-Schnittstelle zu unterstützen, fügt der OLE DB-Treiber für SQL Server zur DBPROPSET_SQLSERVERCOLUMN-Eigenschaftengruppe drei neue Spalten hinzu.  
  
|Name|type|Beschreibung|  
|----------|----------|-----------------|  
|SSPROP_COL_XML_SCHEMACOLLECTION_CATALOGNAME|VT_BSTR|Bei typisierten XML-Spalten ist diese Eigenschaft eine Zeichenfolge, die den Namen des Katalogs angibt, in dem das XML-Schema gespeichert ist. Für andere Spaltentypen gibt diese Eigenschaft eine leere Zeichenfolge zurück.|  
|SSPROP_COL_XML_SCHEMACOLLECTION_SCHEMANAME|VT_BSTR|Bei typisierten XML-Spalten ist diese Eigenschaft eine Zeichenfolge, die den Namen des XML-Schemas angibt, das diese Spalte definiert.|  
|SSPROP_COL_XML_SCHEMACOLLECTIONNAME|VT_BSTR|Bei typisierten XML-Spalten ist diese Eigenschaft eine Zeichenfolge, die den Namen der XML-Schemaauflistung angibt, die den Wert definiert.|  
  
 Wie die SSPROP_PARAM-Werte sind all diese Eigenschaften optional und standardmäßig leer. SSPROP_COL_XML_SCHEMACOLLECTION_CATALOGNAME und SSPROP_COL_XML_SCHEMACOLLECTION_SCHEMANAME können nur angegeben werden, wenn SSPROP_COL_XML_SCHEMACOLLECTIONNAME angegeben ist. Bei der Übergabe von XML an den Server werden diese Werte (falls vorhanden) auf ihr Vorhandensein in der aktuellen Datenbank überprüft, und die Instanzdaten werden mit dem Schema verglichen. In jedem Fall müssen sie entweder alle leer oder alle ausgefüllt sein, um gültig zu sein.  
  
### <a name="ole-db-interface-additions-and-changes"></a>Hinzufügungen und Änderungen an der OLE DB-Schnittstelle  
 Der OLE DB-Treiber für SQL Server fügt vielen der wichtigsten OLE DB-Schnittstellen neue Werte oder Änderungen hinzu.  
  
#### <a name="the-isscommandwithparameters-interface"></a>Die ISSCommandWithParameters-Schnittstelle  
 Um den **XML**-Datentyp durch OLE DB zu unterstützen, implementiert der OLE DB-Treiber für SQL Server eine Reihe von Änderungen, darunter die neue [ISSCommandWithParameters](../../oledb/ole-db-interfaces/isscommandwithparameters-ole-db.md)-Schnittstelle. Diese neue Schnittstelle erbt von der OLE DB-Kernschnittstelle **ICommandWithParameters**. Zusätzlich zu den drei von **ICommandWithParameters** geerbten Methoden (**GetParameterInfo**, **MapParameterNames** und **SetParameterInfo**) stellt **ISSCommandWithParameters** zur Verarbeitung serverspezifischer Datentypen die Methoden [GetParameterProperties](../../oledb/ole-db-interfaces/isscommandwithparameters-getparameterproperties-ole-db.md) und [SetParameterProperties](../../oledb/ole-db-interfaces/isscommandwithparameters-setparameterproperties-ole-db.md) bereit.  
  
> [!NOTE]  
>  Die **ISSCommandWithParameters**-Schnittstelle nutzt auch die neue SSPARAMPROPS-Struktur.  
  
#### <a name="the-icolumnsrowset-interface"></a>Die IDBColumnsRowset-Schnittstelle  
 Der OLE DB-Treiber für SQL Server fügt die folgenden [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-spezifischen Spalten zu dem von der **IColumnRowset::GetColumnsRowset**-Methode zurückgegebenen Rowset hinzu. Diese Spalten enthalten den dreiteiligen Namen einer XML-Schemaauflistung. Für Nicht-XML-Spalten oder nicht typisierte XML-Spalten nehmen alle drei Spalten den Standardwert von NULL an.  
  
|Spaltenname|type|Beschreibung|  
|-----------------|----------|-----------------|  
|DBCOLUMN_SS_XML_SCHEMACOLLECTION_CATALOGNAME|DBTYPE_WSTR|Der Katalog, zu dem eine XML-Schemaauflistung gehört.<br /><br /> Andernfalls NULL.|  
|DBCOLUMN_SS_XML_SCHEMACOLLECTION_SCHEMANAME|DBTYPE_WSTR|Das Schema, zu dem eine XML-Schemaauflistung gehört. Andernfalls NULL.|  
|DBCOLUMN_SS_XML_SCHEMACOLLECTIONNAME|DBTYPE_WSTR|Der Name einer XML-Schemaauflistung für typisierte XML-Spalten, andernfalls NULL.|  
  
#### <a name="the-irowset-interface"></a>Die IRowset-Schnittstelle  
 Eine XML-Instanz in einer XML-Spalte wird über die **IRowset::GetData**-Methode abgerufen. Je nach Bindung, die vom Client angegeben ist, kann eine XML-Instanz als DBTYPE_BSTR, DBTYPE_WSTR, DBTYPE_VARIANT, DBTYPE_XML, DBTYPE_STR, DBTYPE_BYTES oder als Schnittstelle über DBTYPE_IUNKNOWN abgerufen werden. Falls der Consumer DBTYPE_BSTR, DBTYPE_WSTR oder DBTYPE_VARIANT angibt, konvertiert der Anbieter die XML-Instanz in den vom Benutzer angeforderten Typ und legt ihn an dem in der zugehörigen Bindung angegebenen Speicherort ab.  
  
 Falls der Consumer DBTYPE_IUNKNOWN angibt und das *pObject*-Argument auf NULL oder das *pObject*-Argument auf IID_IsequentialStream festlegt, gibt der Anbieter eine **ISequentialStream**-Schnittstelle an den Consumer zurück, damit er den XML-Datenstrom aus der Spalte übertragen kann. **ISequentialStream** gibt die XML-Daten anschließend als Unicode-Zeichendatenstrom zurück.  
  
 Wenn ein an DBTYPE_IUNKNOWN gebundener XML-Wert zurückgegeben wird, meldet der Anbieter einen Größenwert von `sizeof (IUnknown *)`. Dieses Verhalten stimmt mit der Vorgehensweise für Spalten überein, die als DBTYPE_IUnknown oder DBTYPE_IDISPATCH gebunden sind, sowie für DBTYPE_IUNKNOWN/ISequentialStream, wenn die genaue Spaltengröße nicht bestimmt werden kann.  
  
#### <a name="the-irowsetchange-interface"></a>Die IRowsetChange-Schnittstelle  
 Es gibt zwei Methoden, wie ein Consumer eine XML-Instanz in einer Spalte aktualisieren kann. Die erste Methode erfolgt durch das vom Anbieter erstellte Speicherobjekt **ISequentialStream**. Der Consumer kann die **ISequentialStream::Write**-Methode aufrufen, um die vom Anbieter zurückgegebene XML-Instanz direkt zu aktualisieren.  
  
 Der zweite Ansatz ist die **IRowsetChange::SetData**-Methode oder **IRowsetChange::InsertRow**-Methode. Bei dieser Vorgehensweise kann eine XML-Instanz im Consumerpuffer in einer Bindung vom Typ DBTYPE_BSTR, DBTYPE_WSTR, DBTYPE_VARIANT, DBTYPE_XML oder DBTYPE_IUNKNOWN angegeben werden.  
  
 Wenn DBTYPE_BSTR, DBTYPE_WSTR oder DBTYPE_VARIANT angegeben ist, speichert der Anbieter die XML-Instanz, die sich im Consumerpuffer befindet, in der entsprechenden Spalte.  
  
 Wenn DBTYPE_IUNKNOWN/IsequentialStream angegeben ist, muss der Consumer, falls er kein Speicherobjekt angibt, vorher ein **ISequentialStream**-Objekt erstellen, das XML-Dokument an das Objekt binden und das Objekt anschließend mit der **IRowsetChange::SetData**-Methode an den Anbieter übergeben. Der Consumer kann auch ein Speicherobjekt erstellen, das pObject-Argument auf IID_ISequentialStream festlegen, ein **ISequentialStream**-Objekt erstellen und anschließend das **ISequentialStream**-Objekt an die **IRowsetChange::SetData**-Methode übergeben. In beiden Fällen kann der Anbieter das XML-Objekt über das **ISequentialStream**-Objekt abrufen und es in die entsprechende Spalte einfügen.  
  
#### <a name="the-irowsetupdate-interface"></a>Die IRowsetUpdate-Schnittstelle  
 Die **IRowsetUpdate**-Schnittstelle stellt die Funktionen für verzögerte Updates bereit. Die Daten, die in den Rowsets zur Verfügung gestellt wurden, sind erst dann für andere Transaktionen verfügbar, wenn der Consumer die **IRowsetUpdate::Update**-Methode aufruft.  
  
#### <a name="the-irowsetfind-interface"></a>Die IRowsetFind-Schnittstelle  
 Die **IRowsetFind::FindNextRow**-Methode funktioniert nicht mit dem **XML**-Datentyp. Wenn **IRowsetFind::FindNextRow** aufgerufen wird und das *hAccessor*-Argument eine Spalte von DBTYPE_XML angibt, wird DB_E_BADBINDINFO zurückgegeben. Dies tritt unabhängig vom Typ der Spalte auf, die durchsucht wird. Für alle anderen Bindungstypen schlägt **FindNextRow** mit DB_E_BADCOMPAREOP fehl, wenn die zu durchsuchende Spalte vom Datentyp **XML** ist.  
 
  
## <a name="see-also"></a>Weitere Informationen  
 [OLE DB-Treiber für SQL Server-Features](../../oledb/features/oledb-driver-for-sql-server-features.md)    
 [ISSCommandWithParameters &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/isscommandwithparameters-ole-db.md)  
  
  
