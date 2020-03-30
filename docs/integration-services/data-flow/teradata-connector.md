---
title: Microsoft Connector für Teradata | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/22/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ca25b7425ce74cea820e295a6a99bc3a3c1e2817
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "75755852"
---
# <a name="microsoft-connector-for-teradata-preview"></a>Microsoft Connector für Teradata (Vorschau)
[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]

Microsoft Connector für Teradata ermöglicht das Exportieren von Daten aus und das Laden von Daten in Teradata-Datenbanken in einem SSIS-Paket.

Dieser neue Connector unterstützt Datenbanken mit Tabellen mit 1 MB-Unterstützung.

## <a name="version-support"></a>Versionsunterstützung

Die folgenden Microsoft SQL Server-Produkte werden von Microsoft Connector für Teradata unterstützt:

- Microsoft SQL Server 2019
- Microsoft SQL Server Data Tools (SSDT)

Der Microsoft Connector für Teradata verwendet die Teradata Parallel Transporter-Anwendungsprogrammiersprach-Schnittstelle zum Laden von Daten in und zum Exportieren von Daten aus der Teradata-Datenbank. Die folgenden Versionen werden unterstützt:

- Teradata Parallel Transporter (Teradata PT) 16.10
- Teradata Parallel Transporter (Teradata PT) 16.20

Die folgenden Teradata-Datenbankversionen der Datenquelle werden unterstützt:

- Teradata Database 16.20
- Teradata Database 16.10
- Teradata Database 15.10
- Teradata Database 15.00

In der [Teradata-Dokumentation](https://docs.teradata.com/) finden Sie Details im Programmierhandbuch zur Teradata Parallel Transporter-Anwendungsprogrammierschnittstelle.

## <a name="installation"></a>Installation

### <a name="prerequisite"></a>Voraussetzung

Installieren Sie auf 32-Bit-Computern die folgenden Treiber aus dem [Teradata Tools und Hilfsprogramme – Windows-Installationspaket](https://downloads.teradata.com/download/tools/teradata-tools-and-utilities-windows-installation-package):

- Teradata ODBC-Treiber (32-Bit)
- Teradata PT-API (32-Bit)

Installieren Sie auf 64 Bit-Computern die folgenden Treiber:

- Teradata ODBC-Treiber (64-Bit)
- Teradata PT-API (64-Bit)

Laden Sie das Installationsprogramm [der neuesten Version von Microsoft Connector für Teradata](https://www.microsoft.com/download/details.aspx?id=100599) herunter, und führen Sie es aus, um den Connector für Teradata-Datenbanken zu installieren. Folgen Sie anschließend den Anweisungen im Installations-Assistenten.

Nachdem Sie den Connector installiert haben, müssen Sie den SQL Server Integration Services-Dienst neu starten, um sicherzustellen, dass die Teradata-Quelle und das Ziel ordnungsgemäß funktionieren.

Zum Ausführen des SSIS-Pakets für SQL Server 2017 und früher müssen Sie den **Microsoft Connector für Teradata von Attunity** in entsprechender Version über den unten angegebenen Link installieren:

- [SQL Server 2017: Microsoft Connector Version 5.0 für Teradata von Attunity](https://www.microsoft.com/download/details.aspx?id=55179)
- [SQL Server 2016: Microsoft Connector Version 4.0 für Teradata von Attunity](https://www.microsoft.com/download/details.aspx?id=52950)
- [SQL Server 2014: Microsoft Connector Version 3.0 für Teradata von Attunity](https://www.microsoft.com/download/details.aspx?id=44582)
- [SQL Server 2012: Microsoft Connector Version 2.0 für Teradata von Attunity](https://www.microsoft.com/download/details.aspx?id=29283)

## <a name="uninstallation"></a>Deinstallation

Sie können den Deinstallations-Assistenten ausführen, um den **Microsoft Connector für Teradata** zu entfernen.

## <a name="next-steps"></a>Nächste Schritte

- Konfigurieren des [Teradata-Verbindungs-Managers](teradata-connection-manager.md)
- Konfigurieren der [Teradata-Quelle](teradata-source.md)
- Konfigurieren des [Teradata-Ziels](teradata-destination.md)
- Wenn Sie Fragen haben, besuchen Sie die [Tech Community](https://aka.ms/AA6iwdw).
