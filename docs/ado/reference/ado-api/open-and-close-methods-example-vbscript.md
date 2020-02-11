---
title: Open-und Close-Methoden Beispiel (VBScript) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- Close method [ADO], VBScript example
- Open method [ADO], VBScript example
ms.assetid: 66eca011-e258-4d8f-bd67-e017bcf0871b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 87b2753c989ad2996dc7788bb0820d78b3b9b6ec
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67931915"
---
# <a name="open-and-close-methods-example-vbscript"></a>Open- und Close-Methode – Beispiel (VBScript)
In diesem Beispiel werden die [Open](../../../ado/reference/ado-api/open-method-ado-recordset.md) -und [Close](../../../ado/reference/ado-api/close-method-ado.md) -Methode sowohl für [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -als auch für [Verbindungs](../../../ado/reference/ado-api/connection-object-ado.md) Objekte verwendet, die geöffnet wurden.  
  
 Verwenden Sie das folgende Beispiel in einer Active Server Seite (ASP). Verwenden Sie **Suchen** , um die Datei adovsb. Inc zu suchen, und platzieren Sie Sie in dem Verzeichnis, das Sie verwenden möchten. Schneiden Sie den folgenden Code aus, und fügen Sie ihn in Editor oder einen anderen Text-Editor ein, und speichern Sie ihn als **openvsb. ASP**. Sie können das Ergebnis in einem beliebigen Browser anzeigen.  
  
```  
<!-- BeginOpenVBS -->  
<%@ Language=VBScript %>  
<%' use this meta tag instead of adovbs.inc%>  
<!--METADATA TYPE="typelib" uuid="00000205-0000-0010-8000-00AA006D2EA4" -->  
<HTML>  
<HEAD>  
<META name="VI60_DefaultClientScript"  content=VBScript>  
<META NAME="GENERATOR" Content="Microsoft Visual Studio 6.0">  
<title>ADO Open Method</title>  
<STYLE>  
<!--  
BODY {  
   font-family: 'Verdana','Arial','Helvetica',sans-serif;  
   BACKGROUND-COLOR:white;  
   COLOR:black;  
    }  
.thead {  
   background-color: #008080;   
   font-family: 'Verdana','Arial','Helvetica',sans-serif;   
   font-size: x-small;  
   color: white;  
   }  
.thead2 {  
   background-color: #800000;   
   font-family: 'Verdana','Arial','Helvetica',sans-serif;   
   font-size: x-small;  
   color: white;  
   }  
.tbody {   
   text-align: center;  
   background-color: #f7efde;  
   font-family: 'Verdana','Arial','Helvetica',sans-serif;   
   font-size: x-small;  
    }  
-->  
</STYLE>  
</HEAD>  
  
<BODY>  
<H3>ADO Open Method</H3>  
  
<TABLE WIDTH=600 BORDER=0>  
<TR>  
<TD VALIGN=TOP COLSPAN=3>  
<FONT SIZE=2>  
<% ' to integrate/test this code replace the   
   ' Data Source value in the Connection string%>  
<%   
    ' connection and recordset variables  
    Dim Cnxn, strCnxn  
    Dim rsCustomers, strSQLCustomers  
    Dim rsProducts, strSQLProducts  
  
    ' open connection  
    Set Cnxn = Server.CreateObject("ADODB.Connection")  
    strCnxn = "Provider='sqloledb';Data Source=" & _  
            Request.ServerVariables("SERVER_NAME") & ";" & _  
            "Integrated Security='SSPI';Initial Catalog='Northwind';"  
  
    Cnxn.Open strCnxn  
  
    ' create and open first Recordset using Connection - execute  
    Set rsCustomers = Server.CreateObject("ADODB.Recordset")  
    strSQLCustomers = "SELECT CompanyName, ContactName, City FROM Customers"  
    Set rsCustomers = Cnxn.Execute(strSQLCustomers)   
  
    ' create and open second Recordset using recordset - open  
    Set rsProducts = Server.CreateObject("ADODB.Recordset")  
    strSQLProducts = "SELECT ProductName, UnitPrice FROM Products"  
    rsProducts.Open strSQLProducts, Cnxn, adOpenDynamic, adLockPessimistic, adCmdText  
    %>  
  
    <TABLE COLSPAN=8 CELLPADDING=5 BORDER=0>  
    <!-- BEGIN column header row for Customer Table-->  
    <TR CLASS=thead>  
       <TD>Company Name</TD>  
       <TD>Contact Name</TD>  
       <TD>City</TD>  
    </TR>  
  
    <!--Display ADO Data from Customer Table-->  
    <% Do Until rsCustomers.EOF %>  
    <TR CLASS=tbody>  
      <TD> <%=rsCustomers("CompanyName")%> </TD>  
      <TD> <%=rsCustomers("ContactName")%></TD>  
      <TD> <%=rsCustomers("City")%> </TD>  
    </TR>   
    <%rsCustomers.MoveNext   
    Loop   
    %>  
    </TABLE>  
  
    <HR>  
  
    <TABLE COLSPAN=8 CELLPADDING=5 BORDER=0>  
    <!-- BEGIN column header row for Product List Table-->  
  
    <TR CLASS=thead2>  
       <TD>Product Name</TD>  
       <TD>Unit Price</TD>  
    </TR>  
    <!-- Display ADO Data Product List-->  
    <% Do Until rsProducts.EOF %>  
      <TR CLASS=tbody>    
      <TD> <%=rsProducts("ProductName")%> </TD>  
      <TD> <%=rsProducts("UnitPrice")%> </TD>  
      </TR>  
      <!--  Next Row = Record -->  
    <%rsProducts.MoveNext   
    Loop   
  
    ' clean up  
    If rsProducts.State = adStateOpen then  
        rsProducts.Close  
    End If  
    If rsCustomers.State = adStateOpen then  
        rsCustomers.Close  
    End If  
    If Cnxn.State = adStateOpen then  
        Cnxn.Close  
    End If  
    Set rsProducts = Nothing  
    Set rsCustomers = Nothing  
    Set Cnxn = Nothing  
  
    %>  
    </TABLE>  
  
</BODY>  
</HTML>  
<!-- EndOpenVBS -->  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Close-Methode (ADO)](../../../ado/reference/ado-api/close-method-ado.md)   
 [Verbindungs Objekt (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Open-Methode (ADO-Verbindung)](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Open-Methode (ADO-Recordset)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
