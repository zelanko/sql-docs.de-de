---
description: sp_helpmergearticlecolumn (Transact-SQL)
title: sp_helpmergearticlecolumn (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpmergearticlecolumn
- sp_helpmergearticlecolumn_TSQL
helpviewer_keywords:
- sp_helpmergearticlecolumn
ms.assetid: 651c017b-9e9a-48f2-a0bd-6fc896eab334
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f85830c11ca64f3540995411a2cfe1dac6044544
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88474032"
---
# <a name="sp_helpmergearticlecolumn-transact-sql"></a>sp_helpmergearticlecolumn (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Gibt die Liste der Spalten in dem angegebenen Tabellen- oder Sichtartikel für eine Mergeveröffentlichung zurück. Da gespeicherte Prozeduren nicht über Spalten verfügen, gibt diese gespeicherte Prozedur einen Fehler zurück, wenn eine gespeicherte Prozedur als Artikel angegeben ist. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helpmergearticlecolumn [ @publication = ] 'publication' ]  
        , [ @article= ] 'article' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'` Der Name der Veröffentlichung. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @article = ] 'article'` Der Name einer Tabelle oder Sicht, für die Informationen abgerufen werden sollen. der *Artikel* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**column_id**|**sysname**|Identifiziert die Spalte.|  
|**column_name**|**sysname**|Der Name der Spalte für eine Tabelle oder Sicht.|  
|**enes**|**bit**|Gibt an, ob der Spaltenname veröffentlicht ist.<br /><br /> der Wert **1** gibt an, dass die Spalte veröffentlicht wird.<br /><br /> **0** gibt an, dass Sie nicht veröffentlicht wird.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_helpmergearticlecolumn** wird bei der Mergereplikation verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Daten Bank Rolle **replmonitor** in der Verteilungs Datenbank oder der Veröffentlichungs Zugriffsliste für die Veröffentlichung können **sp_helpmergearticlecolumn**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
