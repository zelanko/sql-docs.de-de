---
title: sp_dsninfo (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_dsninfo
- sp_dsninfo_TSQL
helpviewer_keywords:
- sp_dsninfo
ms.assetid: 34648615-814b-42bc-95a3-50e86b42ec4d
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: aa9033b52851b6b678671e94c6d10d71b5a488fc
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82818692"
---
# <a name="sp_dsninfo-transact-sql"></a>sp_dsninfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt Informationen zu ODBC- oder OLE DB-Datenquellen von dem Verteiler zurück, der dem aktuellen Server zugeordnet ist. Diese gespeicherte Prozedur wird auf dem Verteiler für jede Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_dsninfo [ @dsn =] 'dsn'   
    [ , [ @infotype =] 'info_type']   
    [ , [ @login =] 'login']   
    [ , [ @password =] 'password']  
    [ , [ @dso_type=] dso_type]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @dsn = ] 'dsn'`Der Name des ODBC-DSN oder OLE DB Verbindungs Servers. *DSN* ist vom Datentyp **varchar (128)** und hat keinen Standardwert.  
  
`[ @infotype = ] 'info_type'`Der Typ der Informationen, die zurückgegeben werden sollen. Wenn *info_type* nicht angegeben ist oder NULL angegeben ist, werden alle Informationstypen zurückgegeben. *info_type* ist vom Datentyp **varchar (128)** und hat den Standardwert NULL. die folgenden Werte sind möglich:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**DBMS_NAME**|Gibt den Anbieter der Datenquelle an.|  
|**DBMS_VERSION**|Gibt die Version der Datenquelle an.|  
|**DATABASE_NAME**|Gibt den Datenbanknamen an.|  
|**SQL_SUBSCRIBER**|Gibt an, dass die Datenquelle ein Abonnent sein kann.|  
  
`[ @login = ] 'login'`Der Anmelde Name für die Datenquelle. Wenn die Datenquelle einen Anmeldenamen aufweist, geben Sie NULL an, oder lassen Sie den Parameter weg. *Login*ist vom Datentyp **varchar (128)** und hat den Standardwert NULL.  
  
`[ @password = ] 'password'`Das Kennwort für die Anmeldung. Wenn die Datenquelle einen Anmeldenamen aufweist, geben Sie NULL an, oder lassen Sie den Parameter weg. *Password*ist vom Datentyp **varchar (128)** und hat den Standardwert NULL.  
  
`[ @dso_type = ] dso_type`Der Daten Quellentyp. *dso_type* ist vom Datentyp **int**. die folgenden Werte sind möglich:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**1** (Standard)|ODBC-Datenquelle (ODBC data source)|  
|**3**|OLE DB-Datenquelle|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**Informationstyp**|**nvarchar (64)**|Informationstypen, wie z. B. DBMS_NAME, DBMS_VERSION, DATABASE_NAME, SQL_SUBSCRIBER.|  
|**Wert**|**nvarchar(512)**|Der Wert der verknüpften Informationstypen.|  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_dsninfo** wird bei allen Replikations Typen verwendet.  
  
 **sp_dsninfo** ruft ODBC-oder OLE DB Datenquellen Informationen ab, die anzeigen, ob die Datenbank für die Replikation oder Abfrage verwendet werden kann.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** können **sp_dsninfo**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_enumdsn &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-enumdsn-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
