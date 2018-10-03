---
title: SQLXML-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 7c67be98-efb5-446c-a0e3-ee67c43cb170
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6257f3575412bc35b00722a0b5da6b8c5ca74f10
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47815998"
---
# <a name="sqlxml-interface"></a>SQLXML-Schnittstelle

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

JDBC Driver bietet Unterstützung für die JDBC 4.0-API, in der die java.sql.SQLXML-Schnittstelle eingeführt wird. Die SQLXML-Schnittstelle definiert Methoden für die Interaktion mit und die Bearbeitung von XML-Daten. Die **SQLXML** -Datentyp zugeordnet, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Xml** -Datentyp.  
  
Die SQLXML-Schnittstelle bietet Methoden für den Zugriff auf den XML-Wert als eine **Zeichenfolge**, **Reader** oder **Writer**, oder als eine **Stream**. Der Zugriff auf den XML-Wert ist auch über eine **Quelle** möglich, und er kann als **Ergebnis** festgelegt werden. Diese werden mit XML-Parser-APIs wie DOM (Document Object Model), SAX (Simple API for XML) und StAX (Streaming API for XML) sowie mit XSLT-Transformationen und XPath verwendet.  
  
## <a name="remarks"></a>Remarks  

In der folgenden Tabelle werden die in der SQLXML-Schnittstelle definierten Methoden beschrieben:  
  
|Methodensyntax|Methodenbeschreibung|  
|-------------------|------------------------|  
|[void free()](http://go.microsoft.com/fwlink/?LinkId=131685)|Mit dieser Methode werden das SQLXML-Objekt und die von diesem verwendeten Ressourcen freigegeben.|  
|[InputStream getBinaryStream()](http://go.microsoft.com/fwlink/?LinkId=131754)|Gibt einen Eingabedatenstrom zum Lesen von Daten aus dem SQLXML zurück.|  
|[Reader getCharacterStream()](http://go.microsoft.com/fwlink/?LinkId=131755)|Gibt die **XML**-Daten als java.io.Reader-Objekt oder als Zeichendatenstrom zurück.|  
|[T erweitert Quelle T GetSource (Klasse\<T > SourceClass)](http://go.microsoft.com/fwlink/?LinkId=131756)|Gibt eine **Quelle** zum Lesen der **XML** Wert angegeben, die von diesem **SQLXML** Objekt.<br /><br /> **Hinweis:** Die Methode „getSource“ unterstützt die folgenden Quellen: javax.xml.transform.dom.DOMSource, javax.xml.transform.sax.SAXSource, javax.xml.transform.stax.StAXSource und java.io.InputStream.|  
|[String getString()](http://go.microsoft.com/fwlink/?LinkId=131757)|Gibt eine Zeichenfolgendarstellung des **XML**-Werts zurück, der von diesem SQLXML-Objekt angegeben wird.|  
|[OutputStream setBinaryStream()](http://go.microsoft.com/fwlink/?LinkId=131758)|Ruft einen Datenstrom ab, der zum Schreiben des **XML**-Werts verwendet werden kann, der von diesem SQLXML-Objekt angegeben wird.|  
|[Writer setCharacterStream()](http://go.microsoft.com/fwlink/?LinkId=131759)|Gibt einen Datenstrom zurück, der zum Schreiben des **XML**-Werts verwendet werden kann, der von diesem SQLXML-Objekt angegeben wird.|  
|[T erweitert Ergebnis T SetResult (Klasse\<T > ResultClass)](http://go.microsoft.com/fwlink/?LinkId=131760)|Gibt eine **Ergebnis** für die Einstellung der **XML** Wert angegeben, die von diesem **SQLXML** Objekt.<br /><br /> **Hinweis:** Die Methode „setResult“ unterstützt die folgenden Quellen: javax.xml.transform.dom.DOMResult, javax.xml.transform.sax.SAXResult, javax.xml.transform.stax.StaxResult und java.io.OutputStream.|  
|[void setString(String value)](http://go.microsoft.com/fwlink/?LinkId=131762)|Legt den von diesem SQLXML-Objekt angegebenen XML-Wert auf die angegebene **String**-Darstellung fest.|  
  
Die Anwendungen können XML-Werte nur einmal aus einem SQLXML-Objekt lesen bzw. in dieses schreiben.  
  
Nach dem Aufrufen der Methode „free()“ wird ein SQLXML-Objekt ungültig und kann weder gelesen noch geschrieben werden. Wenn die Anwendung versucht, für das SQLXML-Objekt eine andere Methode als „free()“ aufzurufen, wird eine Ausnahme ausgelöst.  
  
Das SQLXML-Objekt nicht mehr gelesen oder beschreibbaren beim Aufrufen einer der folgenden Abrufmethoden: GetSource, GetCharacterStream, GetBinaryStream, und GetString.  
  
Das SQLXML-Objekt wird beschreibbaren weder lesbar, wenn die Anwendung eine der folgenden festlegungsmethoden aufruft: SetResult, SetCharacterStream, SetBinaryStream, und SetString.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  

[Unterstützen von XML-Daten](../../connect/jdbc/supporting-xml-data.md)  
