---
title: sp_cursorfetch (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cursorfetch
- sp_cursorfetch_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cursorfetch
ms.assetid: 14513c5e-5774-4e4c-92e1-75cd6985b6a3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4635bffa5b5b681d0ff202c4231c4d8b8d10ae26
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68108513"
---
# <a name="sp_cursorfetch-transact-sql"></a>sp_cursorfetch (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ruft einen Puffer mit mindestens einer Zeile aus der Datenbank ab. Die Gruppe der Zeilen in diesem Puffer wird als *Fetchpuffer*des Cursors bezeichnet. sp_cursorfetch wird aufgerufen, indem ID = 7 in einem Tabular Data Stream-Paket (TDS) angegeben wird.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_cursorfetch cursor  
    [ , fetchtype[ , rownum [ , nrows] ]]   
```  
  
## <a name="arguments"></a>Argumente  
 *Cursor*  
 Ein *handle* -Wert, der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von generiert und von sp_cursoropen zurückgegeben wird. *Cursor* ist ein erforderlicher Parameter, der einen **int** -Eingabe Wert aufruft. Weitere Informationen finden Sie im Abschnitt mit den Hinweisen weiter unten in diesem Thema.  
  
 *fetchType*  
 Gibt an, welcher Cursorpuffer abgerufen werden soll. *FetchType* ist ein optionaler Parameter, der einen der folgenden ganzzahligen Eingabewerte erfordert.  
  
|Wert|Name|BESCHREIBUNG|  
|-----------|----------|-----------------|  
|0x0001|FIRST|Ruft den ersten Puffer von *nrows* -Zeilen ab. Wenn *nrows* 0 (null) entspricht, wird der Cursor vor dem Resultset positioniert, und es werden keine Zeilen zurückgegeben.|  
|0x0002|NEXT|Ruft den nächsten Puffer von *nrows* -Zeilen ab.|  
|0x0004|PREV|Ruft den vorherigen Puffer von *nrows* -Zeilen ab.<br /><br /> Hinweis: bei Verwendung von Prev für einen FORWARD_ONLY Cursor wird eine Fehlermeldung zurückgegeben, da FORWARD_ONLY nur einen Bildlauf in einer Richtung unterstützt.|  
|0x0008|LAST|Ruft den letzten Puffer von *nrows* -Zeilen ab. Wenn *nrows* 0 (null) entspricht, wird der Cursor nach dem Resultset positioniert, und es werden keine Zeilen zurückgegeben.<br /><br /> Hinweis: bei Verwendung der Last für einen FORWARD_ONLY Cursor wird eine Fehlermeldung zurückgegeben, da FORWARD_ONLY nur einen Bildlauf in einer Richtung unterstützt.|  
|0x10|ABSOLUTE|Ruft einen Puffer von *nrows* -Zeilen ab, beginnend mit der *rowNum* -Zeile.<br /><br /> Hinweis: die Verwendung von "absolute" für einen dynamischen Cursor oder einen FORWARD_ONLY Cursor gibt eine Fehlermeldung zurück, da FORWARD_ONLY nur einen Bildlauf in einer Richtung unterstützt.|  
|0x20|RELATIVE|Ruft den Puffer von *nrows* -Zeilen ab, beginnend mit der Zeile, die als *rowNum* -Wert von Zeilen aus der ersten Zeile im aktuellen Block angegeben wird. In diesem Fall kann *rowNum* eine negative Zahl sein.<br /><br /> Hinweis: bei Verwendung von relative für einen FORWARD_ONLY Cursor wird eine Fehlermeldung zurückgegeben, da FORWARD_ONLY nur einen Bildlauf in einer Richtung unterstützt.|  
|0x80|REFRESH|Füllt den Puffer anhand zugrunde liegender Tabellen auf.|  
|0x100|INFO|Ruft Informationen zum Cursor ab. Diese Informationen werden mithilfe der *rowNum* -und *nrows* -Parameter zurückgegeben. Wenn also info angegeben wird, werden *rowNum* und *nrows* zu Ausgabeparametern.|  
|0x200|PREV_NOADJUST|Wird analog zu PREV verwendet. Wenn der Anfang des Resultsets vorzeitig gefunden wird, können die Ergebnisse jedoch variieren.|  
|0x400|SKIP_UPDT_CNCY|Muss mit einem der anderen *FetchType* -Werte, mit Ausnahme von Informationen, verwendet werden.|  
  
> [!NOTE]  
>  Der Wert 0x40 wird nicht unterstützt.  
  
 Weitere Informationen finden Sie im Abschnitt mit den Hinweisen weiter unten in diesem Thema.  
  
 *rowNum*  
 Ist ein optionaler Parameter, mit dem die Zeilen Position für die absoluten und die Info- *FetchType* -Werte angegeben werden, indem nur ganzzahlige Werte für die Eingabe oder Ausgabe oder beides verwendet werden. *rowNum* fungiert als Zeilen Offset für den Wert des *FetchType* -Bitwerts in Relation. *rowNum* wird für alle anderen Werte ignoriert. Weitere Informationen finden Sie im Abschnitt mit den Hinweisen weiter unten in diesem Thema.  
  
 *nrows*  
 Ein optionaler Parameter, mit dem die Anzahl der abzurufenden Zeilen angegeben wird. Wenn *nrows* nicht angegeben wird, beträgt der Standardwert 20 Zeilen. Um die Position ohne Rückgabe von Daten festzulegen, geben Sie den Wert 0 an. Wenn *nrows* auf die Abfrage " *FetchType* Info" angewendet wird, wird die Gesamtzahl der Zeilen in dieser Abfrage zurückgegeben.  
  
> [!NOTE]  
>  *nrows* wird vom Wert des Werts " *FetchType* aktualisieren" ignoriert.  
>   
>  Weitere Informationen finden Sie im Abschnitt mit den Hinweisen weiter unten in diesem Thema.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 In den folgenden Tabellen sind die Werte dargestellt, die bei Angabe des Bitwerts INFO zurückgegeben werden können.  
  
> [!NOTE]  
>  :   Wenn keine Zeilen zurückgegeben werden, bleibt der Pufferinhalt unverändert.  
  
|*\<rowNum->*|Festlegen auf|  
|------------------|------------|  
|Falls nicht geöffnet|0|  
|Falls vor dem Resultset positioniert|0|  
|Falls nach dem Resultset positioniert|-1|  
|Für KEYSET- und STATIC-Cursor|Die absolute Zeilennummer der aktuellen Position im Resultset|  
|Für DYNAMIC-Cursor|1|  
|Für ABSOLUTE|-1 gibt die letzte Zeile in einem Satz zurück.<br /><br /> -2 gibt die vorletzte Zeile in einem Satz zurück usw.<br /><br /> Hinweis: Wenn in diesem Fall mehr als eine Zeile abgerufen werden soll, werden die letzten beiden Zeilen des Resultsets zurückgegeben.|  
  
|*\<nrows->*|Festlegen auf|  
|-----------------|------------|  
|Falls nicht geöffnet|0|  
|Für KEYSET- und STATIC-Cursor|Normalerweise die aktuelle Keysetgröße.<br /><br /> **-m** , wenn sich der Cursor in einer asynchronen Erstellung befindet, wobei *m* Zeilen zu diesem Zeitpunkt gefunden werden.|  
|Für DYNAMIC-Cursor|-1|  
  
## <a name="remarks"></a>Bemerkungen  
  
## <a name="cursor-parameter"></a>cursor-Parameter  
 Bevor Abrufvorgänge stattgefunden haben, befindet sich die Standardposition eines Cursors vor der ersten Zeile des Resultsets.  
  
## <a name="fetchtype-parameter"></a>fetchtype-Parameter  
 Mit Ausnahme von SKIP_UPD_CNCY schließen sich die *FetchType* -Werte gegenseitig aus.  
  
 Wenn SKIP_UPDT_CNCY angegeben wird, werden die timestamp-Spaltenwerte nicht in die Keysettabelle geschrieben, wenn eine Zeile abgerufen oder aktualisiert wird. Wenn die Keysetzeile aktualisiert wird, wird für die Werte der timestamp-Spalten der vorherige Wert beibehalten. Wenn die Keysetzeile eingefügt wird, wird die Definition der Werte für die timestamp-Spalten aufgehoben.  
  
 Bei KEYSET-Cursorn bedeutet dies, dass die Werte der Keysettabelle während des letzten durchgehenden FETCH-Vorgangs festgelegt wurden, falls einer ausgeführt wurde. Andernfalls werden die Werte während der Auffüllung festgelegt.  
  
 Bei DYNAMIC-Cursorn bedeutet dies, dass die gleichen Ergebnisse erzeugt werden wie bei KEYSET, wenn der SKIP-Vorgang mit einer Aktualisierung ausgeführt wird. Bei jedem anderen Fetchtyp wird die Keysettabelle abgeschnitten. Dies bedeutet, dass die Zeilen eingefügt werden und die Definition der Werte für die timestamp-Spalte(n) aufgehoben wird. Wenn Sie sp_cursorfetch für DYNAMIC-Cursor ausführen, sollten Sie SKIP_UPDT_CNCY bei jedem anderen Vorgang als REFRESH folglich vermeiden.  
  
 Wenn ein Abrufvorgang fehlerhaft ist, weil die angeforderte Cursorposition außerhalb des Resultsets liegt, wird die Cursorposition unmittelbar nach der letzten Zeile festgelegt. Wenn ein Abrufvorgang fehlerhaft ist, weil die angeforderte Cursorposition vor dem Resultset liegt, wird die Cursorposition vor der ersten Zeile festgelegt.  
  
## <a name="rownum-parameter"></a>rownum-Parameter  
 Wenn Sie *rowNum*verwenden, wird der Puffer beginnend mit der angegebenen Zeile aufgefüllt.  
  
 Der *FetchType* -Wert absolute verweist auf die Position von *rowNum* im gesamten Resultset. Eine negative Zahl mit ABSOLUTE gibt an, dass bei dem Vorgang Zeilen vom Ende des Resultsets gezählt werden.  
  
 Der Wert für " *FetchType* " bezieht sich auf die Position von *rowNum* in Bezug auf die Position des Cursors am Anfang des aktuellen Puffers. Eine negative Zahl mit RELATIVE gibt an, dass sich der Cursor von der aktuellen Cursorposition rückwärts bewegt.  
  
## <a name="nrows-parameter"></a>nrows-Parameter  
 Diese Parameter werden durch die Werte für " *FetchType* " und "Info" ignoriert.  
  
 Wenn Sie einen FetchType-Wert First angeben, der einen *nrow* -Wert von 0 aufweist, wird der Cursor vor dem Resultset positioniert, das über keine Zeilen im *Fetchpuffer* verfügt.  
  
 Wenn Sie einen FetchType-Wert von "Last" angeben, der einen *nrow* -Wert von 0 aufweist, wird der Cursor nach dem Resultset positioniert, das keine Zeilen im aktuellen *Fetchpuffer* enthält.  
  
 Für die *FetchType* -Werte "Next", "Prev", "absolute", "relative" und "PREV_NOADJUST" ist ein *nrow* -Wert von "0" ungültig.  
  
## <a name="rpc-considerations"></a>Überlegungen zu RPC  
 Der RPC-Rückgabestatus gibt an, ob der KEYSET_SIZE-Parameter abgeschlossen ist, d. h., ob das Keyset oder die temporäre Tabelle asynchron aufgefüllt wird.  
  
 Der RPC-Statusparameter wird auf einen der Werte in der folgenden Tabelle festgelegt.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|0|Die Prozedur wurde erfolgreich ausgeführt.|  
|0x0001|Fehler bei der Prozedur.|  
|0x0002|Ein Abruf in einer negativen Richtung hätte die Cursorposition auf den Anfang des Resultsets festgelegt, wenn der Abruf logisch vor den Ergebnissen erfolgt wäre.|  
|0x10|Ein schnell vorwärts Cursor wurde automatisch geschlossen.|  
  
 Die Zeilen werden als typisches Resultset zurückgegeben: Spaltenformat (0x2a), Zeilen (0xd1) gefolgt vom fertigen Resultset (0xfd). Metadatentoken werden im gleichen Format gesendet wie für sp_cursoropen angegeben: 0x81, 0xa5 und 0xa4 für SQL Server 7.0-Benutzer usw. Die Zeilenstatusindikatoren werden ähnlich dem BROWSE-Modus als ausgeblendete Spalten am Ende jeder Zeile mit dem Spaltennamen "rowstat" und dem Datentyp INT4 gesendet. Diese rowstat-Spalte verfügt über einen der Werte aus der folgenden Tabelle.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|0x0001|FETCH_SUCCEEDED|  
|0x0002|FETCH_MISSING|  
  
 Weil das TDS-Protokoll keine Möglichkeit bietet, die nachfolgende Statusspalte ohne die vorherigen Spalten zu senden, werden Pseudodaten für fehlende Zeilen gesendet (auf NULL festlegbare Felder sind auf NULL, Felder fester Datenlänge auf 0 (leer) oder ggf. den Standardwert für diese Spalte festgelegt).  
  
 Die DONE-Zeilenanzahl ist immer 0 (null). Die DONE-Meldung enthält die tatsächliche Zeilenanzahl des Resultsets, und Fehler- oder Informationsmeldungen können zwischen allen TDS-Meldungen angezeigt werden.  
  
 Damit die Metadaten zur SELECT-Liste des Cursors im TDS-Datenstrom zurückgegeben werden, legen Sie das RPC RETURN_METADATA-Eingabeflag auf 1 fest.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-using-prev-to-change-a-cursor-position"></a>A. Ändern einer Cursorposition mithilfe von PREV  
 Angenommen, der Cursor h2 würde ein Resultset erzeugen, das über den folgenden Inhalt mit der angegebenen aktuellen Position verfügt:  
  
```  
row 1 contents      
row 2 contents  
row 3 contents  
row 4 contents  <-- current position  
row 5 contents   
row 6 contents  
```  
  
 Als nächstes würde ein sp_cursorfetch Prev mit einem *nrows* -Wert von 5 den Cursor logisch auf zwei Zeilen vor der ersten Zeile des Resultsets positionieren. In diesen Fällen wird der Cursor so eingerichtet, dass er an der ersten Zeile beginnt und die angeforderte Zeilenanzahl zurückgibt. Häufig bedeutet dies, dass er Zeilen aus dem PRIOR-Fetchpuffer zurückgibt.  
  
> [!NOTE]  
>  Genau in diesem Fall wird der RPC-Statusparameter auf 2 festgelegt.  
  
### <a name="b-using-prev_noadjust-to-return-fewer-rows-than-prev"></a>B. Zurückgeben von weniger Zeilen als PREV mithilfe von PREV_NOADJUST  
 PREV_NOADJUST schließt nie Zeilen ein, die sich an oder nach der aktuellen Cursorposition im Block zurückgegebener Zeilen befinden. In Fällen, in denen Prev Zeilen nach der aktuellen Position zurückgibt, gibt PREV_NOADJUST weniger Zeilen zurück, als in *nrows*angefordert wurden. Bei der aktuellen Position in Beispiel A oben ruft  (h2, 4, 1, 5) die folgenden Zeilen ab, wenn PREV angegeben ist:  
  
```  
row1 contents   
row2 contents  
row3 contents  
row4 contents  
row5 contents  
```  
  
 Wenn jedoch PREV_NOADJUST angewendet wird, ruft  (h2, 512, 6, 5) nur die folgenden Zeilen ab:  
  
```  
row1 contents   
row2 contents  
row3 contents   
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_cursoropen &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-cursoropen-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
