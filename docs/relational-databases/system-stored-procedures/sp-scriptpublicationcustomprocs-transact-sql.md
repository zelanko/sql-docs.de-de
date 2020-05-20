---
title: sp_scriptpublicationcustomprocs (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_scriptpublicationcustomprocs
- sp_scriptpublicationcustomprocs_TSQL
helpviewer_keywords:
- sp_scriptpublicationcustomprocs
ms.assetid: b06102d5-4284-4834-b126-bc0baea49be5
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: bb59b3ce367a7f936d4d8bec28b363e493857632
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82816609"
---
# <a name="sp_scriptpublicationcustomprocs-transact-sql"></a>sp_scriptpublicationcustomprocs (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Erstellt Skriptcode für die benutzerdefinierten Prozeduren INSERT, UPDATE und DELETE für alle Tabellenartikel in einer Veröffentlichung, in der die Schemaoption für das automatische Generieren von benutzerdefinierten Prozeduren aktiviert ist. **Sp_scriptpublicationcustomprocs** ist besonders nützlich für das Einrichten von Abonnements, für die die Momentaufnahme manuell angewendet wird.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_scriptpublicationcustomprocs [ @publication = ] 'publication_name'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication_name'`Der Name der Veröffentlichung. *publication_name* ist vom **Datentyp vom Datentyp sysname** und hat keinen Standard.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Gibt ein Resultset zurück, das aus einer einzelnen **nvarchar (4000)** -Spalte besteht. Das Resultset enthält die vollständige CREATE PROCEDURE-Anweisung, die zum Erstellen der benutzerdefinierten, gespeicherten Prozedur notwendig ist.  
  
## <a name="remarks"></a>Bemerkungen  
 Für benutzerdefinierte Prozeduren wird nur bei Artikeln Skriptcode erstellt, für die die Schemaoption für das automatische Generieren von benutzerdefinierten Prozeduren (0x2) aktiviert ist.  
  
 Die folgenden Prozeduren werden von **Sp_scriptpublicationcustomprocs** zum Erstellen von Prozeduren auf dem Abonnenten verwendet und sollten nicht direkt ausgeführt werden:  
  
 **sp_script_reconciliation_delproc**  
  
 **sp_script_reconciliation_insproc**  
  
 **sp_script_reconciliation_vdelproc**  
  
 **sp_script_reconciliation_xdelproc**  
  
 **sp_scriptdelproc**  
  
 **sp_scriptinsproc**  
  
 **sp_scriptmappedupdproc**  
  
 **sp_scriptupdproc**  
  
 **sp_scriptvdelproc**  
  
 **sp_scriptvupdproc**  
  
 **sp_scriptxdelproc**  
  
 **sp_scriptxupdproc**  
  
## <a name="permissions"></a>Berechtigungen  
 Die EXECUTE-Berechtigung wird **Public**erteilt. in dieser gespeicherten Prozedur wird eine prozedurale Sicherheitsüberprüfung durchgeführt, um den Zugriff auf Mitglieder der festen Server Rolle **sysadmin** und der festen Daten Bank Rolle **db_owner** in der aktuellen Datenbank einzuschränken.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
