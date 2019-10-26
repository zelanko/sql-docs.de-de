---
title: sp_fulltext_semantic_unregister_language_statistics_db (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_fulltext_semantic_unregister_language_statistics_db_TSQL
- sp_fulltext_semantic_unregister_language_statistics_db
dev_langs:
- TSQL
helpviewer_keywords:
- sp_fulltext_semantic_unregister_language_statistics_db
ms.assetid: 1426ca4a-9a76-489e-98da-8f6d13ff9732
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d6952d245dfc9083c7cfa6e6d36ad991ffd24654
ms.sourcegitcommit: 2a06c87aa195bc6743ebdc14b91eb71ab6b91298
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2019
ms.locfileid: "72909138"
---
# <a name="sp_fulltext_semantic_unregister_language_statistics_db-transact-sql"></a>sp_fulltext_semantic_unregister_language_statistics_db (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Hebt die Registrierung einer vorhandenen semantischen Sprachstatistikdatenbank in der aktuellen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf und löscht alle zugeordneten Metadaten.  
  
 Diese Anweisung trennt die Datenbank nicht und entfernt die physische Datenbankdatei nicht aus dem Dateisystem. Nachdem Sie die Registrierung der Datenbank aufgehoben haben, können Sie sie trennen und die physische Datenbankdatei löschen.  
  
 ![Themen Link Symbol](../../database-engine/configure-windows/media/topic-link.gif "Link Symbol "Thema"") [Transact-SQL-Syntax Konventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```sql  
EXEC sp_fulltext_semantic_unregister_language_statistics_db;  
GO  
```  
  
##  <a name="Arguments"></a> Argumente  
 Diese Prozedur erfordert keine Argumente. Da eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nur über eine semantische Sprachstatistikdatenbank verfügt, ist es nicht notwendig, die Datenbank zu identifizieren.  
  
## <a name="return-code-value"></a>Rückgabecodewert  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-set"></a>Resultset  
 Keine.  
  
## <a name="general-remarks"></a>Allgemeine Hinweise  
 Wenn die Registrierung einer semantischen Sprachstatistikdatenbank aufgehoben wird, werden auch alle zugeordneten Metadaten entfernt.  
  
 **sp_fulltext_semantic_unregister_language_statistics_db** führt die folgenden Schritte aus:  
  
1.  Überprüft, ob keine semantischen Auffüllungen für die aktuelle Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] durchgeführt werden.  
  
2.  Entfernt alle der angegebenen semantischen Sprachstatistikdatenbank zugeordneten Metadaten.  

 Weitere Informationen finden Sie unter [Installieren und Konfigurieren der semantischen Suche](../../relational-databases/search/install-and-configure-semantic-search.md).  
  
## <a name="metadata"></a>Browser  
 Informationen über die Semantic Language Statistics Datenbank, die auf einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]installiert ist, erhalten Sie, indem Sie die Katalog Sicht [sys. fulltext_semantic_language_statistics_database &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/sys-fulltext-semantic-language-statistics-database-transact-sql.md)Abfragen.  
  
## <a name="security"></a>Sicherheit  
  
### <a name="permissions"></a>Berechtigungen  
 Erfordert CONTROL SERVER-Berechtigungen.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird gezeigt, wie die Registrierung der Semantic Language Statistics-Datenbank durch Aufrufen von **sp_fulltext_semantic_unregister_language_statistics_db**aufgehoben wird.  
  
```sql  
EXEC sp_fulltext_semantic_unregister_language_statistics_db;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Installieren und Konfigurieren der semantischen Suche](../../relational-databases/search/install-and-configure-semantic-search.md)  
  
  
