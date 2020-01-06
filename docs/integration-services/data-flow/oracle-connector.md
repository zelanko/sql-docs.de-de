---
title: Microsoft Connector für Oracle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/14/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ee00232a1c1e64d31b7b6360666bdeebba756db9
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75246952"
---
# <a name="microsoft-connector-for-oracle"></a>Microsoft Connector für Oracle

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]

Microsoft Connector für Oracle ermöglicht das Exportieren von Daten aus einer und das Laden von Daten in eine Oracle-Datenquelle in einem SSIS-Paket.

## <a name="version-support"></a>Versionsunterstützung

Die folgenden Microsoft SQL Server-Produkte werden von Microsoft Connector für Oracle unterstützt:

- Ab SQL Server 2019
- SQL Server Data Tools (SSDT)

Die folgenden Oracle-Datenbankversionen der Datenquelle werden unterstützt:

- Oracle 10.x
- Oracle 11.x
- Oracle 12c
- Oracle 18C (ohne Unterstützung der Windows-Authentifizierung)

Die Oracle-Datenbank wird auf allen Betriebssystemen und Plattformen unterstützt.
> [!NOTE]
>
> Der Oracle-Client ist für den Microsoft Connector für Oracle Database in SQL Server 2019 nicht erforderlich.

## <a name="installation"></a>Installation

Wenn Sie das Paket in SQL Server ausführen müssen, können Sie das Installationsprogramm für den Microsoft-Connector für Oracle Database [hier](https://www.microsoft.com/download/details.aspx?id=58228) herunterladen. Folgen Sie anschließend den Anweisungen im Installations-Assistenten.

Nachdem Sie den Connector installiert haben, müssen Sie den SQL Server Integration Services-Dienst neu starten, um sicherzustellen, dass die Oracle-Quelle und das Ziel ordnungsgemäß funktionieren.

Wenn Sie ein Paket mit dem Connector entwerfen müssen, ist es nicht erforderlich, den Connector herunterzuladen. In den SQL Server Data Tools (SSDT) ist er seit Version 15.9.0 enthalten.

## <a name="uninstallation"></a>Deinstallation

Sie können den Deinstallations-Assistenten ausführen, um den Microsoft Connector für Oracle Database aus SQL Server zu entfernen.

## <a name="design-ssis-package-with-previous-version"></a>Entwerfen des SSIS-Pakets mit vorheriger Version

Da SSDT den Microsoft Connector für Oracle Database bereits ab Version 15.9.0 enthält, ist keine Installation erforderlich, wenn Sie SSIS-Pakete für SQL Server 2019 entwerfen.

Zum Entwerfen von SSIS-Paketen für SQL Server 2017 und früher müssen Sie den Connector für Oracle von Attunity mit entsprechender Version installieren.

**Downloadlinks:**

- [SQL Server 2017: Microsoft Connector Version 5.0 für Oracle von Attunity](https://www.microsoft.com/download/details.aspx?id=55179)
- [SQL Server 2016: Microsoft Connector Version 4.0 für Oracle von Attunity](https://www.microsoft.com/download/details.aspx?id=52950)
- [SQL Server 2014: Microsoft Connector Version 3.0 für Oracle von Attunity](https://www.microsoft.com/download/details.aspx?id=44582)
- [SQL Server 2012: Microsoft Connector Version 2.0 für Oracle von Attunity](https://www.microsoft.com/download/details.aspx?id=29283)

## <a name="next-steps"></a>Nächste Schritte

- Konfigurieren Sie den [Oracle-Verbindungs-Manager](oracle-connection-manager.md).
- Konfigurieren Sie die [Oracle-Quelle](oracle-source.md).
- Konfigurieren Sie das [Oracle-Ziel](oracle-destination.md).
- Wenn Sie Fragen haben, besuchen Sie die [TechCommunity](https://aka.ms/AA5u35j).
