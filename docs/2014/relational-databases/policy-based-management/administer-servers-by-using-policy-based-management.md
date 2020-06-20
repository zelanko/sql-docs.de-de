---
title: Verwalten von Servern mit der richtlinienbasierten Verwaltung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- facet See facets
- Declarative Management Framework See Policy-Based Management
- surface area configuration [SQL Server], Policy-Based Management
- Policy-Based Management
- facets [Policy-Based Management]
- Policy-Based Management, administering
- conditions [Policy-Based Management]
- facets [Policy-Based Management], about facets
- PolicyAdministratorRole role
ms.assetid: ef2a7b3b-614b-405d-a04a-2464a019df40
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c0f415ffbc10b93cee2037da78daef3b7ee5aba9
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85069025"
---
# <a name="administer-servers-by-using-policy-based-management"></a>Verwalten von Servern mit der richtlinienbasierten Verwaltung
  Die richtlinienbasierte Verwaltung ist ein System zum Verwalten einer oder mehrerer Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Richtlinienadministratoren die richtlinienbasierte Verwaltung einsetzen, verwenden sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] zum Erstellen von Richtlinien, mit denen Entitäten auf dem Server verwaltet werden, beispielsweise die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz, Datenbanken oder andere [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Objekte.  
  
## <a name="benefits-of-policy-based-management"></a>Vorteile der richtlinienbasierten Verwaltung  
 Die richtlinienbasierte Verwaltung unterstützt Sie bei der Lösung von Problemen, die in den folgenden Szenarien präsentiert werden:  
  
-   Eine Unternehmensrichtlinie verhindert das Aktivieren von Datenbank-E-Mail oder SQL Mail. Eine Richtlinie wird erstellt, um den Serverstatus dieser zwei Funktionen zu überprüfen. Ein Administrator vergleicht den Serverstatus mit der Richtlinie. Wenn der Serverstatus die Bedingungen der Richtlinie nicht einhält, wählt der Administrator den Konfigurationsmodus, und die Richtlinie ändert den Serverstatus so, dass er den Bedingungen der Richtlinie entspricht.  
  
-   Die Datenbank [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] hat eine Benennungskonvention, die vorschreibt, dass alle gespeicherten Prozeduren mit den Buchstaben AW_ beginnen. Eine Richtlinie wird erstellt, mit der diese Richtlinie erzwungen werden soll. Ein Administrator testet diese Richtlinie und erhält eine Liste gespeicherter Prozeduren, die diese Richtlinie nicht einhalten. Wenn zukünftig gespeicherte Prozeduren diese Benennungskonvention nicht einhalten, erzeugt die Erstellungsanweisung für die gespeicherte Prozedur einen Fehler.  
  
> [!NOTE]  
>  Bitte beachten Sie, dass Richtlinien die Funktionsweise einiger [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Funktionen beeinflussen können. Beispielsweise verwenden Change Data Capture und die Transaktionsreplikation beide die systranschemas-Tabelle, die keinen Index hat. Wenn Sie eine Richtlinie aktivieren, die festlegt, dass alle Tabellen einen Index aufweisen müssen, bewirkt die Erzwingung der Einhaltung der Richtlinie das Fehlschlagen dieser Funktionen.  
  
 Richtlinien werden mit [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]erstellt und verwaltet. Der Vorgang umfasst folgende Schritte:  
  
1.  Wählen Sie ein Facet der richtlinienbasierten Verwaltung aus, das die zu konfigurierenden Eigenschaften enthält.  
  
2.  Definieren Sie eine Bedingung, die den Status eines Verwaltungsfacets angibt.  
  
3.  Definieren Sie eine Richtlinie, die die Bedingung, zusätzliche Bedingungen zum Filtern der Zielsätze und den Auswertungsmodus enthält.  
  
4.  Überprüfen Sie, ob eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in Übereinstimmung mit der Richtlinie ist.  
  
 Für Fehler bei Richtlinien wird im Objekt-Explorer eine kritische Zustandswarnung in Form eines roten Symbols neben dem Ziel und den übergeordneten Knoten in der Strukturansicht des Objekt-Explorers angezeigt.  
  
> [!NOTE]  
>  Wenn das System den Objektsatz für eine Richtlinie berechnet, werden die Systemobjekte standardmäßig ausgeschlossen.  Falls der Objektsatz der Richtlinie z. B. auf alle Tabellen verweist, gilt die Richtlinie nicht für Systemtabellen. Wenn Benutzer eine Richtlinie in Verbindung mit Systemobjekten auswerten möchten, können sie dem Objektsatz Systemobjekte explizit hinzufügen. Obwohl alle Richtlinien für den Auswertungsmodus **Zeitplan prüfen** unterstützt werden, werden aus Leistungsgründen jedoch nicht alle Richtlinien mit beliebigen Objektsätzen für den Auswertungsmodus **Änderungen prüfen** unterstützt. Weitere Informationen finden Sie unter[https://blogs.msdn.com/b/sqlpbm/archive/2009/04/13/policy-evaluation-modes.aspx](https://blogs.msdn.com/b/sqlpbm/archive/2009/04/13/policy-evaluation-modes.aspx)  
  
## <a name="policy-based-management-concepts"></a>Konzepte der richtlinienbasierten Verwaltung  
 Die richtlinienbasierte Verwaltung besteht aus drei Komponenten:  
  
-   Richtlinienverwaltung  
  
     Richtlinienadministratoren erstellen Richtlinien.  
  
-   Explizite Verwaltung  
  
     Administratoren wählen ein oder mehrere verwaltete Ziele aus. Für diese Ziele überprüfen sie explizit, ob sie eine bestimmte Richtlinie einhalten oder veranlassen explizit, dass die Ziele eine Richtlinie einhalten.  
  
-   Auswertungsmodi  
  
     Es gibt vier Auswertungsmodi. Drei dieser Modi können automatisiert werden:  
  
    -   **Bedarfs**gesteuert. Dieser Modus wertet die Richtlinie aus, wenn sie vom Benutzer direkt angegeben wird.  
  
    -   **Bei Änderung - Verhindern**. Dieser automatisierte Modus verwendet DDL-Trigger, um Richtlinienverstöße zu verhindern.  
  
        > [!IMPORTANT]  
        >  Wenn die Serverkonfigurationsoption für geschachtelte Trigger deaktiviert ist, funktioniert **Bei Änderung: Verhindern** nicht ordnungsgemäß. Die richtlinienbasierte Verwaltung basiert auf DDL-Triggern, um DDL-Vorgänge zu erkennen und dafür ein Rollback auszuführen, falls diese Vorgänge nicht mit Richtlinien übereinstimmen, die diesen Auswertungsmodus verwenden. Das Entfernen der DDL-Trigger für die richtlinienbasierte Verwaltung oder das Deaktivieren geschachtelter Trigger bewirkt das Fehlschlagen oder ein unerwartetes Ausführungsverhalten dieses Auswertungsmodus.  
  
    -   **Bei Änderung: nur protokollieren**. Dieser automatisierte Modus verwendet die Ereignisbenachrichtigung, um eine Richtlinie auszuwerten, wenn eine relevante Änderung vorgenommen wurde.  
  
    -   **Nach Zeitplan**. Dieser automatisierte Modus verwendet einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agentauftrag, um eine Richtlinie in regelmäßigen Abständen auszuwerten.  
  
     Wenn keine automatisierten Richtlinien aktiviert sind, hat die richtlinienbasierte Verwaltung keine Auswirkungen auf die Systemleistung.  
  
## <a name="policy-based-management-terms"></a>Bedingungen der richtlinienbasierten Verwaltung  
 Verwaltetes Ziel der richtlinienbasierten Verwaltung  
 Entitäten, die durch die richtlinienbasierte Verwaltung verwaltet werden, beispielsweise eine [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]-Instanz, eine Datenbank, eine Tabelle oder ein Index. Alle Ziele in einer Serverinstanz bilden eine Zielhierarchie. Ein Zielsatz ist der Satz der Ziele, der sich aus der Anwendung eines Satzes von Zielfiltern auf die Zielhierarchie ergibt, z. B. alle Tabellen in der Datenbank, die im Besitz des HumanResources-Schemas sind.  
  
 Facet der richtlinienbasierten Verwaltung  
 Ein Satz logischer Eigenschaften, die das Verhalten oder die Eigenschaften bestimmter Typen von verwalteten Zielen modellieren. Die Anzahl und die Merkmale der Eigenschaften sind in das Facet integriert und können nur durch den Ersteller des Facets hinzugefügt oder entfernt werden. Ein Zieltyp kann ein oder mehrere Verwaltungsfacets implementieren, und ein Verwaltungsfacet kann von einem oder mehreren Zieltypen implementiert werden. Bestimmte Eigenschaften eines Facets können nur für eine bestimmte Version gelten.  
  
 Bedingung der richtlinienbasierten Verwaltung  
 Ein boolescher Ausdruck, der einen Satz zulässiger Zustände eines durch die richtlinienbasierte Verwaltung verwalteten Ziels für ein Verwaltungsfacet angibt. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , Sortierungen beizubehalten. Wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sortierungen den Windows-Sortierungen nicht genau entsprechen, testen Sie die Bedingung, um zu ermitteln, wie Konflikte vom Algorithmus aufgelöst werden.  
  
 Richtlinie der richtlinienbasierten Verwaltung  
 Eine Bedingung der richtlinienbasierten Verwaltung und das erwartete Verhalten, wie z. B. Auswertungsmodus, Zielfilter und Zeitplan. Eine Richtlinie kann nur eine einzige Bedingung enthalten. Richtlinien können aktiviert oder deaktiviert sein. Richtlinien werden in der msdb-Datenbank gespeichert.  
  
 Kategorie der richtlinienbasierten Verwaltung  
 Eine benutzerdefinierte Kategorie, die das Verwalten von Richtlinien unterstützt. Benutzer können Richtlinien in verschiedene Richtlinienkategorien klassifizieren. Eine Richtlinie gehört immer nur zu einer Richtlinienkategorie. Richtlinienkategorien gelten für Datenbanken und Server. Auf der Datenbankebene gelten folgende Bedingungen:  
  
-   Datenbankbesitzer können einen Satz von Richtlinienkategorien für eine Datenbank abonnieren.  
  
-   Nur Richtlinien aus Kategorien, die eine Datenbank abonniert hat, können diese Datenbank steuern.  
  
-   Alle Datenbanken abonnieren implizit die Standardrichtlinienkategorie.  
  
 Auf Serverebene können Richtlinienkategorien auf alle Datenbanken angewendet werden.  
  
 Effektive Richtlinie  
 Die effektiven Richtlinien für ein Ziel sind die Richtlinien, die dieses Ziel steuern. Eine Richtlinie ist nur dann für ein Ziel effektiv, wenn alle folgenden Bedingungen erfüllt werden:  
  
-   Die Richtlinie ist aktiviert.  
  
-   Das Ziel gehört zum Zielsatz der Richtlinie.  
  
-   Für das Ziel oder einen der Vorgänger des Ziels ist die Richtliniengruppe abonniert, die diese Richtlinie enthält.  
  
## <a name="policy-based-management-tasks"></a>Tasks der richtlinienbasierten Verwaltung  
 Die richtlinienbasierte Verwaltung ist ein richtlinienbasiertes System zum Verwalten einer oder mehrerer Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Verwenden Sie die richtlinienbasierte Verwaltung, um Bedingungen zu erstellen, die Bedingungsausdrücke enthalten. Erstellen Sie dann Richtlinien, die die Bedingungen für Datenbankzielobjekte übernehmen.  
  
|Taskbeschreibung|Thema|  
|----------------------|-----------|  
|Beschreibt die Speicherung von Richtlinien der richtlinienbasierten Verwaltung.|Speicher der richtlinienbasierten Verwaltung|  
|Beschreibt die Konfiguration von Warnungen zur Benachrichtigung von Richtlinienadministratoren bei Richtlinienfehlern.|[Konfigurieren von Warnungen zur Benachrichtigung von Richtlinienadministratoren bei Richtlinienfehlern](configure-alerts-to-notify-policy-administrators-of-policy-failures.md)|  
|Beschreibt das Erstellen, Anzeigen, Ändern und Löschen einer richtlinienbasierten Verwaltungsbedingung.|[Erstellen einer neuen Bedingung der richtlinienbasierten Verwaltung](create-a-new-policy-based-management-condition.md)<br /><br /> [Löschen einer Bedingung der richtlinienbasierten Verwaltung](delete-a-policy-based-management-condition.md)<br /><br /> [Anzeigen oder Ändern der Eigenschaften einer Bedingung der richtlinienbasierten Verwaltung](view-or-modify-the-properties-of-a-policy-based-management-condition.md)|  
|Beschreibt das Erstellen, Anzeigen, Ändern und Löschen einer richtlinienbasierten Verwaltungsrichtlinie.|[Erstellen einer Richtlinie der richtlinienbasierten Verwaltung](create-a-policy-based-management-policy.md)<br /><br /> [Löschen einer Richtlinie der richtlinienbasierten Verwaltung](delete-a-policy-based-management-policy.md)<br /><br /> [Anzeigen oder Ändern der Eigenschaften einer Richtlinie der richtlinienbasierten Verwaltung](view-or-modify-the-properties-of-a-policy-based-management-policy.md)|  
|Beschreibt das Exportieren und Importieren einer richtlinienbasierten Verwaltungsrichtlinie.|[Exportieren einer Richtlinie der richtlinienbasierten Verwaltung](export-a-policy-based-management-policy.md)<br /><br /> [Importieren einer Richtlinie der richtlinienbasierten Verwaltung](import-a-policy-based-management-policy.md)|  
|Beschreibt die Überprüfung der Einhaltung einer Richtlinie durch eine Serverinstanz, eine Datenbank, ein Serverobjekt oder ein Datenbankobjekt.|[Auswerten einer Richtlinie der richtlinienbasierten Verwaltung von einem Objekt aus](evaluate-a-policy-based-management-policy-from-an-object.md)<br /><br /> [Auswerten einer Richtlinie der richtlinienbasierten Verwaltung von der Richtlinie aus](evaluate-a-policy-based-management-policy-from-that-policy.md)<br /><br /> [Auswerten einer Richtlinie der richtlinienbasierten Verwaltung nach einem Zeitplan](evaluate-a-policy-based-management-policy-on-a-schedule.md)|  
|Beschreibt das Anzeigen eines richtlinienbasierten Verwaltungsfacet-Status und Kopieren in eine Datei.|[Arbeiten mit Facets der richtlinienbasierten Verwaltung](working-with-policy-based-management-facets.md)|  
|Stellt eine Reihe von Richtliniendateien bereit, die Sie als Richtlinien für Best Practices importieren können, und beschreibt die Auswertung der Richtlinien für einen Zielsatz, der Instanzen, Instanzobjekte, Datenbanken oder Datenbankobjekte enthält.|[Überwachen und Erzwingen von Best Practices mit der richtlinienbasierten Verwaltung](monitor-and-enforce-best-practices-by-using-policy-based-management.md)|  
|Enthält die F1-Hilfethemen zum Knoten **Richtlinienverwaltung** des Objekt-Explorers von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].|[Richtlinienverwaltungsknoten &#40;Objekt-Explorer&#41;](../../ssms/object/object-explorer.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sichten der richtlinienbasierten Verwaltung &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/policy-based-management-views-transact-sql)  
  
  
