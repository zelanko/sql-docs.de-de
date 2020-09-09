---
description: sp_xml_preparedocument (Transact-SQL)
title: sp_xml_preparedocument (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_xml_preparedocument_TSQL
- sp_xml_preparedocument
dev_langs:
- TSQL
helpviewer_keywords:
- sp_xml_preparedocument
ms.assetid: 95f41cff-c52a-4182-8ac6-bf49369d214c
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 45aac298eea19f37fafdca1feb86a0b7f032c0e0
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89543008"
---
# <a name="sp_xml_preparedocument-transact-sql"></a>sp_xml_preparedocument (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Liest den als Eingabe bereitgestellten XML-Text, analysiert diesen mit dem MSXML-Parser (Msxmlsql.dll) und stellt das analysierte Dokument für die Verwendung bereit. Das analysierte Dokument ist eine strukturierte Darstellung der verschiedenen Knoten im XML-Dokument: Elemente, Attribute, Text, Kommentare usw.  
  
 **sp_xml_preparedocument** gibt ein Handle zurück, das für den Zugriff auf die neu erstellte interne Darstellung des XML-Dokuments verwendet werden kann. Dieses Handle ist für die Dauer der Sitzung oder bis zum invalidieren des Handles durch Ausführen von **sp_xml_removedocument**gültig.  
  
> [!NOTE]  
>  Ein analysiertes Dokument wird im internen Cache von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gespeichert. Der MSXML-Parser verwendet ein Achtel des gesamten für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verfügbaren Arbeitsspeichers. Führen Sie **sp_xml_removedocument** aus, um den Arbeitsspeicher freizugeben.  
  
> [!NOTE]  
>  Aus Gründen der Abwärtskompatibilität reduziert **sp_xml_preparedocument** die Zeichen CR (Char (13) und LF (Char (10)) in Attributen, auch wenn diese Zeichen in Entitäten geändert werden.  
  
> [!NOTE]  
>  Der von **sp_xml_preparedocument** aufgerufene XML-Parser kann interne DTDs und Entitäts Deklarationen analysieren. Da böswilliger erstellte DTDs und Entitäts Deklarationen verwendet werden können, um einen Denial-of-Service-Angriff auszuführen, wird dringend empfohlen, dass Benutzer nicht direkt XML-Dokumente aus nicht vertrauenswürdigen Quellen an **sp_xml_preparedocument**übergeben.  
>   
>  Um rekursive Entitäts Erweiterungs Angriffe zu vermeiden, 10.000 begrenzt **sp_xml_preparedocument** die Anzahl der Entitäten, die unter einer einzelnen Entität auf der obersten Ebene eines Dokuments erweitert werden können. Diese Grenze gilt nicht für Zeichen- oder numerische Entitäten. Die Grenze ermöglicht die Speicherung von Dokumenten mit zahlreichen Entitätsverweisen, verhindert jedoch die rekursive Erweiterung einer Entität in eine Kette von mehr als 10.000 Erweiterungen.  
  
> [!NOTE]  
>  **sp_xml_preparedocument** schränkt die Anzahl der Elemente ein, die gleichzeitig auf 256 geöffnet sein können.  

 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_xml_preparedocument  
hdoc   
OUTPUT  
[ , xmltext ]  
[ , xpath_namespaces ]   
```  
  
## <a name="arguments"></a>Argumente  
 *hdoc*  
 Das Handle für das gerade erstellte Dokument. *HDOC* ist eine ganze Zahl.  
  
 [ *XmlText* ]  
 Das ursprüngliche XML-Dokument. Der MSXML-Parser analysiert dieses XML-Dokument. *XmlText* ist ein Text Parameter: **char**, **NCHAR**, **varchar**, **nvarchar**, **Text**, **ntext** oder **XML**. Der Standardwert ist NULL; in diesem Fall wird eine interne Darstellung eines leeren XML-Dokuments erstellt.  
  
> [!NOTE]  
>  **sp_xml_preparedocument** können nur Text oder nicht typisiertes XML verarbeiten. Falls ein Instanzwert, der als Eingabewert verwendet werden soll, bereits ein typisierter XML-Wert ist, müssen Sie ihn zunächst in eine neue nicht typisierte XML-Instanz oder eine Zeichenfolge konvertieren und anschließend diesen Wert als Eingabewert übergeben. Weitere Informationen finden Sie unter [Vergleichen von typisiertem XML mit nicht typisiertem XML](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md).  
  
 [ *xpath_namespaces* ]  
 Gibt die Namespacedeklarationen an, die in XPATH-Ausdrücken für Zeilen und Spalten in OPENXML verwendet werden. *xpath_namespaces* ist ein Text Parameter: **char**, **NCHAR**, **varchar**, **nvarchar**, **Text**, **ntext** oder **XML**.  
  
 Der Standardwert ist **\<root xmlns:mp="urn:schemas-microsoft-com:xml-metaprop">** . *xpath_namespaces* stellt die Namespace-URIs für die Präfixe bereit, die in den XPath-Ausdrücken in OPENXML mithilfe eines wohlgeformten XML-Dokuments verwendet werden. *xpath_namespaces* deklariert das Präfix, das verwendet werden muss, um auf den Namespace **urn: Schemas-Microsoft-com: XML-metaprop**zu verweisen. Dadurch werden Metadaten zu den analysierten XML-Elementen bereitgestellt. Obwohl Sie das Namespacepräfix für den Namespace der Metaeigenschaften mit diesem Verfahren neu definieren können, geht dieser Namespace nicht verloren. Das Präfix- **MP** ist weiterhin gültig für **urn: Schemas-Microsoft-com: XML-metaprop** , auch wenn *xpath_namespaces* keine solche Deklaration enthält.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder >0 (Fehler)  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **public** -Rolle.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-preparing-an-internal-representation-for-a-well-formed-xml-document"></a>A. Erstellen einer internen Darstellung für ein wohlgeformtes XML-Dokument  
 Im folgenden Beispiel wird ein Handle für die neu erstellte interne Darstellung des als Eingabe bereitgestellten XML-Dokuments zurückgegeben. Im Aufruf von `sp_xml_preparedocument` wird die Standardzuordnung für das Namespacepräfix verwendet.  
  
```  
DECLARE @hdoc int;  
DECLARE @doc varchar(1000);  
SET @doc ='  
<ROOT>  
<Customer CustomerID="VINET" ContactName="Paul Henriot">  
   <Order CustomerID="VINET" EmployeeID="5" OrderDate="1996-07-04T00:00:00">  
      <OrderDetail OrderID="10248" ProductID="11" Quantity="12"/>  
      <OrderDetail OrderID="10248" ProductID="42" Quantity="10"/>  
   </Order>  
</Customer>  
<Customer CustomerID="LILAS" ContactName="Carlos Gonzlez">  
   <Order CustomerID="LILAS" EmployeeID="3" OrderDate="1996-08-16T00:00:00">  
      <OrderDetail OrderID="10283" ProductID="72" Quantity="3"/>  
   </Order>  
</Customer>  
</ROOT>';  
--Create an internal representation of the XML document.  
EXEC sp_xml_preparedocument @hdoc OUTPUT, @doc;  
-- Remove the internal representation.  
exec sp_xml_removedocument @hdoc;  
```  
  
### <a name="b-preparing-an-internal-representation-for-a-well-formed-xml-document-with-a-dtd"></a>B. Erstellen einer internen Darstellung für ein wohlgeformtes XML-Dokument mit einer DTD  
 Im folgenden Beispiel wird ein Handle für die neu erstellte interne Darstellung des als Eingabe bereitgestellten XML-Dokuments zurückgegeben. Die gespeicherte Prozedur überprüft das geladene Dokument in Bezug auf die im Dokument enthaltene DTD. Im Aufruf von `sp_xml_preparedocument` wird die Standardzuordnung für das Namespacepräfix verwendet.  
  
```  
DECLARE @hdoc int;  
DECLARE @doc varchar(2000);  
SET @doc = '  
<?xml version="1.0" encoding="UTF-8" ?>   
<!DOCTYPE root   
[<!ELEMENT root (Customers)*>  
<!ELEMENT Customers EMPTY>  
<!ATTLIST Customers CustomerID CDATA #IMPLIED ContactName CDATA #IMPLIED>]>  
<root>  
<Customers CustomerID="ALFKI" ContactName="Maria Anders"/>  
</root>';  
  
EXEC sp_xml_preparedocument @hdoc OUTPUT, @doc;  
```  
  
### <a name="c-specifying-a-namespace-uri"></a>C. Angeben eines Namespace-URI  
 Im folgenden Beispiel wird ein Handle für die neu erstellte interne Darstellung des als Eingabe bereitgestellten XML-Dokuments zurückgegeben. Der-Befehl, `sp_xml_preparedocument` der das `mp` Präfix für die Namespace Zuordnung der Metaeigenschaft beibehält, und fügt das Zuordnungspräfix dem `xyz` Namespace hinzu `urn:MyNamespace` .  
  
```  
DECLARE @hdoc int;  
DECLARE @doc varchar(1000);  
SET @doc ='  
<ROOT>  
<Customer CustomerID="VINET" ContactName="Paul Henriot">  
   <Order CustomerID="VINET" EmployeeID="5"   
           OrderDate="1996-07-04T00:00:00">  
      <OrderDetail OrderID="10248" ProductID="11" Quantity="12"/>  
      <OrderDetail OrderID="10248" ProductID="42" Quantity="10"/>  
   </Order>  
</Customer>  
<Customer CustomerID="LILAS" ContactName="Carlos Gonzlez">  
   <Order CustomerID="LILAS" EmployeeID="3"   
           OrderDate="1996-08-16T00:00:00">  
      <OrderDetail OrderID="10283" ProductID="72" Quantity="3"/>  
   </Order>  
</Customer>  
</ROOT>'  
--Create an internal representation of the XML document.  
EXEC sp_xml_preparedocument @hdoc OUTPUT, @doc, '<ROOT xmlns:xyz="urn:MyNamespace"/>';  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 <br>[Gespeicherte XML-Prozeduren (Transact-SQL)](../../relational-databases/system-stored-procedures/xml-stored-procedures-transact-sql.md)
 <br>[Gespeicherte System Prozeduren (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)
 <br>[OPENXML (Transact-SQL)](../../t-sql/functions/openxml-transact-sql.md)
 <br>[sys. dm_exec_xml_handles (Transact-SQL)](../system-dynamic-management-views/sys-dm-exec-xml-handles-transact-sql.md)
 <br>[sp_xml_removedocument (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-xml-removedocument-transact-sql.md)
  
  
