---
title: Was sind SQL Server-Spracherweiterungen?
titleSuffix: ''
description: Spracherweiterungen sind ein Feature von SQL Server, das zum Ausführen von externem Code verwendet wird. In SQL Server 2019 werden Java, R und Python unterstützt. Die relationalen Daten können über das Erweiterbarkeitsframework im externen Code verwendet werden.
author: dphansen
ms.author: davidph
ms.date: 08/19/2020
ms.topic: overview
ms.prod: sql
ms.technology: language-extensions
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: a7e79d6253c531ef2a008a7284fa8d7cd0365999
ms.sourcegitcommit: 346a37242f889d76cd783f55aeed98023c693610
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/06/2020
ms.locfileid: "91765790"
---
# <a name="what-is-sql-server-language-extensions"></a>Was sind SQL Server-Spracherweiterungen?
[!INCLUDE [SQL Server 2019 and later](../includes/applies-to-version/sqlserver2019.md)]

Spracherweiterungen sind ein Feature von SQL Server, das zum Ausführen von externem Code verwendet wird. Die relationalen Daten können über das [Erweiterbarkeitsframework](concepts/extensibility-framework.md) im externen Code verwendet werden.

In SQL Server 2019 wird Java unterstützt. Die Java-Standardruntime ist Zulu Open JRE. Sie können auch eine andere Java-JRE oder ein anderes SDK verwenden.

> [!NOTE]
> Informationen zum Ausführen von Python oder R in SQL Server finden Sie in der Dokumentation zu [Machine Learning Services](../machine-learning/sql-server-machine-learning-services.md).

## <a name="what-you-can-do-with-language-extensions"></a>Verwendungsmöglichkeiten von Spracherweiterungen

Spracherweiterungen verwenden das Erweiterbarkeitsframework zum Ausführen von externem Code. Die Codeausführung ist von den Prozessen der Kern-Engine isoliert, aber vollständig in die Ausführung von SQL Server-Abfragen integriert. Mit den Erweiterungen können Sie Code dort ausführen, wo sich die Daten befinden – damit entfällt die Notwendigkeit, Daten über das Netzwerk abzurufen.

Externe Sprachen werden mit [CREATE EXTERNAL LANGUAGE](../t-sql/statements/create-external-language-transact-sql.md) definiert. Die gespeicherte Systemprozedur [sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) dient als Schnittstelle für die Ausführung des Codes.

Spracherweiterungen bieten eine Reihe von Vorteilen:

+ Datensicherheit. Indem die externe Sprache näher an der Datenquelle ausgeführt wird, werden ressourcenintensive oder unsichere Datenverschiebungen vermieden.
+ Geschwindigkeit. Datenbanken sind für setbasierte Vorgänge optimiert. Dank neuer Innovationen bei Datenbanken wie z. B. arbeitsspeicherinternen Tabellen lassen sich Zusammenfassungen und Aggregationen im Handumdrehen ausführen – die perfekte Ergänzung für Data Science-Szenarien.
+ Einfache Bereitstellung und Integration. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ist der Dreh- und Angelpunkt für viele andere Aufgaben und Anwendungen zur Datenverwaltung. Durch Nutzung von Daten, die sich bereits in der Datenbank befinden, stellen Sie sicher, dass die von Java verwendeten Daten konsistent und aktuell sind.

## <a name="how-to-get-started"></a>Erste Schritte

### <a name="step-1-install-the-software"></a>Schritt 1: Installieren der Software

+ [SQL Server-Spracherweiterungen unter Windows](install/install-sql-server-language-extensions-on-windows.md)
+ [SQL Server-Spracherweiterungen unter Linux](../linux/sql-server-linux-setup-language-extensions.md)

### <a name="step-2-configure-a-development-tool"></a>Schritt 2: Konfigurieren eines Entwicklungstools

Entwickler schreiben Code in der Regel auf ihrem eigenen Laptop oder auf einer Arbeitsstation für die Entwicklung. Dank der Spracherweiterungen in SQL Server besteht keine Notwendigkeit, dieses Procedere zu ändern. Wenn die Installation abgeschlossen ist, können Sie Java-Code in SQL Server ausführen.

+ **Verwenden Sie Ihre bevorzugte IDE** zum Entwickeln von Java-Code.

+ **Installieren Sie das [Microsoft-Erweiterbarkeits-SDK für Java](how-to/extensibility-sdk-java-sql-server.md)**, um Java-Code in SQL Server auszuführen.

+ **Verwenden Sie [Azure Data Studio](../azure-data-studio/what-is.md) oder [SQL Server Management Studio](../ssms/sql-server-management-studio-ssms.md)**, um externen Code in SQL Server auszuführen.

+ **Verwenden Sie die gespeicherte Systemprozedur [sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)**, um Ihren Java-Code in SQL Server auszuführen.

### <a name="step-3-write-your-first-code"></a>Schritt 3: Schreiben von Code

Führen Sie Java-Code über ein T-SQL-Skript aus:

+ [Tutorial: Reguläre Ausdrücke in Java](tutorials/search-for-string-using-regular-expressions-in-java.md)

## <a name="limitations"></a>Einschränkungen

+ Die Anzahl von Werten in den Eingabe- und Ausgabepuffern darf `MAX_INT (2^31-1)` nicht überschreiten, da dies die maximale Anzahl von Elementen ist, die in einem Array in Java zugeordnet werden können.

## <a name="next-steps"></a>Nächste Schritte

+ [Installieren einer benutzerdefinierten Python-Runtime für SQL Server](../machine-learning/install/custom-runtime-python.md)
+ [Installieren einer benutzerdefinierten R-Runtime für SQL Server](../machine-learning/install/custom-runtime-r.md)
+ Installieren von [SQL Server-Spracherweiterungen unter Windows](install/install-sql-server-language-extensions-on-windows.md) oder [unter Linux](../linux/sql-server-linux-setup-language-extensions.md)
+ Installieren Sie des [Microsoft-Erweiterbarkeits-SDKs für Java](how-to/extensibility-sdk-java-sql-server.md)