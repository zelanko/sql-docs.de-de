---
title: xml (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/26/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- xml_TSQL
- xml
dev_langs:
- TSQL
helpviewer_keywords:
- xml data type [SQL Server], about xml data type
ms.assetid: 9198f671-8e61-4ca4-9c3a-859f84020e62
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 66e49e14785f3e99bde79c1de987ea5ac38d06d2
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85754795"
---
# <a name="xml-transact-sql"></a>xml (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Der Datentyp, in dem XML-Daten gespeichert sind. **xml**-Instanzen können in einer Spalte oder in einer Variablen vom Typ **xml** gespeichert werden.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
xml ( [ CONTENT | DOCUMENT ] xml_schema_collection )  
```  
  
## <a name="arguments"></a>Argumente  
 CONTENT  
 Schränkt die **xml**-Instanz auf ein wohlgeformtes XML-Fragment ein. Die XML-Daten können keine oder auch mehrere Elemente auf der obersten Ebene enthalten. Textknoten sind auf der obersten Ebene ebenfalls zulässig.  
  
 Dies ist das Standardverhalten.  
  
 DOCUMENT  
 Schränkt die **xml**-Instanz auf ein wohlgeformtes XML-Dokument ein. Die XML-Daten müssen genau ein Stammelement aufweisen. Textknoten sind auf der obersten Ebene nicht zulässig.  
  
 *xml_schema_collection*  
 Der Name einer XML-Schemaauflistung. Zum Erstellen einer Spalte oder Variablen vom Typ **xml** können Sie optional den Namen der XML-Schemaauflistung angeben. Weitere Informationen zu typisierten und nicht typisierten XML-Dokumenten finden Sie unter [Vergleichen von typisiertem XML mit nicht typisiertem XML](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md).  
  
## <a name="remarks"></a>Bemerkungen  
 Die gespeicherte Darstellung von Instanzen vom Datentyp **xml** darf die Größe von 2 Gigabyte (GB) nicht überschreiten.  
  
 Die Facets CONTENT und DOCUMENT beziehen sich nur auf typisierte XML-Daten. Weitere Informationen finden Sie unter [Vergleichen von typisiertem XML mit nicht typisiertem XML](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md).  
  
## <a name="examples"></a>Beispiele  
  
```  
USE AdventureWorks;  
GO  
DECLARE @DemographicData xml (Person.IndividualSurveySchemaCollection);  
SET @DemographicData =  (SELECT TOP 1 Demographics FROM Person.Person);  
SELECT @DemographicData;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datentypkonvertierung &#40;Datenbank-Engine&#41;](../../t-sql/data-types/data-type-conversion-database-engine.md)   
 [Datentypen &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [XML-Datentypmethoden](../../t-sql/xml/xml-data-type-methods.md)   
 [XQuery-Sprachreferenz &#40;SQL Server&#41;](../../xquery/xquery-language-reference-sql-server.md)  
  
  
