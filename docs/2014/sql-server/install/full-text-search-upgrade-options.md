---
title: Upgradeoptionen für die Volltextsuche | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Full-Text Search
- Upgrade options, Full-Text Search
ms.assetid: 16c9376b-5fbb-4495-a429-06a2493849c9
caps.latest.revision: 18
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: af3bf4f26b94e6fc8ce18c07ed052ef53087f68c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36162401"
---
# <a name="full-text-search-upgrade-options"></a>Upgradeoptionen für die Volltextsuche
  Verwenden Sie im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Installations-Assistenten die Seite mit den Upgradeoptionen für die Volltextsuche, um die Upgradeoption für die Volltextsuche auszuwählen, die Sie für die zu aktualisierenden Datenbanken verwenden möchten.  
  
 In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] befindet sich jeder Volltextindex in einem Volltextkatalog, der einer Dateigruppe angehört, über einen physischen Pfad verfügt und als Datenbankdatei behandelt wird. Jetzt ist ein Volltextkatalog ein logisches Konzept – ein virtuelles Objekt –, das eine Gruppe von Volltextindizes bezeichnet. Deshalb wird ein neuer Volltextkatalog nicht als Datenbankdatei mit einem physischen Pfad behandelt. Wenn jedoch ein Volltextkatalog aktualisiert wird, der Datendateien enthält, wird auf demselben Datenträger jeweils eine neue Dateigruppe erstellt. Auf diese Weise wird nach dem Upgrade das alte Datenträger-E/A-Verhalten beibehalten. Jeder Volltextindex aus diesem Katalog wird in die neue Dateigruppe eingefügt, wenn der Stammpfad vorhanden ist. Falls der alte Volltextkatalogpfad ungültig ist, wird beim Upgrade der Volltextindex in derselben Dateigruppe als Basistabelle &ndash; bzw. bei einer partitionierten Tabelle in der primären Dateigruppe &ndash; beibehalten.  
  
## <a name="options"></a>Tastatur  
 Wenn Sie auf [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]aktualisieren, wählen Sie eine der folgenden Upgradeoptionen für die Volltextsuche aus.  
  
 **Importieren**  
 Volltextkataloge werden importiert. Normalerweise ist der Import bedeutend schneller als eine Neuerstellung. Wenn Sie zum Beispiel nur eine CPU verwenden, läuft ein Import etwa zehnmal schneller ab als eine Neuerstellung. Ein aus [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] importierter Volltextkatalog verwendet jedoch nicht die neuen und erweiterten Wörtertrennungen. Aus diesem Grund sollten Sie zu einem späteren Zeitpunkt eine Neuerstellung der Volltextkataloge durchführen.  
  
> [!NOTE]  
>  Sie können die Neuerstellung im Multithreadmodus ausführen. Wenn mehr als 10 CPUs verfügbar sind, ist die Neuerstellung ggf. schneller als der Import, falls dabei alle CPUs genutzt werden können.  
  
 Wenn ein Volltextkatalog nicht verfügbar ist, werden die zugehörigen Volltextindizes neu erstellt. Diese Option ist nur für [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] -Datenbanken verfügbar.  
  
 Informationen zu den Auswirkungen eines Imports von Volltextindizes finden Sie unter "Überlegungen beim Auswählen einer Volltextupgrade-Option" weiter unten in diesem Thema.  
  
 **Neu erstellen**  
 Volltextkataloge werden mithilfe der neuen und verbesserten Worttrennmodule neu erstellt. Das Neuerstellen von Indizes kann sehr lange dauern, und nach dem Upgrade ist ggf. eine beträchtliche Menge an CPU-Leistung und Arbeitsspeicherkapazität erforderlich.  
  
 **Zurücksetzen**  
 Volltextkataloge werden zurückgesetzt. Beim Aktualisieren von [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]werden Volltextkatalogdateien entfernt. Die Metadaten für die Volltextkataloge und die Volltextindizes bleiben jedoch erhalten. Nach der Upgrade wird die Änderungsnachverfolgung für alle Volltextindizes deaktiviert, und Durchforstungen werden nicht automatisch gestartet. Der Katalog bleibt leer, bis Sie ihn nach Beendigung des Upgrades manuell vollständig auffüllen.  
  
 Bei all diesen Upgradeoptionen ist sichergestellt, dass aktualisierte Datenbanken von der optimierten Volltextleistung profitieren.  
  
## <a name="considerations-for-choosing-a-full-text-upgrade-option"></a>Überlegungen beim Auswählen einer Volltextupgrade-Option  
 Beachten Sie beim Auswählen der Aktualisierungsoption Folgendes:  
  
-   Wie werden Wörtertrennungen verwendet?  
  
     Der Volltextsuchdienst in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] enthält neue Wörtertrennungen und Wortstammerkennungen. Aus diesem Grund können sich die Ergebnisse von Volltextabfragen für ein bestimmtes Textmuster oder Szenario im Vergleich zu [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] unterscheiden. Es ist also wichtig, beim Auswählen einer geeigneten Upgradeoption auf die verwendete Wörtertrennung zu achten:  
  
    -   Wenn die Wörtertrennung der verwendeten Volltextsprache sich nicht geändert hat oder wenn die Rückrufgenauigkeit nicht entscheidend ist, ist das Importieren eine geeignete Maßnahme. Falls später Rückrufprobleme auftreten, können Sie ein Upgrade auf die neuen Wörtertrennungen durchführen, indem Sie die Volltextkataloge einfach neu erstellen.  
  
    -   Wenn die Rückrufgenauigkeit wichtig ist und Sie eines der Worttrennmodule verwenden, die nach [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]hinzugefügt wurden, sollten Sie eine Neuerstellung durchführen.  
  
-   Wurden Volltextindizes basierend auf ganzzahligen Volltextschlüsselspalten erstellt?  
  
     Bei der Neuerstellung werden interne Optimierungen durchgeführt, die die Abfrageleistung des aktualisierten Volltextindex in einigen Fällen verbessern. Mit der Neuerstellung erzielen Sie nach dem Upgrade besonders dann eine optimale Leistung der Volltextabfragen, wenn Sie Volltextkataloge mit Volltextindizes verwenden, bei denen die Volltextschlüsselspalte der Basistabelle ein integer-Datentyp ist. In diesem Fall ist es sehr zu empfehlen, die Option **Neu erstellen** zu verwenden.  
  
    > [!NOTE]  
    >  Für die Volltextindizes in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]ist es ratsam, dass es sich bei der Spalte, die als Volltextschlüssel dient, um einen ganzzahligen Datentyp handelt. Weitere Informationen finden Sie unter [Verbessern der Leistung von Volltextindizes](../../relational-databases/indexes/indexes.md).  
  
-   Worauf liegt beim Herstellen der Onlineverfügbarkeit der Serverinstanz die Priorität?  
  
     Das Importieren bzw. das Neuerstellen während eines Upgrades belegt viele CPU-Ressourcen. Dies führt zu Verzögerungen beim Aktualisieren und Herstellen der Onlineverfügbarkeit des Rests der Serverinstanz. Wenn die schnellstmögliche Onlineverfügbarkeit der Serverinstanz wichtig und das manuelle Auffüllen nach dem Upgrade akzeptabel ist, eignet sich die Option **Zurücksetzen** .  
  
## <a name="additional-resources"></a>Zusätzliche Ressourcen  
  