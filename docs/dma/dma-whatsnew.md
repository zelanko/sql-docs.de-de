---
title: Neues in Datenmigrations-Assistent (SQL Server) | Microsoft-Dokumentation
description: Erfahren Sie mehr über die neuen Features in jeder Version von Datenmigrations-Assistent für SQL Server und Azure SQL-Datenbank.
ms.custom: ''
ms.date: 11/05/2019
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.technology: dma
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, new features
ms.assetid: ''
author: rajeshsetlem
ms.author: rajpo
ms.openlocfilehash: 19753cddaba236d0de75e492962bd6c8ad2675e2
ms.sourcegitcommit: 822d4b3cfa53269535500a3db5877a82b5076728
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2020
ms.locfileid: "87988506"
---
# <a name="whats-new-in-data-migration-assistant"></a>Neuerungen im Datenmigrations-Assistenten

In diesem Artikel werden die Ergänzungen der einzelnen Releases von Datenmigrations-Assistent aufgeführt.

## <a name="data-migration-assistant-v-52"></a>Datenmigrations-Assistent v 5,2
Die Version 5.2 des Datenmigrations-Assistent bietet Unterstützung für:
- Hochladen von Bewertungen in Azure migrate mit Unterstützung für Azure Government und nationale Clouds (souveränes Angebot).  Mit diesem Feature können Sie die Bereitschaft von SQL Server Data Estate-Migration zu Azure SQL bewerten.
- Befehlszeilen Unterstützung für das Hochladen von Bewertungen in Azure migrate mit Unterstützung für Azure Government und nationale Clouds.  Nun können Sie das Hochladen der Bewertungen in das Azure-Migrationsprojekt vollständig automatisieren, um einen konsolidierten Azure SQL-Bereitschafts Bericht zu erhalten. 

## <a name="data-migration-assistant-v-50"></a>Datenmigrations-Assistent v 5,0

Das Release v 5.0 des Datenmigrations-Assistent bietet Unterstützung für:

- SQL Server 2019 für Windows und SQL Server 2019 für Linux als Ziele für Bewertung und Upgrade.
- Speichern und Laden von Bewertungen, einschließlich der Unterstützung für das Speichern und Laden von Bewertungen, die in früheren Versionen der Datenmigrations-Assistent erstellt wurden.
- Bewerten von SQL Server Integration Services (SSIS)-Projekten, die in ssisdb und SSIS-Paketen gehostet werden, die im Paket Speicher gehostet werden Daten Bank Migration Assistant erkennt nicht unterstützte, teilweise unterstützte oder veraltete Features und Kompatibilitätsprobleme, die in Quellpaketen verwendet werden, und bietet Empfehlungen, die Ihnen helfen, diese Probleme zu beheben.
- Bewerten von SQL-Abfragen aus externer Anwendung, z. b. SQL-Abfragen in c#-Quellcode. Benutzer können mit dem Data Access Migration Toolkit einen vollständigen JSON-Bericht für die SQL-Abfragen generieren, die in c#-Quellcode verwendet werden, und dann den Bericht in Datenmigrations-Assistent hochladen.

Außerdem bietet diese Version von Datenmigrations-Assistent zusätzliche Verbesserungen und Fehlerbehebungen, und das Tool wurde auf .NET 4.7.2 aktualisiert.

## <a name="data-migration-assistant-v45"></a>Datenmigrations-Assistent v 4.5

Die Version 4.5 von Datenmigrations-Assistent bietet Unterstützung für die Bewertung der Migration von SQL Server Integration Services SSIS-Paketen (SSIS), die im Dateisystem gehostet werden, zu Azure SQL-Datenbank oder SQL verwaltete Instanz.

## <a name="data-migration-assistant-v44"></a>Datenmigrations-Assistent v 4.4

Die Version 4.4 von Datenmigrations-Assistent bietet Unterstützung für das Hochladen von Bewertungen in Azure migrate.

## <a name="data-migration-assistant-v43"></a>Datenmigrations-Assistent v 4.3

Die Version 4.3 von Datenmigrations-Assistent bietet Unterstützung für:

- SKU-Empfehlungen für Azure SQL-verwaltete Instanz basierend auf der workloadbewertung.
- RDS-SQL Server als Quelle für Bewertungen.
- Agentauftragsbewertungen für Azure SQL-verwaltete Instanz als Ziel.
- Die Möglichkeit, bestimmte Bewertungsregeln zu ignorieren. die Liste der Fehlercodes, die in der in DMA konfigurierten Eigenschaft "ignoreerrorcodes" angegeben sind, wird in den DMA-Bewertungsergebnissen nicht angezeigt.
- Bewertung von T-SQL-Abfragen in Auftrags Aktivitäts Schritten und Bereitstellen entsprechender Empfehlungen
- Bewertungen für erweiterte Ereignisse (Public Preview).

Außerdem bietet diese Version von DMA eine verbesserte Leistung für die Verarbeitung einer großen Anzahl von Schema Objekten in-Datenbanken sowie Fehlerbehebungen im Zusammenhang mit:

- In einigen Fällen mit nativer Kompilierung kompilierte Prozeduren.
- Komplizierte Datenbankschemas.

## <a name="data-migration-assistant-v42"></a>Datenmigrations-Assistent v 4.2

Das v 4.2-Release von Datenmigrations-Assistent bietet Befehlszeilen Unterstützung für die Ziel Bereitschafts Bewertung für eine oder mehrere Server Instanzen bei der Migration von lokalen SQL Server zu einem SQL-verwaltete Instanz. Kunden können nun mithilfe der Datenmigrations-Assistent Befehlszeile Metadaten zu Ihrem Datenbankschema sammeln, die Blockierer erkennen und sich über teilweise unterstützte oder nicht unterstützte Features informieren, die sich auf die Migration zu einer SQL-verwaltete Instanz auswirken. Die Ergebnisse können dann mithilfe der bereitgestellten Power BI Vorlage gerendert werden.

## <a name="data-migration-assistant-v41"></a>Datenmigrations-Assistent v 4.1

In der Version 4.1 von Datenmigrations-Assistent wird die Unterstützung für die umfassende Bewertung lokaler SQL Server Datenbanken eingeführt, die zu SQL verwaltete Instanz migriert werden.

Mit dem Bewertungs Workflow können Sie folgende Probleme erkennen, die sich auf die Migration zu SQL verwaltete Instanz auswirken können:

- **Nicht unterstützte oder teilweise unterstützte Funktionen**. Datenmigrations-Assistent bewertet Ihre Quelle SQL Server Datenbank für verwendete Features, die auf dem SQL-Ziel verwaltete Instanz teilweise unterstützt oder nicht unterstützt werden. Das Tool bietet dann eine umfassende Reihe von Empfehlungen, alternative Ansätze in Azure und Entschärfung von Schritten, damit Kunden diese Informationen berücksichtigen können, wenn Sie Ihre Migrationsprojekte planen.

- **Kompatibilitätsprobleme**. Datenmigrations-Assistent identifiziert auch Kompatibilitätsprobleme im Zusammenhang mit den folgenden Bereichen:

  - Wichtige Änderungen: die spezifischen Schema Objekte, die die Funktion zur Migration zur Zieldatenbank unterbrechen können.  Es wird empfohlen, diese Schema Objekte nach der Datenbankmigration zu beheben.
  - Verhaltensänderungen: die gemeldeten Schema Objekte funktionieren möglicherweise weiterhin, Sie weisen jedoch möglicherweise ein anderes Verhalten auf, z. b. Leistungseinbußen.
  - Informationsprobleme: diese Objekte haben keine Auswirkungen auf die Migration, sind aber möglicherweise nicht mehr im Funktions SQL Server Releases veraltet.

Verwenden Sie nach Abschluss der Bewertung unsere [Azure Database Migration Service](https://azure.microsoft.com/services/database-migration/) (DMS), um die Migration Ihrer SQL Server-Datenbanken zu SQL verwaltete Instanz durchzuführen.  DMS unterstützt die Datenbankmigrationen [Offline](https://docs.microsoft.com/azure/dms/tutorial-sql-server-to-managed-instance) (einmalig) und [Online](https://docs.microsoft.com/azure/dms/tutorial-sql-server-managed-instance-online) (Minimale Ausfallzeit) in SQL verwaltete Instanz.

## <a name="data-migration-assistant-v40"></a>Datenmigrations-Assistent v 4.0

Mit der Version 4.0 von Datenmigrations-Assistent wird das Azure SQL-Datenbank-SKU-Empfehlungs Feature eingeführt, mit dem Benutzer die empfohlene Azure SQL-Datenbank-SKU auf der Grundlage von Leistungsindikatoren identifizieren können, die von den Computern gesammelt werden, auf denen die Datenbanken gehostet werden. Diese Funktion bietet Empfehlungen im Zusammenhang mit Tarif, computeebene und maximaler Datengröße sowie geschätzten Kosten pro Monat. Außerdem bietet es die Möglichkeit, alle Datenbanken in Azure in einem Massen Vorgang bereitzustellen.

> [!NOTE]
> Diese Funktion ist zurzeit nur über die Befehlszeilenschnittstelle (CLI) verfügbar.

Weitere Details finden Sie im Artikel [Ermitteln der richtigen Azure SQL-Datenbank-SKU für Ihre lokale Datenbank](dma-sku-recommend-sql-db.md).

## <a name="data-migration-assistant-v36"></a>Datenmigrations-Assistent v 3.6

In der Version 3.6 von Datenmigrations-Assistent wird "Automatische Korrektur" für die Schema Objekte eingeführt, die von den gängigsten Migrations blockatoren betroffen sind.

Diese Version bietet automatische Korrektur für die folgenden Probleme bei der Migration und Behavior Change:

- Die Schema Objekte, die die nicht qualifizierte Join-Syntax verwenden.
- Die Schema Objekte, die die Legacy-RaiseError-Anweisung verwenden.
- SQL-Anweisungen, die Order by Integer-Literale verwenden.

Datenmigrations-Assistent führt für die Objekte, die von den aufgelisteten Problemen betroffen sind, eine automatische Schema Konvertierung durch und fordert den Benutzer zur Bestätigung auf, bevor die Schema Konvertierung fortgesetzt wird. Benutzer können die vorgeschlagenen Codeänderungen überprüfen und dann alle Konvertierungen für ein bestimmtes Datenbankobjekt akzeptieren oder ablehnen.

Datenmigrations-Assistent verwendet die Technologie von Microsoft Program Synthesis (Prosa), um die Code Korrekturen vorzuschlagen. Erfahren Sie mehr über [Prosa](https://microsoft.github.io/prose/).

## <a name="data-migration-assistant-v35"></a>Datenmigrations-Assistent v 3.5

Die Version v 3.5 von Datenmigrations-Assistent umfasst die folgenden Ergänzungen:

- Bedeutende Leistungsverbesserungen bei der Migration zu Azure SQL-Datenbank (Benchmarktests deuten darauf hin, dass der Prozess viermal schneller ist als bei früheren Versionen von Datenmigrations-Assistent).
- Der Speicherbedarf wird weiter optimiert, um die Stabilität des Migrations Workflows zu verbessern.
- Die Möglichkeit, Bewertungen während des Schemas und der Datenmigrationen zu überspringen (wenn Sie die Bewertung bereits durchgeführt und vor der Migration alle unter brechnden Schema Objekte adressiert haben).
- Eine Korrektur, um Probleme mit dem Tool abzubrechen, wenn ein ungültiger Netzwerkfreigabe Pfad für Sicherungsdateien bereitgestellt wird, wenn ein Upgrade einer älteren Version von SQL Server lokal auf eine höhere Version SQL Server oder auf Azure-VMS ausgeführt wird.

## <a name="data-migration-assistant-v34"></a>Datenmigrations-Assistent v 3.4

Die Version 3.4 von Datenmigrations-Assistent umfasst die folgenden Ergänzungen:

- Unterstützung für SQL Server 2017 als Quelle für Migrationen zu Azure SQL-Datenbank.
- Verbesserungen an Stabilität, Leistung und Bewertungsregel Richtigkeit.

## <a name="data-migration-assistant-v33"></a>Datenmigrations-Assistent v 3.3

Die Version 3.3 von Datenmigrations-Assistent ermöglicht die Migration einer lokalen SQL Server Instanz zu der neuen Version von SQL Server 2017 unter Windows und Linux. Während der gesamte Migrations Workflow für Windows und Linux identisch ist, erfordert der Umstieg auf SQL Server 2017 für Linux einige zusätzliche Überlegungen.

### <a name="specifying-the-back-up-path"></a>Angeben des Sicherungs Pfads

Linux und Windows verwenden unterschiedliche Pfad Formate. Daher erfordert die Migration zu SQL Server 2017 unter Linux, dass der Benutzer sowohl die Windows-als auch die Linux-Version des Pfads zum Speicherort der physischen Datei bereitstellt. Abhängig vom Speicherort der physischen Datei können Sie beide Versionen des Pfads auf unterschiedliche Weise angeben.
Wenn sich die physische Sicherungsdatei auf einem Computer befindet, auf dem Folgendes ausgeführt wird:

- Linux: Verwenden Sie eine "Samba"-Freigabe, um die Datei für andere Computer im Netzwerk freizugeben.
- Windows, verwenden Sie den Befehl "mnt", um die Freigabe auf dem Computer mit Linux zu installieren.

> [!NOTE]
> Details zur Verwendung einer Samba-Freigabe oder des mnt-Befehls sprengen den Rahmen dieses Artikels.

### <a name="migrating-windows-logins"></a>Migrieren von Windows-Anmeldungen

Während die Migration von Active Directory-Anmeldungen (AD) offiziell von SQL Server 2017 unter Linux unterstützt wird, ist eine zusätzliche Konfiguration erforderlich, damit Sie erfolgreich funktioniert. Ausführliche Informationen zum Einrichten von Active Directory Anmeldungen auf SQL Server 2017 unter Linux finden Sie im Artikel [Active Directory Authentifizierung mit SQL Server für Linux](https://docs.microsoft.com/sql/linux/sql-server-linux-active-directory-authentication) . Nachdem Sie die erforderliche Konfiguration durchgeführt haben, ist das Setup fertiggestellt, und Sie können Active Directory Anmeldungen wie gewohnt migrieren. Die Standard mäßige SQL-Authentifizierung funktioniert erwartungsgemäß ohne weitere Einrichtung.

## <a name="data-migration-assistant-v32"></a>Datenmigrations-Assistent v 3.2

Die v 3.2-Version von Datenmigrations-Assistent umfasst die folgenden Ergänzungen:

- Die Schema-und Datenmigration werden von lokalen SQL Server Datenbanken mithilfe eines neuen Migrations Workflows in Azure SQL-Datenbank aktiviert.
- Bei der Migration von Schemas zu Azure SQL-Datenbank stellt DMA Ihre Quelldaten Bank Objekte bereit, stellt Anleitungen dazu bereit, wie mögliche Kompatibilitätsprobleme behoben werden können, und stellt das Schema dann in Azure bereit.

## <a name="data-migration-assistant-v31"></a>Datenmigrations-Assistent v 3.1

Die Version 3.1 von Datenmigrations-Assistent umfasst die folgenden Ergänzungen:

- Verbesserte Bewertungs Empfehlungen für Azure SQL-Datenbank im Hinblick auf Daten Bank Sortierungen, die Verwendung nicht unterstützter gespeicherter System Prozeduren und CLR-Objekte.
- Bewertungs Leit Faden für die Kompatibilitäts Grade 130, 120, 110 und 100 beim Migrieren zu Azure SQL-Datenbank.

## <a name="data-migration-assistant-v30"></a>Datenmigrations-Assistent v 3.0

Die v 3.0-Version von Datenmigrations-Assistent erweitert die Azure SQL-Daten Bank Bewertung, um umfassende Empfehlungen zur Behebung von Problemen im Zusammenhang mit:

- Probleme beim Blockieren der Migration.
- Teilweise oder nicht unterstützte Features und Funktionen.

## <a name="data-migration-assistant-v21"></a>Datenmigrations-Assistent v 2.1

Das v 2.1-Release von Datenmigrations-Assistent umfasst die folgenden Ergänzungen:

- Befehlszeilen Unterstützung für das Ausführen von Bewertungen in einem unbeaufsichtigten Modus, der das Ausführen von Bewertungen in der Skala erleichtert. Weitere Details finden Sie im Artikel [Ausführen von Datenmigrations-Assistent von der Befehlszeile aus](dma-commandline.md).
- Leistungsverbesserungen beim Starten und Schließen von DMA durch Benutzer.
- Die Möglichkeit, das Timeout für die SQL-Verbindung zu konfigurieren. Weitere Details finden Sie im Artikel [Konfigurationseinstellungen für Datenmigrations-Assistent](dma-configurationsettings.md).

## <a name="data-migration-assistant-v20"></a>Datenmigrations-Assistent v 2.0

Die v 2.0-Version von Datenmigrations-Assistent umfasst verbesserte Features für die Stretch-Datenbankfunktion, um korrekte priorisierte Tabellen bereitzustellen, mit denen die Speicher Einsparungen maximiert werden

## <a name="data-migration-assistant-v10"></a>Datenmigrations-Assistent v 1.0

Die Version 1.0 von Datenmigrations-Assistent ist die erste Version und bietet Folgendes:

- Ermittlung von Problemen, die ein Upgrade auf eine lokale Version von SQL Server beeinflussen können. Alle Ergebnisse werden als Kompatibilitätsprobleme beschrieben und in den folgenden Bereichen kategorisiert:
  - Aktuelle Änderungen
  - Verhaltensänderungen
  - Veraltete Features
- Ermittlung neuer Features auf der Ziel SQL Server Plattform, von der die Datenbank nach einem Upgrade profitieren kann. Alle Ergebnisse werden als Funktions Empfehlungen beschrieben und in den folgenden Bereichen kategorisiert:
  - Leistung
  - Sicherheit
  - Storage
- Moderne Benutzer Funktionen zum Durchführen von Bewertungen.

## <a name="see-also"></a>Weitere Informationen

[Übersicht über den Datenmigrations-Assistenten](../dma/dma-overview.md)
