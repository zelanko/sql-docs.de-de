---
title: Datentypsynonyme (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/23/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- data types [SQL Server], synonyms
- alternate names [SQL Server]
- synonyms [SQL Server], data types
ms.assetid: 390eef67-1a49-4185-a971-e07765be9717
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 30a66dbcf9126031caa84cdf0ff7623d2dd16046
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67927770"
---
# <a name="data-type-synonyms-transact-sql"></a>Datentypsynonyme (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

Synonyme für Datentypen werden für die ISO-Kompatibilität in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt. In der folgenden Tabelle sind die Synonyme und die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Systemdatentypen aufgeführt, denen sie zugeordnet werden.
  
|Synonym|SQL Server-Systemdatentyp|  
|---|---|
|**Binary varying**|**varbinary**|  
|**char varying**|**varchar**|  
|**character**|**char**|  
|**character**|**char(1)**|  
|**character(** _n_ **)**|**char(n)**|  
|**character varying(** _n_ **)**|**varchar(n)**|  
|**Dec**|**decimal**|  
|**Double precision**|**float**|  
|**float**[ **(** _n_ **)** ] for _n_ = 1-7|**real**|  
|**float**[ **(** _n_ **)** ] for _n_ = 8-15|**float**|  
|**integer**|**int**|  
|**national character(** _n_ **)**|**nchar(n)**|  
|**national char(** _n_ **)**|**nchar(n)**|  
|**national character varying(** _n_ **)**|**nvarchar(n)**|  
|**national char varying(** _n_ **)**|**nvarchar(n)**|  
|**national text**|**ntext**|  
|**timestamp**|rowversion|  
  
Synonyme für Datentypen können in DDL-Anweisungen (Data Definition Language, Datendefinitionssprache) statt der entsprechenden Basisdatentypnamen verwendet werden. Zu diesen Anweisungen zählen CREATE TABLE, CREATE PROCEDURE und DECLARE *@variable* . Die Synonyme sind allerdings nicht sichtbar, nachdem die Objekte erstellt wurden. Wenn ein Objekt erstellt wird, wird ihm der Basisdatentyp zugewiesen, der dem Synonym zugeordnet ist. Es gibt keinen Protokolleintrag, dem entnommen werden kann, dass das Synonym in der Anweisung angegeben wurde, mit der das Objekt erstellt wurde.
  
Objekten, die von einem Originalobjekt abgeleitet wurden, wie z. B. Spalten eines Resultsets oder Ausdrücke, ist der Basisdatentyp zugewiesen. Alle Metadatenfunktionen, die das Originalobjekt oder jegliches abgeleitete Objekt verwenden, melden den Basisdatentyp, nicht das Synonym, einschließlich:

* Metadatenvorgänge wie **sp_help** und andere gespeicherte Systemprozeduren,
* Informationsschemasichten und
* Datenzugriffs-API-Metadatenvorgänge, die die Datentypen von Tabellen- oder Resultset-Spalten melden.
  
Sie können z. B. eine Tabelle durch Angabe von `national character varying` erstellen:
  
```sql
CREATE TABLE ExampleTable (PriKey int PRIMARY KEY, VarCharCol national character varying(10))  
```  
  
`VarCharCol` wird ein **nvarchar(10)** -Datentyp zugewiesen, und alle folgenden Metadatenfunktionen melden die Spalte als **nvarchar(10)** -Spalte. Die Metadatenfunktionen melden sie nie als **national character varying(10)** -Spalte.
  
## <a name="see-also"></a>Siehe auch
[Datentypen &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)
  
  
