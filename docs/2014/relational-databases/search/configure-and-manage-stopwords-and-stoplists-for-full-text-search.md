---
title: Konfigurieren und Verwalten von Stoppwörtern und Stopplisten für Volltextsuche | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- stoplists [full-text search]
- full-text search [SQL Server], stoplists
- full-text search [SQL Server], noise words
- noise words [full-text search]
- full-text search [SQL Server], stopwords
- stopwords [full-text search]
ms.assetid: 43b5ce7b-9f09-4443-8a5b-c3da6eb28bcc
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: fe48b26960db591ce803b1f110e9293fd22d6554
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66011516"
---
# <a name="configure-and-manage-stopwords-and-stoplists-for-full-text-search"></a>Konfigurieren und Verwalten von Stoppwörtern und Stopplisten für Volltextsuche
  Um zu verhindern, dass ein Volltextindex unnötig aufgebläht wird, verfügt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] über einen Mechanismus, der häufig vorkommende, für die Suche nutzlose Zeichenfolgen ignoriert. Diese verworfenen Zeichenfolgen werden als *Stoppwörter*bezeichnet. Während der Indexerstellung lässt die Volltext-Engine Stoppwörter vom Volltextindex weg. Dies bedeutet, dass Volltextabfragen nicht nach Stoppwörtern suchen.  
  
##  <a name="understand"></a>Grundlegendes zu Stopp Wörtern und Stopp Listen  
 Ein Stoppwort kann ein Wort mit einer Bedeutung in einer bestimmten Sprache oder ein *Token* ohne jegliche linguistische Bedeutung sein. Beispielsweise werden in der englischen Sprache Wörter wie "a", "and", "is" und "the" im Volltextindex ausgelassen, da sie erfahrungsgemäß keinen Beitrag zur Suche leisten.  
  
 Obwohl der Volltextindex die Inklusion von Stoppwörtern ignoriert, berücksichtigt er ihre Position. Als Beispiel sei der Ausdruck "Instructions are applicable to these Adventure Works Cycles models" angeführt. In der folgenden Tabelle sind die Positionen der Wörter im Ausdruck angegeben:  
  
|Wort|Position|  
|----------|--------------|  
|Instructions|1|  
|are|2|  
|applicable|3|  
|zu|4|  
|these|5|  
|Adventure|6|  
|Works|7|  
|Cycles|8|  
|Modelle|9|  
  
 Die Stoppwörter "are", "to" und "these" an den Positionen 2, 4 und 5 werden im Volltextindex ausgelassen. Die Positionsinformationen bleiben jedoch erhalten, sodass die Positionen der anderen Wörter im Ausdruck unverändert bleiben.  
  
 Stoppwörter werden über Objekte mit dem Namen "Stoplisten" in Datenbanken verwaltet. Eine *Stoppliste* ist eine Liste mit Stoppwörtern, die, wenn sie einem Volltextindex zugeordnet ist, auf Volltextabfragen für diesen Index angewendet wird.  
  
  
##  <a name="creating"></a>Erstellen einer Stopp Liste  
 Zum Erstellen einer Stopliste stehen die folgenden Möglichkeiten zur Verfügung:  
  
-   Verwenden der vom System bereitgestellten Stopliste in der Datenbank. Der Lieferumfang von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] umfasst eine Systemstopliste, die die am häufigsten verwendeten Stoppwörter für jede unterstützte Sprache enthält, d. h. für jede Sprache, die den jeweiligen Wörtertrennungen standardmäßig zugeordnet ist. Die Systemstoppliste enthält gebräuchliche Stoppwörter für alle unterstützten Sprachen.  Sie können die Systemstoppliste kopieren und Ihre Kopie durch das Hinzufügen und Entfernen von Stoppwörtern anpassen.  
  
     Die Systemstoppliste ist in der [Ressourcendatenbank](../databases/resource-database.md) installiert.  
  
-   Erstellen einer eigenen Stoppliste und Hinzufügen von Stoppwörtern für jede Sprache, die Sie angeben. Sie können bei Bedarf auch Stoppwörter aus der Stoppliste löschen.  
  
-   Verwenden einer vorhandenen benutzerdefinierten Stoppliste aus einer anderen Datenbank in der aktuellen Serverinstanz und anschließendes Hinzufügen und Löschen von Stoppwörtern nach Bedarf.  
  
 **So erstellen Sie eine Stoppliste**  
  
-   [CREATE FULLTEXT STOPLIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-stoplist-transact-sql)  
  
#### <a name="to-create-a-full-text-stoplist-in-management-studio"></a>So erstellen Sie eine Volltextstopliste in Management Studio  
  
1.  Erweitern Sie im Objekt-Explorer den Server.  
  
2.  Erweitern Sie **Datenbanken**, und erweitern Sie dann die Datenbank, in der die Volltext-Stopliste erstellt werden soll.  
  
3.  Erweitern Sie **Speicher**, und klicken Sie dann mit der rechten Maustaste auf **Volltext-Stopplisten**.  
  
4.  Wählen Sie **Neue Volltext-Stoppliste**.  
  
5.  Geben Sie den Namen der Stoppliste an.  
  
6.  Optional können Sie eine andere Person als Besitzer der Stoppliste angeben.  
  
7.  Wählen Sie eine der folgenden Optionen zur Erstellung der Stoppliste:  
  
    -   **Leere Stoppliste erstellen**  
  
    -   **Aus der Systemstoppliste erstellen**  
  
    -   **Aus vorhandener Volltext-Stoppliste erstellen**  
  
     Weitere Informationen finden Sie unter [Neue Volltext-Stoppliste &#40;Seite 'Allgemein'&#41;](../../integration-services/general-page-of-integration-services-designers-options.md).  
  
8.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
 **So löschen Sie eine Stopliste**  
  
-   [DROP FULLTEXT STOPLIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-fulltext-stoplist-transact-sql)  
  
  
##  <a name="queries"></a>Verwenden einer Stopp Liste in voll Text Abfragen  
 Wenn Sie eine Stopliste in Abfragen nutzen möchten, müssen Sie diese einem Volltextindex zuordnen. Sie können einem Volltextindex eine Stoppliste zuordnen, wenn Sie den Index erstellen, oder Sie können den Index später ändern, um eine Stoppliste hinzuzufügen.  
  
 **So erstellen Sie einen Volltextindex und ordnen diesem eine Stoppliste zu**  
  
-   [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql)  
  
 **So ordnen Sie einem vorhandenen Volltextindex eine Stoppliste zu oder heben eine Zuordnung auf**  
  
-   [ALTER FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-index-transact-sql)  
  
 **So unterdrücken Sie eine Fehlermeldung, wenn ein boolescher Vorgang für eine Volltextabfrage aufgrund von Stoppwörtern fehlschlägt**  
  
-   [Füllwörtertransformation (Serverkonfigurationsoption)](../../database-engine/configure-windows/transform-noise-words-server-configuration-option.md)  
  
  
##  <a name="viewing"></a>Anzeigen von Stopp Listen und Stopp Listen-Metadaten  
 **So zeigen Sie alle Stoppwörter einer Stopliste an**  
  
-   [sys.fulltext_stopwords &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-stopwords-transact-sql)  
  
 **So rufen Sie Informationen zu allen Stopplisten in der aktuellen Datenbank ab**  
  
-   [sys.fulltext_stoplists &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-stoplists-transact-sql)  
  
-   [sys.fulltext_stopwords &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-stopwords-transact-sql)  
  
 **So zeigen Sie das Tokenisierungsergebnis einer Kombination aus Wörtertrennung, Thesaurus und Stoplisten an**  
  
-   [sys.dm_fts_parser &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-parser-transact-sql)  
  
  
##  <a name="change"></a>Ändern der Stoppwörter in einer Stopp Liste  
 **So fügen Sie einer Stopliste Stoppwörter hinzu oder löschen diese**  
  
-   [ALTER FULLTEXT STOPLIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-stoplist-transact-sql)  
  
#### <a name="to-change-the-stopwords-in-a-stoplist-in-management-studio"></a>So ändern Sie die Stoppwörter in einer Stopliste in Management Studio  
  
1.  Erweitern Sie im Objekt-Explorer den Server.  
  
2.  Erweitern Sie **Datenbanken**und dann die Datenbank.  
  
3.  Erweitern Sie **Speicher**, und wählen Sie dann **Volltext-Stopplisten**.  
  
4.  Klicken Sie mit der rechten Maustaste auf die Stoppliste, deren Eigenschaften Sie ändern möchten, und wählen Sie **Eigenschaften**aus.  
  
5.  Im Dialogfeld [Volltext-Stopplisten-Eigenschaften](../../database-engine/full-text-stoplist-properties.md) :  
  
    1.  Wählen Sie im Listenfeld **Aktion** eine der folgenden Aktionen aus: **Stoppwort hinzufügen**, **Stoppwort löschen**, **Alle Stoppwörter löschen**oder **Inhalt der Stoppliste löschen**.  
  
    2.  Wenn das Textfeld **Stoppwort** für die ausgewählte Aktion aktiviert ist, geben Sie ein einzelnes Stoppwort ein. Dieses Stoppwort muss eindeutig sein; das heißt, es darf noch nicht in dieser Stoppliste für die Sprache, die Sie auswählen, enthalten sein.  
  
    3.  Wenn das Listenfeld **Volltextsprache** für die ausgewählte Aktion aktiviert ist, wählen Sie eine Sprache aus.  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
  
##  <a name="upgrade"></a>Aktualisieren von Füll Wörtern von SQL Server 2005  
 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] -Füllwörter wurden durch Stoppwörter ersetzt. Wenn eine Datenbank von [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]aktualisiert wird, werden die Füllwortdateien nicht mehr verwendet. Die Füllwortdateien werden jedoch im Ordner "FTDATA\FTNoiseThesaurusBak" gespeichert, und Sie können sie später beim Aktualisieren oder Erstellen der entsprechenden Stoplisten verwenden. Informationen zum Upgrade von Füllwortdateien auf Stoplisten finden Sie unter [Upgrade der Volltextsuche](upgrade-full-text-search.md).  
  
  
  
