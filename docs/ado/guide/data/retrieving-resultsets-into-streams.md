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
author: rothja
ms.author: jroth
ms.openlocfilehash: b20363f3ffae96750046ab98bd623ea44d68a8e2
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82760926"
---
# <a name="retrieving-resultsets-into-streams"></a>Abrufen von Resultsets in Datenströme
Anstatt Ergebnisse im herkömmlichen **Recordset** -Objekt zu empfangen, kann ADO Abfrageergebnisse stattdessen in einen Stream abrufen. Das ADO- **Streamobjekt** (oder andere Objekte, die die com **IStream** -Schnittstelle unterstützen, z. b. asp- **Anforderungs** -und- **Antwort** Objekte), kann verwendet werden, um diese Ergebnisse zu enthalten Eine Verwendung für diese Funktion ist das Abrufen von Ergebnissen im XML-Format. Mit SQL Server beispielsweise können XML-Ergebnisse auf verschiedene Weise zurückgegeben werden, z. b. die Verwendung der for XML-Klausel mit einer SQL SELECT-Abfrage oder eine XPath-Abfrage.  
  
 Wenn Sie Abfrageergebnisse im Streamformat anstelle eines **Recordsets**empfangen möchten, müssen Sie die **adExecuteStream** -Konstante von **ExecuteOptionEnum** als Parameter der **Execute** -Methode eines **Befehls** Objekts angeben. Wenn Ihr Anbieter dieses Feature unterstützt, werden die Ergebnisse bei der Ausführung in einem Stream zurückgegeben. Sie müssen möglicherweise zusätzliche anbieterspezifische Eigenschaften angeben, bevor der Code ausgeführt wird. Beispielsweise müssen bei Verwendung des Microsoft OLE DB-Anbieters für SQL Server Eigenschaften wie der **Ausgabestream** in der **Properties** -Auflistung des **Command** -Objekts angegeben werden. Weitere Informationen zu SQL Server spezifischen dynamischen Eigenschaften im Zusammenhang mit diesem Feature finden Sie unter XML-bezogene Eigenschaften in der SQL Server-Onlinedokumentation.  
  
## <a name="for-xml-query-example"></a>Beispiel für XML Query  
 Das folgende Beispiel wird in VBScript in die Northwind-Datenbank geschrieben:  
  
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
  
 Die for XML-Klausel weist SQL Server an, Daten in Form eines XML-Dokuments zurückzugeben.  
  
### <a name="for-xml-syntax"></a>FOR XML-Syntax  
  
```syntax
FOR XML [RAW|AUTO|EXPLICIT]  
```  
  
 FOR XML RAW generiert generische Zeilen Elemente, die über Spaltenwerte als Attribute verfügen. FOR XML Auto verwendet Heuristik, um eine hierarchische Struktur mit Elementnamen zu generieren, die auf Tabellennamen basieren. FOR XML (explizit) generiert eine universelle Tabelle mit in den Metadaten vollständig beschriebenen Beziehungen.  
  
 Es folgt ein Beispiel für eine SQL SELECT for XML-Anweisung:  
  
```sql
SELECT * FROM PRODUCTS ORDER BY PRODUCTNAME FOR XML AUTO  
```  
  
 Der Befehl kann in einer Zeichenfolge angegeben werden, wie zuvor gezeigt, **CommandText**zugewiesen, oder in Form einer XML-Vorlagen Abfrage, die **CommandStream**zugewiesen ist. Weitere Informationen zu XML-Vorlagen Abfragen finden Sie unter [Befehlsdaten Ströme](../../../ado/guide/data/command-streams.md) in ADO oder Verwenden von Streams für Befehlseingaben in der SQL Server-Onlinedokumentation.  
  
 Als XML-Vorlagen Abfrage sieht die for XML-Abfrage wie folgt aus:  
  
```xml
<sql:query> SELECT * FROM PRODUCTS ORDER BY PRODUCTNAME FOR XML AUTO </sql:query>  
```  
  
 In diesem Beispiel wird das ASP- **Antwort** Objekt für die **ausgabestreameigenschaft** angegeben:  
  
```vb
adoCmd.Properties("Output Stream") = Response  
```  
  
 Geben Sie als nächstes den **adExecuteStream** -Parameter von **Execute**an. In diesem Beispiel wird der Datenstrom in XML-Tags eingeschlossen, um eine XML-Daten Insel zu erstellen:  
  
```vb
Response.write "<XML ID=MyDataIsle>"  
adoCmd.Execute , , adExecuteStream  
Response.write "</XML>"  
```  
  
### <a name="remarks"></a>Bemerkungen  
 An diesem Punkt wurde XML an den Client Browser gestreamt und kann nun angezeigt werden. Dies erfolgt mithilfe von Client seitigem VBScript, um das XML-Dokument an eine DOM-Instanz zu binden und die einzelnen untergeordneten Knoten zu durchlaufen, um eine Liste von Produkten in HTML zu erstellen.
