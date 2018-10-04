---
title: Eine Auflistung der gespeicherten XML-Schemas anzeigen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- schema collections [SQL Server], viewing
- XML schemas [SQL Server], viewing
- CREATE XML SCHEMA COLLECTION statement
- xml_schema_namespace function
- XML schema collections [SQL Server], viewing
- displaying XML schema collections
- viewing XML schema collections
ms.assetid: e38031af-22df-4cd9-a14e-e316b822f91b
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 708aed70836bfc5fdccb9dd8ba3afc2545e093f3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48089320"
---
# <a name="view-a-stored-xml-schema-collection"></a>Anzeigen einer gespeicherten XML-Schemaauflistung
  Nach dem Importieren einer XML-Schemaauflistung mithilfe von [CREATE XML SCHEMA COLLECTION](/sql/t-sql/statements/create-xml-schema-collection-transact-sql)werden die Schemakomponenten in den Metadaten gespeichert. Mit der systeminternen Funktion [xml_schema_namespace](/sql/t-sql/xml/xml-schema-namespace)können Sie die XML-Schemaauflistung rekonstruieren. Diese Funktion gibt ein `xml` Datentypinstanz.  
  
 So ruft beispielsweise die folgende Abfrage eine XML-Schemaauflistung (`ProductDescriptionSchemaCollection`) aus dem relationalen Schema 'production' der [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] -Datenbank ab.  
  
```  
SELECT xml_schema_namespace(N'Production',N'ProductDescriptionSchemaCollection')  
GO  
```  
  
 Wenn nur ein Schema aus der XML-schemaauflistung angezeigt werden sollen, können Sie angeben, dass XQuery-Abfrage für die `xml` geben Ergebnis, das von zurückgegebene `xml_schema_namespace`.  
  
```  
SELECT xml_schema_namespace(N'RelationalSchemaName',N'XmlSchemaCollectionName').query('  
/xs:schema[@targetNamespace="TargetNameSpace"]  
')  
GO  
```  
  
 So ruft beispielsweise die folgende Abfrage XML-Schemainformationen zur Produktgarantie und -wartung aus der XML-Schemaauflistung `ProductDescriptionSchemaCollection` ab.  
  
```  
SELECT xml_schema_namespace(N'Production',N'ProductDescriptionSchemaCollection').query('  
/xs:schema[@targetNamespace="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain"]  
')  
GO  
```  
  
 Sie können auch den optionalen Zielnamespace als dritten Parameter an die `xml_schema_namespace` -Funktion übergeben, um ein bestimmtes Schema aus der Auflistung abzurufen, wie es in der folgenden Abfrage gezeigt wird:  
  
```  
SELECT xml_schema_namespace(N'Production',N'ProductDescriptionSchemaCollection', N'http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain')  
GO  
```  
  
 Wenn Sie eine XML-Schemaauflistung mithilfe von CREATE XML SCHEMA COLLECTION in der Datenbank erstellen, speichert die Anweisung die Schemakomponenten in den Metadaten. Beachten Sie, dass nur die von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] interpretierbaren Schemakomponenten gespeichert werden. Kommentare, Anmerkungen oder Nicht-XSD-Attribute werden nicht gespeichert. Daher ist das von **xml_schema_namespace** rekonstruierte Schema zwar hinsichtlich seiner Funktionalität mit dem ursprünglichen Schema gleichwertig, sein Erscheinungsbild jedoch nicht unbedingt identisch. Beispielsweise werden Sie die Präfixe des ursprünglichen Schemas nicht wiederfinden. Das von **xml_schema_namespace** zurückgegebene Schema verwendet **t** als Präfix für den Zielnamespace und **ns1**, **ns2**usw. für andere Namespaces.  
  
 Wenn Sie eine identische Kopie des XML-Schemas aufbewahren möchten, sollten Sie das XML-Schema in einer Datei oder in einer Datenbanktabelle in einer Spalte vom Typ `xml` speichern.  
  
 Die [sys.xml_schema_collections](/sql/relational-databases/system-catalog-views/sys-xml-schema-collections-transact-sql) -Katalogsicht gibt auch Informationen zu XML-Schemaauflistungen zurück. Zu diesen Informationen gehören der Name der Auflistung, das Erstellungsdatum und der Besitzer der Auflistung.  
  
## <a name="see-also"></a>Siehe auch  
 [XML-Schemaauflistungen &#40;SQL Server&#41;](xml-schema-collections-sql-server.md)  
  
  
