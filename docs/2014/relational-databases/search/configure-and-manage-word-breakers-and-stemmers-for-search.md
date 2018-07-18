---
title: Konfigurieren und Verwalten von Wörtertrennungen und Wortstammerkennungen für die Suche | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: search
ms.tgt_pltfrm: ''
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
caps.latest.revision: 88
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 754e9097026fdf1e7a9be5bba6b6115db674a143
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37221110"
---
# <a name="configure-and-manage-word-breakers-and-stemmers-for-search"></a>Konfigurieren und Verwalten von Wörtertrennungen und Wortstammerkennungen für die Suche
  Wörtertrennung und Wortstammerkennung führen eine linguistische Analyse aller volltextindizierten Daten aus. Zur linguistischen Analyse gehört das Auffinden von Wortgrenzen (Trennfugen) und das Konjugieren von Verben (Wortstammerkennung). Wörtertrennungen und Wortstammerkennungen sind sprachspezifisch, und die Regeln für die linguistische Analyse unterscheiden sich für verschiedene Sprachen. Für eine bestimmte Sprache identifiziert eine *Wörtertrennung* einzelne Wörter, indem die Wortgrenzen basierend auf den lexikalischen Regeln der Sprache ermittelt werden. Jedes Wort (auch bezeichnet als *Token*) wird zur Größenreduzierung in einer komprimierten Darstellung in den Volltextindex eingefügt. Die *Wortstammerkennung* generiert Flexionsformen eines bestimmten Worts basierend auf den jeweiligen Regeln der Sprache. (Zum Beispiel sind „laufend“, „lief“ und „gelaufen“ verschiedene Formen des Worts „laufen“.)  
  
 Wenn Sie sprachspezifische Wörtertrennungen verwenden, können Sie für die jeweilige Sprache genauere Ergebnisbegriffe erzielen. Wenn es eine Wörtertrennung für eine Sprachfamilie gibt, jedoch nicht für die jeweilige Untersprache, wird die Hauptsprache verwendet. Beispielsweise wird Text in kanadischem Französisch mit der Wörtertrennung für Französisch behandelt. Ist für eine Sprache keine Wörtertrennung verfügbar, wird die neutrale Wörtertrennung verwendet. Mit der neutralen Wörtertrennung werden neutrale Zeichen, wie Leerzeichen und Satzzeichen, als Wortgrenzen betrachtet.  
  
##  <a name="register"></a> Registrieren der Wörtertrennungen  
 Die Wörtertrennung muss für eine zu verwendende Sprache jeweils registriert sein. Bei registrierten Wörtertrennungen sind die zugeordneten sprachlichen Ressourcen – Wortstammerkennung, Füllwörter (Stoppwörter) und Thesaurusdateien – für Volltextindizierungs- und Volltextabfragevorgänge verfügbar. Wenn Sie eine Liste der Sprachen anzeigen möchten, deren Wörtertrennungen derzeit in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]registriert sind, verwenden Sie die folgende [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung:  
  
 SELECT * FROM sys.fulltext_languages  
  
 Wenn Sie eine Wörtertrennung hinzufügen, entfernen oder ändern, müssen Sie die Liste der Microsoft Windows-Gebietsschemabezeichner (LCID) aktualisieren, die bei Volltextindizierung und -abfrage unterstützt werden. Weitere Informationen finden Sie unter [Anzeigen oder Ändern von registrierten Filtern und Wörtertrennungen](view-or-change-registered-filters-and-word-breakers.md).  
  
##  <a name="default"></a> Festlegen der Option Volltext-Standardsprache  
 Bei einer lokalisierten Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] legt Setup die `default full-text language` option für die Sprache des Servers, wenn eine geeignete Übereinstimmung vorhanden ist. Für eine nicht lokalisierte Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], `default full-text language` Option Englisch ist.  
  
 Beim Erstellen oder Ändern eines Volltextindex können Sie für jede volltextindizierte Spalte eine andere Sprache angeben. Ist für eine Spalte keine Sprache angegeben, wird standardmäßig der Wert der Konfigurationsoption `default full-text language` verwendet.  
  
> [!NOTE]  
>  Alle Spalten, die in einer einzelnen Klausel für eine Volltextabfragefunktion aufgelistet sind, müssen dieselbe Sprache verwenden, sofern nicht die LANGUAGE-Option in der Abfrage angegeben ist. Die Sprache der volltextindizierten Spalte, auf die sich die Abfrage bezieht, bestimmt die linguistische Analyse, die mit Argumenten der Volltext-Abfrageprädikate ([CONTAINS](/sql/t-sql/queries/contains-transact-sql) und [FREETEXT](/sql/t-sql/queries/freetext-transact-sql)) und -Funktionen ([CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) und [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql)) ausgeführt wird.  
  
##  <a name="lang"></a> Auswählen der Sprache für eine indizierte Spalte  
 Beim Erstellen eines Volltextindex wird empfohlen, die Sprache für jede indizierte Spalte anzugeben. Wenn für eine Spalte keine Sprache angegeben ist, wird die Standardsprache des Systems verwendet. Die Sprache einer Spalte bestimmt, welche Wörtertrennung und Wortstammerkennung zum Indizieren dieser Spalte verwendet wird. Außerdem wird die Thesaurusdatei dieser Sprache bei Volltextabfragen der Spalte verwendet.  
  
 Bei der Wahl der Spaltensprache für die Erstellung eines Volltextindex sind mehrere Dinge zu bedenken. Diese beziehen sich darauf, wie der Text von der Volltext-Engine in Token zerlegt und anschließend indiziert wird. Weitere Informationen finden Sie unter [Auswählen einer Sprache beim Erstellen eines Volltextindex](choose-a-language-when-creating-a-full-text-index.md).  
  
 **Um die wörtertrennungssprache einer Spalte anzuzeigen.**  
  
-   [Verwalten von Volltextindizes](../indexes/indexes.md)  
  
-   [sys.fulltext_index_columns &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql)  
  
    ```  
    SELECT 'language_id' AS "LCID" FROM sys.fulltext_index_columns;  
    ```  
  
##  <a name="info"></a> Abrufen von Informationen zu Wörtertrennungen  
 **Anzeigen des tokenisierungsergebnis einer Kombination aus wörtertrennung, Thesaurus und Stoppliste**  
  
-   [sys.dm_fts_parser &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-parser-transact-sql).  
  
 **Zum Zurückgeben von Informationen über die registrierten wörtertrennungen**  
  
-   [sp_help_fulltext_system_components &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql)  
  
##  <a name="tshoot"></a> Problembehandlung von Timeoutfehlern bei der Wörtertrennung  
 Timeoutfehler können bei der Wörtertrennung in verschiedenen Situationen auftreten. Weitere Informationen zu diesen Situationen sowie zur Behandlung dieser Fehler finden Sie unter [MSSQLSERVER_30053](../errors-events/mssqlserver-30053-database-engine-error.md).  
  
##  <a name="impact"></a> Grundlegendes zu den Auswirkungen neuer wörtertrennungen  
 Jede Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] enthält in der Regel neue Wörtertrennungen, die über bessere linguistische Regeln als frühere Wörtertrennungen verfügen und außerdem genauer sind. Gegebenenfalls verhalten sich die neuen Wörtertrennungen im Vergleich zu den Wörtertrennungen in importierten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Volltextindizes etwas anders. Dies ist wichtig, wenn ein Volltextkatalog importiert wurde, während eine Datenbank auf die neue Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]aktualisiert wurde. Eine oder mehrere Sprachen, die von den Volltextindizes im Volltextkatalog verwendet werden, sind jetzt ggf. neuen Wörtertrennungen zugeordnet. Weitere Informationen finden Sie unter [Upgrade der Volltextsuche](upgrade-full-text-search.md).  
  
 Eine vollständige Liste aller Wörtertrennungen finden Sie unter [sys.fulltext_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql).  
  
## <a name="see-also"></a>Siehe auch  
 [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql)   
 [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql)   
 [sp_fulltext_service &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql)   
 [sys.fulltext_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql)   
 [Konfigurieren und Verwalten von Stoppwörtern und Stopplisten für Volltextsuche](configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)   
 [Upgrade der Volltextsuche](upgrade-full-text-search.md)  
  
  
