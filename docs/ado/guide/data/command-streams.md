---
title: Befehl Streams | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- command streams [ADO]
- streams [ADO], command
ms.assetid: 0ac09dbe-2665-411e-8fbb-d1efe6c777be
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e6a5e9581a2a236eab869e74825ee97e7e289d44
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47798571"
---
# <a name="command-streams"></a>Command-Datenströme
ADO hat immer die Eingabe des Befehls unterstützt, im Zeichenfolgenformat angegeben werden, indem die **CommandText** Eigenschaft. Als Alternative mit ADO 2.7 oder höher, Sie können auch verwenden einen Datenstrom von Informationen für die Eingabe des Befehls durch Zuweisen des Streams, in der **' CommandStream '** Eigenschaft. Sie können ein ADO zuweisen **Stream** Objekt oder ein beliebiges Objekt, das die COM unterstützt **IStream** Schnittstelle.  
  
 Der Inhalt der den befehlsdatenstrom ist einfach von ADO zum Anbieter übergeben, damit Ihr Anbieter die Eingabe des Befehls vom Datenstrom für diese Funktion ordnungsgemäß arbeitet unterstützen muss. SQL Server unterstützt z. B. Abfragen in Form von XML-Vorlagen oder OpenXML-Erweiterungen in Transact-SQL an.  
  
 Da die Details des Streams vom Anbieter interpretiert werden müssen, müssen Sie der Befehlsdialekt angeben, durch Festlegen der **Dialekt** Eigenschaft. Der Wert des **Dialekt** ist eine Zeichenfolge mit einer GUID, die von Ihrem Anbieter definiert ist. Informationen zu gültigen Werten für **Dialekt** von Ihrem Anbieter unterstützt werden, finden Sie in der Dokumentation Ihres Anbieters.  
  
## <a name="xml-template-query-example"></a>XML-Abfrage-Vorlagenbeispiel  
 Im folgende Beispiel wird in VBScript in der Northwind-Datenbank geschrieben.  
  
 Zunächst initialisiert werden, und öffnen Sie die **Stream** -Objekt, das verwendet wird, um den Stream für die Abfrage enthält:  
  
```  
Dim adoStreamQuery  
Set adoStreamQuery = Server.CreateObject("ADODB.Stream")  
adoStreamQuery.Open  
```  
  
 Der Inhalt des Streams, der Abfrage wird eine XML-Vorlage Abfrage sein.  
  
 Die Vorlage Abfrage erfordert einen Verweis auf den XML-Namespace identifiziert, die vom Sql: Präfix der \<SQL: Query > Tag. Eine SQL SELECT-Anweisung als Inhalt der XML-Vorlage enthalten ist, und um eine String-Variable wie folgt zugewiesen:  
  
```  
sQuery = "<ROOT xmlns:sql='urn:schemas-microsoft-com:xml-sql'>  
<sql:query> SELECT * FROM PRODUCTS ORDER BY PRODUCTNAME </sql:query>  
</ROOT>"  
```  
  
 Als Nächstes wird schreiben Sie die Zeichenfolge in den Stream:  
  
```  
adoStreamQuery.WriteText sQuery, adWriteChar  
adoStreamQuery.Position = 0  
```  
  
 AdoStreamQuery zum Zuweisen der **' CommandStream '** -Eigenschaft eines ADO **Befehl** Objekt:  
  
```  
Dim adoCmd  
Set adoCmd  = Server.CreateObject("ADODB.Command"")  
adoCmd.CommandStream = adoStreamQuery  
```  
  
 Geben Sie die Befehlssprache **Dialekt**, das angibt, wie die SQL Server-OLE DB-Anbieter den befehlsdatenstrom interpretiert werden soll. Der Dialekt, der von einer anbieterspezifischen-GUID angegeben wird:  
  
```  
adoCmd.Dialect = "{5D531CB2-E6Ed-11D2-B252-00C04F681B71}"  
```  
  
 Abschließend führen Sie die Abfrage und Zurückgeben der Ergebnisse in einem **Recordset** Objekt:  
  
```  
Set objRS = adoCmd.Execute  
```
