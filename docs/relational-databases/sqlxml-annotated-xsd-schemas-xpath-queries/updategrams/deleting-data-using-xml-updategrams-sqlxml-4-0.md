---
title: Löschen von Daten mit XML-Update grams (SQLXML)
description: Erfahren Sie, wie Sie Daten mithilfe eines XML-Update Grams in SQLXML 4,0 löschen.
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- <after> block
- updategrams [SQLXML], deleting data
- <before> block
- mapping-schema attribute
- record deletions [SQLXML]
ms.assetid: 4fb116d7-7652-474a-a567-cb475a20765c
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: f32c1107d886b7bc84590abbd6bab5343d2a2b8b
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2020
ms.locfileid: "84529824"
---
# <a name="deleting-data-using-xml-updategrams-sqlxml-40"></a>Löschen von Daten mit XML-Updategrams (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Ein Update Gram gibt einen Löschvorgang an, wenn eine Daten Satz Instanz im- **\<before>** Block ohne entsprechende Datensätze im-Block angezeigt wird **\<after>** . In diesem Fall löscht das Update Gram den Datensatz im- **\<before>** Block aus der Datenbank.  
  
 Dies ist das Updategramformat für einen Löschvorgang:  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync [mapping-schema="SampleSchema.xml"]  >  
   <updg:before>  
       <ElementName />  
      [<ElementName .../>... ]  
   </updg:before>  
    [<updg:after>  
    </updg:after>]  
  </updg:sync>  
</ROOT>  
```  
  
 Sie können das-Tag weglassen, **\<after>** Wenn das Update Gram nur einen Löschvorgang ausführt. Wenn Sie das optionale **Mapping-Schema-** Attribut nicht angeben, wird der **\<ElementName>** im Update Gram angegebene einer Datenbanktabelle zugeordnet, und die untergeordneten Elemente oder Attribute werden den Spalten in der Tabelle zugeordnet.  
  
 Wenn ein im Update Gram angegebenes Element entweder mehr als eine Zeile in der Tabelle oder nicht mit einer Zeile übereinstimmt, gibt das Update Gram einen Fehler zurück und bricht den gesamten **\<sync>** Block ab. Nur ein Datensatz kann gleichzeitig von einem Element im Updategram gelöscht werden.  
  
## <a name="examples"></a>Beispiele  
 Die Beispiele in diesem Abschnitt verwenden die Standardzuordnung (d. h. es ist kein Zuordnungsschema im Updategram angegeben). Weitere Beispiele für Update grams, die Mapping-Schemas verwenden, finden Sie unter [Angeben eines Mappingschemas mit Anmerkungen in einem Update Gram &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).  
  
 Wenn Sie in den folgenden Beispielen funktionierende Beispiele erstellen möchten, müssen Sie die unter [Anforderungen zum Ausführen von SQLXML-Beispielen](../../../relational-databases/sqlxml/requirements-for-running-sqlxml-examples.md)angegebenen Anforderungen erfüllen.  
  
### <a name="a-deleting-a-record-by-using-an-updategram"></a>A. Löschen eines Datensatzes mithilfe eines Updategrams  
 Die folgenden Updategrams löschen zwei Datensätze aus der Tabelle HumanResources.Shift.  
  
 In diesen Beispielen gibt das Updategram kein Zuordnungsschema an. Daher verwendet das Updategram die Standardzuordnung, in der der Elementname einem Tabellennamen, und die Attribute oder untergeordneten Elemente den Spalten in dieser Tabelle zugeordnet werden.  
  
 Dieses erste Update Gram ist Attribut zentriert und identifiziert zwei Verschiebungen (Tag-Abend und Abend-Nacht) im- **\<before>** Block. Da es keinen entsprechenden Datensatz im-Block gibt, handelt es sich hierbei **\<after>** um einen Löschvorgang.  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync >  
  <updg:before>  
       <HumanResources.Shift ShiftID="4"  
                        Name="Day-Evening"  
                        StartTime="1900-01-01 11:00:00.000"  
                        EndTime="1900-01-01 19:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
       <HumanResources.Shift ShiftID="5"  
                        Name="Evening-Night"  
                        StartTime="1900-01-01 19:00:00.000"  
                        EndTime="1900-01-01 03:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
  </updg:before>  
  <updg:after>  
  </updg:after>  
</updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a>So testen Sie das Updategram  
  
1.  Vervollständigen Sie Beispiel B ("Einfügen mehrerer Datensätze mithilfe eines Update grams") in das [Einfügen von Daten mit XML-Update grams &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/inserting-data-using-xml-updategrams-sqlxml-4-0.md).  
  
2.  Kopieren Sie das oben angegebene Update Gram in Editor, und speichern Sie es als Updategram-RemoveShifts.xml im selben Ordner, in dem Sie den Vorgang durchgeführt haben ("Einfügen mehrerer Datensätze mithilfe eines Update grams"), [indem Sie Daten mithilfe von XML-Update grams &#40;SQLXML 4,0&#41;einfügen ](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/inserting-data-using-xml-updategrams-sqlxml-4-0.md).  
  
3.  Erstellen und verwenden Sie das SQLXML 4.0-Testskript (Sqlxml4test.vbs), um das Updategram auszuführen.  
  
     Weitere Informationen finden Sie unter [Verwenden von ADO zum Ausführen von SQLXML 4,0-Abfragen](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sicherheitsüberlegungen zu Update grams &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
