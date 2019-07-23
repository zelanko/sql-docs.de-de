---
title: Verwenden von ADO mit dem OLE DB-Treiber für SQL Server | Microsoft-Dokumentation
description: Verwenden von ADO mit dem OLE DB-Treiber für SQL Server
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, ADO
- data access [OLE DB Driver for SQL Server], ADO
- ADO [OLE DB Driver for SQL Server]
- MSOLEDBSQL, ADO
author: pmasl
ms.author: pelopes
ms.openlocfilehash: b7e8ab700404aee32140bc935443e5911e4a56db
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67989241"
---
# <a name="using-ado-with-ole-db-driver-for-sql-server"></a>Verwenden von ADO mit dem OLE DB-Treiber für SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Um die neuen Funktionen von [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], beispielsweise mehrere aktive Resultsets (MARS), Abfragebenachrichtigungen, benutzerdefinierte Typen (User-Defined Types, UDTs) oder den neuen Datentyp **XML** verwenden zu können, sollten bestehende Anwendungen, die ADO (ActiveX Data Objects) verwenden, den OLE DB-Anbieter von OLE DB-Treiber für SQL Server als Datenzugriffsanbieter nutzen.  
  
 Damit ADO die neuen Funktionen der letzten Versionen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verwenden kann, wurde der OLE DB-Treiber für SQL Server, der die Kernfunktionen von OLE DB erweitert, um einige Erweiterungen ergänzt. Diese Erweiterungen erlauben es ADO-Anwendungen, neuere [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Features zu verwenden und zwei Datentypen zu verarbeiten, die in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] eingeführt wurden: **XML** und **UDT**. Diese Erweiterungen machen sich auch Erweiterungen der Datentypen **varchar**, **nvarchar** und **varbinary** zunutze. Der OLE DB-Treiber für SQL Server fügt für ADO-Anwendungen die Initialisierungseigenschaft SSPROP_INIT_DATATYPECOMPATIBILITY dem DBPROPSET_SQLSERVERDBINIT-Eigenschaftensatz hinzu, damit die neuen Datentypen in einer mit ADO kompatiblen Weise verfügbar gemacht werden. Außerdem definiert der OLE DB Treiber für SQL Server auch ein neues Verbindungs Zeichenfolgen-Schlüsselwort mit dem Namen **datatypcompatibility** , das in der Verbindungs Zeichenfolge festgelegt wird.  

> [!NOTE]  
>  Vorhandene ADO-Anwendungen können über den SQLOLEDB-Anbieter auf XML, UDT, umfangreiche Textwerte und Werte von Binärfeldern zugreifen und diese aktualisieren. Die neuen größeren Datentypen **varchar(max)** , **nvarchar(max)** und **varbinary(max)** werden als die ADO-Typen **adLongVarChar**, **adLongVarWChar** bzw. **adLongVarBinary** zurückgegeben. XML-Spalten werden als **adLongVarChar** zurückgegeben, und UDT-Spalten werden als **adVarBinary** zurückgegeben. Wenn Sie jedoch den OLE DB Treiber für SQL Server (msoledbsql) anstelle von SQLOLEDB verwenden, müssen Sie sicherstellen, dass das **DataTypeCompatibility** -Schlüsselwort auf "80" festgelegt ist, damit die neuen Datentypen den ADO-Datentypen ordnungsgemäß zugeordnet werden.  

## <a name="enabling-ole-db-driver-for-sql-server-from-ado"></a>Aktivieren des OLE DB Treibers für die SQL Server von ADO  
 Um die Verwendung von OLE DB-Treiber für SQL Server zu ermöglichen, müssen ADO-Anwendungen die folgenden Schlüsselwörter in ihrer Verbindungszeichenfolge angeben:  

-   `Provider=MSOLEDBSQL`  

-   `DataTypeCompatibility=80`  

 Weitere Informationen zu den vom OLE DB-Treiber für SQL Server unterstützten Schlüsselwörtern für ADO-Verbindungszeichenfolgen finden Sie unter [Verwenden von Verbindungszeichenfolgen-Schlüsselwörtern mit dem OLE DB-Treiber für SQL Server](../../oledb/applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md).  

 Es folgt ein Beispiel, in dem eine ADO-Verbindungszeichenfolge eingerichtet wird, mit der die Verwendung von des OLE DB-Treibers für SQL Server in vollem Umfang ermöglicht und die MARS-Funktion aktiviert wird:  

```  
Dim con As New ADODB.Connection  

con.ConnectionString = "Provider=MSOLEDBSQL;" _  
         & "Server=(local);" _  
         & "Database=AdventureWorks;" _   
         & "Integrated Security=SSPI;" _  
         & "DataTypeCompatibility=80;" _  
         & "MARS Connection=True;"  
con.Open  
```  

## <a name="examples"></a>Beispiele  
 In den folgenden Abschnitten finden Sie Beispiele für die Verwendung von ADO mit dem OLE DB-Treiber für SQL Server.  

### <a name="retrieving-xml-column-data"></a>Abrufen von XML-Spaltendaten  
 In diesem Beispiel wird ein Recordset verwendet, um die Daten aus einer XML-Spalte der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Beispieldatenbank **AdventureWorks** abzurufen und anzuzeigen.  

```  
Dim con As New ADODB.Connection  
Dim rst As New ADODB.Recordset  
Dim sXMLResult As String  

con.ConnectionString = "Provider=MSOLEDBSQL;" _  
         & "Server=(local);" _  
         & "Database=AdventureWorks;" _   
         & "Integrated Security=SSPI;" _   
         & "DataTypeCompatibility=80;"  

con.Open  

' Get the xml data as a recordset.  
Set rst.ActiveConnection = con  
rst.Source = "SELECT AdditionalContactInfo FROM Person.Contact " _  
   & "WHERE AdditionalContactInfo IS NOT NULL"  
rst.Open  

' Display the data in the recordset.  
While (Not rst.EOF)  
   sXMLResult = rst.Fields("AdditionalContactInfo").Value  
   Debug.Print (sXMLResult)  
   rst.MoveNext  
End While  

con.Close  
Set con = Nothing  
```  

> [!NOTE]  
>  Recordset-Filter werden bei XML-Spalten nicht unterstützt. Wenn sie verwendet werden, wird ein Fehler zurückgegeben.  

### <a name="retrieving-udt-column-data"></a>Abrufen von UDT-Spaltendaten  
 In diesem Beispiel wird ein **Command**-Objekt verwendet, um eine SQL-Abfrage auszuführen, die einen UDT zurückgibt. Der UDT wird aktualisiert, und neue Daten werden anschließend wieder in die Datenbank eingefügt. In diesem Beispiel wird davon ausgegangen, dass der UDT **Point** bereits in der Datenbank registriert wurde.  

```  
Dim con As New ADODB.Connection  
Dim cmd As New ADODB.Command  
Dim rst As New ADODB.Recordset  
Dim strOldUDT As String  
Dim strNewUDT As String  
Dim aryTempUDT() As String  
Dim strTempID As String  
Dim i As Integer  

con.ConnectionString = "Provider=MSOLEDBSQL;" _  
         & "Server=(local);" _  
         & "Database=AdventureWorks;" _   
         & "Integrated Security=SSPI;" _  
         & "DataTypeCompatibility=80;"  

con.Open  

' Get the UDT value.  
Set cmd.ActiveConnection = con  
cmd.CommandText = "SELECT ID, Pnt FROM dbo.Points.ToString()"  
Set rst = cmd.Execute  
strTempID = rst.Fields(0).Value  
strOldUDT = rst.Fields(1).Value  

' Do something with the UDT by adding i to each point.  
arytempUDT = Split(strOldUDT, ",")  
i = 3  
strNewUDT = LTrim(Str(Int(aryTempUDT(0)) + i)) + "," + _  
   LTrim(Str(Int(aryTempUDT(1)) + i))  

' Insert the new value back into the database.  
cmd.CommandText = "UPDATE dbo.Points SET Pnt = '" + strNewUDT + _  
   "' WHERE ID = '" + strTempID + "'"  
cmd.Execute  

con.Close  
Set con = Nothing  
```  

### <a name="enabling-and-using-mars"></a>Aktivieren und Verwenden von MARS  
 In diesem Beispiel wird die Verbindungszeichenfolge so eingerichtet, dass MARS über den OLE DB-Treiber für SQL Server aktiviert wird, und dann werden zwei Recordset-Objekte erstellt, die über die gleiche Verbindung ausgeführt werden sollen.  

```  
Dim con As New ADODB.Connection  

con.ConnectionString = "Provider=MSOLEDBSQL;" _  
         & "Server=(local);" _  
         & "Database=AdventureWorks;" _   
         & "Integrated Security=SSPI;" _  
         & "DataTypeCompatibility=80;" _  
         & "MARS Connection=True;"  
con.Open  

Dim recordset1 As New ADODB.Recordset  
Dim recordset2 As New ADODB.Recordset  

Dim recordsaffected As Integer  
Set recordset1 =  con.Execute("SELECT * FROM Table1", recordsaffected, adCmdText)  
Set recordset2 =  con.Execute("SELECT * FROM Table2", recordsaffected, adCmdText)  

con.Close  
Set con = Nothing  
```  

 In früheren Versionen des OLE DB-Anbieters hätte dieser Code bewirkt, dass für den zweiten Execute-Aufruf eine Standardverbindung erstellt wird, weil in diesen Versionen nur ein aktives Resultset pro Verbindung geöffnet werden konnte. Weil die Standardverbindung nicht in den OLE DB-Verbindungspool aufgenommen wurde, bedeutete dies zusätzlichen Aufwand. Wenn der OLE DB-Anbieter von OLE DB-Treiber für SQL Server verfügbar macht, sind mehrere aktive Resultsets in einer Verbindung zulässig.  

## <a name="see-also"></a>Weitere Informationen  
 [Erstellen von Anwendungen mit dem OLE DB-Treiber für SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
