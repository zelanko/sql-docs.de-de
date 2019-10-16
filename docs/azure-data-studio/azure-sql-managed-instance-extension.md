---
title: Die Erweiterung „Verwaltete Azure SQL-Instanz“
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
ms.openlocfilehash: d443292fb091679d3d6a18d557a5a7aac464fdec
ms.sourcegitcommit: 512acc178ec33b1f0403b5b3fd90e44dbf234327
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/08/2019
ms.locfileid: "72041142"
---
# <a name="managed-instance-support-for-azure-data-studio-preview"></a>Unterstützung für verwaltete Instanzen für Azure Data Studio (Vorschau)

Diese Erweiterung ermöglicht Ihnen, in [Azure Data Studio](https://github.com/Microsoft/azuredatastudio) mit einer [verwalteten Azure SQL-Instanz](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-index) zu arbeiten. Diese Erweiterung stellt die folgenden Funktionen bereit:

- Anzeigen von Eigenschaften der verwalteten Instanz (virtuelle Kerne, belegter Speicherplatz)
- Überwachung der CPU- und Speicherauslastung in den letzten beiden Stunden
- Anzeigen von Konfigurationswarnungen und Optimierungsempfehlungen
- Anzeigen des Zustands von Datenbankreplikaten
- Anzeigen gefilterter Fehlerprotokolle

## <a name="installations"></a>Installationen

Sie können das offizielle Release der Erweiterung „Verwaltete Instanz“ installieren, indem Sie die Schritte in der [Azure Data Studio](https://docs.microsoft.com/sql/azure-data-studio/extensions)-Dokumentation ausführen.
Suchen Sie im Bereich „Erweiterungen“ nach der Erweiterung „Verwaltete Instanz“, und installieren Sie sie dort.  Sie werden automatisch über alle zukünftigen Updates der Erweiterung benachrichtigt.

Nachdem Sie die Erweiterung „Verwaltete Instanz“ installiert haben, wird in Azure Data Studio die Registerkarte `Managed Instance` angezeigt. Auf dieser Registerkarte finden Sie Informationen, die speziell für die verwaltete Instanz gelten.

## <a name="properties"></a>Eigenschaften

Diese Erweiterung ermöglicht Ihnen, die technischen Merkmale Ihrer verwalteten Instanz und die Nutzung einiger Ressourcen einzusehen.

![Eigenschaften der verwalteten Instanz](media/azure-sql-mi-extension/ads-mi-tab1.png)

Auf dem ersten Blatt werden die folgenden Details angezeigt:

- **Grundlegende Eigenschaften** wie verfügbare Anzahl virtueller Kerne, Arbeitsspeicher, Speicherplatz, aktuelle Dienstebene und Hardwaregeneration sowie E/A-Eigenschaften wie z. B. Schreibdurchsatz bei der Instanzprotokollierung oder Merkmale des Datei-E/A-Durchsatzes.
- **Nutzung des lokalen SSD-Speichers**. Auf der Dienstebene „Universell“ werden ausschließlich **TEMPDB**-Dateien lokal platziert, während auf der Ebene „Unternehmenskritisch“ alle Datenbankdateien auf lokalen SSD-Datenträgern abgelegt werden. In diesem Abschnitt sehen Sie, wie viel Speicherplatz die verwaltete Instanz im lokalen Speicher belegt.
- **Verwendung von Azure Disk Storage Premium**: Die Benutzer- und Systemdatenbank werden auf der Dienstebene „Universell“ in Azure Premium-Speicher platziert. Hier finden Sie den Umfang der von Ihnen verwendeten Daten, den verbleibenden Speicherplatz und die Anzahl der Dateien. Auf der Dienstebene „Unternehmenskritisch“ ist dieser Abschnitt leer.
- **Ressourceneinsatz**, der zeigt, wie viel Speicherplatz und CPU-Kapazität Ihre Instanz in den letzten beiden Stunden genutzt hat. Erhöhen Sie die Instanzgröße, sobald Sie den Grenzwert erreichen.

## <a name="recommendations"></a>Empfehlungen

Diese Erweiterung bietet Empfehlungen und Warnungen, die Ihnen bei der Optimierung Ihrer verwalteten Instanz helfen können.

![Empfehlungen für verwaltete Instanzen](media/azure-sql-mi-extension/ads-mi-tab2.png)

In dieser Tabelle finden Sie die folgenden Empfehlungen:

- Erreichen des Grenzwerts für den Speicherplatz: Sie sollten entweder unnötige Daten löschen oder die Speichergröße der Instanz erhöhen, da Datenbanken, die den Speichergrenzwert erreichen, möglicherweise nicht einmal mehr Leseabfragen verarbeiten können.
- Erreichen des Grenzwerts der Instanz für den Durchsatz: Wenn Sie Daten laden, 22 MB/s auf der Dienstebene „Universell“ oder 48 MB/s auf der Dienstebene „Unternehmenskritisch“, begrenzt die verwaltete Instanz Ihre Datenlast, um sicherzustellen, dass Sicherungen erfolgen können.
- Hohe Arbeitsspeicherauslastung: Niedrige Seitenlebenserwartung oder viele `PAGEIOLATCH`-Wartestatistiken deuten möglicherweise darauf hin, dass Ihre Instanz Seiten aus dem Arbeitsspeicher entfernt und ständig versucht, mehr Seiten von Datenträgern zu laden.
- Grenzwerte für Protokolldateien: Wenn Ihre Protokolle im [Tarif „Universell“ die Datei-E/A-Grenzwerte](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-resource-limits#file-io-characteristics-in-general-purpose-tier) erreichen, müssen Sie möglicherweise die Dateigröße erhöhen, um eine bessere Leistung zu erzielen.
- Grenzwerte für Datendateien: Wenn Ihre Datendateien auf der [Dienstebene „Universell“ die Datei-E/A-Grenzwerte](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-resource-limits#file-io-characteristics-in-general-purpose-tier) erreichen, müssen Sie möglicherweise die Dateigröße erhöhen, um eine bessere Leistung zu erzielen. Dieses Problem kann zu Arbeitsspeicherauslastung führen und Sicherungen verlangsamen.
- Verfügbarkeitsprobleme: Eine hohe Anzahl virtueller Protokolldateien kann auf der Dienstebene „Universell“ bei einem Prozessausfall zu Leistungseinbußen und einer möglicherweise längeren Datenbankwiederherstellung führen.

Sie sollten diese Empfehlungen regelmäßig überprüfen, die Ursachen untersuchen und Korrekturmaßnahmen ergreifen. Die Erweiterung „Verwaltete Instanz“ stellt die Skripts zur Verfügung, die Sie ausführen können, um einige der gemeldeten Probleme zu beheben.

## <a name="replicas"></a>Replikate

Die Erweiterung „Verwaltete Instanz“ ermöglicht Ihnen, den Status von Datenbankreplikaten in Ihrer verwalteten Instanz anzuzeigen.

![Replikate verwalteter Instanzen](media/azure-sql-mi-extension/ads-mi-tab3.png)

Auf der Dienstebene „Universell“ hat jede Datenbank ein einzelnes (primäres) Replikat. Im Tarif „Unternehmenskritisch“ hat jede Datenbank ein primäres und drei sekundäre Replikate (von denen eines für schreibgeschützte Arbeitsauslastungen verwendet wird). Hier können Sie den Synchronisierungsprozess überwachen und sicherstellen, dass alle sekundären Replikate synchron mit dem primären Replikat sind.

## <a name="logs"></a>Protokolle

Die Erweiterung „Verwaltete Instanz“ zeigt die relevantesten neuesten SQL Server-Fehlerprotokolleinträge.

![Protokolleinträge für verwaltete Instanzen](media/azure-sql-mi-extension/ads-mi-tab4.png)

Die Erweiterung „Verwaltete Instanz“ gibt eine große Anzahl von Protokolleinträgen aus, von denen die meisten interne und Systeminformationen sind. Einige Protokolleinträge zeigen physische Datenbanknamen (`GUID`-Werte) anstelle tatsächlicher logischer Datenbanknamen.

Die Erweiterung „Verwaltete Instanz“ filtert unnötige Protokolleinträge basierend auf der [Dimitri Furman-Methode](https://techcommunity.microsoft.com/t5/DataCAT/Azure-SQL-DB-Managed-Instance-sp-readmierrorlog/ba-p/305506) heraus und zeigt tatsächliche logische Dateinamen anstelle physischer Namen.

## <a name="reporting-problems"></a>Melden von Problemen

Wenn Sie Probleme mit der Erweiterung „Verwaltete Instanz“ haben, melden Sie das Problem im [GitHub-Projekt zur Erweiterung](https://github.com/JocaPC/AzureDataStudio-Managed-Instance/issues).

## <a name="maintainers"></a>Maintainer

- [Jovan Popovic(MSFT)](https://github.com/jovanpop_msft) - [@jovanpop_msft](https://twitter.com/JovanPop_MSFT)

## <a name="code-of-conduct"></a>Verhaltensregeln

Für dieses Projekt gelten die Microsoft-Verhaltensregeln für Open Source ([Microsoft Open Source Code of Conduct][conduct-code]).
Um weitere Informationen zu erhalten, lesen Sie die häufig gestellten Fragen zu den Verhaltensregeln ([Code of Conduct FAQ][conduct-FAQ]), oder wenden Sie sich mit weiteren Fragen und Kommentaren an [opencode@microsoft.com][conduct-email].

[conduct-code]: http://opensource.microsoft.com/codeofconduct/
[conduct-FAQ]: http://opensource.microsoft.com/codeofconduct/faq/
[conduct-email]: mailto:opencode@microsoft.com
[conduct-md]: https://github.com/PowerShell/vscode-powershell/blob/master/CODE_OF_CONDUCT.md
