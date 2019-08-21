---
title: SQLXML-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 7c67be98-efb5-446c-a0e3-ee67c43cb170
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 72cccce89d5e30a92f38b956c8b7996949d3bb46
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2019
ms.locfileid: "69027699"
---
# <a name="sqlxml-interface"></a>SQLXML-Schnittstelle

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

JDBC Driver bietet Unterstützung für die JDBC 4.0-API, in der die java.sql.SQLXML-Schnittstelle eingeführt wird. Die SQLXML-Schnittstelle definiert Methoden für die Interaktion mit und die Bearbeitung von XML-Daten. Der **SQLXML** -Datentyp wird dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **XML** -Datentyp zugeordnet.  
  
Die SQLXML-Schnittstelle stellt Methoden für den Zugriff auf den XML-Wert als **Zeichen**Folge, als **Reader** oder **Writer**oder als **Stream**bereit. Der Zugriff auf den XML-Wert ist auch über eine **Quelle** möglich, und er kann als **Ergebnis** festgelegt werden. Diese werden mit XML-Parser-APIs wie DOM (Document Object Model), SAX (Simple API for XML) und StAX (Streaming API for XML) sowie mit XSLT-Transformationen und XPath verwendet.  
  
## <a name="remarks"></a>Remarks  

In der folgenden Tabelle werden die in der SQLXML-Schnittstelle definierten Methoden beschrieben:  
  
|Methodensyntax|Methodenbeschreibung|  
|-------------------|------------------------|  
|[void free()](https://go.microsoft.com/fwlink/?LinkId=131685)|Mit dieser Methode werden das SQLXML-Objekt und die von diesem verwendeten Ressourcen freigegeben.|  
|[InputStream getBinaryStream()](https://go.microsoft.com/fwlink/?LinkId=131754)|Gibt einen Eingabedatenstrom zum Lesen von Daten aus dem SQLXML zurück.|  
|[Reader getCharacterStream()](https://go.microsoft.com/fwlink/?LinkId=131755)|Gibt die **XML**-Daten als java.io.Reader-Objekt oder als Zeichendatenstrom zurück.|  
|[T erweitert Quelle t GetSource (Klasse\<t > SourceClass)](https://go.microsoft.com/fwlink/?LinkId=131756)|Gibt eine **Quelle** zum Lesen des **XML** -Werts zurück, der von diesem **SQLXML** -Objekt angegeben wird.<br /><br /> **Hinweis:** Die Methode „getSource“ unterstützt die folgenden Quellen: javax.xml.transform.dom.DOMSource, javax.xml.transform.sax.SAXSource, javax.xml.transform.stax.StAXSource und java.io.InputStream.|  
|[String getString()](https://go.microsoft.com/fwlink/?LinkId=131757)|Gibt eine Zeichenfolgendarstellung des **XML**-Werts zurück, der von diesem SQLXML-Objekt angegeben wird.|  
|[OutputStream setBinaryStream()](https://go.microsoft.com/fwlink/?LinkId=131758)|Ruft einen Datenstrom ab, der zum Schreiben des **XML**-Werts verwendet werden kann, der von diesem SQLXML-Objekt angegeben wird.|  
|[Writer setCharacterStream()](https://go.microsoft.com/fwlink/?LinkId=131759)|Gibt einen Datenstrom zurück, der zum Schreiben des **XML**-Werts verwendet werden kann, der von diesem SQLXML-Objekt angegeben wird.|  
|[T erweitert Ergebnis t setResult (Klasse\<t > resultClass)](https://go.microsoft.com/fwlink/?LinkId=131760)|Gibt ein **Ergebnis** zum Festlegen des **XML** -Werts zurück, der von diesem **SQLXML** -Objekt angegeben wird.<br /><br /> **Hinweis:** Die Methode „setResult“ unterstützt die folgenden Quellen: javax.xml.transform.dom.DOMResult, javax.xml.transform.sax.SAXResult, javax.xml.transform.stax.StaxResult und java.io.OutputStream.|  
|[void setString(String value)](https://go.microsoft.com/fwlink/?LinkId=131762)|Legt den von diesem SQLXML-Objekt angegebenen XML-Wert auf die angegebene **String**-Darstellung fest.|  
  
Die Anwendungen können XML-Werte nur einmal aus einem SQLXML-Objekt lesen bzw. in dieses schreiben.  
  
Nach dem Aufrufen der Methode „free()“ wird ein SQLXML-Objekt ungültig und kann weder gelesen noch geschrieben werden. Wenn die Anwendung versucht, für das SQLXML-Objekt eine andere Methode als „free()“ aufzurufen, wird eine Ausnahme ausgelöst.  
  
Das SQLXML-Objekt ist weder lesbar noch beschreibbar, wenn eine der folgenden Getter-Methoden von der Anwendung aufgerufen wird: GetSource, getcharakteristream, getBinaryStream und GetString.  
  
Das SQLXML-Objekt wird weder beschreibbar noch lesbar, wenn die Anwendung eine der folgenden Setter-Methoden aufruft: setResult, setcharakteristream, setBinaryStream und SetString.  
  
## <a name="see-also"></a>Siehe auch  

[Unterstützen von XML-Daten](../../connect/jdbc/supporting-xml-data.md)  
