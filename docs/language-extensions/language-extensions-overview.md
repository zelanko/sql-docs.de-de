---
title: Was sind SQL Server-Spracherweiterungen?
titleSuffix: ''
description: Spracherweiterungen sind ein Feature von SQL Server, das zum Ausführen von externem Code verwendet wird. In SQL Server 2019 werden Java, Python und R unterstützt. Die relationalen Daten können über das Erweiterbarkeitsframework im externen Code verwendet werden.
author: dphansen
ms.author: davidph
ms.date: 10/07/2020
ms.topic: overview
ms.prod: sql
ms.technology: language-extensions
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 09d5643b3a39493843adc0ad2da716b7fda1b332
ms.sourcegitcommit: fe59f8dc27fd633f5dfce54519d6f5dcea577f56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2020
ms.locfileid: "91934897"
---
# <a name="what-is-sql-server-language-extensions"></a>Was sind SQL Server-Spracherweiterungen?
[!INCLUDE [SQL Server 2019 and later](../includes/applies-to-version/sqlserver2019.md)]

Spracherweiterungen sind ein Feature von SQL Server, das zum Ausführen von externem Code verwendet wird. Die relationalen Daten können über das [Erweiterbarkeitsframework](concepts/extensibility-framework.md) im externen Code verwendet werden.

In SQL Server 2019 werden Java, Python und R unterstützt.

> [!NOTE]
> Informationen zum Ausführen von Python oder R in SQL Server finden Sie in der Dokumentation zu [Maschinelles Lernen mit SQL](../machine-learning/index.yml). Für SQL Server 2019 und höher können Sie eine benutzerdefinierte Python- und R-Runtime mit Sprachenerweiterungen verwenden. Weitere Informationen finden Sie unter [Benutzerdefinierte Python-Runtime](../machine-learning/install/custom-runtime-python.md) und [Benutzerdefinierte R-Runtime](../machine-learning/install/custom-runtime-r.md).

## <a name="what-you-can-do-with-language-extensions"></a>Verwendungsmöglichkeiten von Spracherweiterungen

Spracherweiterungen verwenden das Erweiterbarkeitsframework zum Ausführen von externem Code. Die Codeausführung ist von den Prozessen der Kern-Engine isoliert, aber vollständig in die Ausführung von SQL Server-Abfragen integriert. Sie können Code an der Quelle der Daten ausführen und so die Notwendigkeit umgehen, Daten im Netzwerk zu übertragen.

Externe Sprachen werden mit [CREATE EXTERNAL LANGUAGE](../t-sql/statements/create-external-language-transact-sql.md) definiert. Die gespeicherte Systemprozedur [sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) dient als Schnittstelle für die Ausführung des Codes.

Spracherweiterungen bieten eine Reihe von Vorteilen:

+ Datensicherheit. Indem die externe Sprache näher an der Datenquelle ausgeführt wird, werden ressourcenintensive oder unsichere Datenverschiebungen vermieden.
+ Geschwindigkeit. Datenbanken sind für setbasierte Vorgänge optimiert. Dank neuer Innovationen bei Datenbanken wie z. B. arbeitsspeicherinternen Tabellen lassen sich Zusammenfassungen und Aggregationen im Handumdrehen ausführen – die perfekte Ergänzung für Data Science-Szenarien.
+ Einfache Bereitstellung und Integration. [!INCLUDE [ssNoVersion](../includes/ssnoversion-md.md)] ist der Dreh- und Angelpunkt für viele andere Aufgaben und Anwendungen zur Datenverwaltung. Durch Nutzung von in der Datenbank enthaltenen Daten stellen Sie sicher, dass die von der Sprachenerweiterung verwendeten Daten konsistent und aktuell sind.

## <a name="next-steps"></a>Nächste Schritte

+ Installieren der [Benutzerdefinierten Python-Runtime für SQL Server](../machine-learning/install/custom-runtime-python.md)
+ Installieren der [Benutzerdefinierten R-Runtime für SQL Server](../machine-learning/install/custom-runtime-r.md)
+ Installieren der [SQL Server-Sprachenerweiterungen unter Windows](install/install-sql-server-language-extensions-on-windows.md) oder [unter Linux](../linux/sql-server-linux-setup-language-extensions.md)
+ Installieren Sie des [Microsoft-Erweiterbarkeits-SDKs für Java](how-to/extensibility-sdk-java-sql-server.md)
