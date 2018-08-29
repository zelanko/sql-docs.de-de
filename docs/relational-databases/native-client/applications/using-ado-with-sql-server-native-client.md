---
title: Verwenden von ADO mit SQL Server Native Client | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client, ADO
- data access [SQL Server Native Client], ADO
- ADO [SQL Server Native Client]
- SQLNCLI, ADO
ms.assetid: 118a7cac-4c0d-44fd-b63e-3d542932d239
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 779b0e9c53f048afea3ab5ca6ea2b46dbd608bd7
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43081640"
---
# <a name="using-ado-with-sql-server-native-client"></a>Verwenden von ADO mit SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Um die Vorteile der neuen Funktionen in nutzen [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] wie z. B. mehrere aktive Resultsets (MARS), abfragebenachrichtigungen, benutzerdefinierte Typen (UDTs) oder das neue **Xml** -Datentyp, vorhandene Anwendungen, verwenden von ActiveX, Data Objects (ADO) verwenden, sollten die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter als Datenzugriffsanbieter.  
  
 Wenn keine der neuen Funktionen von [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] erforderlich ist, dann ist es auch nicht notwendig, den OLE DB-Anbieter von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client zu verwenden. Sie können weiterhin mit dem aktuellen Datenzugriffsanbieter (in der Regel SQLOLEDB) arbeiten. Wenn Sie eine bestehende Anwendung erweitern und die neuen Funktionen von [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] verwenden müssen, dann sollten Sie den OLE DB-Anbieter von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client verwenden.  
  
> [!NOTE]  
>  Wenn Sie eine neue Anwendung entwickeln, wird empfohlen, über ADO.NET und den .NET Framework-Datenanbieter für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] statt über [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client auf die neuen Funktionen der letzten Versionen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] zuzugreifen. Weitere Informationen zum .NET Framework-Datenanbieter für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] finden Sie in der .NET Framework-SDK-Dokumentation für ADO.NET.  
  
 Damit ADO die neuen Funktionen der letzten Versionen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nutzen kann, wurde der OLE DB-Anbieter von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, der die Kernfunktionen von OLE DB erweitert, um einige Erweiterungen ergänzt. Diese Erweiterungen erlauben es ADO-Anwendungen, neuere [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Features zu verwenden und zwei Datentypen zu verarbeiten, die in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] eingeführt wurden: **XML** und **UDT**. Diese Erweiterungen machen sich auch Erweiterungen der Datentypen **varchar**, **nvarchar** und **varbinary** zunutze. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client fügt die Initialisierungseigenschaft SSPROP_INIT_DATATYPECOMPATIBILITY dem DBPROPSET_SQLSERVERDBINIT Eigenschaftensatz für die Verwendung von ADO-Anwendungen, damit die neuen Datentypen in einer mit ADO kompatiblen Weise verfügbar gemacht werden. Darüber hinaus die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter definiert auch ein neues Schlüsselwort für Verbindungszeichenfolgen mit dem Namen **DataTypeCompatibility** , die in der Verbindungszeichenfolge festgelegt ist.  
  
> [!NOTE]  
>  Vorhandene ADO-Anwendungen können über den SQLOLEDB-Anbieter auf XML, UDT, umfangreiche Textwerte und Werte von Binärfeldern zugreifen und diese aktualisieren. Die neuen größeren Datentypen **varchar(max)**, **nvarchar(max)** und **varbinary(max)** werden als die ADO-Typen **adLongVarChar**, **adLongVarWChar** bzw. **adLongVarBinary** zurückgegeben. XML-Spalten werden als **adLongVarChar** zurückgegeben, und UDT-Spalten werden als **adVarBinary** zurückgegeben. Allerdings bei Verwendung der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter (SQLNCLI11) statt des SQLOLEDB, müssen Sie Sie sicher, dass die **DataTypeCompatibility** Schlüsselwort auf "80", damit die neuen Datentypen richtig zugeordnet werden, auf die ADO-Daten Typen.  
  
## <a name="enabling-sql-server-native-client-from-ado"></a>Aktivieren von SQL Server Native Client über ADO  
 So aktivieren Sie die Verwendung von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, ADO-Anwendungen müssen die folgenden Schlüsselwörter in den Verbindungszeichenfolgen zu implementieren:  
  
-   `Provider=SQLNCLI11`  
  
-   `DataTypeCompatibility=80`  
  
 Weitere Informationen zu den ADO-Verbindungszeichenfolgen unterstützt Schlüsselwörter [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client finden Sie unter [Schlüsselwörtern für Verbindungszeichenfolgen mit SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
 Folgendes ist ein Beispiel für das Herstellen einer ADO-Verbindungszeichenfolge, die vollständig aktiviert ist, um die Arbeit mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, ermöglicht die MARS-Funktion:  
  
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
 Die folgenden Abschnitte enthalten Beispiele für die Verwendung von ADO mit dem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter.  
  
### <a name="retrieving-xml-column-data"></a>Abrufen von XML-Spaltendaten  
 In diesem Beispiel wird ein Recordset verwendet, um die Daten aus einer XML-Spalte der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Beispieldatenbank **AdventureWorks** abzurufen und anzuzeigen.  
  
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
 In diesem Beispiel wird die Verbindungszeichenfolge erstellt, zum Aktivieren von MARS über den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter, und klicken Sie dann zwei Recordset-Objekte werden zum Ausführen über die gleiche Verbindung erstellt.  
  
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
  
 In früheren Versionen des OLE DB-Anbieters hätte dieser Code bewirkt, dass für den zweiten Execute-Aufruf eine Standardverbindung erstellt wird, weil in diesen Versionen nur ein aktives Resultset pro Verbindung geöffnet werden konnte. Weil die Standardverbindung nicht in den OLE DB-Verbindungspool aufgenommen wurde, bedeutete dies zusätzlichen Aufwand. Mit der MARS-Funktion verfügbar gemacht werden, indem die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB-Anbieter, erhalten Sie mehrere aktive Resultsets in einer Verbindung.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Anwendungen mit SQL Server Native Client](../../../relational-databases/native-client/applications/building-applications-with-sql-server-native-client.md)  
  
  
