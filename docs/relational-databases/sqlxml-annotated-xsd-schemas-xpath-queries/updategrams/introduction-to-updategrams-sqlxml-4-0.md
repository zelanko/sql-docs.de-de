---
title: Einführung in Updategramms (SQLXML 4.0) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: sqlxml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- explicit schema mapping [SQLXML]
- updategrams [SQLXML], mapping schema specifying
- namespaces [SQLXML]
- updategrams [SQLXML], about updategrams
- attribute-centric mapping
- invalid characters [SQLXML]
- element-centric mapping [SQLXML]
- mapping schema [SQLXML], updategrams
- namespaces [SQLXML], updategrams
- executing updategrams [SQLXML]
- implicit schema mapping
ms.assetid: cfe24e82-a645-4f93-ab16-39c21f90cce6
caps.latest.revision: 12
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 77fb8dde53daeb779181a75ccc6b698c568e7a40
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43058788"
---
# <a name="introduction-to-updategrams-sqlxml-40"></a>Einführung in Updategrams (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Sie können ändern (einfügen, aktualisieren oder löschen) eine Datenbank in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] aus einem vorhandenen XML-Dokument mithilfe eines Updategrams oder der OPENXML- [!INCLUDE[tsql](../../../includes/tsql-md.md)] Funktion.  
  
 Die OPENXML-Funktion ändert eine Datenbank durch Aufteilen des vorhandenen XML-Dokuments und Bereitstellen eines Rowsets, das an eine INSERT-, UPDATE- oder DELETE-Anweisung übergeben werden kann. Mit OPENXML werden Operationen direkt für die Datenbanktabellen ausgeführt. Daher eignet sich OPENXML besonders gut, wenn Rowsetanbieter, wie Tabellen, als Quelle auftreten können.  
  
 Wie mit OPENXML können Sie mit einem Updategram Daten in der Datenbank einfügen, aktualisieren oder löschen. Ein Updategram wird jedoch für die XML-Sichten verwendet, die vom XSD-Schema (oder einem XDR-Schema) bereitgestellt werden. So werden beispielsweise die Updates auf die vom Zuordnungsschema bereitgestellte XML-Sicht angewendet. Das Zuordnungsschema enthält die erforderlichen Informationen zum Zuordnen von XML-Elementen und -Attributen zu den entsprechenden Datenbanktabellen und -spalten. Das Updategram verwendet diese Zuordnungsinformationen zum Aktualisieren der Datenbanktabellen und -spalten.  
  
> [!NOTE]  
>  Diese Dokumentation setzt voraus, dass Sie mit Vorlagen und der Unterstützung von Zuordnungsschemas in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] vertraut sind. Weitere Informationen finden Sie unter [Einführung in XSD-Schemas mit Anmerkungen versehen &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md). Für ältere Anwendungen, die XDR verwenden, finden Sie unter [XDR-Schemas mit Anmerkungen versehen &#40;in SQLXML 4.0 veraltet&#41;](../../../relational-databases/sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md).  
  
## <a name="required-namespaces-in-the-updategram"></a>Erforderliche Namespaces im Updategram  
 Die Schlüsselwörter in einem Updategram, wie z. B.  **\<Sync >**,  **\<vor >**, und  **\<nach >**, vorhanden sind, in der **Urn: Schemas-Microsoft-com: XML-Updategrams** Namespace. Sie können ein beliebiges Namespacepräfix verwenden. In dieser Dokumentation wird die **Updg** Präfix bezeichnet das **Updategram** Namespace.  
  
## <a name="reviewing-syntax"></a>Überprüfen der Syntax  
 Ein Updategram ist eine Vorlage mit  **\<Sync >**,  **\<vor >**, und  **\<nach >** Blöcke, die die Syntax der bilden die Updategram. Der folgende Code zeigt diese Syntax in ihrer einfachsten Form:  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync [mapping-schema= "AnnotatedSchemaFile.xml"] >  
    <updg:before>  
        ...  
    </updg:before>  
    <updg:after>  
        ...  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 In den folgenden Definitionen werden die Rollen der einzelnen Blöcke beschrieben:  
  
 **\<before>**  
 Identifiziert den vorhandenen Status (auch als "Vorher-Status" bezeichnet) der Datensatzinstanz.  
  
 **\<after>**  
 Identifiziert den neuen Status, in den Daten geändert werden sollen.  
  
 **\<sync>**  
 Enthält die  **\<vor >** und  **\<nach >** Blöcke. Ein  **\<Sync >** Block kann mehr als ein Satz von enthalten  **\<vor >** und  **\<nach >** Blöcke. Wenn es mehr als eine Reihe von gibt  **\<vor >** und  **\<nach >** blockiert und diese Blöcke (selbst wenn sie leer sind) müssen paarweise angegeben werden. Darüber hinaus ein Updategram kann mehr als einen haben  **\<Sync >** Block. Jede  **\<Sync >** Block ist eine Transaktionseinheit (was bedeutet, dass entweder der gesamte der  **\<Sync >** -Block oder nichts ausgeführt). Bei Angabe mehrerer  **\<Sync >** , freigegebene Blöcke in einem Updategram, das beim Ausfall eines  **\<Sync >** Block hat keine Auswirkungen auf die andere  **\<synchronisieren >** Blöcke.  
  
 Gibt an, ob ein Updategram löscht, einfügt oder aktualisiert eine Datensatzinstanz hängt von den Inhalt der  **\<vor >** und  **\<nach >** Blöcken:  
  
-   Kommt eine nur im Datensatzinstanz der  **\<vor >** -Block ohne entsprechende Instanz in der  **\<nach >** das Updategram-Block führt einen Löschvorgang aus.  
  
-   Kommt eine nur im Datensatzinstanz der  **\<nach >** -Block ohne entsprechende Instanz in der  **\<vor >** blockieren, es ist ein Einfügevorgang.  
  
-   Kommt eine im Datensatzinstanz der  **\<vor >** blockieren und verfügt über eine entsprechende Instanz der  **\<nach >** Block, es ist ein Updatevorgang. In diesem Fall das Updategram die Datensatzinstanz, die Werte, die im angegebenen aktualisiert die  **\<nach >** Block.  
  
## <a name="specifying-a-mapping-schema-in-the-updategram"></a>Angeben eines Zuordnungsschemas im Updategram  
 In einem Updategram kann die von einem Zuordnungsschema (sowohl XSD- als auch XDR-Schemas werden unterstützt) bereitgestellte XML-Abstraktion implizit oder explizit sein (d. h., ein Updategram kann mit angegebenem Zuordnungsschema oder ohne angegebenes Zuordnungsschema verwendet werden). Wenn Sie kein Zuordnungsschema angeben, wird das Updategram eine implizite Zuordnung (standardzuordnung) vorausgesetzt, wobei jedes Element in der  **\<vor >** Block oder  **\<nach >** Block ordnet einer Tabelle und eines jeden Elements untergeordnete Element oder Attribut an eine Spalte in der Datenbank zugeordnet. Wenn Sie ausdrücklich ein Zuordnungsschema angeben, müssen die Elemente und Attribute im Updategram mit den Elementen und Attributen im Zuordnungsschema übereinstimmen.  
  
### <a name="implicit-default-mapping"></a>Implizite Zuordnung (Standardzuordnung)  
 Ein Updategram, das einfache Updates durchführt, benötigt in der Regel kein Zuordnungsschema. In diesem Fall verwendet das Updategram das Standardzuordnungsschema.  
  
 Das folgende Updategram zeigt eine implizite Zuordnung. In diesem Beispiel fügt das Updategram einen neuen Kunden in die Sales.Customer-Tabelle ein. Da das Updategram die implizite Zuordnung, verwendet der \<Sales.Customer >-Element der Sales.Customer-Tabelle zugeordnet, und die Attribute CustomerID und SalesPersonID den entsprechenden Spalten in der Sales.Customer-Tabelle zugeordnet.  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync >  
<updg:before>  
</updg:before>  
<updg:after>  
    <Sales.Customer CustomerID="1" SalesPersonID="277" />  
    </updg:after>  
</updg:sync>  
</ROOT>  
```  
  
### <a name="explicit-mapping"></a>Explizite Zuordnung  
 Wenn Sie ein Zuordnungsschema angeben (XSD oder XDR) verwendet das Updategram das Schema um zu bestimmen, welche Datenbanktabellen und -spalten aktualisiert werden sollen.  
  
 Wenn das Updategram ein komplexes Update (z. B. Einfügen von Datensätzen in mehreren Tabellen anhand der über-/ unterordnungsbeziehung, die im Zuordnungsschema angegeben wird) ausgeführt wird, müssen Sie das Zuordnungsschema explizit angeben, mit der  **Mapping-Schema** Attribut, für das Updategram ausgeführt wird.  
  
 Da ein Updategram eine Vorlage ist, ist der für das Zuordnungsschema im Updategram angegebene Pfad bezieht sich auf den Speicherort der Vorlagendatei (relativ zum Speicherort des Updategrams). Weitere Informationen finden Sie unter [angeben eines Zuordnungsschemas in einem Updategram &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).  
  
## <a name="element-centric-and-attribute-centric-mapping-in-updategrams"></a>Elementzentrierte und attributzentrierte Zuordnung in Updategrams  
 Bei der Standardzuordnung (wenn im Updategram kein Zuordnungsschema angegeben ist) werden die Updategramelemente Tabellen und die untergeordneten Elemente (bei der elementzentrierten Zuordnung) und die Attribute (bei der attributzentrierten Zuordnung) Spalten zugeordnet.  
  
### <a name="element-centric-mapping"></a>Elementzentrierte Zuordnung  
 Ein Element in einem elementzentrierten Updategram enthält untergeordnete Elemente, die die Eigenschaften des Elements angeben. Ein Beispiel finden Sie im folgenden Updategram. Die  **\<Person.Contact >** Element enthält die  **\<FirstName >** und  **\<"LastName" >** untergeordnete Elemente. Diese untergeordneten Elemente sind Eigenschaften der  **\<Person.Contact >** Element.  
  
 Da es sich bei diesem Updategram kein Zuordnungsschema angegeben ist, verwendet das Updategram die implizite Zuordnung, in denen die  **\<Person.Contact >** Element wird der Person.Contact-Tabelle und seine untergeordneten Elemente auf das FirstName und LastName-Spalten.  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync >  
  <updg:after>  
    <Person.Contact>  
       <FirstName>Catherine</FirstName>  
       <LastName>Abel</LastName>  
    </Person.Contact>  
  </updg:after>  
</updg:sync>  
</ROOT>  
```  
  
### <a name="attribute-centric-mapping"></a>Attributzentrierte Zuordnung  
 Die Elemente in einer attributzentrierten Zuordnung verfügen über Attribute. Im folgenden Updategram wird die attributzentrierte Zuordnung verwendet. In diesem Beispiel die  **\<Person.Contact >** Element besteht aus den **FirstName** und **"LastName"** Attribute. Diese Attribute sind die Eigenschaften der  **\<Person.Contact >** Element. Wie im vorherigen Beispiel, in diesem Updategram kein Zuordnungsschema angegeben, daher implizit zugeordnet der  **\<Person.Contact >** -Element der Person.Contact-Tabelle und die Attribute des Elements auf der entsprechende Spalten in der Tabelle.  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync >  
  <updg:before>  
  </updg:before>  
  <updg:after>  
    <Person.Contact FirstName="Catherine" LastName="Abel" />  
  </updg:after>  
</updg:sync>  
</ROOT>  
```  
  
### <a name="using-both-element-centric-and-attribute-centric-mapping"></a>Verwenden der elementzentrierten und der attributzentrierten Zuordnung  
 Sie können eine Mischung elementzentrierter und attributzentrierter Zuordnung angeben, wie im folgenden Updategram dargestellt. Beachten Sie, dass die  **\<Person.Contact >** -Element enthält sowohl ein Attribut als auch ein untergeordnetes Element. Für dieses Updategram wird die implizite Zuordnung verwendet. Daher die **FirstName** Attribut und die  **\<"LastName" >** untergeordneten Element entsprechenden Spalten in der Person.Contact-Tabelle zugeordnet.  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync >  
  <updg:before>  
  </updg:before>  
  <updg:after>  
    <Person.Contact FirstName="Catherine" >  
       <LastName>Abel</LastName>  
    </Person.Contact>  
  </updg:after>  
</updg:sync>  
</ROOT>  
```  
  
## <a name="working-with-characters-valid-in-sql-server-but-not-valid-in-xml"></a>Verwenden von Zeichen, die in SQL Server gültig sind, in XML jedoch nicht  
 In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dürfen Tabellennamen Leerzeichen enthalten. Dieser Tabellennamentyp ist in XML jedoch nicht gültig.  
  
 Zum Codieren von Zeichen, die gültig sind [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Bezeichner, sind jedoch keine gültigen XML-Bezeichner, verwenden Sie ' __xHHHH\_\_' als Codierungswert, wobei HHHH für den vierstelligen hexadezimalen UCS-2-Code für das Zeichen in der meisten steht erhebliche Bitfolge. Verwenden dieses Codierungsschema, ruft ein Leerzeichen durch X0020 (der vierstellige hexadezimale Code für ein Leerzeichen) ersetzt. daher den Tabellennamen [Order Details] in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] wird _x005B_Order_x0020_Details_x005D\_ im XML-Format.  
  
 Auf ähnliche Weise müssen möglicherweise dreiteilige Elementnamen angeben, z. B. \<[Database]. [ Owner]. [Table] >. Da die Klammern ([ und ]) in XML nicht gültig sind, müssen Sie dies als angeben \<_x005B_database_x005D\_._x005B_owner_x005D\_._x005B_table_x005D\_>, wobei _x005B\_ ist die Codierung für die öffnende Klammer ([) und _x005D\_ ist die Codierung für die Rechte Klammer (]).  
  
## <a name="executing-updategrams"></a>Ausführen von Updategrams  
 Da ein Updategram eine Vorlage ist, gelten alle Verarbeitungsmechanismen einer Vorlage auch für ein Updategram. Zum Ausführen eines Updategrams in SQLXML 4.0 können Sie eine der beiden folgenden Möglichkeiten verwenden:  
  
-   Senden des Updategrams in einem ADO-Befehl  
  
-   Senden des Updategrams in einem OLE DB-Befehl  
  
## <a name="see-also"></a>Siehe auch  
 [Sicherheitsüberlegungen zu Updategramms &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
