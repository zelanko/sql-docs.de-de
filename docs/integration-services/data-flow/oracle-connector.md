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
ms.openlocfilehash: ce461246f0afef31ab4b60b772f92aeeb479a4cb
ms.sourcegitcommit: dc965772bd4dbf8dd8372a846c67028e277ce57e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83606884"
---
# <a name="microsoft-connector-for-oracle"></a>Microsoft Connector für Oracle

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]

Microsoft Connector für Oracle ermöglicht das Exportieren von Daten aus einer und das Laden von Daten in eine Oracle-Datenquelle in einem SSIS-Paket.

## <a name="version-support"></a>Versionsunterstützung

Die folgenden Microsoft SQL Server-Produkte werden von Microsoft Connector für Oracle unterstützt:

- Ab SQL Server 2019 CU1
- SQL Server Data Tools (SSDT) ab Version 15.9.3

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

Laden Sie das Installationsprogramm [der neuesten Version von Microsoft Connector für Oracle](https://www.microsoft.com/download/details.aspx?id=58228) herunter, und führen Sie es aus, um den Connector für Oracle Database zu installieren. Folgen Sie anschließend den Anweisungen im Installations-Assistenten.

Nachdem Sie den Connector installiert haben, müssen Sie SQL Server Integration Services neu starten, um sicherzustellen, dass die Oracle-Quelle und das Ziel ordnungsgemäß funktionieren können.

Zum Ausführen von SSIS-Paketen für SQL Server 2017 und frühere Versionen müssen Sie zusätzlich zum **Microsoft Connector für Oracle** den **Oracle-Client** sowie den **Microsoft Connector für Oracle von Attunity** über folgende Links in der entsprechenden Version installieren:

- [SQL Server 2017: Microsoft Connector Version 5.0 für Oracle von Attunity](https://www.microsoft.com/download/details.aspx?id=55179)
- [SQL Server 2016: Microsoft Connector Version 4.0 für Oracle von Attunity](https://www.microsoft.com/download/details.aspx?id=52950)
- [SQL Server 2014: Microsoft Connector Version 3.0 für Oracle von Attunity](https://www.microsoft.com/download/details.aspx?id=44582)
- [SQL Server 2012: Microsoft Connector Version 2.0 für Oracle von Attunity](https://www.microsoft.com/download/details.aspx?id=29283)

## <a name="uninstallation"></a>Deinstallation

Sie können den Deinstallations-Assistenten ausführen, um den Microsoft Connector für Oracle Database aus SQL Server zu entfernen.

## <a name="next-steps"></a>Nächste Schritte

- Konfigurieren Sie den [Oracle-Verbindungs-Manager](oracle-connection-manager.md).
- Konfigurieren Sie die [Oracle-Quelle](oracle-source.md).
- Konfigurieren Sie das [Oracle-Ziel](oracle-destination.md).
- Wenn Sie Fragen haben, besuchen Sie die [TechCommunity](https://aka.ms/AA5u35j).
