---
description: Beibehalten von Datensätzen im XML-Format
title: Beibehalten von Datensätzen im XML-Format | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- persisting data [ADO]
- data updates [ADO], persisting data
- data persistence [ADO]
- XML persistence [ADO]
- updating data [ADO], persisting data
ms.assetid: f3113ec4-ae31-428f-89c6-bc1024f128ea
author: rothja
ms.author: jroth
ms.openlocfilehash: b88bef75b0cbe13402d90264b766adf5a3005efd
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88453042"
---
# <a name="persisting-records-in-xml-format"></a>Beibehalten von Datensätzen im XML-Format
Ebenso wie das ADTG-Format wird die **recordsetpersistenz** im XML-Format mit dem Microsoft OLE DB Dauerhaftigkeits Anbieter implementiert. Dieser Anbieter generiert ein Schreib geschütztes vorwärts-Rowset aus einer gespeicherten XML-Datei oder einem Datenstrom, der die von ADO generierten Schema Informationen enthält. Ebenso kann Sie ein ADO- **Recordset**verwenden, XML generieren und in einer Datei oder einem beliebigen Objekt speichern, das die com- **IStream** -Schnittstelle implementiert. (Tatsächlich ist eine Datei nur ein weiteres Beispiel für ein Objekt, das **IStream**unterstützt.) Bei Version 2,5 und höher stützt ADO den Microsoft XML-Parser (MSXML), um den XML-Code in das **Recordset**zu laden. Daher ist msxml.dll erforderlich.  
  
> [!NOTE]
>  Wenn hierarchische **Recordsets** (Daten Formen) im XML-Format gespeichert werden, gelten einige Einschränkungen. In XML kann nicht gespeichert werden, wenn das hierarchische **Recordset** ausstehende Updates enthält, und Sie können kein parametrisiertes hierarchisches **Recordset**speichern. Weitere Informationen finden Sie unter [persistente gefilterte und hierarchische Recordsets](../../../ado/guide/data/persisting-filtered-and-hierarchical-recordsets.md).  
  
 Die einfachste Möglichkeit zum Speichern von Daten in XML und zum erneuten Laden der Daten über ADO besteht darin, die Methoden zum Speichern und **Öffnen** zu **Speichern** . Im folgenden ADO-Codebeispiel wird veranschaulicht, wie die Daten in der **Titel** Tabelle in einer Datei mit dem Namen "Titeln. SAV" gespeichert werden.  
  
```  
Dim rs as new Recordset  
Dim rs2 as new Recordset  
Dim c as new Connection  
Dim s as new Stream  
  
' Query the Titles table.  
c.Open "provider=sqloledb;data source=MySQLServer;initial catalog=pubs;Integrated Security='SSPI'"  
rs.cursorlocation = adUseClient  
rs.Open "select * from titles", c, adOpenStatic  
  
' Save to the file in the XML format. Note that if you don't specify   
' adPersistXML, a binary format (ADTG) will be used by default.  
rs.Save "titles.sav", adPersistXML  
  
' Save the recordset into the ADO Stream object.  
rs.save s, adPersistXML  
rs.Close  
c.Close  
  
set rs = nothing  
  
' Reopen the file.  
rs.Open "titles.sav",,,,adCmdFile  
' Open the Stream back into a Recordset.  
rs2.open s  
```  
  
 ADO speichert immer das gesamte **Recordset** -Objekt. Wenn Sie eine Teilmenge der Zeilen des **Recordset** -Objekts beibehalten möchten, verwenden Sie die **Filter** -Methode, um die Zeilen einzugrenzen oder die Auswahl Klausel zu ändern. Sie müssen jedoch ein **Recordset** -Objekt mit einem Client seitigen Cursor (**CursorLocation**  =  **adUseClient**) öffnen, um die **Filter** Methode zum Speichern einer Teilmenge von Zeilen zu verwenden. Wenn Sie z. b. Titel abrufen möchten, die mit dem Buchstaben "b" beginnen, können Sie einen Filter auf ein offenes **Recordset** -Objekt anwenden:  
  
```  
rs.Filter "title_id like 'B*'"  
rs.Save "btitles.sav", adPersistXML  
```  
  
 ADO verwendet immer das Clientcursormodul-Rowset, um ein scrollbares, Lese **Recordset** markerbares Recordsetobjekt zusätzlich zu den vorwärts Daten zu erzeugen, die vom Persistenzanbieter generiert werden.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [XML Persistence Format (XML-Beibehaltungsformat)](../../../ado/guide/data/xml-persistence-format.md)  
  
-   [Namespaces](../../../ado/guide/data/namespaces.md)  
  
-   [Schema-Abschnitt](../../../ado/guide/data/schema-section.md)  
  
-   [Datenabschnitt](../../../ado/guide/data/data-section.md)  
  
-   [Hierarchische Recordsets im XML-Format](../../../ado/guide/data/hierarchical-recordsets-in-xml.md)  
  
-   [Recordset Dynamic Properties in XML (Dynamische Recordset-Eigenschaften in XML)](../../../ado/guide/data/recordset-dynamic-properties-in-xml.md)  
  
-   [XSLT Transformations (XSLT-Transformationen)](../../../ado/guide/data/xslt-transformations.md)  
  
-   [Saving to the XML DOM Object (Speichern in das XML DOM-Objekts)](../../../ado/guide/data/saving-to-the-xml-dom-object.md)  
  
-   [Überlegungen zur Sicherheit bei XML](../../../ado/guide/data/xml-security-considerations.md)  
  
-   [Speicherszenario für XML-Recordsets](../../../ado/guide/data/xml-recordset-persistence-scenario.md)
