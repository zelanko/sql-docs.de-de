---
description: Command-Datenströme
title: Befehlsdaten Ströme | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- command streams [ADO]
- streams [ADO], command
ms.assetid: 0ac09dbe-2665-411e-8fbb-d1efe6c777be
author: rothja
ms.author: jroth
ms.openlocfilehash: 2ae54835836fecdfbf3b026fe9e6a701a5602d3d
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88991541"
---
# <a name="command-streams"></a>Command-Datenströme
ADO hat die Befehls Eingabe im von der **CommandText** -Eigenschaft angegebenen Zeichen folgen Format immer unterstützt. Als Alternative können Sie mit ADO 2,7 oder höher auch einen Informationsstrom für Befehlseingaben verwenden, indem Sie den Stream der **CommandStream** -Eigenschaft zuweisen. Sie können ein ADO- **Stream** -Objekt oder ein beliebiges Objekt zuweisen, das die com **IStream** -Schnittstelle unterstützt.  
  
 Der Inhalt des Befehlsdaten Stroms wird einfach von ADO an Ihren Anbieter übermittelt, sodass der Anbieter Befehlseingaben nach Stream unterstützen muss, damit dieses Feature funktioniert. Beispielsweise unterstützt SQL Server Abfragen in Form von XML-Vorlagen oder OPENXML-Erweiterungen an Transact-SQL.  
  
 Da die Details des Streams vom Anbieter interpretiert werden müssen, müssen Sie den Befehls Dialekt durch Festlegen der **Dialekt** -Eigenschaft angeben. Der Wert von **Dialekt** ist eine Zeichenfolge, die eine GUID enthält, die vom Anbieter definiert wird. Informationen zu gültigen Werten für den von Ihrem Anbieter unterstützten **Dialekt** finden Sie in der Dokumentation des Anbieters.  
  
## <a name="xml-template-query-example"></a>Beispiel für eine XML-Vorlagen Abfrage  
 Das folgende Beispiel wird in VBScript in die Northwind-Datenbank geschrieben.  
  
 Initialisieren und öffnen Sie zunächst das **Stream** -Objekt, das zum enthalten des Abfrage Datenstroms verwendet wird:  
  
```  
Dim adoStreamQuery  
Set adoStreamQuery = Server.CreateObject("ADODB.Stream")  
adoStreamQuery.Open  
```  
  
 Der Inhalt des Abfrage Datenstroms wird als XML-Vorlagen Abfrage verwendet.  
  
 Die Vorlagen Abfrage erfordert einen Verweis auf den XML-Namespace, der durch das SQL:-Präfix des Tags identifiziert wird \<sql:query> . Eine SQL-SELECT-Anweisung wird als Inhalt der XML-Vorlage eingeschlossen und einer Zeichen folgen Variablen wie folgt zugewiesen:  
  
```  
sQuery = "<ROOT xmlns:sql='urn:schemas-microsoft-com:xml-sql'>  
<sql:query> SELECT * FROM PRODUCTS ORDER BY PRODUCTNAME </sql:query>  
</ROOT>"  
```  
  
 Schreiben Sie anschließend die Zeichenfolge in den Stream:  
  
```  
adoStreamQuery.WriteText sQuery, adWriteChar  
adoStreamQuery.Position = 0  
```  
  
 Weisen Sie adostreamquery der **CommandStream** -Eigenschaft eines ADO- **Befehls** Objekts zu:  
  
```  
Dim adoCmd  
Set adoCmd  = Server.CreateObject("ADODB.Command"")  
adoCmd.CommandStream = adoStreamQuery  
```  
  
 Geben Sie den **Dialekt**der Befehlssprache an, der angibt, wie der SQL Server OLE DB Anbieters den Befehlsdaten Strom interpretieren soll. Der durch eine anbieterspezifische GUID angegebene Dialekt:  
  
```  
adoCmd.Dialect = "{5D531CB2-E6Ed-11D2-B252-00C04F681B71}"  
```  
  
 Führen Sie abschließend die Abfrage aus, und geben Sie die Ergebnisse an ein **Recordset** -Objekt zurück:  
  
```  
Set objRS = adoCmd.Execute  
```
