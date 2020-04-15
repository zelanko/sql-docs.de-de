---
title: Verwenden von ADO mit SQL Server Native Client | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client, ADO
- data access [SQL Server Native Client], ADO
- ADO [SQL Server Native Client]
- SQLNCLI, ADO
ms.assetid: 118a7cac-4c0d-44fd-b63e-3d542932d239
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 81f7ff71643776eb3116dab0157a4f2cd32b788a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302464"
---
# <a name="using-ado-with-sql-server-native-client"></a>Verwenden von ADO mit SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Um neue Funktionen [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] wie mehrere aktive Resultsets (MARS), Abfragebenachrichtigungen, benutzerdefinierte Typen (UDTs) oder den neuen **XML-Datentyp** nutzen zu können, sollten [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] vorhandene Anwendungen, die ActiveX Data Objects (ADO) verwenden, den nativen Client-OLE-DB-Anbieter als Datenzugriffsanbieter verwenden.  
  
 Wenn keine der neuen Funktionen von [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] erforderlich ist, dann ist es auch nicht notwendig, den OLE DB-Anbieter von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client zu verwenden. Sie können weiterhin mit dem aktuellen Datenzugriffsanbieter (in der Regel SQLOLEDB) arbeiten. Wenn Sie eine bestehende Anwendung erweitern und die neuen Funktionen von [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] verwenden müssen, dann sollten Sie den OLE DB-Anbieter von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client verwenden.  
  
> [!NOTE]  
>  Wenn Sie eine neue Anwendung entwickeln, wird empfohlen, über ADO.NET und den .NET Framework-Datenanbieter für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] statt über [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client auf die neuen Funktionen der letzten Versionen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] zuzugreifen. Weitere Informationen zum .NET Framework-Datenanbieter für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] finden Sie in der .NET Framework-SDK-Dokumentation für ADO.NET.  
  
 Damit ADO die neuen Funktionen der letzten Versionen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nutzen kann, wurde der OLE DB-Anbieter von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, der die Kernfunktionen von OLE DB erweitert, um einige Erweiterungen ergänzt. Diese Erweiterungen erlauben es ADO-Anwendungen, neuere [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Features zu verwenden und zwei Datentypen zu verarbeiten, die in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] eingeführt wurden: **XML** und **UDT**. Diese Erweiterungen machen sich auch Erweiterungen der Datentypen **varchar**, **nvarchar** und **varbinary** zunutze. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client fügt die SSPROP_INIT_DATATYPECOMPATIBILITY Initialisierungseigenschaft zur DBPROPSET_SQLSERVERDBINIT-Eigenschaft für die Verwendung durch ADO-Anwendungen hinzu, sodass die neuen Datentypen auf eine Weise verfügbar gemacht werden, die mit ADO kompatibel ist. Darüber hinaus [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] definiert der native Client-OLE-DB-Anbieter auch ein neues Verbindungszeichenfolgenschlüsselwort namens **DataTypeCompatibility,** das in der Verbindungszeichenfolge festgelegt ist.  
  
> [!NOTE]  
>  Vorhandene ADO-Anwendungen können über den SQLOLEDB-Anbieter auf XML, UDT, umfangreiche Textwerte und Werte von Binärfeldern zugreifen und diese aktualisieren. Die neuen größeren Datentypen **varchar(max)**, **nvarchar(max)** und **varbinary(max)** werden als die ADO-Typen **adLongVarChar**, **adLongVarWChar** bzw. **adLongVarBinary** zurückgegeben. XML-Spalten werden als **adLongVarChar** zurückgegeben, und UDT-Spalten werden als **adVarBinary** zurückgegeben. Wenn Sie jedoch [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] den Native Client OLE DB-Anbieter (SQLNCLI11) anstelle von SQLOLEDB verwenden, müssen Sie sicherstellen, dass das **DataTypeCompatibility-Schlüsselwort** auf "80" festgelegt wird, damit die neuen Datentypen den ADO-Datentypen korrekt zugeordnet werden.  
  
## <a name="enabling-sql-server-native-client-from-ado"></a>Aktivieren von SQL Server Native Client über ADO  
 Um die Verwendung [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] von Native Client zu aktivieren, müssen ADO-Anwendungen die folgenden Schlüsselwörter in ihren Verbindungszeichenfolgen implementieren:  
  
-   `Provider=SQLNCLI11`  
  
-   `DataTypeCompatibility=80`  
  
 Weitere Informationen zu den ADO-Verbindungszeichenfolgen, die in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client unterstützt werden, finden Sie unter Verwenden von [Verbindungszeichenfolgenschlüsselwörtern mit SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
 Im Folgenden finden Sie ein Beispiel für das Einrichten einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ADO-Verbindungszeichenfolge, die für die Arbeit mit Native Client vollständig aktiviert ist, einschließlich der Aktivierung der MARS-Funktion:  
  
```  
Dim con As New ADODB.Connection  
  
con.ConnectionString = "Provider=SQLNCLI11;" _  
         & "Server=(local);" _  
         & "Database=AdventureWorks;" _   
         & "Integrated Security=SSPI;" _  
         & "DataTypeCompatibility=80;" _  
         & "MARS Connection=True;"  
con.Open  
```  
  
## <a name="examples"></a>Beispiele  
 Die folgenden Abschnitte enthalten Beispiele für die Verwendung [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] von ADO mit dem nativen Client-OLE-DB-Anbieter.  
  
### <a name="retrieving-xml-column-data"></a>Abrufen von XML-Spaltendaten  
 In diesem Beispiel wird ein Recordset verwendet, um die Daten aus einer XML-Spalte der -Beispieldatenbank [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **AdventureWorks** abzurufen und anzuzeigen.  
  
```  
Dim con As New ADODB.Connection  
Dim rst As New ADODB.Recordset  
Dim sXMLResult As String  
  
con.ConnectionString = "Provider=SQLNCLI11;" _  
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
  
con.ConnectionString = "Provider=SQLNCLI11;" _  
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
 In diesem Beispiel wird die Verbindungszeichenfolge erstellt, um MARS über den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nativen Client-OLE-DB-Anbieter zu aktivieren, und dann werden zwei Recordset-Objekte erstellt, um sie mit derselben Verbindung auszuführen.  
  
```  
Dim con As New ADODB.Connection  
  
con.ConnectionString = "Provider=SQLNCLI11;" _  
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
  
 In früheren Versionen des OLE DB-Anbieters hätte dieser Code bewirkt, dass für den zweiten Execute-Aufruf eine Standardverbindung erstellt wird, weil in diesen Versionen nur ein aktives Resultset pro Verbindung geöffnet werden konnte. Weil die Standardverbindung nicht in den OLE DB-Verbindungspool aufgenommen wurde, bedeutete dies zusätzlichen Aufwand. Mit der MARS-Funktion, die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] vom Native Client OLE DB-Anbieter verfügbar gemacht wird, erhalten Sie mehrere aktive Ergebnisse für die eine Verbindung.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen von Anwendungen mit SQL Server Native Client](../../../relational-databases/native-client/applications/building-applications-with-sql-server-native-client.md)  
  
  
