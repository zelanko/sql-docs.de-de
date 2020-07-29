---
title: TEXTVALID (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- TEXTVALID_TSQL
- TEXTVALID
dev_langs:
- TSQL
helpviewer_keywords:
- invalid text pointers [SQL Server]
- valid text pointers [SQL Server]
- TEXTVALID function
- checking text pointers
- text-pointer values
- verifying text pointers
ms.assetid: 9411c349-b59b-4740-a270-92f91d81ad23
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 808e0c57888cfdb7daa64ca5ec70c9068e1d12c0
ms.sourcegitcommit: 768f046107642f72693514f51bf2cbd00f58f58a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2020
ms.locfileid: "87112624"
---
# <a name="text-and-image-functions---textvalid-transact-sql"></a>Text- und Bildfunktionen: TEXTVALID (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Eine **text**-, **ntext**- oder **image**-Funktion, die prüft, ob der angegebene Textzeiger gültig ist.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Es steht keine alternative Funktionalität zur Verfügung.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
TEXTVALID ( 'table.column' ,text_ ptr )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Argumente
 *Tabelle*  
 Der Name der zu verwendenden Tabelle  
  
 *column*  
 Der Name der zu verwendenden Spalte  
  
 *text_ptr*  
 Der zu prüfende Textzeiger  
  
## <a name="return-types"></a>Rückgabetypen  
 **int**  
  
## <a name="remarks"></a>Bemerkungen  
 Gibt 1 zurück, wenn der Zeiger gültig ist, oder 0, wenn er ungültig ist. Beachten Sie, dass der Bezeichner für die **text**-Spalte auch den Tabellennamen enthalten muss. Sie können UPDATETEXT, WRITETEXT oder READTEXT nicht ohne einen gültigen Textzeiger verwenden.  
  
 Die folgenden Funktionen und Anweisungen sind auch bei Daten vom Typ **text**, **ntext** oder **image** hilfreich.  
  
|Funktion oder Anweisung|BESCHREIBUNG|  
|---------------------------|-----------------|  
|PATINDEX **(** ' _%pattern%_ ' **,** _expression_ **)**|Gibt die Zeichenposition einer angegebenen Zeichenfolge in Spalten vom Typ **text** oder **ntext** zurück.|  
|DATALENGTH **(** _expression_ **)**|Gibt die Länge der Daten in den **text**-, **ntext**- und **image**-Spalten zurück.|  
|SET TEXTSIZE|Gibt das Limit der **text**-, **ntext**- oder **image**-Daten, die von einer SELECT-Anweisung zurückgegeben werden sollen, in Byte zurück.|  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird gemeldet, ob für jeden Wert in der `logo`-Spalte der `pub_info`-Tabelle ein gültiger Textzeiger vorhanden ist.  
  
> [!NOTE]  
>  Um dieses Beispiel auszuführen, müssen Sie die **pubs**-Datenbank installieren.  
  
```  
USE pubs;  
GO  
SELECT pub_id, 'Valid (if 1) Text data'   
   = TEXTVALID ('pub_info.logo', TEXTPTR(logo))   
FROM pub_info  
ORDER BY pub_id;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
pub_id Valid (if 1) Text data   
------ ----------------------   
0736   1                        
0877   1                        
1389   1                        
1622   1                        
1756   1                        
9901   1                        
9952   1                        
9999   1                        
  
(8 row(s) affected)  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [DATALENGTH &#40;Transact-SQL&#41;](../../t-sql/functions/datalength-transact-sql.md)   
 [PATINDEX &#40;Transact-SQL&#41;](../../t-sql/functions/patindex-transact-sql.md)   
 [SET TEXTSIZE &#40;Transact-SQL&#41;](../../t-sql/statements/set-textsize-transact-sql.md)   
 [Text- und Bildfunktionen &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/b9c70488-1bf5-4068-a003-e548ccbc5199)   
 [TEXTPTR &#40;Transact-SQL&#41;](../../t-sql/functions/text-and-image-functions-textptr-transact-sql.md)  
  
  
