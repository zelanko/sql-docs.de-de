---
title: Erweiterung für die verwaltete Azure SQL-Datenbank-Instanz
titleSuffix: Azure Data Studio
description: Verwenden von Azure Data Studio mit einer verwalteten Azure SQL-Instanz
ms.custom: seodec18
ms.date: 10/07/2019
ms.reviewer: alayu; sstein
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: jovanpop-msft
ms.author: jovanpop
manager: alanyu
ms.openlocfilehash: 2269c594bd0fff036d4fe5d5d722aa5d78d4ca6d
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "75883997"
---
# <a name="azure-sql-database-managed-instance-dashboard-for-azure-data-studio-preview"></a>Dashboard für verwaltete Azure SQL-Datenbank-Instanzen für Azure Data Studio (Vorschauversion)

Die Erweiterung für die verwaltete Azure SQL-Datenbank-Instanz bietet ein Dashboard für die Arbeit mit einer [verwalteten Azure SQL-Datenbank-Instanz](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-index) in [Azure Data Studio](https://github.com/Microsoft/azuredatastudio). Diese Erweiterung stellt die folgenden Funktionen bereit:

- Anzeige von Eigenschaften der verwalteten Instanz, einschließlich V-Kernen und genutztem Speicher
- Überwachung der CPU- und Speichernutzung für die letzten zwei Stunden
- Anzeige von Konfigurationswarnungen und Optimierungsempfehlungen
- Anzeige des Zustands von Datenbankreplikaten
- Anzeige gefilterter Fehlerprotokolle

## <a name="install"></a>Installieren

Sie können das offizielle Release dieser Erweiterung installieren. Führen Sie die Schritte in der [Azure Data Studio-Dokumentation](https://docs.microsoft.com/sql/azure-data-studio/extensions) aus.
Suchen Sie im Bereich **Erweiterungen** nach „Verwaltete Instanz“, und installieren Sie sie dort. Nach der Installation werden Sie automatisch über alle zukünftigen Updates der Erweiterung benachrichtigt.

Wenn die Erweiterung installiert ist, wird die Registerkarte **Verwaltete Instanz** in Azure Data Studio angezeigt. Dort finden Sie spezifische Informationen zu Ihrer verwalteten Instanz.

## <a name="properties"></a>Eigenschaften

Die Erweiterung zeigt technische Merkmale und Informationen zur Ressourcennutzung der verwalteten Instanz an.

[ ![Eigenschaften der verwalteten Instanz](media/azure-sql-mi-extension/ads-mi-tab1.png )](media/azure-sql-mi-extension/ads-mi-tab1.png#lightbox)

Im oberen Bereich werden die folgenden Details angezeigt:

- **Eigenschaften**. Erhalten Sie grundlegende Informationen über die verwaltete Instanz, z. B. zu virtuellen Kernen, Arbeitsspeicher und Speicher, die verfügbar sind. Ermitteln Sie auch Ihre aktuelle Dienstebene, Hardwaregeneration und E/A-Merkmale wie z. B. den Durchsatz der Instanzprotokollerfassung oder Merkmale des E/A-Durchsatzes.
- **Lokaler SSD-Speicher**. Auf der universellen Dienstebene werden **TempDB**-Dateien lokal gespeichert. Auf der unternehmenskritischen Dienstebene werden _alle_ Datenbankdateien auf einem lokalen SSD-Datenträger gespeichert. In diesem Abschnitt sehen Sie, wie viel Speicherplatz die verwaltete Instanz im lokalen Speicher belegt.
- **Azure Disk Storage Premium**. Die Benutzer- und Systemdatenbankdateien werden auf der universellen Dienstebene in Azure Premium-Speicher platziert. In diesem Abschnitt sehen Sie die Menge der verwendeten Daten, die Anzahl der Dateien und den verfügbaren Speicherplatz. Auf der unternehmenskritischen Dienstebene ist dieser Abschnitt leer.
- **Ressourcennutzung**. Zeigen Sie den Prozentsatz des Speichers und der CPU an, den Ihre verwaltete Instanz in den letzten zwei Stunden genutzt hat. Auf diese Weise können Sie die Instanzgröße erhöhen, wenn sich diese dem Grenzwert nähert.

## <a name="recommendations"></a>Empfehlungen

Wenn Sie den zweiten Bereich auf der Registerkarte **Verwaltete Instanz** auswählen, erhalten Sie Empfehlungen und Warnungen, die Ihnen helfen, die verwaltete Instanz zu optimieren.

[ ![Empfehlungen für verwaltete Instanzen](media/azure-sql-mi-extension/ads-mi-tab2.png )](media/azure-sql-mi-extension/ads-mi-tab2.png#lightbox)

Möglicherweise werden einige der folgenden Empfehlungen angezeigt:

- **Erreichen der Speicherbegrenzung**. Sie können entweder unnötige Daten löschen oder die Speichergröße der Instanz erhöhen. Datenbanken, die die Speicherbegrenzung erreichen, können möglicherweise nicht einmal Leseabfragen verarbeiten.
- **Erreichen der Durchsatzbegrenzung für die Instanz** Sie werden benachrichtigt, wenn beim Laden das Limit Ihrer Dienstebene erreicht wird: 22 MB/s für „universell“ bzw. 48 MB/s für „unternehmenskritisch“. Beachten Sie, dass die verwaltete Instanz Ihre Last begrenzt, um sicherzustellen, dass Sicherungen durchgeführt werden können.
- **Hohe Arbeitsspeicherauslastung**. Niedrige Seitenlebenserwartung oder viele `PAGEIOLATCH`-Wartestatistiken deuten möglicherweise darauf hin, dass Ihre Instanz Seiten aus dem Arbeitsspeicher entfernt und ständig versucht, mehr Seiten von Datenträgern zu laden.
- **Grenzwerte für Protokolldateien**. Wenn Ihre Protokolldateien in der [Dienstebene „Universell“ die Datei-E/A-Grenzwerte](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-resource-limits#file-io-characteristics-in-general-purpose-tier) erreichen, müssen Sie möglicherweise die Protokolldateigröße erhöhen, um eine bessere Leistung zu erzielen.
- **Grenzwerte für Datendateien**. Wenn Ihre Datendateien in der [Dienstebene „Universell“ die Datei-E/A-Grenzwerte](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-resource-limits#file-io-characteristics-in-general-purpose-tier) erreichen, müssen Sie möglicherweise die Dateigröße erhöhen, um eine bessere Leistung zu erzielen. Dieses Problem kann zu Arbeitsspeicherauslastung führen und Sicherungen verlangsamen.
- **Verfügbarkeitsprobleme**. Eine große Anzahl virtueller Protokolldateien kann sich auf die Leistung auswirken. Wenn ein Prozess fehlschlägt, kann dies zu einer längeren Datenbankwiederherstellung auf der universellen Dienstebene führen.

Überprüfen Sie regelmäßig diese Empfehlungen, untersuchen Sie die Ursachen und ergreifen Sie Maßnahmen zur Problembehebung. Die Erweiterung für die verwaltete Azure SQL-Datenbank-Instanz stellt Skripts zur Verfügung, die Sie ausführen können, um einige der gemeldeten Probleme zu beheben.

## <a name="replicas"></a>Replikate

Der dritte Bereich auf der Registerkarte **Verwaltete Instanz** zeigt Ihnen den Status von Datenbankreplikaten in Ihrer verwalteten Instanz an.

[ ![Replikate verwalteter Instanzen](media/azure-sql-mi-extension/ads-mi-tab3.png )](media/azure-sql-mi-extension/ads-mi-tab3.png#lightbox)

Auf der universellen Dienstebene verfügt jede Datenbank über ein einziges (primäres) Replikat. Auf der unternehmenskritischen Ebene der Instanz verfügt jede Datenbank über ein primäres und drei sekundäre Replikate, wobei eines für schreibgeschützte Workloads verwendet wird. Im Bereich **Replikate** können Sie den Synchronisierungsprozess überwachen und sicherstellen, dass alle sekundären Replikate synchron mit dem primären Replikat sind.

## <a name="logs"></a>Protokolle

Im vierten Bereich unter **Verwaltete Instanz** werden die aktuellsten und relevantesten SQL-Fehlerprotokolleinträge angezeigt.

[ ![Protokolleinträge für verwaltete Instanzen](media/azure-sql-mi-extension/ads-mi-tab4.png )](media/azure-sql-mi-extension/ads-mi-tab4.png#lightbox)

Obwohl Ihre verwaltete Instanz eine große Anzahl von Protokolleinträgen generiert, sind die meisten davon interne und Systeminformationen. Zudem enthalten einige Protokolleinträge physische Datenbanknamen (`GUID`-Werte) anstelle tatsächlicher logischer Datenbanknamen.

Die Erweiterung für die verwaltete Azure SQL-Datenbank-Instanz filtert unnötige Protokolleinträge anhand der [Dimitri-Furman-Methode](https://techcommunity.microsoft.com/t5/DataCAT/Azure-SQL-DB-Managed-Instance-sp-readmierrorlog/ba-p/305506) heraus. Außerdem zeigt die Erweiterung tatsächliche logische Dateinamen anstelle von physischen Namen an.

## <a name="reporting-problems"></a>Melden von Problemen

Wenn Sie Probleme mit der Erweiterung für die verwaltete Azure SQL-Datenbank-Instanz haben, melden Sie das Problem im [GitHub-Projekt zur Erweiterung](https://github.com/JocaPC/AzureDataStudio-Managed-Instance/issues).

## <a name="code-of-conduct"></a>Verhaltensregeln

Für dieses Projekt gelten die Microsoft-Verhaltensregeln für Open Source ([Microsoft Open Source Code of Conduct][conduct-code]).

Um weitere Informationen zu erhalten, lesen Sie die häufig gestellten Fragen zu den Verhaltensregeln ([Code of Conduct FAQ][conduct-FAQ]), oder wenden Sie sich mit weiteren Fragen und Kommentaren an [opencode@microsoft.com][conduct-email].

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen finden Sie auf der Seite zum [GitHub-Projekt](https://github.com/JocaPC/AzureDataStudio-Managed-Instance/).

[conduct-code]: https://opensource.microsoft.com/codeofconduct/
[conduct-FAQ]: https://opensource.microsoft.com/codeofconduct/faq/
[conduct-email]: mailto:opencode@microsoft.com
