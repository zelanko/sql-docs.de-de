---
title: sp_cursorprepexec (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/20/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cursorprepexec_TSQL
- sp_cursorprepexec
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cursorprepexec
ms.assetid: 8094fa90-35b5-4cf4-8012-0570cb2ba1e6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 660a75f1e6fea9b5a825372501c2e65f2dd3874b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "69652435"
---
# <a name="sp_cursorprepexec-transact-sql"></a>sp_cursorprepexec (Transact-SQL)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md.md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Kompiliert einen Plan für die gesendete Cursoranweisung oder den gesendeten Batch, erstellt dann den Cursor und füllt ihn auf. sp_cursorprepexec kombiniert die Funktionen von sp_cursorprepare und sp_cursorexecute. Diese Prozedur wird aufgerufen, indem ID = 5 in einem Tabular Data Stream-Paket (TDS) angegeben wird.  
  
 ![Linksymbol](../../database-engine/configure-windows/media/topic-link.gif "Linksymbol") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_cursorprepexec prepared handle OUTPUT, cursor OUTPUT, params , statement , options  
    [ , scrollopt [ , ccopt [ , rowcount ] ] ]  
    [, '@parameter_name[,...n ]']
```  
  
## <a name="arguments"></a>Argumente  
 *vorbereitetes handle*  
 Ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] generierter vorbereiteter *handle* -Bezeichner. *vorbereitetes handle* ist erforderlich und gibt **int**zurück.  
  
 *Cursor*  
 Der von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] generierte Cursorbezeichner. der *Cursor* ist ein erforderlicher Parameter, der für alle nachfolgenden Prozeduren angegeben werden muss, die auf diesen Cursor (z. b. sp_cursorfetch) reagieren.  
  
 *params*  
 Identifiziert parametrisierte Anweisungen. Die *params* -Definition der Variablen wird in der Anweisung an die Stelle der Parametermarkierungen gesetzt. *params* ist ein erforderlicher Parameter, der einen Eingabewert vom Typ **ntext**, **nchar**,oder **nvarchar** erfordert.  
  
> [!NOTE]  
>  Verwenden Sie eine **ntext** -Zeichenfolge als Eingabe Wert, wenn *stmt* parametrisiert und der *scrollopt* -PARAMETERIZED_STMT Wert aktiviert ist.  
  
 *an*  
 Definiert das Resultset des Cursors. Der *Anweisungs* Parameter ist erforderlich und erfordert einen Eingabe Wert vom Typ **ntext**, **NCHAR**oder **nvarchar** .  
  
> [!NOTE]  
>  Die Regeln zum Angeben des stmt-Werts sind identisch mit denen für sp_cursoropen, mit der Ausnahme, dass der *stmt* -Zeichen folgen Datentyp **ntext**lauten muss.  
  
 *options*  
 Ein optionaler Parameter, der eine Beschreibung der Spalten im Cursorresultset zurückgibt. * Optionen erfordern den folgenden **int** -Eingabe Wert.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|0x0001|RETURN_METADATA|  
  
 *scrollopt*  
 Scrolloption. *scrollopt* ist ein optionaler Parameter, der einen der folgenden **int** -Eingabewerte erfordert.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|0x0001|KEYSET|  
|0x0002|DYNAMIC|  
|0x0004|FORWARD_ONLY|  
|0x0008|STATIC|  
|0x10|FAST_FORWARD|  
|0x1000|PARAMETERIZED_STMT|  
|0x2000|AUTO_FETCH|  
|0x4000|AUTO_CLOSE|  
|0x8000|CHECK_ACCEPTED_TYPES|  
|0x10000|KEYSET_ACCEPTABLE|  
|0x20000|DYNAMIC_ACCEPTABLE|  
|0x40000|FORWARD_ONLY_ACCEPTABLE|  
|0x80000|STATIC_ACCEPTABLE|  
|0x100000|FAST_FORWARD_ACCEPTABLE|  
  
 Aufgrund der Möglichkeit, dass die angeforderte Option nicht für den von * \<stmt>* definierten Cursor geeignet ist, dient dieser Parameter sowohl als Eingabe als auch als Ausgabe. In solchen Fällen weist [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] einen entsprechenden Typ zu und ändert diesen Wert.  
  
 *ccopt*  
 Option für die Parallelitätssteuerung. *ccopt* ist ein optionaler Parameter, der einen der folgenden **int** -Eingabewerte erfordert.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|0x0001|READ_ONLY|  
|0x0002|SCROLL_LOCKS (vormals bekannt als LOCKCC)|  
|0x0004|**Optimistische** (vormals als optcc bezeichnet)|  
|0x0008|OPTIMISTIC (vormals bekannt als OPTCCVAL)|  
|0x2000|ALLOW_DIRECT|  
|0x4000|UPDT_IN_PLACE|  
|0x8000|CHECK_ACCEPTED_OPTS|  
|0x10000|READ_ONLY_ACCEPTABLE|  
|0x20000|SCROLL_LOCKS_ACCEPTABLE|  
|0x40000|OPTIMISTIC_ACCEPTABLE|  
|0x80000|OPTIMISITC_ACCEPTABLE|  
  
 Wie bei *scrollpt* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kann einen anderen Wert als den angeforderten zuweisen.  
  
 *RowCount*  
 Ein optionaler Parameter, der die Anzahl der mit AUTO_FETCH zu verwendenden Fetchpufferzeilen angibt. Der Standardwert ist 20 Zeilen. die Zeilen *Anzahl* verhält sich anders, wenn Sie als Eingabe Wert im Vergleich zu einem Rückgabewert zugewiesen wird.  
  
|Als Eingabewert|Als Rückgabewert|  
|--------------------|---------------------|  
|Wenn AUTO_FETCH mit FAST_FORWARD Cursorn angegeben wird, stellt die *Zeilen Anzahl die* Anzahl der Zeilen dar, die im Fetchpuffer platziert werden sollen.|Stellt die Anzahl der Zeilen im Resultset dar. Wenn der *scrollopt* -AUTO_FETCH Wert angegeben wird, gibt *ROWCOUNT* die Anzahl der Zeilen zurück, die in den Abruf Puffer abgerufen wurden.|  

*parameter_name* Legen Sie einen oder mehrere Parameternamen fest, wie im params-Argument definiert.  Für jeden Parameter, der in den Parametern enthalten ist, muss ein Parameter angegeben werden. Dieses Argument ist nicht erforderlich, wenn für die Transact-SQL-Anweisung oder den Batch in params keine Parameter definiert sind.
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 Wenn Parameter einen NULL-Wert zurückgibt, wird die Anweisung nicht parametrisiert.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_cursoropen &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-cursoropen-transact-sql.md)   
 [sp_cursorexecute &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-cursorexecute-transact-sql.md)   
 [sp_cursorprepare &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-cursorprepare-transact-sql.md)   
 [sp_cursorfetch &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-cursorfetch-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
