---
title: Befehle und Parameter
description: Erfahren Sie, wie Sie Command-Objekte für Microsoft SqlClient-Datenanbieter für SQL Server verwenden, um Befehle auszuführen und Ergebnisse aus einer Datenquelle zurückzugeben.
ms.date: 11/25/2020
ms.assetid: b623f810-d871-49a5-b0f5-078cc3c34db6
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-chmalh
ms.openlocfilehash: 931c36619f5eaed0159ee04db3a08eb745634698
ms.sourcegitcommit: debaff72dbfae91b303f0acd42dd6d99e03135a2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/01/2020
ms.locfileid: "96428277"
---
# <a name="commands-and-parameters"></a>Befehle und Parameter

[!INCLUDE[appliesto-netfx-netcore-netst-md](../../includes/appliesto-netfx-netcore-netst-md.md)]

[!INCLUDE[Driver_ADONET_Download](../../includes/driver_adonet_download.md)]

Nach dem Herstellen einer Verbindung mit einer Datenquelle können Sie mit einem <xref:System.Data.Common.DbCommand>-Objekt Befehle ausführen und sich Ergebnisse aus der Datenquelle zurückgeben lassen. Befehle können mit einem der Befehlskonstruktoren für den Microsoft SqlClient-Datenanbieter für SQL Server erstellt werden. Konstruktoren können optionale Argumente verwenden, z. B. eine an der Datenquelle auszuführende SQL-Anweisung, ein <xref:System.Data.Common.DbConnection>-Objekt oder ein <xref:System.Data.Common.DbTransaction>-Objekt.

Sie können diese Objekte auch als Eigenschaften des Befehls konfigurieren. Sie können außerdem mit der <xref:System.Data.Common.DbConnection.CreateCommand%2A>-Methode eines `DbConnection`-Objekts einen Befehl für eine bestimmte Verbindung erstellen. Die SQL-Anweisung, die vom Befehl ausgeführt wird, kann mit der <xref:System.Data.Common.DbCommand.CommandText%2A>-Eigenschaft konfiguriert werden. Der Microsoft SqlClient-Datenanbieter für SQL Server verfügt über das <xref:Microsoft.Data.SqlClient.SqlCommand>-Objekt.

## <a name="in-this-section"></a>In diesem Abschnitt

[Ausführen eines Befehls](execute-command.md) Beschreibt das ADO.NET-Objekt `Command` sowie die Verwendung dieses Objekts, um Abfragen und Befehle für eine Datenquelle auszuführen.

[Konfigurieren von Parametern](configure-parameters.md) Beschreibt die Verwendung von `Command`-Parametern, einschließlich Richtung, Datentypen und Parametersyntax.

[Generieren von Befehlen mit CommandBuilder-Objekten](generate-commands-with-commandbuilders.md)  
Beschreibt, wie mit den Befehls-Generatoren automatisch INSERT-, UPDATE- und DELETE-Befehle für einen `DataAdapter` generiert werden können, der über einen SELECT-Befehl für eine einzelne Tabelle verfügt.

[Abrufen eines Einzelwerts aus einer Datenbank](obtain-single-value-from-database.md) Beschreibt die Verwendung der `ExecuteScalar`-Methode eines `Command`-Objekts, um einen Einzelwert aus einer Datenbankabfrage zurückzugeben.

[Verwenden von Befehlen zum Ändern von Daten](use-commands-to-modify-data.md) Beschreibt die Verwendung des Microsoft SqlClient-Datenanbieters für SQL Server, um gespeicherte Prozeduren oder DDL-Anweisungen (Data Definition Language, Datendefinitionssprache) auszuführen.

## <a name="see-also"></a>Weitere Informationen:

- [Herstellen einer Verbindung mit Datenquellen](connecting-to-data-source.md)
