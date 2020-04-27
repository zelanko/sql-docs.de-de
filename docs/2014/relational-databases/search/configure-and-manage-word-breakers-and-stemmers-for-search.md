---
title: Konfigurieren und Verwalten von Wörtertrennungen und Wortstammerkennungen für die Suche | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- languages [full-text search]
- full-text search [SQL Server], stemmers
- linguistic analysis [full-text search]
- full-text indexes [SQL Server], linguistic analysis
- full-text search [SQL Server], word breakers
- default full-text language option
- stemmers [full-text search]
- conjugating verbs [full-text search]
- word breakers [full-text search]
ms.assetid: d4bdd16b-a2db-4101-a946-583d1c674229
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: eaa80c71dcc58cbd780a664d2466a3bf3cec2a4c
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66011541"
---
# <a name="configure-and-manage-word-breakers-and-stemmers-for-search"></a>Konfigurieren und Verwalten von Wörtertrennungen und Wortstammerkennungen für die Suche
  Wörtertrennung und Wortstammerkennung führen eine linguistische Analyse aller volltextindizierten Daten aus. Zur linguistischen Analyse gehört das Auffinden von Wortgrenzen (Trennfugen) und das Konjugieren von Verben (Wortstammerkennung). Wörtertrennungen und Wortstammerkennungen sind sprachspezifisch, und die Regeln für die linguistische Analyse unterscheiden sich für verschiedene Sprachen. Für eine bestimmte Sprache identifiziert eine *Wörtertrennung* einzelne Wörter, indem die Wortgrenzen basierend auf den lexikalischen Regeln der Sprache ermittelt werden. Jedes Wort (auch bezeichnet als *Token*) wird zur Größenreduzierung in einer komprimierten Darstellung in den Volltextindex eingefügt. Die *Wortstammerkennung* generiert Flexionsformen eines bestimmten Worts basierend auf den jeweiligen Regeln der Sprache. (Zum Beispiel sind „laufend“, „lief“ und „gelaufen“ verschiedene Formen des Worts „laufen“.)  
  
 Wenn Sie sprachspezifische Wörtertrennungen verwenden, können Sie für die jeweilige Sprache genauere Ergebnisbegriffe erzielen. Wenn es eine Wörtertrennung für eine Sprachfamilie gibt, jedoch nicht für die jeweilige Untersprache, wird die Hauptsprache verwendet. Beispielsweise wird Text in kanadischem Französisch mit der Wörtertrennung für Französisch behandelt. Ist für eine Sprache keine Wörtertrennung verfügbar, wird die neutrale Wörtertrennung verwendet. Mit der neutralen Wörtertrennung werden neutrale Zeichen, wie Leerzeichen und Satzzeichen, als Wortgrenzen betrachtet.  
  
##  <a name="registering-word-breakers"></a><a name="register"></a>Registrieren von Wörter Trennungen  
 Die Wörtertrennung muss für eine zu verwendende Sprache jeweils registriert sein. Bei registrierten Wörter Trennungen sind die zugeordneten linguistischen Ressourcen Wort Stamm Erkennung, Füll Wörter (Stoppwörter) und Thesaurusdateien auch für Volltextindizierungs-und Abfrage Vorgänge verfügbar. Wenn Sie eine Liste der Sprachen anzeigen möchten, deren Wörtertrennungen derzeit in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]registriert sind, verwenden Sie die folgende [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung:  
  
 SELECT * FROM sys.fulltext_languages  
  
 Wenn Sie eine Wörtertrennung hinzufügen, entfernen oder ändern, müssen Sie die Liste der Microsoft Windows-Gebietsschemabezeichner (LCID) aktualisieren, die bei Volltextindizierung und -abfrage unterstützt werden. Weitere Informationen finden Sie unter [anzeigen oder Ändern von registrierten filtern und Wörtertrennungen](view-or-change-registered-filters-and-word-breakers.md).  
  
##  <a name="setting-the-default-full-text-language-option"></a><a name="default"></a>Festlegen der Volltext-Standardsprache (Option)  
 Bei einer lokalisierten Version [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird die `default full-text language` Option von Setup auf die Sprache des Servers festgelegt, wenn eine entsprechende Entsprechung vorhanden ist. Bei einer nicht lokalisierten Version [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird Englisch für die Option `default full-text language` verwendet.  
  
 Beim Erstellen oder Ändern eines Volltextindex können Sie für jede volltextindizierte Spalte eine andere Sprache angeben. Ist für eine Spalte keine Sprache angegeben, wird standardmäßig der Wert der Konfigurationsoption `default full-text language` verwendet.  
  
> [!NOTE]  
>  Alle Spalten, die in einer einzelnen Klausel für eine Volltextabfragefunktion aufgelistet sind, müssen dieselbe Sprache verwenden, sofern nicht die LANGUAGE-Option in der Abfrage angegeben ist. Die Sprache der volltextindizierten Spalte, auf die sich die Abfrage bezieht, bestimmt die linguistische Analyse, die mit Argumenten der Volltext-Abfrageprädikate ([CONTAINS](/sql/t-sql/queries/contains-transact-sql) und [FREETEXT](/sql/t-sql/queries/freetext-transact-sql)) und -Funktionen ([CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) und [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql)) ausgeführt wird.  
  
##  <a name="choosing-the-language-for-an-indexed-column"></a><a name="lang"></a>Auswählen der Sprache für eine indizierte Spalte  
 Beim Erstellen eines Volltextindex wird empfohlen, die Sprache für jede indizierte Spalte anzugeben. Wenn für eine Spalte keine Sprache angegeben ist, wird die Standardsprache des Systems verwendet. Die Sprache einer Spalte bestimmt, welche Wörtertrennung und Wortstammerkennung zum Indizieren dieser Spalte verwendet wird. Außerdem wird die Thesaurusdatei dieser Sprache bei Volltextabfragen der Spalte verwendet.  
  
 Bei der Wahl der Spaltensprache für die Erstellung eines Volltextindex sind mehrere Dinge zu bedenken. Diese beziehen sich darauf, wie der Text von der Volltext-Engine in Token zerlegt und anschließend indiziert wird. Weitere Informationen finden Sie unter [Auswählen einer Sprache beim Erstellen eines Volltextindex](choose-a-language-when-creating-a-full-text-index.md).  
  
 **So zeigen Sie die Wörtertrennungssprache einer Spalte an**  
  
-   [Verwalten von Volltextindizes](../indexes/indexes.md)  
  
-   [sys.fulltext_index_columns &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql)  
  
    ```  
    SELECT 'language_id' AS "LCID" FROM sys.fulltext_index_columns;  
    ```  
  
##  <a name="obtaining-information-about-word-breakers"></a><a name="info"></a>Abrufen von Informationen zu Wörter Trennungen  
 **Anzeigen des Tokenisierungsergebnis einer Kombination aus Wörtertrennung, Thesaurus und Stopliste**  
  
-   [sys.dm_fts_parser &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-parser-transact-sql).  
  
 **So geben Sie Informationen über die registrierten Wörtertrennungen zurück**  
  
-   [sp_help_fulltext_system_components &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql)  
  
##  <a name="troubleshooting-word-breaking-time-out-errors"></a><a name="tshoot"></a>Behandlung von Timeout Fehlern bei der Wörter Trennung  
 Timeoutfehler können bei der Wörtertrennung in verschiedenen Situationen auftreten. Weitere Informationen zu diesen Situationen sowie zur Behandlung dieser Fehler finden Sie unter [MSSQLSERVER_30053](../errors-events/mssqlserver-30053-database-engine-error.md).  
  
##  <a name="understanding-the-impact-of-new-word-breakers"></a><a name="impact"></a>Grundlegendes zu den Auswirkungen der neuen Wörter Trennungen  
 Jede Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] enthält in der Regel neue Wörtertrennungen, die über bessere linguistische Regeln als frühere Wörtertrennungen verfügen und außerdem genauer sind. Gegebenenfalls verhalten sich die neuen Wörtertrennungen im Vergleich zu den Wörtertrennungen in importierten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Volltextindizes etwas anders. Dies ist wichtig, wenn ein Volltextkatalog importiert wurde, während eine Datenbank auf die neue Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]aktualisiert wurde. Eine oder mehrere Sprachen, die von den Volltextindizes im Volltextkatalog verwendet werden, sind jetzt ggf. neuen Wörtertrennungen zugeordnet. Weitere Informationen finden Sie unter [Upgrade der Volltextsuche](upgrade-full-text-search.md).  
  
 Eine vollständige Liste aller Wörtertrennungen finden Sie unter [sys.fulltext_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql).  
  
## <a name="see-also"></a>Weitere Informationen  
 [ALTER FULLTEXT Index &#40;Transact-SQL-&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql)   
 [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql)   
 [sp_fulltext_service &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql)   
 [sys. fulltext_languages &#40;Transact-SQL-&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql)   
 [Konfigurieren und Verwalten von Stopp Wörtern und Stopp Listen für die voll Text Suche](configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)   
 [Upgrade der Volltextsuche](upgrade-full-text-search.md)  
  
  
