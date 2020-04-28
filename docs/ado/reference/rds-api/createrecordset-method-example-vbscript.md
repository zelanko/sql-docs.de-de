---
title: Beispiel für die Methode "kreaterecordset" (VBScript) | Microsoft-Dokumentation
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
- CreateRecordset method [RDS], VBScript example
ms.assetid: cce0d8b5-e87b-4f7b-a8a0-37d5025a1f5d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8dde6e14283195ef3b56d545a58a95c307774223
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67964527"
---
# <a name="createrecordset-method-example-vbscript"></a>CreateRecordset-Methode – Beispiel (VBScript)
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
 In diesem Codebeispiel wird ein [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) auf der Serverseite erstellt. Sie verfügt über zwei Spalten mit jeweils vier Zeilen. Schneiden Sie den folgenden Code aus, und fügen Sie ihn in Editor oder einen anderen Text-Editor ein, und speichern Sie **ihn als "**" "" "" "".  
  
```  
<!-- BeginCreateRecordsetVBS -->  
<%@ Language=VBScript %>  
<html>  
<head>  
    <meta name="VI60_DefaultClientScript"  content=VBScript>  
    <meta name="GENERATOR" content="Microsoft Visual Studio 6.0">  
    <title>CreateRecordset Method Example (VBScript)</title>  
<style>  
<!--  
body {  
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
</style>  
</head>  
  
<body>  
  
<OBJECT classid=clsid:BD96C556-65A3-11D0-983A-00C04FC29E33 height=1 id=DC1 width=1>  
</OBJECT>  
<h1>CreateRecordset Method Example (VBScript)</h1>  
<script language = "vbscript">  
    ' use the RDS.DataControl to create an empty recordset;   
    ' takes an array of variants where every element is itself another  
    ' array of variants, one for every column required in the recordset  
  
    ' the elements of the inner array are the column's  
    ' name, type, size, and nullability  
Sub GetRS()  
   Dim Record(2)  
   Dim Field1(3)  
   Dim Field2(3)  
   Dim Field3(3)  
  
    ' for each field, specify the name type, size, and nullability  
  
   Field1(0) = "Name"   ' Column name.  
   Field1(1) = CInt(129)   ' Column type.  
   Field1(2) = CInt(40)   ' Column size.  
   Field1(3) = False      ' Nullable?  
  
   Field2(0) = "Age"  
   Field2 (1) = CInt(3)  
   Field2 (2) = CInt(-1)  
   Field2 (3) = True  
  
   Field3 (0) = "DateOfBirth"  
   Field3 (1) = CInt(7)  
   Field3 (2) = CInt(-1)  
   Field3 (3) = True  
  
    ' put all fields into an array of arrays  
   Record(0) = Field1  
   Record(1) = Field2  
   Record(2) = Field3  
  
   Dim NewRs   
   Set NewRS = DC1.CreateRecordset(Record)  
  
   Dim fields(2)  
   fields(0) = Field1(0)  
   fields(1) = Field2(0)  
   fields(2) = Field3(0)  
  
    ' Populate the new recordset with data values.  
   Dim fieldVals(2)  
  
    ' Use AddNew to add the records.  
   fieldVals(0) = "Joe"  
   fieldVals(1) = 5  
   fieldVals(2) = CDate(#1/5/96#)  
   NewRS.AddNew fields, fieldVals  
  
   fieldVals(0) = "Mary"  
   fieldVals(1) = 6  
   fieldVals(2) = CDate(#6/5/94#)  
   NewRS.AddNew fields, fieldVals  
  
   fieldVals(0) = "Alex"  
   fieldVals(1) = 13  
   fieldVals(2) = CDate(#1/6/88#)  
   NewRS.AddNew fields, fieldVals  
  
   fieldVals(0) = "Susan"  
   fieldVals(1) = 13  
   fieldVals(2) = CDate(#8/6/87#)  
   NewRS.AddNew fields, fieldVals  
  
   NewRS.MoveFirst  
  
    ' Set the newly created and populated Recordset to  
    ' the SourceRecordset property of the  
    ' RDS.DataControl to bind to visual controls  
  
   Set DC1.SourceRecordset = NewRS  
End Sub  
</script>  
<table datasrc="#DC1" align="center">  
<thead>  
<tr id="ColHeaders" class="thead2">  
   <th>Name</th>  
   <th>Age</th>  
    <th>D.O.B.</th>  
</tr>  
</thead>  
<tbody class="tbody">  
<tr>  
   <td><input datafld="Name" size=15 id=text1 name=text1> </td>  
   <td><input datafld="Age" size=25 id=text2 name=text2> </td>  
   <td><input datafld="DateOfBirth" size=25 id=text3 name=text3> </td>  
</tr>  
</tbody>  
</table>  
<input type = "button" onclick = "GetRS()" value="Go!">  
</body>  
</html>  
<!-- EndCreateRecordsetVBS -->  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Methode "samaterecordset" (RDS)](../../../ado/reference/rds-api/createrecordset-method-rds.md)   
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)


