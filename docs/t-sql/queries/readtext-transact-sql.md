---
title: READTEXT (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- READTEXT_TSQL
- READTEXT
dev_langs:
- TSQL
helpviewer_keywords:
- column reading [SQL Server]
- READTEXT statement
- reading columns
ms.assetid: 91b69853-1381-4306-8343-afdb73105738
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 8fde97db271ccd0307d0af75ea0c7d4aacad9703
ms.sourcegitcommit: 8ffc23126609b1cbe2f6820f9a823c5850205372
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2020
ms.locfileid: "81634802"
---
# <a name="readtext-transact-sql"></a>READTEXT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Liest **text**-, **ntext**- oder **image**-Werte aus einer **text**-, **ntext**- oder **image**-Spalte. Beginnt mit dem Lesen bei einem angegebenen Offset und liest die angegebene Anzahl von Bytes.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Verwenden Sie stattdessen die Funktion [SUBSTRING](../../t-sql/functions/substring-transact-sql.md).  
  
![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```syntaxsql
  
READTEXT { table.column text_ptr offset size } [ HOLDLOCK ]  
```  
  
## <a name="arguments"></a>Argumente  
_table_ **.** _column_  
Dies ist der Name einer Tabelle und Spalte, aus der gelesen wird. Tabellen- und Spaltennamen müssen den Regeln für [Bezeichner](../../relational-databases/databases/database-identifiers.md) entsprechen. Die Angabe der Tabellen- und Spaltennamen ist erforderlich, wohingegen die Angabe des Datenbank- und Besitzernamens optional ist.  
  
_text\_ptr_  
Ein gültiger Textzeiger. _text\_ptr_ muss vom Datentyp **binary(16)** sein.  
  
_offset_  
Die Anzahl von Bytes bei Verwendung des Datentyps **text** oder **image**. Oder die Anzahl von Bytes für Zeichen (bei Verwendung des Datentyps **ntext**), die ausgelassen werden sollen, bevor mit dem Lesen der **text**-, **image**- oder **ntext**-Daten begonnen wird.  
  
_size_ ist die Anzahl von Bytes bei Verwendung des Datentyps **text** oder **image**. Es kann sich dabei auch um die Anzahl von Bytes für Zeichen bei Verwendung des Datentyps **ntext** für die zu lesenden Daten handeln. Wenn _size_ gleich 0 ist, werden 4 KB Daten gelesen.  
  
HOLDLOCK  
Bewirkt, dass der Textwert bis zum Ende der Transaktion gesperrt wird und nur gelesen werden kann. Andere Benutzer können den Wert lesen, aber nicht ändern.  
  
## <a name="remarks"></a>Bemerkungen  
Verwenden Sie die Funktion [TEXTPTR](../../t-sql/functions/text-and-image-functions-textptr-transact-sql.md), um einen gültigen _text\_ptr_-Wert abzurufen. TEXTPTR gibt einen Zeiger auf die **text**-, **ntext**- oder **image**-Spalte in der angegebenen Zeile zurück. TEXTPRT kann auch einen Zeiger auf die **text**-, **ntext**- oder **image**-Spalte in der letzten Zeile zurückgeben, die von der Abfrage zurückgegeben wird, wenn mehrere Zeilen zurückgegeben werden. Da TEXTPTR eine 16 Bytes große binäre Zeichenfolge zurückgibt, ist es empfehlenswert, eine lokale Variable für den Textzeiger zu deklarieren und dann die Variable mit READTEXT einzusetzen. Weitere Informationen zum Deklarieren einer lokalen Variablen finden Sie unter [DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md).  
  
In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gibt es möglicherweise Textzeiger in Zeilen, die jedoch ungültig sind. Weitere Informationen zur Option **text in row** finden Sie unter [sp_tableoption &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-tableoption-transact-sql.md). Weitere Informationen dazu, wie Textzeiger ungültig gemacht werden können, finden Sie unter [sp_invalidate_textptr &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-invalidate-textptr-transact-sql.md).  
  
Der Wert der @@TEXTSIZE-Funktion ersetzt die für READTEXT angegebene Größe, wenn er kleiner als die für READTEXT angegebene Größe ist. Die @@TEXTSIZE-Funktion gibt die von der SET TEXTSIZE-Anweisung festgelegte Beschränkung der Anzahl zurückgegebener Datenbytes an. Weitere Informationen zum Festlegen der Sitzungseinstellung für TEXTSIZE finden Sie unter [SET TEXTSIZE &#40;Transact-SQL&#41;](../../t-sql/statements/set-textsize-transact-sql.md).  
  
## <a name="permissions"></a>Berechtigungen  
READTEXT-Berechtigungen werden standardmäßig an Benutzer mit SELECT-Berechtigungen für die angegebene Tabelle vergeben. Die Berechtigungen sind übertragbar, wenn SELECT-Berechtigungen übertragen werden.  
  
## <a name="examples"></a>Beispiele  
Im folgenden Beispiel werden die Zeichen 2 bis 26 der `pr_info`-Spalte in der `pub_info`-Tabelle gelesen.  
  
> [!NOTE]  
>  Um dieses Beispiel auszuführen, müssen Sie die **pubs**-Beispieldatenbank installieren.  
  
```  
USE pubs;  
GO  
DECLARE @ptrval varbinary(16);  
SELECT @ptrval = TEXTPTR(pr_info)   
   FROM pub_info pr INNER JOIN publishers p  
      ON pr.pub_id = p.pub_id   
      AND p.pub_name = 'New Moon Books'  
READTEXT pub_info.pr_info @ptrval 1 25;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
[@@TEXTSIZE &#40;Transact-SQL&#41;](../../t-sql/functions/textsize-transact-sql.md)   
[UPDATETEXT (Transact-SQL)](../../t-sql/queries/updatetext-transact-sql.md)   
[WRITETEXT (Transact-SQL)](../../t-sql/queries/writetext-transact-sql.md)  
  
  
