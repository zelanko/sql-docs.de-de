---
title: Stretch Database
ms.date: 06/27/2016
ms.service: sql-server-stretch-database
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Stretch Database
ms.assetid: ce6db775-21a5-40bc-95a1-f560376d4ee2
author: rothja
ms.author: jroth
ms.custom: seo-dt-2019
ms.openlocfilehash: cbd815ee666f4f3a2fd144dd08161bbbf57d0fbe
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "75623263"
---
# <a name="stretch-database"></a>Stretch Database
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md-winonly](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md-winonly.md)]


  Stretch Database migriert Ihre inaktiven Daten (Cold Data) transparent und sicher zu Microsoft Azure Cloud.  
  
 Wenn Sie sofort mit Stretch Database beginnen möchten, lesen Sie [Ausführen des Assistenten zum Ausführen einer Datenbank für Stretch](../../sql-server/stretch-database/get-started-by-running-the-enable-database-for-stretch-wizard.md).  
  
## <a name="what-are-the-benefits-of-stretch-database"></a>Was sind die Vorteile von Stretch Database?  
 Stretch Database bietet die folgenden Vorteile:  
  
 **Kostengünstige Verfügbarkeit für kalte Daten**  
 Verlagern Sie aktive und inaktive Transaktionsdaten mit SQL Server Stretch Database dynamisch von SQL Server zu Microsoft Azure. Im Gegensatz zu typischen Speicherlösungen für kalte Daten sind Ihre Daten online und stehen stets für Abfragen zur Verfügung. Sie können längere Zeitziele für die Datenaufbewahrung erreichen, ohne mit großen Tabellen, wie einem Kundenbestellungsverlauf, die Bank zu sprengen. Nutzen Sie die niedrigen Kosten von Azure, statt Geld in die Skalierung von teurem, lokalem Speicher zu investieren. Indem Sie die Preisstufe auswählen und Einstellungen im Azure-Portal konfigurieren, behalten Sie die Kontrolle über Preise und Kosten. Skalieren Sie ganz nach Bedarf hoch oder herunter. Details dazu finden Sie unter [SQL Server Stretch Database – Preise](https://azure.microsoft.com/pricing/details/sql-server-stretch-database/) .  
  
 **Keine Änderungen an Abfragen oder Anwendungen erforderlich**  
 Greifen Sie nahtlos auf Ihre SQL Server-Daten zu, unabhängig davon, ob diese lokal oder per Stretching in der Cloud gespeichert sind.  Sie legen die Richtlinie fest, die bestimmt, wo Daten gespeichert werden, und SQL Server übernimmt die Verschiebung der Daten im Hintergrund. Die gesamte Tabelle ist ständig online und kann jederzeit abgefragt werden. Und für Stretch Database sind keine Änderungen an vorhandenen Abfragen oder Anwendungen erforderlich. Der Speicherort der Daten ist für die Anwendung vollständig transparent.  
  
 **Optimiert die lokale Wartung von Daten**  
 Reduzieren Sie den Aufwand für die lokale Verwaltung und Speicherung Ihrer Daten. Sicherungen für Ihre lokalen Daten werden schneller ausgeführt und innerhalb des Wartungsfensters abgeschlossen. Sicherungen des Cloudanteils Ihrer Daten werden automatisch ausgeführt. Der lokale Speicherbedarf wird erheblich reduziert. Azure-Speicher kann bis zu 80 % günstiger als das Hinzufügen lokaler SSDs sein.  
  
 **Ihre Daten bleiben selbst während der Migration sicher**  
 Bleiben Sie gelassen, wenn Sie für Ihre wichtigsten Anwendungen ein sicheres Stretching in die Cloud durchführen. Das Always Encrypted-Feature von SQL Server bietet Schutz für Ihre Daten während des Verschiebens. Sicherheit auf Zeilenebene (RLS) und andere erweiterte Sicherheitsfunktionen von SQL Server funktionieren auch mit Stretch Database zum Schutz Ihrer Daten.  
  
## <a name="what-does-stretch-database-do"></a>Wie funktioniert Stretch Database?  
 Nachdem Sie Stretch Database für eine SQL Server-Instanz und eine Datenbank aktiviert und mindestens eine Tabelle ausgewählt haben, beginnt Stretch Database im Hintergrund, Ihre kalten Daten zu Azure zu migrieren.  
  
-   Wenn Sie kalte Daten in einer separaten Tabelle speichern, können Sie die gesamte Tabelle migrieren.  
  
-   Wenn Ihre Tabelle sowohl heiße als auch kalte Daten enthält, können Sie eine Filterfunktion zum Auswählen der zu migrierenden Zeilen angeben.

**Sie müssen vorhandene Abfragen und Clientanwendungen nicht ändern.** Sie haben auch weiterhin nahtlosen Zugriff sowohl auf lokale als auch auf Remotedaten, sogar während der Datenmigration. Bei Remoteabfragen tritt eine geringfügige Latenz auf, diese Wartezeit macht sich jedoch nur beim Abfragen der kalten Daten bemerkbar.

**Stretch Database stellt sicher, dass keine Daten verloren gehen**, falls während der Migration ein Failover auftritt. Sie weist außerdem Logik für Wiederholungsversuche zur Behandlung von Verbindungsproblemen auf, die möglicherweise während der Migration auftreten. Eine dynamische Verwaltungsansicht gibt über den Status der Migration Auskunft.

**Sie können die Datenmigration anhalten** , um Probleme auf dem lokalen Server zu behandeln oder um die verfügbare Netzwerkbandbreite zu maximieren.  
  
 ![Übersicht über Stretchdatenbanken](../../sql-server/stretch-database/media/stretch-overview.png "Übersicht über Stretchdatenbanken")  
  
## <a name="is-stretch-database-for-you"></a>Eignet sich Stretch Database für Sie?  
 Wenn die folgenden Aussagen auf Sie zutreffen, kann Ihnen Stretch Database helfen, Ihre Ansprüche umzusetzen und Ihre Probleme zu lösen.  
  
|Wenn Sie ein Entscheidungsträger sind|Wenn Sie ein Datenbankadministrator sind|  
|--------------------------------|---------------------|  
|Ich muss Transaktionsdaten über einen langen Zeitraum aufbewahren.|Die Größe meiner Tabellen ist nicht mehr praktikabel zu verwalten.|  
|Manchmal müssen die kalten Daten abgefragt werden.|Meine Benutzer geben an, dass sie Zugriff auf die kalten Daten wünschen, sie nutzen sie jedoch nur selten.|  
|Ich verfüge über Apps, einschließlich älterer, die ich nicht aktualisieren möchte.|Ich muss weiterhin Speicher kaufen und hinzufügen.|  
|Ich suche nach einer Möglichkeit, Geld für Speicher zu sparen.|Ich kann derart große Tabellen nicht innerhalb des SLAs sichern oder wiederherstellen.|  
  
## <a name="what-kind-of-databases-and-tables-are-candidates-for-stretch-database"></a>Welche Art von Datenbanken und Tabellen eignen sich für Stretch Database?  
 Stretch Database ist für Transaktionsdatenbanken mit großen Mengen an inaktiven Daten gedacht, wobei diese Datenmengen in der Regel in wenigen Tabellen gespeichert werden. Diese Tabellen können mehr als eine Milliarde Zeilen enthalten.  
  
 Wenn Sie das Feature für temporale Tabellen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verwenden, nutzen Sie Stretch Database, um die zugeordnete Verlaufstabelle ganz oder teilweise zum kostengünstigen Speicher in Azure zu migrieren. Weitere Informationen finden Sie unter [Verwalten der Beibehaltung von Verlaufsdaten in temporalen Tabellen mit Systemversionsverwaltung](../../relational-databases/tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md).  
  
 Verwenden Sie Stretch Database Advisor, eine Funktion von SQL Server 2016-Upgraderatgeber, zum Identifizieren von Datenbanken und Tabellen für Stretch Database. Weitere Informationen finden Sie unter [Identifizieren von Datenbanken und Tabellen für Stretch Database durch Ausführen des Ratgebers für Stretch Database](../../sql-server/stretch-database/stretch-database-databases-and-tables-stretch-database-advisor.md). Weitere Informationen zu möglichen Blockierungsproblemen finden Sie unter [Einschränkungen für Stretch Database](../../sql-server/stretch-database/limitations-for-stretch-database.md).  

## <a name="test-drive-stretch-database"></a>Testen Sie Stretch Database  
 **Testen Sie Stretch Database mit der AdventureWorks-Beispieldatenbank.** Laden Sie zum Abrufen der AdventureWorks-Beispieldatenbank zumindest die Datenbankdatei und die Beispiel- und Skriptdatei [here](https://www.microsoft.com/download/details.aspx?id=49502). Nachdem Sie die Beispieldatenbank auf einer Instanz von SQL Server 2016 wiederhergestellt haben, entpacken Sie die Datei „Stretch DB Samples“ aus dem Ordner „Stretch DB “. Führen Sie die Skripts in dieser Datei aus, um den von Ihren Daten verwendeten Speicherplatz vor und nach der Aktivierung von Stretch Database zu überprüfen, den Fortschritt der Datenmigration zu verfolgen und zu bestätigen, dass Sie weiterhin vorhandene Daten abfragen und neue Daten einfügen können, sowohl während als auch nach der Datenmigration.  
  
## <a name="next-step"></a>Nächster Schritt  
 **Identifizieren Sie Datenbanken und Tabellen, die sich für Stretch Database eignen.** Laden Sie den Datenmigrations-Assistent herunter, und führen Sie einer Bewertung durch, um die Datenbanken und Tabellen zu identifizieren, die als Kandidaten für die Stretchdatenbank infrage kommen. Weitere Informationen finden Sie unter [Identifizieren von Datenbanken und Tabellen für Stretch Database durch Ausführen des Ratgebers für Stretch Database](../../sql-server/stretch-database/stretch-database-databases-and-tables-stretch-database-advisor.md).  
  
  
