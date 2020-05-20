---
title: sp_delete_category (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_delete_category_TSQL
- sp_delete_category
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_category
ms.assetid: 63ea7d0d-a567-456e-a778-bee99e21d16c
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 2e150318d4c334c67c51f6cf47c127793a25edb2
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82831254"
---
# <a name="sp_delete_category-transact-sql"></a>sp_delete_category (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Entfernt die angegebene Kategorie von Aufträgen, Warnungen oder Operatoren auf dem aktuellen Server.  
  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_delete_category [ @class = ] 'class' , [ @name = ] 'name'   
```  
  
## <a name="arguments"></a>Argumente  
`[ @class = ] 'class'`Die Klasse der Kategorie. die *Klasse* ist vom Datentyp **varchar (8)** und hat keinen Standardwert und muss einen der folgenden Werte aufweisen.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**Auftrag**|Löscht eine Auftragskategorie|  
|**Warnung**|Löscht eine Warnungskategorie|  
|**KOM**|Löscht eine Operatorkategorie|  
  
`[ @name = ] 'name'`Der Name der Kategorie, die entfernt werden soll. *Name ist vom Datentyp* **vom Datentyp sysname**und hat keinen Standardwert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_delete_category** müssen von der **msdb** -Datenbank aus ausgeführt werden.  
  
 Durch das Löschen einer Kategorie werden alle Aufträge, Warnungen oder Operatoren in dieser Kategorie zur Standardkategorie für die Klasse neu zugeordnet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Serverrolle **sysadmin** können diese Prozedur ausführen.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die Auftragskategorie `AdminJobs` gelöscht.  
  
```  
USE msdb ;  
GO   
  
EXEC dbo.sp_delete_category  
    @name = N'AdminJobs',  
    @class = N'JOB' ;  
GO   
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_add_category &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-add-category-transact-sql.md)   
 [sp_help_category &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-help-category-transact-sql.md)   
 [sp_update_category &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-update-category-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
