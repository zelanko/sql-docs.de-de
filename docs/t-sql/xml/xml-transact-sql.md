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
ms.openlocfilehash: d8d863a6ca6a44a323c05f26298c68de774dfc3b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67948011"
---
# <a name="xml-transact-sql"></a>xml (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Der Datentyp, in dem XML-Daten gespeichert sind. **xml**-Instanzen können in einer Spalte oder in einer Variablen vom Typ **xml** gespeichert werden.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Themenlinksymbol") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
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
  
## <a name="remarks"></a>Remarks  
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
  
  
