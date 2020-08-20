---
description: sp_cursoropen (Transact-SQL)
title: sp_cursoropen (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cursoropen
- sp_cursoropen_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cursoropen
ms.assetid: 16462ede-4393-4293-a598-ca88c48ca70b
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 1faec2f41d2396102b4ee675f2dac40be4b9b216
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88489499"
---
# <a name="sp_cursoropen-transact-sql"></a>sp_cursoropen (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Öffnet einen Cursor. sp_cursoropen definiert die SQL-Anweisung, die den Cursor-und Cursor Optionen zugeordnet ist, und füllt dann den Cursor auf. sp_cursoropen entspricht der Kombination der [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen DECLARE_CURSOR und geöffnet. Diese Prozedur wird aufgerufen, indem ID = 2 in einem Tabular Data Stream-Paket (TDS) angegeben wird.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_cursoropen cursor OUTPUT, stmt  
    [, scrollopt[ OUTPUT ] [ , ccopt[ OUTPUT ]  
    [ ,rowcount OUTPUT [ ,boundparam][,...n]]] ]]  
```  
  
## <a name="arguments"></a>Argumente  
 *Cursor*  
 Ein von SQL Server generierter Cursorbezeichner. der *Cursor* ist ein *handle* -Wert, der für alle nachfolgenden Prozeduren mit dem Cursor angegeben werden muss, z. b. sp_cursorfetch. der *Cursor* ist ein erforderlicher Parameter mit einem **int** -Rückgabewert.  
  
 *Cursor* ermöglicht das Aktivieren mehrerer Cursor auf einer einzelnen Datenbankverbindung.  
  
 *stmt*  
 Ein erforderlicher Parameter, der das Cursorresultset definiert. Jede gültige Abfrage Zeichenfolge (Syntax und Bindung) eines beliebigen Zeichen folgen Typs (unabhängig von Unicode, Größe usw.) kann als gültiger *stmt* -Werttyp fungieren.  
  
 *scrollopt*  
 Option für den Bildlauf. *scrollopt* ist ein optionaler Parameter, der einen der folgenden **int** -Eingabewerte erfordert.  
  
|Wert|Beschreibung|  
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
  
 Aufgrund der Möglichkeit, dass der angeforderte Wert nicht für den von *stmt*definierten Cursor geeignet ist, dient dieser Parameter sowohl als Eingabe als auch als Ausgabe. In solchen Fällen weist SQL Server einen passenden Wert zu.  
  
 *ccopt*  
 Option für die Parallelitätssteuerung. *ccopt* ist ein optionaler Parameter, der einen der folgenden **int** -Eingabewerte erfordert.  
  
|Wert|Beschreibung|  
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
  
 Wie bei *scrollopt* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kann die angeforderten *ccopt* -Werte überschreiben.  
  
 *RowCount*  
 Die Anzahl der mit AUTO_FETCH zu verwendenden Fetchpufferzeilen. Der Standardwert ist 20 Zeilen. die Zeilen *Anzahl* verhält sich anders, wenn Sie als Eingabe Wert im Vergleich zu einem Rückgabewert zugewiesen wird.  
  
|Als Eingabewert|Als Rückgabewert|  
|--------------------|---------------------|  
|Wenn der AUTO_FETCH *scrollopt* -Wert angegeben wird, stellt *ROWCOUNT* die Anzahl der Zeilen dar, die im Fetchpuffer platziert werden sollen.<br /><br /> Hinweis: >0 ist ein gültiger Wert, wenn AUTO_FETCH angegeben, aber andernfalls ignoriert wird.|Stellt die Anzahl der Zeilen im Resultset dar, außer wenn der Wert für *scrollopt* AUTO_FETCH angegeben wird.|  
  
-  
  
 *boundparam*  
 Gibt die Verwendung zusätzlicher Parameter an. *boundparam* ist ein optionaler Parameter, der angegeben werden muss, wenn der *scrollopt* -PARAMETERIZED_STMT Wert auf ON festgelegt ist.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 Wenn kein Fehler ausgelöst wird, gibt sp_cursoropen einen der folgenden Werte zurück.  
  
 0  
 Die Prozedur wurde erfolgreich ausgeführt.  
  
 0x0001  
 Fehler während der Ausführung (geringfügiger Fehler, nicht schwerwiegend genug, um einen Fehler im Betriebsablauf auszulösen).  
  
 0x0002  
 Ein asynchroner Vorgang wird ausgeführt.  
  
 0x0002  
 Ein FETCH-Vorgang wird ausgeführt.  
  
 Ein  
 Die Zuordnung dieses Cursors wurde von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aufgehoben, und er ist nicht verfügbar.  
  
 Wenn ein Fehler ausgelöst wird, sind die Rückgabewerte möglicherweise inkonsistent, und die Genauigkeit kann nicht gewährleistet werden.  
  
 Wenn der *ROWCOUNT* -Parameter als Rückgabewert angegeben wird, tritt das folgende Resultset auf.  
  
 -1  
 Wird zurückgegeben, wenn die Anzahl der Zeilen unbekannt oder nicht anwendbar ist.  
  
 -n  
 Wird zurückgegeben, wenn eine asynchrone Auffüllung aktiviert ist. Stellt die Anzahl der Zeilen dar, die im Fetchpuffer platziert wurden, wenn der *scrollopt* -AUTO_FETCH Wert angegeben wird.  
  
 Wenn RPC verwendet wird, lauten die Rückgabewerte wie folgt.  
  
 0  
 Die Prozedur ist erfolgreich.  
  
 1  
 Fehler bei der Prozedur.  
  
 2  
 Ein KEYSET-Cursor wird asynchron generiert.  
  
 16  
 Ein FAST_FORWARD-Cursor wurde automatisch geschlossen.  
  
> [!NOTE]  
>  Wenn die sp_cursoropen Prozedur erfolgreich ausgeführt wird, werden die RPC-Rückgabe Parameter und ein Resultset mit TDS-Spalten Formatinformationen (0xa0 & 0xA1-Meldungen) gesendet. Andernfalls wird mindestens eine TDS-Fehlermeldung gesendet. In beiden Fällen werden keine Zeilendaten zurückgegeben, *und die Anzahl* der abgeschlossenen Nachrichten ist 0 (null). Wenn Sie eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Version vor 7.0 verwenden, werden 0xa0 und 0xa1 (Standard für SELECT-Anweisungen) zusammen mit den Tokendatenströmen 0xa5 und 0xa4 zurückgegeben. Wenn Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 verwenden, wird 0x81 (Standard für SELECT-Anweisungen) zusammen mit den Tokendatenströmen 0xa5 und 0xa4 zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
  
## <a name="stmt-parameter"></a>stmt-Parameter  
 Wenn *stmt* die Ausführung einer gespeicherten Prozedur angibt, können die Eingabeparameter entweder als Konstanten als Teil der *stmt* -Zeichenfolge definiert oder als *boundparam* -Argumente angegeben werden. Deklarierte Variablen können auf diese Weise als gebundene Parameter übergeben werden.  
  
 Der zulässige Inhalt des *stmt* -Parameters hängt davon ab, ob der *ccopt* -ALLOW_DIRECT Rückgabewert durch oder mit den restlichen *ccopt* -Werten verknüpft wurde, d. h.:  
  
-   Wenn ALLOW_DIRECT nicht angegeben ist, muss entweder eine [!INCLUDE[tsql](../../includes/tsql-md.md)] Select-oder eine EXECUTE-Anweisung verwendet werden, die für eine gespeicherte Prozedur mit einer einzelnen SELECT-Anweisung aufgerufen wird. Weiterhin muss sich die SELECT-Anweisung als Cursor qualifizieren; d. h., sie darf nicht die Schlüsselwörter SELECT INTO oder FOR BROWSE enthalten.  
  
-   Wenn ALLOW_DIRECT angegeben wird, kann dies zu mindestens einer [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung führen, einschließlich der Anweisungen, die ihrerseits andere gespeicherte Prozeduren mit mehreren Anweisungen ausführen. Nicht-SELECT-Anweisungen oder beliebige SELECT-Anweisungen, die die Schlüsselwörter SELECT INTO oder FOR BROWSE enthalten, werden einfach ausgeführt und führen nicht zur Erstellung eines Cursors. Dies trifft auch auf jede SELECT-Anweisung zu, die in einem aus mehreren Anweisungen bestehenden Batch enthalten ist. Wenn eine SELECT-Anweisung Klauseln enthält, die nur Cursor betreffen, werden diese Klauseln ignoriert. Wenn der Wert von *ccopt* beispielsweise 0x2002 lautet, ist dies eine Anforderung für:  
  
    -   Ein Cursor mit Bildlaufsperren, wenn es nur eine einzelne SELECT-Anweisung gibt, die sich als Cursor qualifiziert, oder  
  
    -   Eine direkte Anweisungsausführung, wenn mehrere Anweisungen, eine einzelne Nicht-SELECT-Anweisung oder eine SELECT-Anweisung, die sich nicht als Cursor qualifiziert, vorhanden sind.  
  
## <a name="scrollopt-parameter"></a>scrollopt-Parameter  
 Die ersten fünf *scrollopt* -Werte (Keysey, Dynamic, FORWARD_ONLY, static und FAST_FORWARD) schließen sich gegenseitig aus.  
  
 PARAMETERIZED_STMT und CHECK_ACCEPTED_TYPES können durch OR mit einem der ersten fünf Werte verknüpft werden.  
  
 AUTO_FETCH und AUTO_CLOSE können durch OR mit FAST_FORWARD verknüpft werden.  
  
 Wenn CHECK_ACCEPTED_TYPES aktiviert ist, muss mindestens einer der letzten fünf *scrollopt* -Werte (KEYSET_ACCEPTABLE `,` DYNAMIC_ACCEPTABLE, FORWARD_ONLY_ACCEPTABLE, STATIC_ACCEPTABLE oder FAST_FORWARD_ACCEPTABLE) aktiviert sein.  
  
 STATIC-Cursor werden immer als READ_ONLY geöffnet. Dies bedeutet, dass die zugrunde liegende Tabelle über diesen Cursor nicht aktualisiert werden kann.  
  
## <a name="ccopt-parameter"></a>ccopt-Parameter  
 Die ersten vier *ccopt* -Werte (READ_ONLY, SCROLL_LOCKS und beide optimistischen Werte) schließen sich gegenseitig aus.  
  
> [!NOTE]  
>  Wenn Sie einen der ersten vier *ccopt* -Werte auswählen, wird bestimmt, ob der Cursor schreibgeschützt ist oder ob Sperr-oder optimistische Methoden verwendet werden, um verlorene Updates zu verhindern. Wenn kein *ccopt* -Wert angegeben wird, ist der Standardwert optimistisch.  
  
 ALLOW_DIRECT und CHECK_ACCEPTED_TYPES können durch OR mit einem der ersten vier Werte verknüpft werden.  
  
 UPDT_IN_PLACE kann durch OR mit READ_ONLY, SCROLL_LOCKS oder einem der OPTIMISTIC-Werte verknüpft werden.  
  
 Wenn CHECK_ACCEPTED_TYPES ist, muss mindestens einer der letzten vier *ccopt* -Werte (READ_ONLY_ACCEPTABLE, SCROLL_LOCKS_ACCEPTABLE und einer der OPTIMISTIC_ACCEPTABLE Werte) gleich sein.  
  
 Positionierte UPDATE-und DELETE-Funktionen können nur innerhalb des Fetchpuffers und nur dann ausgeführt werden, wenn der *ccopt* -Wert SCROLL_LOCKS oder optimistischer ist. Wenn SCROLL_LOCKS als Wert angegeben wird, verläuft der Vorgang mit Sicherheit erfolgreich. Wenn OPTIMISTIC als Wert angegeben wird, ist der Vorgang fehlerhaft, wenn die Zeile seit dem letzten Abruf geändert wurde.  
  
 Die Fehlerursache liegt darin, dass bei Angabe des Werts OPTIMISTIC eine Funktion für die Steuerung durch vollständige Parallelität ausgeführt wird, indem entsprechend der Vorgabe in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Zeitstempel oder Prüfsummenwerte verglichen werden. Wenn beliebige dieser Zeilen nicht übereinstimmen, ist der Vorgang fehlerhaft.  
  
 Wenn UPDT_IN_PLACE als Rückgabewert angegeben wird, sind die Ergebnisse wie folgt:  
  
-   Wenn der Parameter beim Ausführen eines positionierten Updates für eine Tabelle mit einem eindeutigen Index nicht festgelegt ist, löscht der Cursor die Zeile aus seiner Arbeitstabelle und fügt sie am Ende einer beliebigen vom Cursor verwendeten Schlüsselspalte ein. Dabei werden die Spalten geändert.  
  
-   Wenn der Parameter auf ON festgelegt ist, aktualisiert der Cursor einfach die Schlüsselspalten in der ursprünglichen Zeile der Arbeitstabelle.  
  
## <a name="bound_param-parameter"></a>bound_param-Parameter  
 Der Parameter Name sollte *ParamDef* lauten, wenn PARAMETERIZED_STMT entsprechend der Fehlermeldung im Code angegeben wird. Wenn PARAMETERIZED_STMT nicht angegeben ist, wird kein Name in der Fehlermeldung angegeben.  
  
## <a name="rpc-considerations"></a>Überlegungen zu RPC  
 Das RPC-RETURN_METADATA-Eingabeflag kann auf 0x0001 festgelegt werden. Dadurch wird angefordert, dass Metadaten zur SELECT-Liste des Cursors im TDS-Datenstrom zurückgegeben werden.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="bound_param-parameter"></a>bound_param-Parameter  
 Alle nach dem fünften Parameter übergebenen Parameter werden als Eingabeparameter an den Anweisungsplan übergeben. Der erste derartige Parameter muss eine Zeichenfolge im folgenden Format sein:  
  
 *{lokaler Variablenname Datentyp} [,... Nr*  
  
 Nachfolgende Parameter werden verwendet, um die Werte zu übergeben, die für den *Namen der lokalen Variablen* in der-Anweisung ersetzt werden sollen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_cursorfetch &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-cursorfetch-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
