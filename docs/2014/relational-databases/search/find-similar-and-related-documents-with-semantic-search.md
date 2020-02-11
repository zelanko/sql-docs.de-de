---
title: Suchen von ähnlichen und verwandten Dokumenten mit semantischer Suche | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- semantic search [SQL Server], document similarity queries
ms.assetid: 9f527883-031b-442f-8e95-24bc0151ecbf
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 1b2e30534fb5e0232ff2046e30e2e14075dfb807
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66011320"
---
# <a name="find-similar-and-related-documents-with-semantic-search"></a>Suchen von ähnlichen und verwandten Dokumenten mit semantischer Suche
  Beschreibt, wie ähnliche oder verwandte Dokumente oder Textwerte sowie Informationen zur Ähnlichkeit oder Verwandtschaft über Spalten gesucht werden, die für die statistische semantische Indizierung konfiguriert sind.  
  
##  <a name="BasicsQuerySimilar"></a>Suchen von ähnlichen oder verwandten Dokumenten  
  
###  <a name="HowToQuerySimilar"></a>Gewusst wie: Suchen von ähnlichen oder verwandten Dokumenten mit semanticsimilaritytable  
 Fragen Sie zum Identifizieren ähnlicher oder verwandter Dokumente in einer bestimmten Spalte die Funktion [semanticsimilaritytable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semanticsimilaritytable-transact-sql) ab.  
  
 **SEMANTICSIMILARITYTABLE** gibt eine Tabelle mit keiner Zeile, einer Zeile oder mehreren Zeilen zurück, deren Inhalt in der angegebenen Spalte dem angegebenen Dokument semantisch ähnelt. Auf diese Rowsetfunktion kann in der FROM-Klausel einer SELECT-Anweisung wie auf einen regulären Tabellennamen verwiesen werden.  
  
 Ähnliche Dokumente können nicht über Spalten hinweg abgefragt werden. Die **SEMANTICSIMILARITYTABLE** -Funktion ruft nur Ergebnisse aus derselben Spalte wie die Quellspalte ab, die durch das **source_key** -Argument identifiziert wird.  
  
 Ausführliche Informationen zu den für die **SEMANTICSIMILARITYTABLE**-Funktion erforderlichen Parametern und zu der von ihr zurückgegebenen Ergebnistabelle finden Sie unter [semanticsimilaritytable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semanticsimilaritytable-transact-sql).  
  
> [!IMPORTANT]  
>  Für die Spalten, auf die Sie abzielen, muss die Volltext- und die semantische Indizierung aktiviert sein.  
  
###  <a name="HowToIdentifySimilar"></a>Beispiel: Suchen der wichtigsten Dokumente, die einem anderen Dokument ähneln  
 Im folgenden Beispiel werden die ersten 10 Kandidaten abgerufen, die dem von *@CandidateID* angegebenen Kandidaten aus der HumanResources. JobCandidate-Tabelle in der AdventureWorks2012-Beispieldatenbank ähneln.  
  
```scr  
SELECT TOP(10) KEY_TBL.matched_document_key AS Candidate_ID  
FROM SEMANTICSIMILARITYTABLE  
    (  
    HumanResources.JobCandidate,  
    Resume,  
    @CandidateID  
    ) AS KEY_TBL  
ORDER BY KEY_TBL.score DESC;  
GO  
```  
  
##  <a name="BasicsQuerySimilarity"></a>Suchen von Informationen zur Art und Weise, wie Dokumente ähnlich oder verwandt sind  
  
###  <a name="HowToQuerySimilarity"></a>Gewusst wie: Suchen nach Informationen zur Ähnlichkeit von Dokumenten mit semanticsimilaritydetailstable  
 Um weitere Informationen zu den Schlüsselausdrücken abzurufen, die bewirken, dass Dokumente ähnlich oder verwandt sind, können Sie die Funktion [semanticsimilaritydetailstable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semanticsimilaritydetailstable-transact-sql) abfragen.  
  
 **SEMANTICSIMILARITYDETAILSTABLE** gibt eine Tabelle mit keiner, einer oder mehreren Zeilen von Schlüsselausdrücken zurück, die in zwei Dokumenten (einem Quelldokument und einem verglichenen Dokument) vorkommen, deren Inhalt semantisch ähnlich ist. Auf diese Rowsetfunktion kann in der FROM-Klausel einer SELECT-Anweisung wie auf einen regulären Tabellennamen verwiesen werden.  
  
 Ausführliche Informationen zu den für die **SEMANTICSIMILARITYDETAILSTABLE**-Funktion erforderlichen Parametern und zu der von ihr zurückgegebenen Ergebnistabelle finden Sie unter [semanticsimilaritydetailstable &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/semanticsimilaritydetailstable-transact-sql).  
  
> [!IMPORTANT]  
>  Für die Spalten, auf die Sie abzielen, muss die Volltext- und die semantische Indizierung aktiviert sein.  
  
###  <a name="HowToSimilarPhrases"></a>Beispiel: Suchen der wichtigsten Schlüssel Ausdrücke, die zwischen Dokumenten ähnlich sind  
 Im folgenden Beispiel werden die fünf Schlüsselausdrücke mit der größten Ähnlichkeit zwischen den in der **HumanResources.JobCandidate** -Tabelle angegebenen Kandidaten der AdventureWorks2012-Beispieldatenbank abgerufen.  
  
```sql  
SELECT TOP(5) KEY_TBL.keyphrase, KEY_TBL.score  
FROM SEMANTICSIMILARITYDETAILSTABLE  
    (  
    HumanResources.JobCandidate,  
    Resume, @CandidateID,  
    Resume, @MatchedID  
    ) AS KEY_TBL  
ORDER BY KEY_TBL.score DESC;  
GO  
```  
  
  
