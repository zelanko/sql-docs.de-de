---
title: sp_fulltext_semantic_register_language_statistics_db (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_fulltext_semantic_register_language_statistics_db
- sp_fulltext_semantic_register_language_statistics_db_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_fulltext_semantic_register_language_statistics_db
ms.assetid: bef1b104-5a44-4327-9ae4-45eae3000f7e
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: bb0dcefe09bba8f3df06ed5730ea5bdae2be27d0
ms.sourcegitcommit: 5ed48c7dc6bed153079bc2b23a1e0506841310d1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/21/2019
ms.locfileid: "65983004"
---
# <a name="spfulltextsemanticregisterlanguagestatisticsdb-transact-sql"></a>sp_fulltext_semantic_register_language_statistics_db (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Registriert eine im Voraus aufgefüllte semantische Sprachstatistikdatenbank in der aktuellen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Sie können eine semantische Extraktion nur initiieren, nachdem Sie diese Sprachstatistikdatenbank angefügt und sie mit dieser gespeicherten Prozedur registriert haben. Sie müssen diesen Task nur einmal für jede Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ausführen.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```sql  
EXEC sp_fulltext_semantic_register_language_statistics_db  
    [ @dbname = ] 'database_name';  
GO  
```  
  
##  <a name="Arguments"></a> Argumente  
 [ @dbname =] '*Database_name*"  
 Ist der Name der semantischen Sprachstatistikdatenbank, die für die aktuelle Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]registriert werden soll. Die Datenbank muss bereits angefügt sein. *database_name* ist vom Datentyp **sysname**und kann nicht NULL sein.  
  
## <a name="return-code-value"></a>Rückgabecodewert  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-set"></a>Resultset  
 Keine.  
  
## <a name="general-remarks"></a>Allgemeine Hinweise  
 Die semantische Sprachstatistikdatenbank enthält sprachbezogene Statistiken, die für die semantische Verarbeitung von Textinhalt erforderlich sind.  
  
 **sp_fulltext_semantic_register_language_statistics_db** führt die folgenden Schritte aus:  
  
1.  Überprüft, ob die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eine Version ist, die die semantische Verarbeitung unterstützt.  
  
2.  Überprüft, ob für die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] keine semantische Sprachstatistikdatenbank definiert ist.  
  
3.  Überprüft, ob die Datenbank eine gültige semantische Sprachstatistikdatenbank ist.  
  
4.  Legt Berechtigungen für die semantische Sprachstatistikdatenbank fest, um den Zugriff auf die Datenbank durch Benutzer einzuschränken.  
  
5.  Fügt die Metadaten ein, die den Namen der semantischen Sprachstatistikdatenbank für die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]definieren.  
  
6.  Fügt die Metadaten ein, die die Zuordnungen zwischen der installierten semantischen Sprachstatistikdatenbank und den internen Sprachenmodelltabellen definieren.  
  
7.  Führt eine Überprüfung durch, um sicherzustellen, dass die Datenbank zur Verwendung bereitsteht.  
  
 Weitere Informationen finden Sie unter [Installieren und Konfigurieren der semantischen Suche](../../relational-databases/search/install-and-configure-semantic-search.md).  
  
## <a name="metadata"></a>Metadaten  
 Informationen über die Semantic Language Statistics-Datenbank auf einer Instanz von installiert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Fragen Sie die Katalogsicht [Sys. fulltext_semantic_language_statistics_database &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-semantic-language-statistics-database-transact-sql.md).  
  
## <a name="security"></a>Sicherheit  
  
### <a name="permissions"></a>Berechtigungen  
 Erfordert CONTROL SERVER-Berechtigungen.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird gezeigt, wie die semantische Sprachstatistikdatenbank durch den Aufruf von **sp_fulltext_semantic_register_language_statistics_db**registriert wird.  
  
```sql  
EXEC sp_fulltext_semantic_register_language_statistics_db @dbname = 'semanticsDb';  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Installieren und Konfigurieren der semantischen Suche](../../relational-databases/search/install-and-configure-semantic-search.md)  
  
  
