---
title: sp_changearticlecolumndatatype (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changearticlecolumndatatype
- sp_changearticlecolumndatatype_TSQL
helpviewer_keywords:
- sp_changearticlecolumndatatype
ms.assetid: 0db80e08-fb77-4d0c-aa41-455b13ffa9b4
author: stevestein
ms.author: sstein
ms.openlocfilehash: f101d9081c7eb898d43c461a3bd64eca0c043b64
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67995515"
---
# <a name="sp_changearticlecolumndatatype-transact-sql"></a>sp_changearticlecolumndatatype (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ändert die Datentypzuordnung der Artikelspalte für eine Oracle-Veröffentlichung. Diese gespeicherte Prozedur wird auf dem Verteiler für jede Datenbank ausgeführt.  
  
> [!NOTE]  
>  Die Datentypzuordnungen zwischen unterstützten Verlegertypen werden standardmäßig bereitgestellt. Verwenden Sie **sp_changearticlecolumndatatype** nur, wenn Sie diese Standardeinstellungen überschreiben.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_changearticlecolumndatatype [ @publication= ] 'publication'  
    [ @article = ] 'article'   
    [ @column = ] 'column'  
    [ , [ @type = ] 'type' ]  
    [ , [ @length = ] length ]  
    [ , [ @precision = ] precision ]  
    [ , [ @scale = ] scale ]  
    [ , [ @publisher = ] 'publisher'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'`Der Name der Oracle-Veröffentlichung. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @article = ] 'article'`Der Name des Artikels. der *Artikel* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @column = ] 'column'`Der Name der Spalte, für die die Datentyp Zuordnung geändert werden soll. *Column* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @type = ] 'type'`Der Name des [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datentyps in der Ziel Spalte. *Type ist vom Datentyp* **vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @length = ] length`Die Länge des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datentyps in der Ziel Spalte. *length* ist vom Datentyp **bigint**und hat den Standardwert NULL.  
  
`[ @precision = ] precision`Die Genauigkeit des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datentyps in der Ziel Spalte. die *Genauigkeit* ist vom Datentyp **bigint**und hat den Standardwert NULL.  
  
`[ @publisher = ] 'publisher'`Gibt einen nicht- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Verleger an. *Publisher* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **Sp_changearticlecolumndatatype** wird verwendet, um die standardmäßigen Datentyp Zuordnungen zwischen unterstützten Verleger Typen ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Oracle und) zu überschreiben. Führen Sie [sp_getdefaultdatatypemapping](../../relational-databases/system-stored-procedures/sp-getdefaultdatatypemapping-transact-sql.md)aus, um diese standardmäßigen Datentyp Zuordnungen anzuzeigen.  
  
 **sp_changearticlecolumndatatype** wird nur für Oracle-Verleger unterstützt. Das Ausführen dieser gespeicherten Prozedur für eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Veröffentlichung führt zu einem Fehler.  
  
 für jede Artikel Spalten Zuordnung, die geändert werden muss, muss **sp_changearticlecolumndatatype** ausgeführt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_changearticlecolumndatatype**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ändern von Veröffentlichungs- und Artikeleigenschaften](../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [Data Type Mapping for Oracle Publishers](../../relational-databases/replication/non-sql/data-type-mapping-for-oracle-publishers.md)   
 [Gespeicherte Automatisierungsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
