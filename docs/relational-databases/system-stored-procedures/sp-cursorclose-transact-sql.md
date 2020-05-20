---
title: sp_cursorclose (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cursor_close_TSQL
- sp_cursor_close
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cursorclose
ms.assetid: d9b7b44d-cdff-456e-97df-7031a3b9beb6
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f21e6db8e9c1cb8ec33f9bddd9610d8179b3e5ac
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82820608"
---
# <a name="sp_cursorclose-transact-sql"></a>sp_cursorclose (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Schließt den Cursor und hebt deren Zuordnung auf und gibt alle zugeordneten Ressourcen frei. Das heißt, Sie löscht die temporäre Tabelle, die zur Unterstützung von Keyset oder statischem **Cursor**verwendet wird. sp_cursorclose wird aufgerufen, indem ID = 9 in einem Tabular Data Stream-Paket (TDS) angegeben wird.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_cursorclose cursor  
```  
  
## <a name="arguments"></a>Argumente  
 *Cursor*  
 Ein Cursor *handle* -Wert, der von generiert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und von der sp_cursoropen Prozedur zurückgegeben wird. *Cursor* ist ein erforderlicher Parameter, der einen **int** -Eingabe Wert aufruft.  
  
> [!NOTE]  
>  Der Eingabewert -1 gilt für alle Cursor der aktuellen Verbindung.  
  
## <a name="remarks"></a>Bemerkungen  
 der *Cursor* gibt Fehlermeldungen zurück, wenn die Prozedur ausgeführt wurde, nachdem der Cursor geschlossen wurde, oder wenn ein ungültiges Handle angegeben wurde.  
  
 Der RPC-Status gibt an, ob der Vorgang erfolgreich oder fehlerhaft war.  
  
 Die DONE-Zeilenanzahl beträgt immer 0.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_cursoropen &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-cursoropen-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
