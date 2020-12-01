---
title: Abrufen und Ändern von Daten
description: In .NET Framework dient der Microsoft SqlClient-Datenanbieter für SQL Server als Brücke zwischen einer Anwendung und einer Datenquelle, um Daten zu lesen und zu aktualisieren.
ms.date: 11/13/2020
ms.assetid: 722e7f87-3691-46c6-87e8-7d159722d675
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-chmalh
ms.openlocfilehash: cbe61aafd8dcd1681230c355187a65a231535e00
ms.sourcegitcommit: 192f6a99e19e66f0f817fdb1977f564b2aaa133b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/25/2020
ms.locfileid: "96126388"
---
# <a name="retrieving-and-modifying-data-in-adonet"></a>Abrufen und Ändern von Daten in ADO.NET

[!INCLUDE[appliesto-netfx-netcore-netst-md](../../includes/appliesto-netfx-netcore-netst-md.md)]

[!INCLUDE[Driver_ADONET_Download](../../includes/driver_adonet_download.md)]

Eine der wichtigsten Funktionen einer Datenbankanwendung ist das Herstellen einer Verbindung mit einer Datenquelle und das Abrufen der darin enthaltenen Daten. Der SqlClient-Datenanbieter dient als Brücke zwischen einer Anwendung und einer Datenquelle, die das Ausführen von Befehlen sowie das Abrufen von Daten mithilfe von **DataReader** oder **DataAdapter** ermöglicht. Eine Hauptfunktion jeder Datenbank ist die Fähigkeit, die in ihr gespeicherten Daten zu aktualisieren. Im Microsoft SqlClient-Datenanbieter für SQL Server werden zum Aktualisieren von Daten **DataAdapter**, die Objekte <xref:System.Data.DataSet> und **Command** und u. U. auch Transaktionen verwendet.

## <a name="in-this-section"></a>In diesem Abschnitt

[Herstellen einer Verbindung mit einer Datenquelle](connecting-to-data-source.md) Beschreibt, wie eine Verbindung mit einer Datenquelle hergestellt und mit Verbindungsereignissen gearbeitet wird.

[Verbindungszeichenfolgen](connection-strings.md) Enthält Themen mit Erläuterungen verschiedener Aspekte von Verbindungszeichenfolgen, einschließlich Schlüsselwörter für Verbindungszeichenfolgen, Sicherheitsinformationen sowie Speicherung und Abruf von Verbindungszeichenfolgen.

[Verbindungspooling](connection-pooling.md) Beschreibt das Verbindungspooling für den Microsoft SqlClient-Datenanbieter für SQL Server.

## <a name="see-also"></a>Weitere Informationen

- [Datentypzuordnungen in ADO.NET](data-type-mappings-ado-net.md)
- [SQL Server und ADO.NET](./sql/index.md)
