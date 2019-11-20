---
title: Was sind SQL Server-Spracherweiterungen?
titleSuffix: ''
description: Spracherweiterungen sind ein Feature von SQL Server, das zum Ausführen von externem Code verwendet wird. In SQL Server 2019 wird Java unterstützt. Die relationalen Daten können über das Erweiterbarkeitsframework im externen Code verwendet werden.
author: dphansen
ms.author: davidph
ms.date: 11/05/2019
ms.topic: overview
ms.prod: sql
ms.technology: language-extensions
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 57755782f2907eff25db942600cebc63f09598e0
ms.sourcegitcommit: baa40306cada09e480b4c5ddb44ee8524307a2ab
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2019
ms.locfileid: "73658821"
---
# <a name="what-is-sql-server-language-extensions"></a>Was sind SQL Server-Spracherweiterungen?
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Spracherweiterungen sind ein Feature von SQL Server, das zum Ausführen von externem Code verwendet wird. Die relationalen Daten können über das [Erweiterbarkeitsframework](concepts/extensibility-framework.md) im externen Code verwendet werden.

In SQL Server 2019 wird Java unterstützt. Die Java-Standardruntime ist Zulu Open JRE. Sie können auch eine andere Java-JRE oder ein anderes SDK verwenden.

## <a name="what-you-can-do-with-language-extensions"></a>Verwendungsmöglichkeiten von Spracherweiterungen

Spracherweiterungen verwenden das Erweiterbarkeitsframework zum Ausführen von externem Code. Die Codeausführung ist von den Prozessen der Kern-Engine isoliert, aber vollständig in die Ausführung von SQL Server-Abfragen integriert. Mit den Erweiterungen können Sie Code dort ausführen, wo sich die Daten befinden – damit entfällt die Notwendigkeit, Daten über das Netzwerk abzurufen.

Externe Sprachen werden mit [CREATE EXTERNAL LANGUAGE](https://docs.microsoft.com/sql/t-sql/statements/create-external-language-transact-sql) definiert. Die gespeicherte Systemprozedur [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) dient als Schnittstelle für die Ausführung des Codes.

Spracherweiterungen bieten eine Reihe von Vorteilen:

+ Datensicherheit. Indem die externe Sprache näher an der Datenquelle ausgeführt wird, werden ressourcenintensive oder unsichere Datenverschiebungen vermieden.
+ Geschwindigkeit. Datenbanken sind für setbasierte Vorgänge optimiert. Dank neuer Innovationen bei Datenbanken wie z. B. arbeitsspeicherinternen Tabellen lassen sich Zusammenfassungen und Aggregationen im Handumdrehen ausführen – die perfekte Ergänzung für Data Science-Szenarien.
+ Einfache Bereitstellung und Integration. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ist der Dreh- und Angelpunkt für viele andere Aufgaben und Anwendungen zur Datenverwaltung. Durch Nutzung von Daten, die sich bereits in der Datenbank befinden, stellen Sie sicher, dass die von Java verwendeten Daten konsistent und aktuell sind.

## <a name="how-to-get-started"></a>Einstieg

### <a name="step-1-install-the-software"></a>Schritt 1: Installieren der Software

+ [SQL Server-Spracherweiterungen unter Windows](install/install-sql-server-language-extensions-on-windows.md)
+ [SQL Server-Spracherweiterungen unter Linux](../linux/sql-server-linux-setup-language-extensions.md)

### <a name="step-2-configure-a-development-tool"></a>Schritt 2: Konfigurieren eines Entwicklungstools

Entwickler schreiben Code in der Regel auf ihrem eigenen Laptop oder auf einer Arbeitsstation für die Entwicklung. Dank der Spracherweiterungen in SQL Server besteht keine Notwendigkeit, dieses Procedere zu ändern. Wenn die Installation abgeschlossen ist, können Sie Java-Code in SQL Server ausführen.

+ **Verwenden Sie Ihre bevorzugte IDE** zum Entwickeln von Java-Code.

+ **Installieren Sie das [Microsoft-Erweiterbarkeits-SDK für Java](how-to/extensibility-sdk-java-sql-server.md)** , um Java-Code in SQL Server auszuführen.

+ **Verwenden Sie [Azure Data Studio](https://docs.microsoft.com/sql/azure-data-studio/what-is) oder [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms)** , um externen Code in SQL Server auszuführen.

+ **Verwenden Sie die gespeicherte Systemprozedur [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql)** , um Ihren Java-Code in SQL Server auszuführen.

### <a name="step-3-write-your-first-code"></a>Schritt 3: Schreiben von Code

Führen Sie Java-Code über ein T-SQL-Skript aus:

+ [Tutorial: Reguläre Ausdrücke in Java](tutorials/search-for-string-using-regular-expressions-in-java.md)

## <a name="limitations"></a>Einschränkungen

+ Die Anzahl von Werten in den Eingabe- und Ausgabepuffern darf `MAX_INT (2^31-1)` nicht überschreiten, da dies die maximale Anzahl von Elementen ist, die in einem Array in Java zugeordnet werden können.

## <a name="next-steps"></a>Nächste Schritte

+ Installieren von [SQL Server-Spracherweiterungen unter Windows](install/install-sql-server-language-extensions-on-windows.md) oder [unter Linux](../linux/sql-server-linux-setup-language-extensions.md)
+ Installieren Sie des [Microsoft-Erweiterbarkeits-SDKs für Java](how-to/extensibility-sdk-java-sql-server.md)
