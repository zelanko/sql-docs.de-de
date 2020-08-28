---
description: Weitere Informationen zur Beibehaltung von Recordsets
title: Weitere Informationen zu recordsetpersistenz | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- persisting data [ADO]
- data updates [ADO], persisting data
- data persistence [ADO]
- updating data [ADO], persisting data
ms.assetid: a9b287f5-04b0-4514-8143-f67879ca9842
author: rothja
ms.author: jroth
ms.openlocfilehash: 1dca646b07c441a4fccd617723aba98536f1a7e1
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88980331"
---
# <a name="more-about-recordset-persistence"></a>Weitere Informationen zur Beibehaltung von Recordsets
Das ADO-Recordset-Objekt unterstützt das Speichern des Inhalts eines **Recordset** -Objekts in einer Datei mithilfe der [Save](../../reference/ado-api/save-method.md) -Methode. Die permanent gespeicherte Datei ist möglicherweise auf einem lokalen Laufwerk, Server oder als URL auf einer Website vorhanden. Später kann die Datei entweder mit der [Open](../../reference/ado-api/open-method-ado-recordset.md) -Methode des **Recordset** -Objekts oder mit der [Execute](../../reference/ado-api/execute-method-ado-connection.md) -Methode des [Connection](../../reference/ado-api/connection-object-ado.md) -Objekts wieder hergestellt werden.  
  
 Außerdem konvertiert die [GetString](../../reference/ado-api/getstring-method-ado.md) -Methode ein **Recordset** -Objekt in ein Formular, in dem die Spalten und Zeilen mit den von Ihnen angegebenen Zeichen getrennt sind.  
  
 Wenn Sie ein **Recordset**persistent speichern möchten, müssen Sie es zunächst in ein Formular umrechnen, das in einer Datei gespeichert werden kann. **Recordset** -Objekte können im proprietären Format des erweiterten Daten tablegrams (ADTG) oder im Open Extensible Markup Language-Format (XML) gespeichert werden. ADTG-Beispiele werden im nächsten Abschnitt angezeigt. Weitere Informationen zur XML-Persistenz finden Sie unter [persistente Datensätze im XML-Format](./persisting-records-in-xml-format.md).  
  
 Speichern Sie alle ausstehenden Änderungen in der persistenten Datei. Auf diese Weise können Sie eine Abfrage ausgeben, die ein **Recordset** -Objekt zurückgibt, das **Recordset**bearbeitet, es speichert und ausstehende Änderungen, später das **Recordset**wiederherstellt und dann die Datenquelle mit den gespeicherten ausstehenden Änderungen aktualisiert.  
  
 Informationen zum persistenten Speichern von **Streamobjekten** finden Sie unter [Streams und Persistenz](./streams-and-persistence.md).  
  
 Ein Beispiel für die Speicherung von **Recordsets** finden Sie im Szenario zur Persistenz von XML-Recordsets.  
  
## <a name="example"></a>Beispiel  
  
### <a name="save-a-recordset"></a>Speichern eines Recordsets:  
  
```  
Dim rs as New ADODB.Recordset  
rs.Save "c:\yourFile.adtg", adPersistADTG  
```  
  
### <a name="open-a-persisted-file-with-recordsetopen"></a>Öffnen Sie eine persistente Datei mit Recordset. Open:  
  
```  
Dim rs as New ADODB.Recordset  
rs.Open "c:\yourFile.adtg", "Provider=MSPersist",,,adCmdFile  
```  
  
 Wenn das **Recordset** nicht über eine aktive Verbindung verfügt, können Sie optional alle Standardwerte und den folgenden Code akzeptieren:  
  
```  
Dim rs as New ADODB.Recordset  
rs.Open "c:\yourFile.adtg"  
```  
  
### <a name="open-a-persisted-file-with-connectionexecute"></a>Öffnen Sie eine persistente Datei mit Connection.Exe"niedlich":  
  
```  
Dim conn as New ADODB.Connection  
Dim rs as ADODB.Recordset  
conn.Open "Provider=MSPersist"  
Set rs = conn.execute("c:\yourFile.adtg")  
```  
  
### <a name="open-a-persisted-file-with-rdsdatacontrol"></a>Öffnen Sie eine persistente Datei mit RDS. DataControl  
 In diesem Fall ist die **Server** Eigenschaft nicht festgelegt.  
  
```  
Dim dc as New RDS.DataControl  
dc.Connection = "Provider=MSPersist"  
dc.SQL = "c:\yourFile.adtg"  
dc.Refresh  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [GetString-Methode (ADO)](../../reference/ado-api/getstring-method-ado.md)   
 [Microsoft OLE DB-Persistenzanbieter (ADO-Dienstanbieter)](../appendixes/microsoft-ole-db-persistence-provider-ado-service-provider.md)   
 [Recordset-Objekt (ADO)](../../reference/ado-api/recordset-object-ado.md)   
 [Datenströme und Persistenz](./streams-and-persistence.md)