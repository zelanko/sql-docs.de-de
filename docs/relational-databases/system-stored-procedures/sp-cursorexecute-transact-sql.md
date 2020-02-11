---
title: sp_cursorexecute (Transact-SQL) | Microsoft-Dokumentation
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
ms.openlocfilehash: 5d0979ba7df97ebc9fc5b79d8fd0cbd34b6a59a4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68108531"
---
# <a name="sp_cursorexecute-transact-sql"></a>sp_cursorexecute (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Erstellt einen Cursor, der auf dem von sp_cursorprepare erstellten Ausführungsplan basiert, und füllt ihn auf. Dieses Verfahren, das mit sp_cursorprepare gekoppelt ist, verfügt über die gleiche Funktion wie sp_cursoropen, ist jedoch in zwei Phasen unterteilt. sp_cursorexecute wird aufgerufen, indem ID = 4 in einem Tabular Data Stream-Paket (TDS) angegeben wird.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_cursorexecute prepared_handle, cursor  
    [ , scrollopt[ OUTPUT ]  
    [ , ccopt[ OUTPUT ]  
    [ ,rowcount OUTPUT [ ,bound param][,...n]]]]]  
```  
  
## <a name="arguments"></a>Argumente  
 *prepared_handle*  
 Der vorbereitete Anweisungs *handle* -Wert, der von sp_cursorprepare zurückgegeben wird. *prepared_handle* ist ein erforderlicher Parameter, der einen **int** -Eingabe Wert aufruft.  
  
 *Hand*  
 Der von SQL Server generierte Cursorbezeichner. der *Cursor* ist ein erforderlicher Parameter, der für alle nachfolgenden Prozeduren angegeben werden muss, die auf den Cursor (z. b. sp_cursorfetch  
  
 *scrollopt*  
 Option für den Bildlauf. *scrollopt* ist ein optionaler Parameter, der einen **int** -Eingabe Wert erfordert. Der sp_cursorexecute*scrollopt* -Parameter hat dieselben Wert Optionen wie für sp_cursoropen.  
  
> [!NOTE]  
>  Der PARAMETERIZED_STMT-Wert wird nicht unterstützt.  
  
> [!IMPORTANT]  
>  Wenn kein *scrollopt* -Wert angegeben wird, ist der Standardwert unabhängig von dem in sp_cursorprepare angegebenen *scrollopt* -Wert Keyset.  
  
 *ccopt*  
 Option für die Währungssteuerung. *ccopt* ist ein optionaler Parameter, der einen **int** -Eingabe Wert erfordert. Der sp_cursorexecute*ccopt* -Parameter hat dieselben Wert Optionen wie für sp_cursoropen.  
  
> [!IMPORTANT]  
>  Wenn kein *ccopt* -Wert angegeben wird, ist der Standardwert unabhängig von dem in sp_cursorprepare angegebenen *ccopt* -Wert optimistisch.  
  
 *RowCount*  
 Ein optionaler Parameter, der die Anzahl der mit AUTO_FETCH zu verwendenden Fetchpufferzeilen angibt. Der Standardwert ist 20 Zeilen. die Zeilen *Anzahl* verhält sich anders, wenn Sie als Eingabe Wert im Vergleich zu einem Rückgabewert zugewiesen wird.  
  
|Als Eingabewert|Als Rückgabewert|  
|--------------------|---------------------|  
|Wenn AUTO_FETCH mit FAST_FORWARD Cursorn angegeben wird, stellt die *Zeilen Anzahl die* Anzahl der Zeilen dar, die im Fetchpuffer platziert werden sollen.|Stellt die Anzahl der Zeilen im Resultset dar. Wenn der *scrollopt* -AUTO_FETCH Wert angegeben wird, gibt *ROWCOUNT* die Anzahl der Zeilen zurück, die in den Abruf Puffer abgerufen wurden.|  
  
 *bound_param*  
 Gibt die optionale Verwendung zusätzlicher Parameter an.  
  
> [!NOTE]  
>  Alle nach dem fünften Parameter übergebenen Parameter werden als Eingabeparameter an den Anweisungsplan übergeben.  
  
## <a name="code-return-value"></a>Code Rückgabewert  
 *ROWCOUNT* kann die folgenden Werte zurückgeben.  
  
|value|BESCHREIBUNG|  
|-----------|-----------------|  
|-1|Die Anzahl der unbekannten Zeilen.|  
|-n|Eine asynchrone Auffüllung ist wirksam.|  
  
## <a name="remarks"></a>Bemerkungen  
  
## <a name="scrollopt-and-ccopt-parameters"></a>scrollopt-Parameter und ccopt-Parameter  
 *scrollopt* und *ccopt* sind nützlich, wenn die zwischengespeicherten Pläne für den Server Cache vorzeitig entfernt werden, was bedeutet, dass das vorbereitete handle, das die Anweisung identifiziert, neu kompiliert werden muss. Die *scrollopt* -und *ccopt* -Parameterwerte müssen den Werten entsprechen, die in der ursprünglichen Anforderung an sp_cursorprepare gesendet wurden.  
  
> [!NOTE]  
>  PARAMETERIZED_STMT sollte *scrollopt*nicht zugewiesen werden.  
  
 Nicht übereinstimmende Werte bewirken eine Neukompilierung der Pläne, wodurch Vorbereitungs- und Ausführungsvorgänge negiert werden.  
  
## <a name="rpc-and-tds-considerations"></a>Überlegungen zu RPC und TDS  
 Das RPC-RETURN_METADATA-Eingabeflag kann auf 1 festgelegt werden. Dadurch wird angefordert, dass Metadaten zur SELECT-Liste des Cursors im TDS-Datenstrom zurückgegeben werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_cursoropen &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-cursoropen-transact-sql.md)   
 [sp_cursorfetch &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-cursorfetch-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
