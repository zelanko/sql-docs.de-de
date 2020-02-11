---
title: Funktionen für die voll Text Suche und die semantische Suche (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- semantic search [SQL Server], system functions
ms.assetid: a61a3694-7604-4583-962e-fc30f771c6fa
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 58bf5650a5ab06783ad0c889bc3286184a7d73ed
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68042751"
---
# <a name="full-text-search-and-semantic-search-functions-transact-sql"></a>Funktionen für Volltextsuche und semantische Suche (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  In diesem Abschnitt werden die Systemfunktionen für die Volltextsuche und die semantische Suche beschrieben.  
  
## <a name="full-text-search-functions"></a>Funktionen für die Volltextsuche  
 [CONTAINSTABLE &#40;Transact-SQL&#41;](../../relational-databases/system-functions/containstable-transact-sql.md)  
 Gibt eine Tabelle mit keiner, einer oder mehreren Zeilen für jene Spalten zurück, die präzise oder weniger präzise (fuzzy) Übereinstimmungen mit einzelnen Wörtern bzw. Ausdrücken aufweisen, die den Abstand von Wörtern oder gewichtete Treffer enthalten.  
  
 [FREETEXTTABLE &#40;Transact-SQL&#41;](../../relational-databases/system-functions/freetexttable-transact-sql.md)  
 Gibt eine Tabelle mit keiner, einer oder mehreren Zeilen für die Spalten zurück, die Werte enthalten, die mit der Bedeutung und nicht nur mit dem genauen Wortlaut des Texts in der angegebenen *freetext_string*identisch sind.  
  
## <a name="semantic-search-functions"></a>Funktionen für die semantische Suche  
 [semantickeyphrasetable &#40;Transact-SQL&#41;](../../relational-databases/system-functions/semantickeyphrasetable-transact-sql.md)  
 Gibt eine Tabelle mit keiner, einer oder mehreren Zeilen für die Schlüsselausdrücke zurück, die in der angegebenen Tabelle Spalten zugeordnet sind.  
  
 [semanticsimilaritydetailstable &#40;Transact-SQL&#41;](../../relational-databases/system-functions/semanticsimilaritydetailstable-transact-sql.md)  
 Gibt eine Tabelle mit keiner, einer oder mehreren Zeilen von Schlüssel Ausdrücken zurück, die in zwei Dokumenten (einem Quelldokument und einem übereinstimmenden Dokument) vorkommen, deren Inhalt semantisch ähnlich ist.  
  
 [semanticsimilaritytable &#40;Transact-SQL&#41;](../../relational-databases/system-functions/semanticsimilaritytable-transact-sql.md)  
 Gibt eine Tabelle mit keiner, einer oder mehreren Zeilen für die Spalten zurück, deren Inhalt einem angegebenen Dokument semantisch ähnlich ist.  
  
  
