---
title: xp_sprintf (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/09/2020
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- xp_sprintf_TSQL
- xp_sprintf
dev_langs:
- TSQL
helpviewer_keywords:
- xp_sprintf
ms.assetid: 1eedd65c-03cc-4eab-b76e-04684fdfec52
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 3ba1648da108762b03155eb93e1ee11c53a75583
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "75831768"
---
# <a name="xp_sprintf-transact-sql"></a>xp_sprintf (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Formatiert und speichert eine Folge von Zeichen und Werten im Ausgabeparameter vom Zeichenfolgendatentyp. Jedes Formatierungsargument wird dabei durch das entsprechende Argument ersetzt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
xp_sprintf { string OUTPUT , format }  
     [ , argument [ ,...n ] ]  
```  
  
## <a name="arguments"></a>Argumente  
 *string*  
 Eine **varchar** -Variable für die Ausgabe.  
  
 OUTPUT  
 Wenn dieser Parameter angegeben wird, wird der Wert der Variablen in den Ausgabeparameter gesetzt.  
  
 *format*  
 Eine Formatierungszeichenfolge mit Platzhaltern für *argument* -Werte, ähnlich wie bei der **sprintf** -Funktion der Programmiersprache C. Derzeit wird nur das %s-Formatierungsargument unterstützt.  
  
 *argument*  
 Eine Zeichenfolge, die den Wert des entsprechenden Formatierungsarguments darstellt.  
  
 *n*  
 Ein Platzhalter, der anzeigt, dass bis zu 50 Argumente angegeben werden können.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
 **xp_sprintf** gibt die folgende Nachricht zurück:  
  
 `The command(s) completed successfully.`  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **public** -Rolle.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte System Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Allgemeine erweiterte gespeicherte Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/general-extended-stored-procedures-transact-sql.md)   
 [xp_sscanf &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/xp-sscanf-transact-sql.md)  
  
  
