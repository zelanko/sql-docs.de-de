---
description: semanticsimilaritydetailstable (Transact-SQL)
title: semanticsimilaritydetailstable (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- semanticsimilaritydetailstable
- semanticsimilaritydetailstable_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- semanticsimilaritydetailstable function
ms.assetid: 038d751a-fca5-4b4c-9129-cba741a4e173
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: fa94a6c16eaaf2548b3c0375d43848d5e03a7f12
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88474579"
---
# <a name="semanticsimilaritydetailstable-transact-sql"></a>semanticsimilaritydetailstable (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Gibt eine Tabelle mit keiner, einer oder mehreren Zeilen von Schlüsselausdrücken zurück, die in zwei Dokumenten (einem Quelldokument und einem übereinstimmenden Dokument) vorkommen, deren Inhalt semantisch ähnlich ist.  
  
 Auf diese Rowsetfunktion kann in der from-Klausel einer SELECT-Anweisung verwiesen werden. 
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```sql  
SEMANTICSIMILARITYDETAILSTABLE  
    (  
    table,  
    source_column,  
    source_key,  
    matched_column,  
    matched_key  
    )  
```  
  
##  <a name="arguments"></a><a name="Arguments"></a>Argumente  
 **Tabelle**  
 Ist der Name einer Tabelle, für die die Volltext- und die semantische Indizierung aktiviert ist.  
  
 Dieser Name kann einteilig sein oder aus bis zu vier Teilen bestehen, aber ein Remoteservername ist nicht zugelassen.  
  
 **source_column**  
 Name der Spalte in der Quellzeile, deren Inhalt auf Ähnlichkeit überprüft werden soll.  
  
 **source_key**  
 Der eindeutige Schlüssel, der die Zeile des Quelldokuments angibt.  
  
 Dieser Schlüssel wird nach Möglichkeit immer implizit in den Typ des eindeutigen Volltextschlüssels in der Quelltabelle konvertiert. Der Schlüssel kann als Konstante oder Variable angegeben werden. Er kann jedoch kein Ausdruck oder das Ergebnis einer skalaren Unterabfrage sein. Wenn ein ungültiger Schlüssel angegeben wird, werden keine Zeilen zurückgegeben.  
  
 **matched_column**  
 Name der Spalte in der übereinstimmenden Zeile, deren Inhalt auf Ähnlichkeit überprüft werden soll.  
  
 **matched_key**  
 Der eindeutige Schlüssel, der die Zeile des übereinstimmenden Dokuments angibt.  
  
 Dieser Schlüssel wird nach Möglichkeit immer implizit in den Typ des eindeutigen Volltextschlüssels in der Quelltabelle konvertiert. Der Schlüssel kann als Konstante oder Variable angegeben werden. Er kann jedoch kein Ausdruck oder das Ergebnis einer skalaren Unterabfrage sein.  
  
## <a name="table-returned"></a>Zurückgegebene Tabelle  
 In der folgenden Tabelle werden die Schlüsselausdrücke beschrieben, die von dieser Rowset-Funktion zurückgegeben werden.  
  
|Column_name|type|Beschreibung|  
|------------------|----------|-----------------|  
|**Schlüssel Ausdruck**|**NVARCHAR**|Der Schlüsselausdruck, der zur Ähnlichkeit zwischen Quelldokument und übereinstimmendem Dokument beiträgt.|  
|**Endergebnis**|**Wirkliche**|Ein relativer Wert für diesen Schlüsselausdruck in der Beziehung mit allen anderen Schlüsselausdrücken, die in den beiden Dokumenten ähnlich sind.<br /><br /> Der Wert ist eine Dezimalzahl im Bereich [0,0; 1,0], wobei ein höheres Ergebnis eine höhere Gewichtung und 1,0 ein perfektes Ergebnis darstellt.|  
  
## <a name="general-remarks"></a>Allgemeine Hinweise  
 Weitere Informationen finden Sie untersuchen von [ähnlichen und verwandten Dokumenten mit der semantischen Suche](../../relational-databases/search/find-similar-and-related-documents-with-semantic-search.md).  
  
## <a name="metadata"></a>Metadaten  
 Führen Sie eine Abfrage der folgenden dynamischen Verwaltungssichten durch, um Informationen, einschließlich Statusinformationen, zur semantischen Ähnlichkeitsextraktion und Auffüllung zu erhalten:  
  
-   [sys.dm_db_fts_index_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-fts-index-physical-stats-transact-sql.md)  
  
-   [sys.dm_fts_semantic_similarity_population &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-semantic-similarity-population-transact-sql.md)  
  
## <a name="security"></a>Sicherheit  
  
### <a name="permissions"></a>Berechtigungen  
 Erfordert SELECT-Berechtigungen für die Basistabelle, für die der Volltextindex und der semantische Index erstellt wurden.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden die fünf Schlüsselausdrücke mit der größten Ähnlichkeit zwischen den in der **HumanResources.JobCandidate** -Tabelle angegebenen Kandidaten der AdventureWorks2012-Beispieldatenbank abgerufen. Die @CandidateId @MatchedID Variablen und stellen Werte aus der Schlüssel Spalte des voll Text Indexes dar.  
  
```sql  
SELECT TOP(5) KEY_TBL.keyphrase, KEY_TBL.score  
FROMSEMANTICSIMILARITYDETAILSTABLE  
    (  
    HumanResources.JobCandidate,  
    Resume, @CandidateID,  
    Resume, @MatchedID  
    ) AS KEY_TBL  
ORDER BY KEY_TBL.score DESC;  
  
```  
  
  
