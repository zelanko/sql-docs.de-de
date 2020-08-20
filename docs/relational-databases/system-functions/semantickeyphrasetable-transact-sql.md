---
description: semantickeyphrasetable (Transact-SQL)
title: semantickeyphraltable (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- semantickeyphrasetable
- semantickeyphrasetable_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- semantickeyphrasetable function
ms.assetid: d33b973a-2724-4d4b-aaf7-67675929c392
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8026760d93132e3a18b51145bc1802e416bc0934
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88464797"
---
# <a name="semantickeyphrasetable-transact-sql"></a>semantickeyphrasetable (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Gibt eine Tabelle mit keiner, einer oder mehreren Zeilen für die Schlüsselausdrücke zurück, die den angegebenen Spalten in der angegebenen Tabelle zugeordnet sind.  
  
 Auf diese Rowsetfunktion kann in der FROM-Klausel einer SELECT-Anweisung so verwiesen werden, als handelte es sich dabei um einen regulären Tabellennamen.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```sql  
SEMANTICKEYPHRASETABLE  
    (  
    table,  
    { column | (column_list) | * }  
     [ , source_key ]  
    )  
```  
  
##  <a name="arguments"></a><a name="Arguments"></a>Argumente  
 **Tabelle**  
 Ist der Name einer Tabelle, für die die Volltext- und die semantische Indizierung aktiviert ist.  
  
 Dieser Name kann einteilig sein oder aus bis zu vier Teilen bestehen, aber ein Remoteservername ist nicht zugelassen.  
  
 **column**  
 Name der indizierten Spalte, für die Ergebnisse zurückgegeben werden sollen. Für die Spalte muss die semantische Indizierung aktiviert sein.  
  
 **column_list**  
 Gibt mehrere durch Trennzeichen getrennte Spalten an, die in Klammern eingeschlossen sind. Für alle Spalten muss die semantische Indizierung aktiviert sein.  
  
 **\***  
 Gibt an, dass alle Spalten eingeschlossen werden, für die die semantische Indizierung aktiviert ist.  
  
 **source_key**  
 Eindeutiger Schlüssel für die Zeile, um Ergebnisse für eine bestimmte Zeile anzufordern.  
  
 Der Schlüssel wird nach Möglichkeit implizit in den Typ des eindeutigen voll Text Schlüssels in der Quell Tabelle konvertiert. Der Schlüssel kann als Konstante oder Variable angegeben werden. Er kann jedoch kein Ausdruck oder das Ergebnis einer skalaren Unterabfrage sein. Wird "source_key" nicht angegeben, werden Ergebnisse für alle Zeilen zurückgegeben.  
  
## <a name="table-returned"></a>Zurückgegebene Tabelle  
 In der folgenden Tabelle werden die Schlüsselausdrücke beschrieben, die von dieser Rowset-Funktion zurückgegeben werden.  
  
|Column_name|type|Beschreibung|  
|------------------|----------|-----------------|  
|**column_id**|**int**|Die ID der Spalte, aus der der aktuelle Schlüsselausdruck extrahiert und indiziert wurde.<br /><br /> Im Abschnitt über die COL_NAME-Funktion und COLUMNPROPERTY-Funktion finden Sie ausführliche Informationen zum Abrufen des Spaltennamens aus "column_id" und umgekehrt.|  
|**document_key**|**\***<br /><br /> Dieser Schlüssel stimmt mit dem Typ des eindeutigen Schlüssels in der Quelltabelle überein.|Eindeutiger Schlüsselwert des Dokuments oder der Zeile, anhand dem der aktuelle Schlüsselausdruck indiziert wurde.|  
|**Schlüssel Ausdruck**|**NVARCHAR**|Der Schlüsselausdruck in der durch "column_id" angegebenen Spalte, der dem durch "document_key" angegebenen Dokument zugeordnet ist.|  
|**Endergebnis**|**Wirkliche**|Ein relativer Wert für diesen Schlüsselausdruck in der Beziehung mit allen anderen Schlüsselausdrücken im gleichen Dokument in der indizierten Spalte.<br /><br /> Der Wert ist eine Dezimalzahl im Bereich [0,0; 1,0], wobei ein höheres Ergebnis eine höhere Gewichtung und 1,0 ein perfektes Ergebnis darstellt.|  
  
## <a name="general-remarks"></a>Allgemeine Hinweise  
 Weitere Informationen finden Sie untersuchen von [Schlüssel Ausdrücken in Dokumenten mit der semantischen Suche](../../relational-databases/search/find-key-phrases-in-documents-with-semantic-search.md).  
  
## <a name="metadata"></a>Metadaten  
 Führen Sie eine Abfrage der folgenden dynamischen Verwaltungssichten durch, um Informationen, einschließlich Statusinformationen, zur semantischen Schlüsselausdruckextraktion und Auffüllung zu erhalten:  
  
-   [sys.dm_db_fts_index_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-fts-index-physical-stats-transact-sql.md)  
  
-   [sys.dm_fts_index_population &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-population-transact-sql.md)  
  
## <a name="security"></a>Sicherheit  
  
### <a name="permissions"></a>Berechtigungen  
 Erfordert SELECT-Berechtigungen für die Basistabelle, für die der Volltextindex und der semantische Index erstellt wurden.  
  
## <a name="examples"></a>Beispiele  
  
###  <a name="example-1-find-the-top-key-phrases-in-a-specific-document"></a><a name="HowToTopPhrases"></a> Beispiel 1: Suchen der wichtigsten Schlüssel Ausdrücke in einem bestimmten Dokument  
 Im folgenden Beispiel werden die obersten 10 Schlüsselausdrücke aus dem von der @DocumentId-Variable in der Spalte "Dokument" der Production.Document-Tabelle der AdventureWorks-Beispieldatenbank angegebenen Dokument abgerufen. Die @DocumentId-Variable stellt einen Wert aus der Schlüsselspalte des Volltextindexes dar. Die **SEMANTICKEYPHRASETABLE** -Funktion ruft diese Ergebnisse effizient mithilfe eines Indexsuchvorgangs anstelle eines Tabellenscans ab. In diesem Beispiel wird davon ausgegangen, dass die Spalte für die Volltextindizierung und die semantische Indizierung konfiguriert wurde.  
  
```sql  
SELECT TOP(10) KEYP_TBL.keyphrase  
FROM SEMANTICKEYPHRASETABLE  
    (  
    Production.Document,  
    Document,  
    @DocumentId  
    ) AS KEYP_TBL  
ORDER BY KEYP_TBL.score DESC;  
  
```  
  
###  <a name="example-2-find-the-top-documents-that-contain-a-specific-key-phrase"></a><a name="HowToTopDocuments"></a> Beispiel 2: Suchen der wichtigsten Dokumente, die einen bestimmten Schlüssel Ausdruck enthalten  
 Im folgenden Beispiel werden die obersten 25 Dokumente mit dem Schlüsselausdruck „Bracket“ in der Spalte „Document“ der Production.Document-Tabelle der AdventureWorks-Beispieldatenbank abgerufen. In diesem Beispiel wird davon ausgegangen, dass die Spalte für die Volltextindizierung und die semantische Indizierung konfiguriert wurde.  
  
```sql  
SELECT TOP (25) DOC_TBL.DocumentID, DOC_TBL.DocumentSummary  
FROM Production.Document AS DOC_TBL  
    INNER JOIN SEMANTICKEYPHRASETABLE  
    (  
    Production.Document,  
    Document  
    ) AS KEYP_TBL  
ON DOC_TBL.DocumentID = KEYP_TBL.document_key  
WHERE KEYP_TBL.keyphrase = 'Bracket'  
ORDER BY KEYP_TBL.Score DESC;  
  
```  
  
  
