---
title: sp_cursorprepare (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cursor_prepare_TSQL
- sp_cursor_prepare
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cursor_prepare
ms.assetid: 6207e110-f4bf-4139-b3ec-b799c9cb3ad7
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 641086797c9d6b8ddf6a86a83de1b5d7b69dcb39
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82831712"
---
# <a name="sp_cursorprepare-transact-sql"></a>sp_cursorprepare (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Kompiliert die Cursoranweisung oder den Batch in einen Ausführungsplan, erstellt jedoch keinen Cursor. Die kompilierte Anweisung kann später von sp_cursorexecute verwendet werden. Dieses Verfahren, das mit sp_cursorexecute gekoppelt ist, verfügt über die gleiche Funktion wie sp_cursoropen, ist jedoch in zwei Phasen unterteilt. sp_cursorprepare wird aufgerufen, indem ID = 3 in einem Tabular Data Stream-Paket (TDS) angegeben wird.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_cursorprepare prepared_handle OUTPUT, params , stmt , options  
    [ , scrollopt[ , ccopt]]  
```  
  
## <a name="arguments"></a>Argumente  
 *prepared_handle*  
 Ein SQL Server generierter *Bezeichner,* der einen ganzzahligen Wert zurückgibt.  
  
> [!NOTE]  
>  *prepared_handle* wird anschließend für eine sp_cursorexecute Prozedur bereitgestellt, um einen Cursor zu öffnen. Nach der Erstellung bleibt ein Handle so lange bestehen, bis Sie sich abmelden oder es über die sp_cursorunprepare-Prozedur explizit entfernen.  
  
 *params*  
 Identifiziert parametrisierte Anweisungen. Die *params* -Definition der Variablen wird in der Anweisung an die Stelle der Parametermarkierungen gesetzt. *params* ist ein erforderlicher Parameter, der einen Eingabewert vom Typ **ntext**, **nchar**,oder **nvarchar** erfordert. Geben Sie einen NULL-Wert ein, wenn die Anweisung nicht parametrisiert ist.  
  
> [!NOTE]  
>  Verwenden Sie eine **ntext** -Zeichenfolge als Eingabe Wert, wenn *stmt* parametrisiert und der *scrollopt* -PARAMETERIZED_STMT Wert aktiviert ist.  
  
 *stmt*  
 Definiert das Resultset des Cursors. Der *stmt* -Parameter ist erforderlich und erfordert einen der Eingabewerte **ntext**, **nchar** oder **nvarchar** .  
  
> [!NOTE]  
>  Die Regeln zum Angeben des *stmt* -Werts sind identisch mit denen für sp_cursoropen, mit der Ausnahme, dass der *stmt* -Zeichen folgen Datentyp **ntext**lauten muss.  
  
 *options*  
 Ein optionaler Parameter, der eine Beschreibung der Spalten im Cursorresultset zurückgibt. *Optionen* erfordern den folgenden **int** -Eingabe Wert.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|0x0001|RETURN_METADATA|  
  
 *scrollopt*  
 Scrolloption. *scrollopt* ist ein optionaler Parameter, der einen der folgenden **int** -Eingabewerte erfordert.  
  
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
  
 Da der angeforderte Wert möglicherweise nicht für den von *stmt*definierten Cursor geeignet ist, dient dieser Parameter sowohl als Eingabe als auch als Ausgabe. In solchen Fällen weist [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] einen passenden Wert zu.  
  
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
  
 Wie bei *scrollpt* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kann einen anderen Wert als den angeforderten zuweisen.  
  
## <a name="remarks"></a>Bemerkungen  
 Der RPC-Statusparameter entspricht einem der folgenden Werte:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|0|Erfolg|  
|0x0001|Fehler|  
|1FF6|Es konnten keine Metadaten zurückgegeben werden.<br /><br /> Hinweis: der Grund hierfür ist, dass die Anweisung kein Resultset erzeugt. Beispielsweise handelt es sich um eine INSERT-oder DDL-Anweisung.|  
  
## <a name="examples"></a>Beispiele  
  Im folgenden finden Sie ein Beispiel für die Verwendung von sp_cursorprepare und sp_cursorexecute

```sql
declare @handle int , @p5 int, @p6 int
exec sp_cursorprepare @handle OUTPUT, 
    N'@dbid int', 
    N'select * from sys.databases where database_id < @dbid',
    1,
    @p5 output,
    @p6 output


declare @p1 int  
set @P1 = @handle 
declare @p2 int   
declare @p3 int  
declare @p4 int  
set @P6 = 4 
exec sp_cursorexecute @p1, @p2 OUTPUT, @p3 output , @p4 output, @p5 OUTPUT, @p6

exec sp_cursorfetch @P2

exec sp_cursorunprepare @handle
exec sp_cursorclose @p2
```
 
 Wenn *stmt* parametrisiert und der *scrollopt* -PARAMETERIZED_STMT Wert aktiviert ist, lautet das Format der Zeichenfolge wie folgt:  
  
 { * \< Name der lokalen Variablen> * * \< Datentyp>* } [,... *n* ]  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_cursorexecute &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-cursorexecute-transact-sql.md)   
 [sp_cursoropen &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-cursoropen-transact-sql.md)   
 [sp_cursorunprepare &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-cursorunprepare-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
