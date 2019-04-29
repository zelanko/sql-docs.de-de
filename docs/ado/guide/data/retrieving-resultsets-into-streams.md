---
title: Abrufen von Resultsets in Streams | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/20/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- streams [ADO], retrieving query results
- query results into stream [ADO]
- retrieving results into stream [ADO]
ms.assetid: 996c1321-c926-4f57-8297-85c8c20de974
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3ad9c21deb365428a6642f3ee9b7f48396d7c4f9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63188109"
---
# <a name="retrieving-resultsets-into-streams"></a>Abrufen von Resultsets in Datenströme
Anstatt die Ergebnisse der herkömmlichen empfängt **Recordset** Objekt ADO kann stattdessen die Abfrageergebnisse abzurufen, in einen Stream. Das ADO **Stream** Objekt (oder andere Objekte, die die COM unterstützt **IStream** Schnittstelle, z. B. die ASP **anfordern** und **Antwort** Objekte ) kann verwendet werden, um diese Ergebnisse enthalten. Eine Verwendung für diese Funktion ist zum Abrufen von Ergebnissen im XML-Format. Mit SQL Server können z. B. XML-Ergebnisse auf verschiedene Weise, wie z. B. mithilfe der FOR XML-Klausel mit einer SQL-SELECT-Abfrage oder eine XPath-Abfrage zurückgegeben.  
  
 Zum Empfangen von Abfrageergebnissen im Stream-Format nicht in eine **Recordset**, müssen Sie angeben der **AdExecuteStream** aus Konstanten **ExecuteOptionEnum** als Parameter für die **Execute** Methode eine **Befehl** Objekt. Wenn Ihr Anbieter diese Funktion unterstützt, werden die Ergebnisse in einem Stream bei der Ausführung zurückgegeben werden. Sie ist möglicherweise erforderlich, um zusätzliche anbieterspezifische-Eigenschaften angeben, bevor der Code ausgeführt wird. Beispielsweise mit der Microsoft OLE DB-Anbieter für SQL Server, Eigenschaften, z. B. **Output Stream** in die **Eigenschaften** Auflistung von der **Befehl** Objekt sein. angegeben. Weitere Informationen zu SQL Server-spezifische dynamische Eigenschaften, die im Zusammenhang mit diesem Feature finden Sie unter XML-Related Eigenschaften in der SQL Server-Onlinedokumentation.  
  
## <a name="for-xml-query-example"></a>Beispiel für FOR XML-Abfrage  
 Im folgende Beispiel wird mit der Datenbank Northwind in VBScript geschrieben:  
  
```html
<!-- BeginRecordAndStreamVBS -->  
<%@ LANGUAGE = VBScript %>  
<%  Option Explicit      %>  
  
<HTML>  
<HEAD>  
<META NAME="GENERATOR" Content="Microsoft Developer Studio"/>  
<META HTTP-EQUIV="Content-Type" content="text/html"; charset="iso-8859-1">  
<TITLE>FOR XML Query Example</TITLE>  
  
<STYLE>  
   BODY  
   {  
      FONT-FAMILY: Tahoma;  
      FONT-SIZE: 8pt;  
      OVERFLOW: auto  
   }  
  
   H3  
   {  
      FONT-FAMILY: Tahoma;  
      FONT-SIZE: 8pt;  
      OVERFLOW: auto  
   }  
</STYLE>  
  
<!-- #include file="adovbs.inc" -->  
<%  
   Response.Write "<H3>Server-side processing</H3>"  
  
   Response.Write "Page Generated @ " & Now() & "<BR/>"  
  
   Dim adoConn  
   Set adoConn = Server.CreateObject("ADODB.Connection")  
  
   Dim sConn  
   sConn = "Provider=SQLOLEDB;Data Source=" & _  
      Request.ServerVariables("SERVER_NAME") & ";" & _  
      Initial Catalog=Northwind;Integrated Security=SSPI;"  
  
   Response.write "Connect String = " & sConn & "<BR/>"  
  
   adoConn.ConnectionString = sConn  
   adoConn.CursorLocation = adUseClient  
  
   adoConn.Open  
  
   Response.write "ADO Version = " & adoConn.Version & "<BR/>"  
   Response.write "adoConn.State = " & adoConn.State & "<BR/>"  
  
   Dim adoCmd  
   Set adoCmd = Server.CreateObject("ADODB.Command")  
   Set adoCmd.ActiveConnection = adoConn  
  
   Dim sQuery  
   sQuery = "<ROOT xmlns:sql='urn:schemas-microsoft-com:xml-sql'><sql:query>SELECT * FROM PRODUCTS WHERE ProductName='Gumbr Gummibrchen' FOR XML AUTO</sql:query></ROOT>"  
  
   Response.write "Query String = " & sQuery & "<BR/>"  
  
   Dim adoStreamQuery  
   Set adoStreamQuery = Server.CreateObject("ADODB.Stream")  
   adoStreamQuery.Open  
   adoStreamQuery.WriteText sQuery, adWriteChar  
   adoStreamQuery.Position = 0  
  
   adoCmd.CommandStream = adoStreamQuery  
   adoCmd.Dialect = "{5D531CB2-E6Ed-11D2-B252-00C04F681B71}"  
  
   Response.write "Pushing XML to client for processing "  & "<BR/>"  
  
   adoCmd.Properties("Output Stream") = Response  
   Response.write "<XML ID='MyDataIsle'>"  
   adoCmd.Execute , , 1024  
   Response.write "</XML>"  
  
%>  
  
<SCRIPT language="VBScript" For="window" Event="onload">  
   Dim xmlDoc  
   Set xmlDoc = MyDataIsle.XMLDocument  
   xmlDoc.resolveExternals=false  
   xmlDoc.async=false  
  
   If xmlDoc.parseError.Reason <> "" then  
      Msgbox "parseError.Reason = " & xmlDoc.parseError.Reason  
   End If  
  
   Dim root, child  
   Set root = xmlDoc.documentElement  
   For each child in root.childNodes  
      dim OutputXML  
      OutputXML = document.all("log").innerHTML  
      document.all("log").innerHTML = OutputXML & "<LI>" & child.getAttribute("ProductName") & "</LI>"  
   Next  
</SCRIPT>  
  
</HEAD>  
  
<BODY>  
  
   <H3>Client-side processing of XML Document MyDataIsle</H3>  
   <UL id=log>  
   </UL>  
  
</BODY>  
</HTML>  
<!-- EndRecordAndStreamVBS -->  
  
```  
  
 Die FOR XML-Klausel weist SQL Server, um Daten in Form eines XML-Dokuments zurückzugeben.  
  
### <a name="for-xml-syntax"></a>XML-Syntax  
  
```syntax
FOR XML [RAW|AUTO|EXPLICIT]  
```  
  
 XML-ROHDATEN generische Zeilenelemente generiert, die Spaltenwerte als Attribute aufweisen. FOR XML AUTO verwendet Heuristik, um eine hierarchische Struktur mit Elementnamen, die basierend auf den Tabellennamen zu generieren. FOR XML EXPLICIT generiert eine universelle Tabelle mit Beziehungen, die vollständig durch Metadaten beschrieben aus.  
  
 Beispielsweise SQL SELECT FOR XML-Anweisung wie folgt:  
  
```sql
SELECT * FROM PRODUCTS ORDER BY PRODUCTNAME FOR XML AUTO  
```  
  
 Der Befehl kann in eine Zeichenfolge angegeben werden, wie zuvor, zugewiesen an gezeigt **CommandText**, oder in Form einer XML-Vorlage Abfrage zugewiesen **' CommandStream '**. Weitere Informationen zu Abfragen von XML-Vorlage finden Sie unter [Befehl Streams](../../../ado/guide/data/command-streams.md) in ADO oder Using-Streams für die Eingabe des Befehls in der SQL Server-Onlinedokumentation.  
  
 Als XML-Vorlage-Abfrage folgt die FOR XML-Abfrage wie:  
  
```xml
<sql:query> SELECT * FROM PRODUCTS ORDER BY PRODUCTNAME FOR XML AUTO </sql:query>  
```  
  
 In diesem Beispiel wird die ASP **Antwort** -Objekt für die **Output Stream** Eigenschaft:  
  
```vb
adoCmd.Properties("Output Stream") = Response  
```  
  
 Geben Sie als Nächstes **AdExecuteStream** Parameter **Execute**. In diesem Beispiel dient als Wrapper für den Datenstrom im XML-Tags, um eine XML-Dateninsel zu erstellen:  
  
```vb
Response.write "<XML ID=MyDataIsle>"  
adoCmd.Execute , , adExecuteStream  
Response.write "</XML>"  
```  
  
### <a name="remarks"></a>Hinweise  
 An diesem Punkt XML wurde an den Clientbrowser gestreamt wurden, und ist bereit, die angezeigt werden. Dies erfolgt mithilfe der clientseitigen VBScript zum Binden von XML-Dokument an eine Instanz des DOM und auf jeden untergeordneten Knoten durchlaufen, um eine Liste der Produkte im HTML-Format zu erstellen.
