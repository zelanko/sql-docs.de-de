---
title: sp_prepexec (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cursor_prepexec
- sp_cursor_prepexec_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_prepexec
ms.assetid: f9141850-a62b-43bf-8e46-b2f92b75ca56
author: stevestein
ms.author: sstein
ms.openlocfilehash: 670b64cb107610fe8b5506654b9e655b0da5fb16
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68794715"
---
# <a name="sp_prepexec-transact-sql"></a>sp_prepexec (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Bereitet eine parametrisierte [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung vor und führt sie aus. sp_prepexec kombiniert die Funktionen von sp_prepare und sp_execute. Diese Aktion wird von ID = 13 in einem Tabular Data Stream-Paket (TDS) aufgerufen.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_prepexec handle OUTPUT, params , stmt  
    [ , bound param ] [ ,...n]]  
```  
  
## <a name="arguments"></a>Argumente  
 *bewältigen*  
 Der von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]generierte *Handlebezeichner* . *handle* ist ein erforderlicher Parameter mit einem **int** -Rückgabewert.  
  
 *params*  
 Identifiziert parametrisierte Anweisungen. Die *params* -Definition der Variablen wird in der Anweisung an die Stelle der Parametermarkierungen gesetzt. " *para* meters" ist ein erforderlicher Parameter, der den Eingabe Wert " **ntext**", " **NCHAR**" oder " **nvarchar** " aufruft. Geben Sie einen NULL-Wert ein, wenn die Anweisung nicht parametrisiert ist.  
  
 *stmt*  
 Definiert das Resultset des Cursors. Der *stmt* -Parameter ist erforderlich und erfordert einen Eingabe Wert vom Typ **ntext**, **NCHAR**oder **nvarchar** .  
  
 *bound_param*  
 Gibt die optionale Verwendung zusätzlicher Parameter an. *bound_param* einen Eingabe Wert eines beliebigen Datentyps aufrufen, um die zusätzlichen verwendeten Parameter festzulegen.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine einfache-Anweisung vorbereitet und ausgeführt:  
  
```  
Declare @Out int;  
EXEC sp_prepexec @Out output,   
    N'@P1 nvarchar(128), @P2 nvarchar(100)',  
    N'SELECT database_id, name  
      FROM sys.databases  
      WHERE name=@P1 AND state_desc = @P2',   
          @P1 = 'tempdb', @P2 = 'ONLINE';   
EXEC sp_unprepare @Out;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_prepare &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-prepare-transact-sql.md)   
 [sp_execute &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-execute-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
