---
title: Sp_cursorexecute (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cursorexecute
- sp_cursorexecute_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cursor_execute
ms.assetid: 6a204229-0a53-4617-a57e-93d4afbb71ac
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: fcc62c09d42adb10f8984a8f48d8b70e2f5c78de
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62723995"
---
# <a name="spcursorexecute-transact-sql"></a>sp_cursorexecute (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Erstellt einen Cursor, der auf dem von sp_cursorprepare erstellten Ausführungsplan basiert, und füllt ihn auf. Diese mit Sp_cursorprepare gekoppelte Prozedur verfügt über die gleiche Funktion wie Sp_cursoropen, aber es ist in zwei Phasen unterteilt. Sp_cursorexecute wird aufgerufen, indem ID = 4 in einem tabular Data Stream (TDS)-Paket.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_cursorexecute prepared_handle, cursor  
    [ , scrollopt[ OUTPUT ]  
    [ , ccopt[ OUTPUT ]  
    [ ,rowcount OUTPUT [ ,bound param][,...n]]]]]  
```  
  
## <a name="arguments"></a>Argumente  
 *prepared_handle*  
 Ist die vorbereitete Anweisung *behandeln* von Sp_cursorprepare zurückgegebene Wert. *Prepared_handle* ist ein erforderlicher Parameter, die bei Aufrufen einer **Int** Eingabewert.  
  
 *Cursor*  
 Der von SQL Server generierte Cursorbezeichner. *Cursor* ist ein erforderlicher Parameter, die für alle nachfolgenden Prozeduren angegeben werden muss, die auf den Cursor auswirken, z. B. Sp_cursorfetch fungieren  
  
 *scrollopt*  
 Option für den Bildlauf. *Scrollopt* ist ein optionaler Parameter, der erfordert eine **Int** Eingabewert. Die Sp_cursorexecute*Scrollopt* Parameter hat die gleichen Wertoptionen wie denen für Sp_cursoropen.  
  
> [!NOTE]  
>  Der PARAMETERIZED_STMT-Wert wird nicht unterstützt.  
  
> [!IMPORTANT]  
>  Wenn eine *Scrollopt* kein Wert angegeben wird, der Standardwert ist KEYSET, unabhängig von *Scrollopt* in Sp_cursorprepare angegebenen Wert.  
  
 *ccopt*  
 Option für die Währungssteuerung. *Ccopt* ist ein optionaler Parameter, der erfordert eine **Int** Eingabewert. Die Sp_cursorexecute*Ccopt* Parameter hat die gleichen Wertoptionen wie denen für Sp_cursoropen.  
  
> [!IMPORTANT]  
>  Wenn eine *Ccopt* kein Wert angegeben wird, wird der Standardwert OPTIMISTIC unabhängig von *Ccopt* in Sp_cursorprepare angegebenen Wert.  
  
 *rowcount*  
 Ein optionaler Parameter, der die Anzahl der mit AUTO_FETCH zu verwendenden Fetchpufferzeilen angibt. Der Standardwert ist 20 Zeilen. *Überprüfung der Zeilenanzahl* verhält sich anders, wenn als Eingabewert oder Rückgabewert zugewiesen.  
  
|Als Eingabewert|Als Rückgabewert|  
|--------------------|---------------------|  
|Wenn AUTO_FETCH mit FAST_FORWARD-Cursorn angegeben *Rowcount* stellt die Anzahl der Zeilen im Fetchpuffer platziert.|Stellt die Anzahl der Zeilen im Resultset dar. Wenn die *Scrollopt* -Wert AUTO_FETCH angegeben wird, *Rowcount* gibt die Anzahl der Zeilen im Fetchpuffer abgerufen wurden.|  
  
 *bound_param*  
 Gibt die optionale Verwendung zusätzlicher Parameter an.  
  
> [!NOTE]  
>  Alle nach dem fünften Parameter übergebenen Parameter werden als Eingabeparameter an den Anweisungsplan übergeben.  
  
## <a name="code-return-value"></a>Code-Rückgabewert  
 *Überprüfung der Zeilenanzahl* möglicherweise die folgenden Werte zurück.  
  
|Wert|Description|  
|-----------|-----------------|  
|-1|Die Anzahl der unbekannten Zeilen.|  
|-n|Eine asynchrone Auffüllung ist wirksam.|  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="scrollopt-and-ccopt-parameters"></a>scrollopt-Parameter und ccopt-Parameter  
 *Scrollopt* und *Ccopt* sind nützlich, wenn die zwischengespeicherten Pläne vorzeitig entfernt werden, für den Servercache, was bedeutet, dass das vorbereitete Handle identifizieren die Anweisung erneut kompiliert werden muss. Die *Scrollopt* und *Ccopt* Parameter müssen mit den Werten übereinstimmen in der ursprünglichen Anforderung an Sp_cursorprepare gesendet.  
  
> [!NOTE]  
>  PARAMETERIZED_STMT nicht zugewiesen werden soll *Scrollopt*.  
  
 Nicht übereinstimmende Werte bewirken eine Neukompilierung der Pläne, wodurch Vorbereitungs- und Ausführungsvorgänge negiert werden.  
  
## <a name="rpc-and-tds-considerations"></a>Überlegungen zu RPC und TDS  
 Das RPC-RETURN_METADATA-Eingabeflag kann auf 1 festgelegt werden. Dadurch wird angefordert, dass Metadaten zur SELECT-Liste des Cursors im TDS-Datenstrom zurückgegeben werden.  
  
## <a name="see-also"></a>Siehe auch  
 [sp_cursoropen &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cursoropen-transact-sql.md)   
 [sp_cursorfetch &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cursorfetch-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
