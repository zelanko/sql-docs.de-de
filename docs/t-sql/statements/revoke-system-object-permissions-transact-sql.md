---
title: REVOKE (Berechtigungen für Systemobjekte) (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- REVOKE statement, system objects
- permissions [SQL Server], system objects
ms.assetid: 84983238-dd7d-45bd-99bb-52c9d8e96a87
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 6009e17ed735ab9a2f8aa93bc460a78bbef06119
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47755328"
---
# <a name="revoke-system-object-permissions-transact-sql"></a>REVOKE (Berechtigungen für Systemobjekte) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Hebt Berechtigungen für Systemobjekte wie z. B. gespeicherte Prozeduren, erweiterte gespeicherte Prozeduren, Funktionen und Sichten für einen Prinzipal auf.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
REVOKE { SELECT | EXECUTE } ON [sys.]system_object FROM principal   
```  
  
## <a name="arguments"></a>Argumente  
 [**sys.**] .  
 Der **sys**-Qualifizierer ist nur erforderlich, wenn auf Katalogsichten und dynamische Verwaltungssichten verwiesen wird.  
  
 *system_object*  
 Gibt das Objekt an, für das die Berechtigung aufgehoben wird.  
  
 *principal*  
 Gibt den Prinzipal an, für den die Berechtigung aufgehoben wird.  
  
## <a name="remarks"></a>Remarks  
 Mit dieser Anweisung können Berechtigungen für bestimmte gespeicherte Prozeduren, erweiterte gespeicherte Prozeduren, Tabellenwertfunktionen, Skalarfunktionen, Sichten, Katalogsichten, Kompatibilitätssichten, INFORMATION_SCHEMA-Sichten, dynamische Verwaltungssichten und Systemtabellen aufgehoben werden, die von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installiert wurden. Jedes Systemobjekt ist als eindeutiger Datensatz in der Ressourcendatenbank (**mssqlsystemresource**) vorhanden. Die Ressourcendatenbank ist schreibgeschützt. Ein Link zum Objekt wird in einem Datensatz im **sys**-Schema jeder Datenbank verfügbar gemacht.  
  
 Die Standardnamensauflösung löst nicht qualifizierte Prozedurnamen für die Ressourcendatenbank auf. Daher ist der **sys.**-Qualifizierer nur erforderlich, wenn Katalogsichten und dynamische Verwaltungssichten angegeben werden.  
  
> [!CAUTION]  
>  Durch das Aufheben von Berechtigungen für Systemobjekte werden Fehler in abhängigen Anwendungen verursacht. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] verwendet Katalogsichten und funktioniert möglicherweise nicht wie erwartet, wenn Sie die Standardberechtigungen für Katalogsichten ändern.  
  
 Das Aufheben von Berechtigungen für Trigger und für Spalten von Systemobjekten wird nicht unterstützt.  
  
 Berechtigungen für Systemobjekte werden bei Upgrades von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] beibehalten.  
  
 Systemobjekte werden in der [sys.system_objects](../../relational-databases/system-catalog-views/sys-system-objects-transact-sql.md) -Katalogsicht angezeigt.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die CONTROL SERVER-Berechtigung.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die `EXECUTE`-Berechtigung für `sp_addlinkedserver` für die `public`-Rolle aufgehoben.  
  
```  
REVOKE EXECUTE ON sys.sp_addlinkedserver FROM public;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [sys.system_objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-system-objects-transact-sql.md)   
 [sys.database_permissions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-permissions-transact-sql.md)   
 [GRANT (Berechtigungen für Systemobjekte) &#40;Transact-SQL&#41;](../../t-sql/statements/grant-system-object-permissions-transact-sql.md)   
 [DENY (Berechtigungen für Systemobjekte) &#40;Transact-SQL&#41;](../../t-sql/statements/deny-system-object-permissions-transact-sql.md)  
  
  
