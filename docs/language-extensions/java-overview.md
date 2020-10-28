---
title: Was ist die Java-Spracherweiterung?
description: In SQL Server 2019 werden Spracherweiterungen für Java, Python und R unterstützt. Spracherweiterungen sind ein Feature von SQL Server, das zum Ausführen von externem Code verwendet wird.  Relationale Daten können über das Erweiterbarkeitsframework im externen Code verwendet werden.
author: cawrites
ms.author: chadam
ms.date: 10/06/2020
ms.topic: overview
ms.prod: sql
ms.technology: language-extensions
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: f6b7f2c21aa79ee5c0c9657cf817d9801b5d2891
ms.sourcegitcommit: 2b6760408de3b99193edeccce4b92a2f9ed5bcc6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2020
ms.locfileid: "92175904"
---
# <a name="what-is-java-language-extension"></a>Was ist die Java-Spracherweiterung?
[!INCLUDE [SQL Server 2019 and later](../includes/applies-to-version/sqlserver2019.md)]

Spracherweiterungen sind ein Feature von SQL Server, das zum Ausführen von externem Code verwendet wird. Die relationalen Daten können über das [Erweiterbarkeitsframework](concepts/extensibility-framework.md) im externen Code verwendet werden.

In SQL Server 2019 wird Java unterstützt. Die Java-Standardruntime ist Zulu Open JRE. Sie können auch eine andere Java-JRE oder ein anderes SDK verwenden.

> [!NOTE]
> Informationen zum Ausführen von Python oder R in SQL Server finden Sie in der Dokumentation zu [Maschinelles Lernen mit SQL](../machine-learning/index.yml). Für SQL Server 2019 und höher können Sie eine benutzerdefinierte Python- und R-Runtime mit Sprachenerweiterungen verwenden. Weitere Informationen finden Sie unter [Benutzerdefinierte Python-Runtime](../machine-learning/install/custom-runtime-python.md) und [Benutzerdefinierte R-Runtime](../machine-learning/install/custom-runtime-r.md).

## <a name="what-you-can-do-with-language-extensions"></a>Verwendungsmöglichkeiten von Spracherweiterungen

Spracherweiterungen verwenden das Erweiterbarkeitsframework zum Ausführen von externem Code. Die Codeausführung ist von den Prozessen der Kern-Engine isoliert, aber vollständig in die Ausführung von SQL Server-Abfragen integriert. Sie können Code an der Quelle der Daten ausführen und so die Notwendigkeit umgehen, Daten im Netzwerk zu übertragen.

Externe Sprachen werden mit [CREATE EXTERNAL LANGUAGE](https://docs.microsoft.com/sql/t-sql/statements/create-external-language-transact-sql) definiert. Die gespeicherte Systemprozedur [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) dient als Schnittstelle für die Ausführung des Codes.

Spracherweiterungen bieten verschiedene Vorteile:

+ Datensicherheit. Indem die externe Sprache näher an der Datenquelle ausgeführt wird, werden ressourcenintensive oder unsichere Datenverschiebungen vermieden.
+ Geschwindigkeit. Datenbanken sind für setbasierte Vorgänge optimiert. Dank neuer Innovationen bei Datenbanken wie z. B. arbeitsspeicherinternen Tabellen lassen sich Zusammenfassungen und Aggregationen im Handumdrehen ausführen – die perfekte Ergänzung für Data Science-Szenarien.
+ Einfache Bereitstellung und Integration. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ist der Dreh- und Angelpunkt für viele andere Aufgaben und Anwendungen zur Datenverwaltung. Durch die Nutzung von Daten aus der Datenbank stellen Sie sicher, dass die von Java verwendeten Daten konsistent und aktuell sind.

## <a name="how-to-get-started"></a>Erste Schritte

### <a name="step-1-install-the-software"></a>Schritt 1: Installieren der Software

+ [SQL Server-Spracherweiterungen unter Windows](install/windows-java.md)
+ [SQL Server-Spracherweiterungen unter Linux](../linux/sql-server-linux-setup-language-extensions-java.md)

### <a name="step-2-configure-a-development-tool"></a>Schritt 2: Konfigurieren eines Entwicklungstools

Entwickler schreiben Code in der Regel auf ihrem eigenen Laptop oder auf einer Arbeitsstation für die Entwicklung. Dank der Spracherweiterungen in SQL Server besteht keine Notwendigkeit, diese Vorgehensweise zu ändern. Wenn die Installation abgeschlossen ist, können Sie Java-Code in SQL Server ausführen.

+ **Verwenden Sie Ihre bevorzugte IDE** zum Entwickeln von Java-Code.

+ **Installieren Sie das [Microsoft-Erweiterbarkeits-SDK für Java](how-to/extensibility-sdk-java-sql-server.md)** , um Java-Code in SQL Server auszuführen.

+ **Verwenden Sie [Azure Data Studio](https://docs.microsoft.com/sql/azure-data-studio/what-is) oder [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms)** , um externen Code in SQL Server auszuführen.

+ **Verwenden Sie die gespeicherte Systemprozedur [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql)** , um Ihren Java-Code in SQL Server auszuführen.

### <a name="step-3-write-your-first-code"></a>Schritt 3: Schreiben von Code

Führen Sie Java-Code über ein T-SQL-Skript aus:

+ [Tutorial: Reguläre Ausdrücke in Java](tutorials/search-for-string-using-regular-expressions-in-java.md)

## <a name="limitations"></a>Einschränkungen

+ Die Anzahl von Werten in den Ein- und Ausgabepuffern darf `MAX_INT (2^31-1)` nicht überschreiten, da dies die maximale Anzahl von Elementen ist, die einem Array in Java zugeordnet werden können.

## <a name="next-steps"></a>Nächste Schritte

+ Installieren der [Benutzerdefinierten Python-Runtime für SQL Server](../machine-learning/install/custom-runtime-python.md)
+ Installieren der [Benutzerdefinierten R-Runtime für SQL Server](../machine-learning/install/custom-runtime-r.md)
+ Installieren der [SQL Server-Sprachenerweiterungen unter Windows](../language-extensions/install/windows-java.md) oder [unter Linux](../linux/sql-server-linux-setup-language-extensions-java.md)
+ Installieren Sie des [Microsoft-Erweiterbarkeits-SDKs für Java](how-to/extensibility-sdk-java-sql-server.md)
