---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 263f83093c46f4265559fe0b1844112687d4fc67
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67924593"
---
# <a name="persisting-records-in-xml-format"></a>Beibehalten von Datensätzen im XML-Format
Wie beim ADTG **Recordset** Persistenz im XML-Format wird implementiert, mit der Microsoft OLE DB-Persistenz-Provider. Dieser Anbieter generiert einen Vorwärtscursor, schreibgeschützte Rowset aus einer gespeicherten XML-Datei oder einem Stream, der die Schemainformationen, die vom ADO enthält. Auf ähnliche Weise kann ein ADO dauern **Recordset**, Generieren von XML, und speichern Sie ihn in einer Datei oder ein Objekt, das die COM implementiert **IStream** Schnittstelle. (Eine Datei ist einfach ein weiteres Beispiel für ein Objekt, das unterstützt **IStream**.) ADO verwendet, Version 2.5 und höher, auf der Microsoft XML Parser (MSXML) beim Laden der XML-Daten in die **Recordset**; daher msxml.dll ist erforderlich.  
  
> [!NOTE]
>  Einige Einschränkungen gelten beim Speichern von hierarchischen **Recordsets** (Daten-Shapes) in XML-Format. Sie können nicht in XML gespeichert, wenn die hierarchische **Recordset** ausstehende Updates enthält und Sie können eine parametrisierte speichern hierarchische **Recordset**. Weitere Informationen finden Sie unter [beibehalten von gefilterten und hierarchischen Recordsets](../../../ado/guide/data/persisting-filtered-and-hierarchical-recordsets.md).  
  
 Die einfachste Möglichkeit zum Beibehalten von Daten in XML-Code, und Laden Sie sie wieder wieder über ADO ist mit der **speichern** und **öffnen** Methoden bzw. Im folgenden Beispiel der ADO-Code wird veranschaulicht, speichern die Daten in die **Titel** Tabelle in eine Datei mit dem Namen titles.sav.  
  
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
  
 ADO speichert immer die gesamte **Recordset** Objekt. Wenn Sie eine Teilmenge von Zeilen beibehalten möchten die **Recordset** -Objekts die **Filter** Methode zum eingrenzen, der Zeilen, oder ändern Sie Ihre Auswahlklausel. Allerdings müssen Sie öffnen ein **Recordset** Objekt mit einem clientseitigen Cursor (**CursorLocation** = **AdUseClient**) verwenden die **Filtern** -Methode für eine Teilmenge von Zeilen gespeichert. Z. B. um Titel abzurufen, die mit dem Buchstaben "b" beginnen, Sie können einen Filter anwenden, ein offenes **Recordset** Objekt:  
  
```  
rs.Filter "title_id like 'B*'"  
rs.Save "btitles.sav", adPersistXML  
```  
  
 ADO verwendet immer das Client-Cursor-Engine-Rowset einer bildlauffähigen erzeugt lesezeichenfähig **Recordset** Objekt für die Vorwärts-Daten, die generiert werden, indem Sie den Persistenz-Provider.  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [XML Persistence Format (XML-Beibehaltungsformat)](../../../ado/guide/data/xml-persistence-format.md)  
  
-   [Namespaces](../../../ado/guide/data/namespaces.md)  
  
-   [Schema-Abschnitt](../../../ado/guide/data/schema-section.md)  
  
-   [Datenabschnitt](../../../ado/guide/data/data-section.md)  
  
-   [Hierarchische Recordsets im XML-Format](../../../ado/guide/data/hierarchical-recordsets-in-xml.md)  
  
-   [Recordset Dynamic Properties in XML (Dynamische Recordset-Eigenschaften in XML)](../../../ado/guide/data/recordset-dynamic-properties-in-xml.md)  
  
-   [XSLT-Transformationen](../../../ado/guide/data/xslt-transformations.md)  
  
-   [Saving to the XML DOM Object (Speichern in das XML DOM-Objekts)](../../../ado/guide/data/saving-to-the-xml-dom-object.md)  
  
-   [XML-Sicherheitsüberlegungen](../../../ado/guide/data/xml-security-considerations.md)  
  
-   [Speicherszenario für XML-Recordsets](../../../ado/guide/data/xml-recordset-persistence-scenario.md)
