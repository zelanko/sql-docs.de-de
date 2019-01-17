---
title: DROP SYNONYM (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/26/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP SYNONYM
- DROP_SYNONYM_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- deleting synonyms
- synonyms [SQL Server], removing
- removing synonyms
- DROP SYNONYM statement
- dropping synonyms
ms.assetid: 23578932-e4de-4c39-a5a0-ce45139c4269
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: f44ba9c4d2b882e97b397fdf959c41d7a9b35fbf
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "53213139"
---
# <a name="drop-synonym-transact-sql"></a>DROP SYNONYM (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Entfernt ein Synonym aus einem angegebenen Schema.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Themenlinksymbol") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DROP SYNONYM [ IF EXISTS ] [ schema. ] synonym_name  
```  
  
## <a name="arguments"></a>Argumente  
 *IF EXISTS*  
**Gilt für**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] bis zur [aktuellen Version](https://go.microsoft.com/fwlink/p/?LinkId=299658))
  
 Löscht das Synonym nur, wenn dieses bereits vorhanden ist.  
  
 *schema*  
 Gibt das Schema an, in dem das Synonym vorhanden ist. Wird kein Schema angegeben, verwendet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] das Standardschema des aktuellen Benutzers.  
  
 *synonym_name*  
 Der Name des Synonyms, das gelöscht werden soll.  
  
## <a name="remarks"></a>Remarks  
 Verweise auf Synonyme sind nicht an ein Schema gebunden. Deshalb können Sie ein Synonym jederzeit löschen. Verweise auf gelöschte Synonyme werden erst zur Laufzeit gefunden.  
  
 In dynamischem SQL können Synonyme erstellt und gelöscht werden. Außerdem kann auf sie verwiesen werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Zum Löschen eines Synonyms muss ein Benutzer mindestens eine der folgenden Bedingungen erfüllen. Folgende Voraussetzungen müssen erfüllt sein:  
  
-   Der Benutzer muss der aktuelle Besitzer eines Synonyms sein.  
  
-   Der Benutzer muss ein Berechtigter für CONTROL für ein Synonym sein.  
  
-   Der Benutzer muss ein Berechtigter sein, der über die ALTER SCHEMA-Berechtigung für das enthaltene Schema verfügt.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird zuerst das Synonym `MyProduct` erstellt und dann gelöscht.  
  
```  
USE tempdb;  
GO  
-- Create a synonym for the Product table in AdventureWorks2012.  
CREATE SYNONYM MyProduct  
FOR AdventureWorks2012.Production.Product;  
GO  
-- Drop synonym MyProduct.  
USE tempdb;  
GO  
DROP SYNONYM MyProduct;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [CREATE SYNONYM &#40;Transact-SQL&#41;](../../t-sql/statements/create-synonym-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
