---
title: Angeben von expliziten Konvertierungsfunktionen in XPath-Abfragen (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- explicit conversion functions [SQLXML]
- string function
- number function
- XPath queries [SQLXML], explicit conversion functions
ms.assetid: 1111cb5d-2bd9-4bdb-8de2-dc0e47452dd6
caps.latest.revision: 24
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 59a2a54b1a3fe7a8136fa2ab0cb56f4cd215c245
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36058867"
---
# <a name="specifying-explicit-conversion-functions-in-xpath-queries-sqlxml-40"></a>Angeben von expliziten Konvertierungsfunktionen in XPath-Abfragen (SQLXML 4.0)
  In den folgenden Beispielen wird gezeigt, wie explizite Konvertierungsfunktionen in XPath-Abfragen angegeben werden. Die XPath-Abfragen in diesen Beispielen werden für das in SampleSchema1.xml enthaltene Zuordnungsschema angegeben. Informationen zu diesem Beispielschema finden Sie unter [Beispiel Annotated XSD-Schema für XPath-Beispiele &#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md).  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-use-the-number-explicit-conversion-function"></a>A. Verwenden der expliziten Konvertierungsfunktion number()  
 Die `number()`-Funktion konvertiert ein Argument in eine Zahl.  
  
 Wenn den Wert der **ContactID** ist nicht numerisch, die folgende Abfrage konvertiert **ContactID** in eine Zahl und vergleicht ihn mit dem Wert 4. Die Abfrage gibt dann alle  **\<Mitarbeiter >** untergeordneten-Elemente des Kontextknotens mit der **ContactID** -Attribut den numerischen Wert 4 aufweist:  
  
```  
/child::Contact[number(attribute::ContactID)= 4]  
```  
  
 Es kann eine Abkürzung für die `attribute`-Achse (@) angegeben werden, und da die `child`-Achse die Standardachse ist, muss sie in der Abfrage nicht angegeben werden:  
  
```  
/Contact[number(@ContactID) = 4]  
```  
  
 Anders ausgedrückt, gibt die Abfrage einen Mitarbeiter mit einem **ContactID** 4.  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a>So testen Sie die XPath-Abfrage mit dem Zuordnungsschema  
  
1.  Kopieren der [Schema Beispielcode](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) und fügen Sie ihn in eine Textdatei. Speichern Sie die Datei unter dem Dateinamen SampleSchema1.xml.  
  
2.  Erstellen Sie die folgende Vorlage (ExplicitConversionA.xml), und speichern Sie sie in dem Verzeichnis, in dem SampleSchema1.xml gespeichert wurde.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /Contact[number(@ContactID)=4]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Der für das Zuordnungsschema (SampleSchema1.xml) angegebene Verzeichnispfad bezieht sich auf das Verzeichnis, in dem die Vorlage gespeichert wird. Es kann auch ein absoluter Pfad angegeben werden. Beispiel:  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  Erstellen und verwenden Sie das SQLXML 4.0-Testskript (Sqlxml4test.vbs), um die Vorlage auszuführen.  
  
     Weitere Informationen finden Sie unter [mithilfe von ADO zum Ausführen von SQLXML 4.0-Abfragen](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Das Resultset für diese Vorlagenausführung sieht so aus:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Contact ContactID="4" LastName="Acevedo" FirstName="Humberto" Title="Sr." />   
</ROOT>  
```  
  
### <a name="b-use-the-string-explicit-conversion-function"></a>B. Verwenden der expliziten Konvertierungsfunktion string()  
 Die `string()`-Funktion konvertiert ein Argument in eine Zeichenfolge.  
  
 Die folgende Abfrage konvertiert **ContactID** zu einer Zeichenfolge und vergleicht Wert mit dem Zeichenfolgenwert "4". Die Abfrage gibt alle  **\<Mitarbeiter >** untergeordneten-Elemente des Kontextknotens mit einem **ContactID** mit einem Zeichenfolgenwert "4":  
  
```  
/child::Contact[string(attribute::ContactID)="4"]  
```  
  
 Es kann eine Abkürzung für die `attribute`-Achse (@) angegeben werden, und da die `child`-Achse die Standardachse ist, muss sie in der Abfrage nicht angegeben werden:  
  
```  
/Contact[string(@ContactID)="4"]  
```  
  
 Diese Abfrage gibt praktisch die gleichen Ergebnisse wie das vorherige Abfragebeispiel zurück, obwohl hier der Zeichenfolgenwert und nicht der numerische Wert (d. h. die Zahl 4) ausgewertet wird.  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a>So testen Sie die XPath-Abfrage mit dem Zuordnungsschema  
  
1.  Kopieren der [Schema Beispielcode](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) und fügen Sie ihn in eine Textdatei. Speichern Sie die Datei unter dem Dateinamen SampleSchema1.xml.  
  
2.  Erstellen Sie die folgende Vorlage (ExplicitConversionB.xml), und speichern Sie sie in dem Verzeichnis, in dem SampleSchema1.xml gespeichert wurde.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        Contact[string(@ContactID)="4"]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Der für das Zuordnungsschema (SampleSchema1.xml) angegebene Verzeichnispfad bezieht sich auf das Verzeichnis, in dem die Vorlage gespeichert wird. Es kann auch ein absoluter Pfad angegeben werden. Beispiel:  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  Erstellen und verwenden Sie das SQLXML 4.0-Testskript (Sqlxml4test.vbs), um die Vorlage auszuführen.  
  
     Weitere Informationen finden Sie unter [mithilfe von ADO zum Ausführen von SQLXML 4.0-Abfragen](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Im Folgenden finden Sie das Resultset der Vorlagenausführung:  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Contact ContactID="4" LastName="Acevedo" FirstName="Humberto" Title="Sr." />   
</ROOT>  
```  
  
  