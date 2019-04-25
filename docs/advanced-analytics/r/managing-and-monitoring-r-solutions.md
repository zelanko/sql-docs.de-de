---
title: Verwalten und Integrieren von Machine Learning-Workloads – SQL Server Machine Learning Services
description: Überprüfen Sie als eine SQL Server-Datenbankadministrator die administrativen Aufgaben für die Bereitstellung eines Machine learning-R und Python-Subsystem in einer Datenbank-Engine-Instanz aus.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/10/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: c9b1b4eca18a9d4d8d1819eee399676046cc9d78
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62503844"
---
# <a name="manage-and-integrate-machine-learning-workloads-on-sql-server"></a>Verwalten und Integrieren von Machine Learning-Workloads auf SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieser Artikel ist für SQL Server-Datenbankadministratoren, die für die Bereitstellung einer effizienten Data Science-Infrastruktur auf eine Server-Ressource, die Unterstützung von mehreren Workloads zuständig sind. Sie frames des Verwaltungsproblem Speicherplatzes, die relevant für die Verwaltung von R und Python-code die Ausführung auf SQL Server. 

## <a name="what-is-feature-integration"></a>Was ist die Funktion zur Integration

R und Python-Machine-Learning erfolgt über [SQL Server Machine Learning Services](../what-is-sql-server-machine-learning.md) als Erweiterung für eine Datenbank-Engine-Instanz. Die Integration ist in erster Linie durch die Sicherheitsstufe und der Data Definition Language, die wie folgt zusammengefasst werden:

+ Gespeicherte Prozeduren verfügen über die Fähigkeit, akzeptieren R und Python-code als Eingabeparameter. Entwickler und Data Scientists können eine [gespeicherte Systemprozedur](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql?view=sql-server-2017) , oder erstellen Sie eine benutzerdefinierte Prozedur, die ihren Code umschließt.
+ T-SQL-Funktionen (d. h., [PREDICT](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql)) einer zuvor trainierten Datenmodell nutzen können. Diese Funktion ist über T-SQL verfügbar. Daher ist es möglich, kann er aufgerufen auf einem System, die nicht speziell die Machine learning-Erweiterungen installiert.
+ Vorhandene Datenbank-Anmeldenamen und rollenbasierte Berechtigungen behandelt die Benutzer aufgerufenen Skripts, die dieselben Daten nutzen. Als allgemeine Regel Wenn Benutzer über eine Abfrage auf Daten zugreifen können nicht können nicht sie per Skript entweder darauf zugreifen.

## <a name="feature-availability"></a>Verfügbarkeit von Features

R und Python-Integration wird durch eine Folge von Schritten verfügbar. Das erste Setup ist, wenn Sie [ein- oder Hinzufügen der **Machine Learning Services** ](../install/sql-machine-learning-services-windows-install.md) Feature eine Instanz der Datenbank-Engine. Im nachfolgenden Schritt müssen Sie die externe Skripts in der Datenbank-Engine-Instanz (es ist standardmäßig deaktiviert) aktivieren.

An diesem Punkt nur Administratoren verfügen über umfassende Berechtigung zum Erstellen und Ausführen von externen Skripts, hinzufügen oder Löschen von Paketen und gespeicherten Prozeduren und anderen Objekten zu erstellen.

Alle anderen Benutzer müssen EXECUTE ANY EXTERNAL SCRIPT-Berechtigung erteilt werden. Zusätzliche [standard Datenbankberechtigungen](../security/user-permission.md) zu bestimmen, ob Benutzer Objekte erstellen, Ausführen von Skripts, serialisiert und trainierte Modelle nutzen und so weiter. 

## <a name="resource-allocation"></a>Ressourcenzuordnung

Gespeicherte Prozeduren und T-SQL-Abfragen, die extern ausgeführt aufrufen verwenden die verfügbaren Ressourcen, um den standardressourcenpool. Im Rahmen der Standardkonfiguration sind der externe Prozesse wie R und Python-Sitzungen bis zu 20 % des Gesamtspeichers auf dem Hostsystem zulässig. 

Wenn die enthaltenen angepasst werden sollen, können Sie die Standard-Pool mit entsprechenden Auswirkungen auf die Machine Learning-Workloads, die auf diesem System ausgeführten ändern.

Eine weitere Möglichkeit ist die Erstellung ein benutzerdefinierten externen Ressourcenpools, um Sitzungen von bestimmten Programme, Hosts oder -Aktivität, die während einer bestimmten Zeitintervallen zu erfassen. Weitere Informationen finden Sie unter [Ressourcenkontrolle zum Ändern von Ressourcenebenen für die Ausführung von R und Python](../administration/resource-governance.md) und [Gewusst wie: Erstellen eines Ressourcenpools](../administration/how-to-create-a-resource-pool.md) schrittweise Anweisungen.

## <a name="isolation-and-containment"></a>Isolation und Kapselung

Die Verarbeitungsarchitektur wurde konzipiert, um externe Skripts von der Kern-Engine-Verarbeitung zu isolieren. Führen Sie R- und Python-Skripts als separate Prozesse unter lokalen Konten. Im Task-Manager können Sie R und Python-Prozesse überwachen, unter einem Konto mit niedrigen Berechtigungen lokaler Benutzer, die sich von den SQL Server-Dienstkonto ausgeführt wird. 

Ausführen von R und Python-Prozesse in einzelkonten mit geringen Rechten hat die folgenden Vorteile:

+ Isoliert die Kern-Engine-Prozesse von R und Python-Sitzungen, die einen R- oder Python-Prozess beendet werden kann, ohne Auswirkungen auf die Core-Datenbankvorgänge. 

+ Reduziert die Berechtigungen von dem externen Skript-Laufzeitprozessen, auf dem Hostcomputer.

Konten mit minimalprivilegien während des Setups erstellt und platziert Sie in einer Windows *benutzerkontenpool* namens **SQLRUserGroup**. Standardmäßig ist dieser Gruppe die Berechtigung zur Verwendung von ausführbaren Dateien, Bibliotheken und integrierten Datasets im Programmordner für R und Python unter SQL Server. 

Greifen als ein DBA der, Sie datensicherheit für SQL Server verwenden können, um anzugeben, die über die Berechtigung zum Ausführen von Skripts verfügt, und in Aufträgen verwendete Daten unter den gleichen Sicherheitsrollen verwaltet werden, die steuern, über T-SQL-Abfragen. Als Systemadministrator können Sie explizit verweigern **SQLRUserGroup** Zugriff auf sensible Daten auf dem lokalen Server durch Erstellen von ACLs.

>[!NOTE]
> In der Standardeinstellung die **SQLRUserGroup** verfügt nicht über einen Anmeldenamen oder Berechtigungen in SQL Server selbst. Workerkonten eine Anmeldung für den Datenzugriff benötigen, müssen Sie ihn selbst erstellen. Supportanfragen über ein Skript bei der Ausführung für Daten oder Vorgänge in der Datenbank-Engine-Instanz, wenn die Identität des Benutzers ein Windows-Benutzer ist und die Verbindungszeichenfolge einen vertrauenswürdigen Benutzer gibt ist ein Szenario, das speziell für die Erstellung einer Anmeldung aufgerufen werden. Weitere Informationen finden Sie unter [Hinzufügen der SQLRUserGroup als Datenbankbenutzer](../../advanced-analytics/security/add-sqlrusergroup-to-database.md).

## <a name="disable-script-execution"></a>Deaktivieren Sie die Ausführung des Skripts

Bei einem Limit für Skripts können Sie alle skriptausführung, deaktivieren, die Schritte, die zuvor sich verpflichtet, aktivieren Sie die Ausführung des externen Skripts im vornherein umkehren.

1. Führen Sie diesen Befehl aus, um festzulegen, in SQL Server Management Studio oder einem anderen Abfragetool, `external scripts enabled` auf 0 oder "false".

    ```sql
    EXEC sp_configure  'external scripts enabled', 0
    RECONFIGURE WITH OVERRIDE
    ```
2. Starten Sie den Datenbank-Engine-Dienst neu.

Nachdem Sie das Problem zu beheben, denken Sie daran, um die Ausführung des Skripts für die Instanz erneut zu aktivieren, wenn Sie zum Fortsetzen von R und Python-Skripts, in der Datenbank-Engine-Instanz unterstützen. Weitere Informationen finden Sie unter [skriptausführung aktivieren](../install/sql-machine-learning-services-windows-install.md#enable-script-execution)

## <a name="extend-functionality"></a>Erweitern der Funktionalität

Data Science führt häufig zu neuen Anforderungen für die Bereitstellung und Verwaltung. Für Datenanalysten ist es üblich, Open Source- und Drittanbieter-Pakete in benutzerdefinierte Lösungen zu nutzen. Einige dieser Pakete hat Abhängigkeiten von anderen Paketen, in diesem Fall möglicherweise müssen Sie bewerten und installieren mehrere Pakete aus, um Ihr Ziel zu erreichen.

Als ein DBA, der für eine Server-Ressource zuständig ist stellt eine unbekannte Herausforderung dar, wenn Sie beliebige R und Python-Paketen auf einem Produktionsserver bereitstellen. Vor dem Hinzufügen von Paketen, sollten Sie bewerten, ob die Funktionalität von das externe Paket wirklich erforderlich ist, wobei keine Entsprechung in der integrierten [Sprache "R"](r-libraries-and-data-types.md) und [Python-Bibliotheken](../python/python-libraries-and-data-types.md) installiert von SQL Server-Setup. 

Als Alternative zur Installation des Server-Paket, ein Data Scientist möglicherweise [erstellen und Ausführen von Lösungen auf einer externen Arbeitsstation](../r/set-up-a-data-science-client.md), Abrufen von Daten aus SQL Server, jedoch mit allen Analysis lokal ausgeführt auf der Arbeitsstation anstelle von auf dem Server selbst. 

Wenn Sie später feststellen, dass externe Bibliothek-Funktionen erforderlich sind, und stellen ein Risiko für Servervorgänge oder Daten als Ganzes nicht dar, können Sie über mehrere Methoden Pakete hinzufügen. In den meisten Fällen sind Administratorrechte erforderlich, Pakete mit SQL Server hinzufügen. Weitere Informationen finden Sie unter [Installieren von Python-Paketen in SQL Server](../python/install-additional-python-packages-on-sql-server.md) und [Installieren von R-Paketen in SQL Server](install-additional-r-packages-on-sql-server.md).

> [!NOTE]
> Für R-Pakete sind die serverweiten Administratorrechten nicht speziell für die Paketinstallation erforderlich, wenn Sie alternative Methoden zum verwenden. Finden Sie unter [Installieren von R-Paketen in SQL Server](install-additional-r-packages-on-sql-server.md) Details.

## <a name="monitoring-script-execution"></a>Überwachen der Ausführung des Skripts

R und Python-Skripts, die parallel [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] gestartet werden, indem die [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] Schnittstelle. Das Launchpad ist jedoch nicht die Ressourcen gesteuert oder separat überwacht, da es ist eine sichere Dienste von Microsoft, die Ressourcen entsprechend verwalten.

Externer Skripts, die unter dem Launchpad-Dienst ausgeführt werden mithilfe von verwaltet die [Windows-Auftragsobjekt](/windows/desktop/ProcThread/job-objects). Ein Auftragsobjekt ermöglicht es, Gruppen von Prozessen als Einheit zu verwalten. Jedes Objekt ist hierarchisch aufgebaut und steuert die Attribute aller zugeordneten Prozesse. Vorgänge für ein Auftragsobjekt wirken sich auf alle Prozesse aus, die dem Auftragsobjekt zugeordnet sind.

Daher sollten Sie daran denken, auch alle zugehörigen Prozesse beendet werden, wenn Sie einen Auftrag im Zusammenhang mit einem Objekt beenden müssen. Wenn Sie ein R-Skript ausführen, das einem Windows-Auftragsobjekt zugewiesen ist, und das Skript einen entsprechenden ODBC-Auftrag ausführt, der beendet werden muss, wird der übergeordnete Prozess des R-Skripts ebenfalls beendet.

Wenn Sie ein externes Skript, das parallelen Verarbeitung verwendet starten, verwaltet ein einzelnes Windows-Auftragsobjekt alle untergeordneten Prozesse.

Verwenden Sie die Funktion `IsProcessInJob`, um festzustellen, ob ein Prozess in einem Auftrag ausgeführt wird.

## <a name="next-steps"></a>Nächste Schritte

+ Überprüfen Sie die Konzepte und Komponenten von der [erweiterbarkeitsarchitektur](../concepts/extensibility-framework.md) und [Sicherheit](../concepts/security.md) Weitere Hintergrundinformationen.

+ Im Rahmen der Installation von Features, Sie möglicherweise bereits vertraut sein, mit der Endbenutzer Daten Steuerung des Zugriffs, aber wenn dies nicht der Fall, finden Sie unter [Gewähren von Benutzerberechtigungen für SQL Server Machine Learning](../security/user-permission.md) Details. 

+ Erfahren Sie, wie die Systemressourcen für rechenintensive Machine learning-Workloads angepasst. Weitere Informationen finden Sie unter [Gewusst wie: Erstellen eines Ressourcenpools](../administration/how-to-create-a-resource-pool.md).
