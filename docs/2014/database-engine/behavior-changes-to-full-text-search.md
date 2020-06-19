---
title: Verhaltensänderungen der voll Text Suche | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text search [SQL Server], breaking changes
- behavior changes [full-text search]
- full-text indexes [SQL Server], breaking changes
ms.assetid: 573444e8-51bc-4f3d-9813-0037d2e13b8f
author: rothja
ms.author: jroth
ms.openlocfilehash: cbe807237651bd8bb81fa1c9f028847654b97889
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84936176"
---
# <a name="behavior-changes-to-full-text-search"></a>Verhaltensänderungen der Volltextsuche
  In diesem Thema werden Verhaltensänderungen der Volltextsuche beschrieben. Ein verändertes Programmverhalten wirkt sich darauf aus, wie Funktionen in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] im Vergleich zu früheren Versionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]funktionieren oder zusammenwirken.  
  
## <a name="behavior-changes-in-full-text-search-in-sssql14"></a>Verändertes Programmverhalten in der Volltextsuche in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]  
 Informationen werden später bereitgestellt.  
  
## <a name="behavior-changes-in-full-text-search-in-sssql11"></a>Verändertes Programmverhalten in der Volltextsuche in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]  
 Von [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] wird eine neue Version der Wörtertrennungen und der Wortstammerkennungen für amerikanisches Englisch (LCID 1033) und britisches Englisch (LCID 2057) installiert. Sie können jedoch zur früheren Version dieser Komponenten wechseln, wenn Sie das vorherige Verhalten beibehalten möchten. Weitere Informationen finden Sie unter [Ändern der für Englisch (USA) und Englisch (Vereinigtes Königreich) verwendeten Wörtertrennung](../relational-databases/search/change-the-word-breaker-used-for-us-english-and-uk-english.md).  
  
### <a name="new-word-breakers-and-stemmers-installed"></a>Neue Wörtertrennungen und Wortstammerkennungen wurden installiert  
 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] aktualisiert alle Wörtertrennungen und Wortstammerkennungen, die von der Volltextsuche und der semantischen Suche verwendet werden. Aus Gründen der Konsistenz zwischen dem Inhalt von Indizes und den Ergebnissen von Abfragen empfiehlt es sich, dass Sie vorhandene Volltextindizes wieder auffüllen.  
  
1.  Es gibt neue Wörtertrennungen für Englisch. Informationen zum Beibehalten des vorherigen Verhaltens finden Sie unter [Change the Word Breaker Used for US English and UK English](../relational-databases/search/change-the-word-breaker-used-for-us-english-and-uk-english.md).  
  
2.  Die Wörtertrennungen von Drittanbietern für Dänisch, Polnisch und Türkisch, die in vorherigen Versionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] enthalten waren, wurden durch [!INCLUDE[msCoName](../includes/msconame-md.md)] -Komponenten ersetzt. Die neuen Komponenten werden standardmäßig aktiviert.  
  
3.  Es gibt neue Wörtertrennungen für Tschechisch und Griechisch. Vorherige Versionen der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Volltextsuche unterstützten diese zwei Sprachen nicht.  
  
### <a name="behavior-changes-of-new-word-breakers-and-stemmers"></a>Verhaltensänderungen der neuen Wörtertrennungen und Wortstammerkennungen  
 Die neuen Komponenten geben möglicherweise andere Ergebnisse zurück als die älteren Komponenten, wenn Sie Volltextindizes auffüllen und abfragen. Die folgenden Tabellen veranschaulichen einige Unterschiede, die in englischen Ergebnissen zu erwarten sind.  
  
 Wenn Sie das vorherige Verhalten der Wörtertrennungen und der Wortstammerkennungen beibehalten müssen, finden Sie weitere Informationen in den folgenden Themen:  
  
-   [Ändern der für Englisch (USA) und Englisch (Großbritannien) verwendeten Wörtertrennung](../relational-databases/search/change-the-word-breaker-used-for-us-english-and-uk-english.md)  
  
-   [Wiederherstellen der von der Suche verwendeten Wörtertrennungen auf die vorherige Version](../relational-databases/search/revert-the-word-breakers-used-by-search-to-the-previous-version.md)  
  
 In einigen Fällen geben die neuen Komponenten *mehr* Ergebnisse zurück:  
  
|**Begriff**|**Ergebnisse aus vorheriger Wörtertrennung und Wortstammerkennung**|**Ergebnisse aus neuer Wörtertrennung und Wortstammerkennung**|  
|--------------|--------------------------------------------------------|---------------------------------------------------|  
|Katze-Hund|cat<br /><br /> Hund|cat<br /><br /> Katze-Hund<br /><br /> Hund|  
|cat@dog.com|cat<br /><br /> de<br /><br /> Hund|cat<br /><br /> cat@dog.com<br /><br /> de<br /><br /> Hund|  
|12/11/2011<br /><br /> *(wenn der Begriff ein Datum ist)*|12/11/2011<br /><br /> dd20111211|11<br /><br /> 12<br /><br /> 12/11/2011<br /><br /> 2011<br /><br /> dd20111211|  
  
 In einigen Fällen geben die neuen Komponenten *ebenso viele* Ergebnisse zurück:  
  
|**Begriff**|**Ergebnisse aus vorheriger Wörtertrennung und Wortstammerkennung**|**Ergebnisse aus neuer Wörtertrennung und Wortstammerkennung**|  
|--------------|--------------------------------------------------------|---------------------------------------------------|  
|100$|100$<br /><br /> nn100$|100$<br /><br /> nn100usd|  
|022|022<br /><br /> nn022|022<br /><br /> nn22|  
|10:49AM<br /><br /> *(wenn der Begriff eine Uhrzeit ist)*|10:49am<br /><br /> tt1049|10:49am<br /><br /> tt24104900|  
  
 In einigen Fällen geben die neuen Komponenten *weniger* Ergebnisse oder Ergebnisse zurück, die möglicherweise nicht von den Anwendungen erwartet werden:  
  
|**Begriff**|**Ergebnisse aus vorheriger Wörtertrennung und Wortstammerkennung**|**Ergebnisse aus neuer Wörtertrennung und Wortstammerkennung**|  
|--------------|--------------------------------------------------------|---------------------------------------------------|  
|jě ˊ ÿqcžl<br /><br /> *(wenn die Begriffe keine gültigen englischen Zeichen sind)*|"jě ˊ ÿqcžl"|je yq zl|  
|Tabelle|Tabelle<br /><br /> table|Tabelle|  
|Katze-|cat<br /><br /> Katze-|cat|  
|v-z *(wobei v und z Füllwörter sind)*|*(keine Ergebnisse)*|v-z|  
|$100 000 USD|$100<br /><br /> 000<br /><br /> nn000<br /><br /> nn100$<br /><br /> usd|$100 000 USD<br /><br /> nn100000usd|  
|schöne USA|schön<br /><br /> Land<br /><br /> USA<br /><br /> USA|schön<br /><br /> Land|  
|Mt. Kent und Mt Challenger|Challenger<br /><br /> Kent<br /><br /> Mt<br /><br /> Mt.|Mt<br /><br /> Kent<br /><br /> Challenger|  
  
## <a name="behavior-changes-in-full-text-search-in-sql-server-2008"></a>Verhaltensänderungen in der Volltextsuche in SQL Server 2008  
 In [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] und späteren Versionen ist die Volltext-Engine als Datenbankdienst in die relationale Datenbank integriert. Sie ist darin als Teil der Infrastruktur der Engine für Serverabfragen und Speicherung vorhanden. Die neue Architektur der Volltextsuche erfüllt folgende Zwecke:  
  
-   Integrierter Speicher und Verwaltung: die Volltextsuche ist jetzt direkt in die inhärenten Speicher-und Verwaltungsfunktionen von integriert [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , und der MSFTESQL-Dienst ist nicht mehr vorhanden.  
  
    -   Volltextindizes werden in den Datenbankdateigruppen gespeichert, anstatt im Dateisystem. Administratorvorgänge in einer Datenbank, z. B. das Erstellen einer Sicherung, wirken sich automatisch auf die entsprechenden Volltextindizes aus.  
  
    -   Ein Volltextkatalog ist jetzt ein virtuelles Objekt, das keiner Dateigruppe angehört. Es ist ein logisches Konzept, das für eine Gruppe von Volltextindizes steht. Aus diesem Grund sind viele Katalogverwaltungsfunktionen als veraltet markiert worden, was bei einigen Funktionen zu größeren Änderungen geführt hat. Weitere Informationen finden Sie unter [Als veraltet markierte Funktionen der Datenbank-Engine in SQL Server 2014](deprecated-database-engine-features-in-sql-server-2016.md) und [Fehlerhafte Änderungen der Volltextsuche](breaking-changes-to-full-text-search.md).  
  
        > [!NOTE]  
        >  [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)][!INCLUDE[tsql](../includes/tsql-md.md)]DDL-Anweisungen, die voll Text Kataloge angeben, funktionieren ordnungsgemäß.  
  
-   Integrierte Abfrage Verarbeitung: der neue Abfrage Prozessor für die Volltextsuche ist Teil des Datenbank-Engine und ist vollständig in den SQL Server-Abfrage Prozessor integriert. Dies bedeutet, dass der Abfrageoptimierer die Prädikate der Volltextabfrage erkennt und automatisch so effizient wie möglich ausführt.  
  
-   Verbesserte Verwaltung und Problembehandlung: in der integrierten Volltextsuche finden Sie Tools, mit denen Sie Such Strukturen analysieren können, wie z. b. den Volltextindex, die Ausgabe einer bestimmten Wörter Trennung, die Stopp Wort Konfiguration usw.  
  
-   Füllwörter und Füllwortdateien sind durch Stoppwörter und Stoplisten ersetzt worden. Eine Stoppliste ist ein Datenbankobjekt, das für Stoppwörter Verwaltbarkeitstasks bereitstellt und die Integrität zwischen verschiedenen Serverinstanzen und -umgebungen verbessert. Weitere Informationen finden sie unter [Konfigurieren und Verwalten von Stoppwörtern und Stopplisten für Volltextsuche](../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md).  
  
-   [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] und höhere Versionen enthalten für viele in [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] vorhandene Sprachen neue Wörtertrennungen. Nur die Wörtertrennungen für Englisch, Koreanisch, Thailändisch und Chinesisch (alle Formen) bleiben gleich. Wenn für andere Sprachen beim Upgrade einer [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]-Datenbank auf [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] oder eine höhere Version ein Volltextkatalog importiert wurde, ist mindestens eine Sprache, die von den Volltextindizes im Volltextkatalog verwendet wird, jetzt ggf. neuen Wörtertrennungen zugeordnet. Diese Wörtertrennungen verhalten sich ggf. etwas anders als die importierten Wörtertrennungen. Weitere Informationen zur Gewährleistung der Konsistenz zwischen Abfragen und dem Inhalt des Volltextindexes finden Sie unter [Upgrade der Volltextsuche](../relational-databases/search/upgrade-full-text-search.md).  
  
-   Es wurde ein neuer FDHOST-Startprogrammdienst (MSSQLFDLauncher) hinzugefügt. Weitere Informationen finden Sie unter [Erste Schritte mit der Volltextsuche](../relational-databases/search/get-started-with-full-text-search.md).  
  
-   Die Volltextindizierung funktioniert mit einer [FileStream](../relational-databases/blob/filestream-sql-server.md) -Spalte genauso wie mit einer- `varbinary(max)` Spalte. Die FILESTREAM-Tabelle muss eine Spalte aufweisen, die die Dateinamenerweiterung für jeden FILESTREAM BLOB enthält. Weitere Informationen finden Sie unter [Abfragen mit Volltextsuche](../relational-databases/search/query-with-full-text-search.md),[Konfigurieren und Verwalten von Filtern für die Suche](../relational-databases/search/configure-and-manage-filters-for-search.md) und [sys.fulltext_document_types &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-document-types-transact-sql).  
  
     Die Volltext-Engine indiziert den Inhalt der FILESTREAM-BLOBs. Dateien wie beispielsweise Images zu indizieren, ist möglicherweise nicht nützlich. Wenn ein FILESTREAM BLOB aktualisiert wird, wird er neu indiziert.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Volltextsuche](../relational-databases/search/full-text-search.md)   
 [Abwärtskompatibilität der voll Text Suche](../../2014/database-engine/full-text-search-backward-compatibility.md)   
 [Upgrade der voll Text Suche](../relational-databases/search/upgrade-full-text-search.md)   
 [Erste Schritte mit der Volltextsuche](../relational-databases/search/get-started-with-full-text-search.md)  
  
  
