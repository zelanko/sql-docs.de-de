---
title: Server seitige XML-Formatierung (SQLXML 4,0) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- FOR XML clause, formatting
- server-side XML formatting
ms.assetid: ae9ea068-0857-4505-a3b2-f53d256b644c
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 13e20c9c4b415ad5dabc53baad813126a81afcae
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/01/2020
ms.locfileid: "82702875"
---
# <a name="server-side-xml-formatting-sqlxml-40"></a>Serverseitige XML-Formatierung (SQLXML 4.0)
  Dieses Thema enthält Informationen über das serverseitige Formatieren von XML-Dokumenten aus den Rowsets, die von Abfragen generiert werden, die in einer Datenbank in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ausgeführt werden.  
  
 In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] können Sie XML-Dokumente in Datenbanktabellen speichern und aus Datenbanktabellen abrufen. Um ein XML-Dokument abzurufen, verwenden Sie die FOR XML-Abfrageerweiterung in einer SELECT-Abfrage.  
  
 Nehmen Sie beispielsweise an, eine Client Anwendung führt einen Befehl für aus, der aus [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] der folgenden [!INCLUDE[tsql](../../../includes/tsql-md.md)] Abfrage besteht:  
  
```  
SELECT FirstName, LastName  
FROM   Person.Contact  
FOR XML AUTO  
```  
  
 Der Server führt die Abfrage in zwei Schritten aus. Zuerst führt der Server diese SELECT-Anweisung aus:  
  
```  
SELECT FirstName, LastName  
FROM   Person.Contact  
```  
  
 Dann wendet der Server die FOR XML-Transformation auf das generierte Rowset an. Der resultierende XML-Code wird dann an den Client als ein einspaltiges Rowset gesendet. In dieser Dokumentation wird dieser Prozess als serverseitige XML-Formatierung bezeichnet.  
  
 Auf der Serverseite können Sie die folgenden Modi mit einer FOR XML-Klausel angeben:  
  
-   RAW  
  
-   AUTO  
  
-   EXPLICIT  
  
 Weitere Informationen zur for XML-Klausel finden Sie unter [Erstellen von XML mithilfe von for XML](../../xml/for-xml-sql-server.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Architektur der Client seitigen und Server seitigen XML-Formatierung &#40;SQLXML 4,0&#41;](architecture-of-client-side-and-server-side-xml-formatting-sqlxml-4-0.md)   
 [Client seitige XML-Formatierung &#40;SQLXML 4,0&#41;](client-side-xml-formatting-sqlxml-4-0.md)   
 [FOR XML &#40;SQL Server&#41;](../../xml/for-xml-sql-server.md)  
  
  
