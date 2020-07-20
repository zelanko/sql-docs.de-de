---
title: xml_schema_namespace (Transact-SQL)
ms.custom: ''
ms.date: 07/27/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- xml_schema_namespace_TSQL
- xml_schema_namespace
dev_langs:
- TSQL
helpviewer_keywords:
- XML schema collections [SQL Server], reconstructing schemas
- xml_schema_namespace function
- reconstructing schemas
- schemas [SQL Server], XML
- schema collections [SQL Server], reconstructing schemas
ms.assetid: ee9873d8-dd3a-4bff-a10c-68bbadbdf1a6
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4f3035f1883f12924956958ab35ac4f3ca571814
ms.sourcegitcommit: cb620c77fe6bdefb975968837706750c31048d46
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2020
ms.locfileid: "86391855"
---
# <a name="xml_schema_namespace"></a>xml_schema_namespace
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Rekonstruiert alle Schemas oder ein bestimmtes Schema in der angegebenen XML-Schemaauflistung. Diese Funktion gibt eine Instanz vom Datentyp **xml** zurück.  
  
![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntax  
  
```  
  
xml_schema_namespace( Relational_schema , XML_schema_collection_name , [ Namespace ] )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Argumente
 *Relational_schema*  
 Der Name des relationalen Schemas. *Relational_schema* ist vom Datentyp **sysname**.  
  
 *XML_schema_collection_name*  
 Der Name der XML-Schemaauflistung, die rekonstruiert werden soll. *XML_schema_collection_name* ist vom Datentyp **sysname**.  
  
 *Namespace*  
 Der Namespace-URI des zu rekonstruierenden XML-Schemas. Die Eingabe ist auf 1.000 Zeichen beschränkt. Wenn kein Namespace-URI bereitgestellt wurde, wird die gesamte XML-Schemaauflistung rekonstruiert. *Namespace* ist vom Datentyp **nvarchar(4000)** .  
  
## <a name="return-types"></a>Rückgabetypen  
 **xml**  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn Sie XML-Schemakomponenten in der Datenbank mithilfe von [CREATE XML SCHEMA COLLECTION](../../t-sql/statements/create-xml-schema-collection-transact-sql.md) oder [ALTER XML SCHEMA COLLECTION](../../t-sql/statements/alter-xml-schema-collection-transact-sql.md) importieren, bleiben Aspekte des Schemas erhalten, die zur Überprüfung verwendet werden. Deshalb kann es sein, dass das rekonstruierte Schema lexikalisch nicht mit dem ursprünglichen Schemadokument identisch ist. Insbesondere Kommentare, Leerzeichen und Anmerkungen gehen verloren; und implizite Informationen werden zu expliziten Informationen. \<xs:element name="e1" /> wird beispielsweise zu \<xs:element name="e1" type="xs:anyType"/>. Außerdem werden Namespacepräfixe nicht beibehalten.  
  
 Wenn Sie einen Namespaceparameter angeben, enthält das resultierende Schemadokument Definitionen für alle Schemakomponenten in diesem Namespace, selbst wenn sie in verschiedenen Schemadokumenten und/oder DDL-Schritten hinzugefügt wurden.  
  
 Mit dieser Funktion können keine XML-Schemadokumente von der XML-Schemaauflistung **sys.sys** erstellt werden.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die XML-Schemaauflistung `ProductDescriptionSchemaCollection` vom relationalen Schema Production in der `AdventureWorks`-Datenbank abgerufen.  
  
```  
USE AdventureWorks;  
GO  
SELECT xml_schema_namespace(N'production',N'ProductDescriptionSchemaCollection');  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Anzeigen einer gespeicherten XML-Schemaauflistung](../../relational-databases/xml/view-a-stored-xml-schema-collection.md)   
 [XML-Schemaauflistungen &#40;SQL Server&#41;](../../relational-databases/xml/xml-schema-collections-sql-server.md)  
  
  
