---
title: Verwalten und integrieren von Machine Learning-Workloads
description: Überprüfen Sie als SQL Server DBA die administrativen Aufgaben für die Bereitstellung eines Machine Learning R-und python-Subsystems in einer Datenbank-Engine-Instanz.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/10/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 705df9d06a7dbf4563df3670894351d15c0962a5
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2019
ms.locfileid: "68470098"
---
# <a name="manage-and-integrate-machine-learning-workloads-on-sql-server"></a>Verwalten und integrieren von Machine Learning-Workloads auf SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Dieser Artikel richtet sich an SQL Server Datenbankadministratoren, die für die Bereitstellung einer effizienten Data Science-Infrastruktur auf einem Server Asset zuständig sind, das mehrere Workloads unterstützt. Der Bereich für administrative Probleme, der für die Verwaltung von R-und python-Codeausführung relevant ist, wird in SQL Server Frames. 

## <a name="what-is-feature-integration"></a>Was ist die Funktionsintegration?

R und python Machine Learning werden von [SQL Server Machine Learning Services](../what-is-sql-server-machine-learning.md) als Erweiterung einer Instanz der Datenbank-Engine bereitgestellt. Die Integration erfolgt in erster Linie über die Sicherheitsschicht und die Datendefinitionssprache, die wie folgt zusammengefasst werden:

+ Gespeicherte Prozeduren sind mit der Möglichkeit ausgestattet, R-und Python-Code als Eingabeparameter zu akzeptieren. Entwickler und Datenanalysten können eine [gespeicherte System Prozedur](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql?view=sql-server-2017) verwenden oder eine benutzerdefinierte Prozedur erstellen, die Ihren Code umschließt.
+ T-SQL-Funktionen ( [Vorhersagen](https://docs.microsoft.com/sql/t-sql/queries/predict-transact-sql)), die ein zuvor trainiertes Datenmodell nutzen können. Diese Funktion ist über T-SQL verfügbar. Daher kann Sie auf einem System aufgerufen werden, auf dem nicht ausdrücklich die Machine Learning-Erweiterungen installiert sind.
+ Vorhandene Daten Bank Anmeldungen und rollenbasierte Berechtigungen umfassen die vom Benutzer aufgerufenen Skripts, die dieselben Daten verwenden. Als allgemeine Regel gilt: Wenn Benutzer nicht über eine Abfrage auf Daten zugreifen können, können Sie auch nicht über Skripts darauf zugreifen.

## <a name="feature-availability"></a>Funktions Verfügbarkeit

Die Integration von R und python wird durch eine Reihe von Schritten verfügbar. Der erste ist Setup, wenn Sie das Machine Learning Services Feature in eine Instanz der Datenbank-Engine [einschließen oder hinzufügen  ](../install/sql-machine-learning-services-windows-install.md) . Als nachfolgenden Schritt müssen Sie die externe Skripterstellung für die Datenbank-Engine-Instanz aktivieren (standardmäßig deaktiviert).

An diesem Punkt haben nur Datenbankadministratoren die volle Berechtigung zum Erstellen und Ausführen externer Skripts, zum Hinzufügen oder Löschen von Paketen und zum Erstellen von gespeicherten Prozeduren und anderen Objekten.

Allen anderen Benutzern muss die Berechtigung zum Ausführen beliebiger externer Skripts erteilt werden. Zusätzliche [Standarddaten Bank Berechtigungen](../security/user-permission.md) bestimmen, ob Benutzer Objekte erstellen, Skripts ausführen, serialisierte und trainierte Modelle nutzen können usw. 

## <a name="resource-allocation"></a>Ressourcen Zuordnung

Gespeicherte Prozeduren und T-SQL-Abfragen, die externe Verarbeitung aufrufen, verwenden die Ressourcen, die für den Standard Ressourcenpool verfügbar sind. Im Rahmen der Standardkonfiguration sind externe Prozesse wie R-und python-Sitzungen bis zu 20% des gesamten Arbeitsspeichers auf dem Host System zulässig. 

Wenn Sie die Resourcing-Bereitstellung durchführen möchten, können Sie den Standard Pool mit entsprechender Auswirkung auf Machine Learning-Workloads ändern, die auf diesem System ausgeführt werden.

Eine andere Möglichkeit besteht darin, einen benutzerdefinierten externen Ressourcenpool zu erstellen, um Sitzungen zu erfassen, die von bestimmten Programmen, Hosts oder Aktivitäten stammen, die in bestimmten Zeitintervallen auftreten. Weitere Informationen finden Sie unter [Ressourcenkontrolle zum Ändern von Ressourcen Ebenen für die R-und python-Ausführung](../administration/resource-governance.md) und [Erstellen eines Ressourcenpools](../administration/how-to-create-a-resource-pool.md) für Schritt-für-Schritt-Anleitungen.

## <a name="isolation-and-containment"></a>Isolation und Kapselung

Die Verarbeitungs Architektur ist so konzipiert, dass externe Skripts von der Verarbeitung von Kernmodulen isoliert werden. R-und python-Skripts werden unter Lokale workerkonten als separate Prozesse ausgeführt. Im Task-Manager können Sie R-und python-Prozesse überwachen, die unter einem lokalen Benutzerkonto mit geringen Berechtigungen ausgeführt werden, das sich vom SQL Server-Dienst Konto unterscheidet. 

Das Ausführen von R-und python-Prozessen in einzelnen Konten mit geringen Rechten bietet die folgenden Vorteile:

+ Isoliert die Kern-Engine-Prozesse von r-und python-Sitzungen. Sie können einen R-oder python-Prozess beenden, ohne die Hauptdaten Bank Vorgänge zu beeinträchtigen 

+ Verringert die Berechtigungen der externen Skript-Lauf Zeit Prozesse auf dem Host Computer.

Konten mit geringsten Rechten werden während des Setups erstellt und in einem Windows- *Benutzerkonto Pool* namens **sqlrusergroup**abgelegt. Standardmäßig ist dieser Gruppe die Berechtigung erteilt, ausführbare Dateien, Bibliotheken und integrierte Datasets im Programmordner für R und Python unter SQL Server zu verwenden. 

Als Datenbankadministrator können Sie mit SQL Server Datensicherheit angeben, wer über die Berechtigung zum Ausführen von Skripts verfügt, und dass die in Aufträgen verwendeten Daten unter den gleichen Sicherheitsrollen verwaltet werden, die den Zugriff über T-SQL-Abfragen steuern. Als Systemadministrator können Sie den **sqlrusergroup** -Zugriff auf vertrauliche Daten auf dem lokalen Server explizit verweigern, indem Sie ACLs erstellen.

>[!NOTE]
> Standardmäßig verfügt die **sqlrusergroup** nicht über einen Anmelde Namen oder Berechtigungen in SQL Server selbst. Sollten workerkonten einen Anmelde Namen für den Datenzugriff benötigen, müssen Sie ihn selbst erstellen. Ein Szenario, das speziell für die Erstellung eines Anmelde namens aufruft, ist die Unterstützung von Anforderungen von einem Skript zur Ausführung, für Daten oder Vorgänge auf der Datenbank-Engine-Instanz, wenn die Benutzeridentität ein Windows-Benutzer ist und die Verbindungs Zeichenfolge einen vertrauenswürdigen Benutzer angibt. Weitere Informationen finden Sie unter [Hinzufügen von sqlrusergroup als Datenbankbenutzer](../../advanced-analytics/security/create-a-login-for-sqlrusergroup.md).

## <a name="disable-script-execution"></a>Skriptausführung deaktivieren

Im Fall von endlos Skripts können Sie die gesamte Skriptausführung deaktivieren und die zuvor durchgeführten Schritte umkehren, um die Ausführung externer Skripts zu ermöglichen.

1. Führen Sie in SQL Server Management Studio oder einem anderen Abfrage Tool diesen Befehl aus `external scripts enabled` , um auf 0 oder false festzulegen.

    ```sql
    EXEC sp_configure  'external scripts enabled', 0
    RECONFIGURE WITH OVERRIDE
    ```
2. Starten Sie den Datenbank-Engine-Dienst neu.

Wenn Sie das Problem behoben haben, denken Sie daran, die Skriptausführung für die Instanz erneut zu aktivieren, wenn Sie die Unterstützung für R und python-Skripts für die Datenbank-Engine-Instanz fortsetzen möchten Weitere Informationen finden Sie unter [Aktivieren der Skriptausführung](../install/sql-machine-learning-services-windows-install.md#enable-script-execution) .

## <a name="extend-functionality"></a>Erweitern der Funktionalität

Data Science führt häufig zu neuen Anforderungen für die Paket Bereitstellung und-Verwaltung. Für einen Datenanalysten ist es gängige Praxis, Open Source-und Drittanbieter Pakete in benutzerdefinierten Lösungen zu nutzen. Einige dieser Pakete weisen Abhängigkeiten von anderen Paketen auf. in diesem Fall müssen Sie möglicherweise mehrere Pakete auswerten und installieren, um Ihr Ziel zu erreichen.

Als Datenbankadministrator, der für ein Server Objekt zuständig ist, stellt die Bereitstellung beliebiger R-und Python-Pakete auf einem Produktionsserver eine unbekannte Herausforderung dar Vor dem Hinzufügen von Paketen sollten Sie bewerten, ob die vom externen Paket bereitgestellte Funktionalität wirklich erforderlich ist, ohne dass es in der integrierten [R-Sprache](r-libraries-and-data-types.md) und den von SQL Server-Setup installierten Python- [Bibliotheken](../python/python-libraries-and-data-types.md) keine Entsprechung gibt. 

Als Alternative zur Installation des Server Pakets kann ein Daten Analyst möglicherweise [Lösungen auf einer externen Arbeitsstation erstellen und ausführen und](../r/set-up-a-data-science-client.md)Daten aus SQL Server abrufen, wobei alle Analysen lokal auf der Arbeitsstation statt auf dem Server ausgeführt werden. etabliert. 

Wenn Sie anschließend feststellen, dass externe Bibliotheksfunktionen erforderlich sind und kein Risiko für Server Vorgänge oder Daten als Ganzes darstellen, können Sie aus mehreren Methoden auswählen, um Pakete hinzuzufügen. In den meisten Fällen sind Administratorrechte erforderlich, um SQL Server Pakete hinzuzufügen. Weitere Informationen finden Sie unter [Installieren von Python-Paketen in SQL Server](../python/install-additional-python-packages-on-sql-server.md) und [Installieren von R-Paketen in SQL Server](install-additional-r-packages-on-sql-server.md).

> [!NOTE]
> Für R-Pakete sind Server Administratorrechte für die Paketinstallation nicht besonders erforderlich, wenn Sie alternative Methoden verwenden. Weitere Informationen finden Sie [unter Installieren von R-Paketen in SQL Server](install-additional-r-packages-on-sql-server.md) .

## <a name="monitoring-script-execution"></a>Überwachen der Skriptausführung

Skripts, die in [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] ausgeführt werden, werden von der [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] -Schnittstelle gestartet. Das Launchpad wird jedoch nicht separat verwaltet oder überwacht, da es sich um einen von Microsoft bereitgestellten sicheren Dienst handelt, der Ressourcen entsprechend verwaltet.

Externe Skripts, die unter dem Launchpad-Dienst ausgeführt werden, werden mithilfe des [Windows-Auftrags Objekts](/windows/desktop/ProcThread/job-objects)verwaltet. Ein Auftragsobjekt ermöglicht es, Gruppen von Prozessen als Einheit zu verwalten. Jedes Objekt ist hierarchisch aufgebaut und steuert die Attribute aller zugeordneten Prozesse. Vorgänge für ein Auftragsobjekt wirken sich auf alle Prozesse aus, die dem Auftragsobjekt zugeordnet sind.

Daher sollten Sie daran denken, auch alle zugehörigen Prozesse beendet werden, wenn Sie einen Auftrag im Zusammenhang mit einem Objekt beenden müssen. Wenn Sie ein R-Skript ausführen, das einem Windows-Auftragsobjekt zugewiesen ist, und das Skript einen entsprechenden ODBC-Auftrag ausführt, der beendet werden muss, wird der übergeordnete Prozess des R-Skripts ebenfalls beendet.

Wenn Sie ein externes Skript starten, das die parallele Verarbeitung verwendet, verwaltet ein einzelnes Windows-Auftrags Objekt alle parallelen untergeordneten Prozesse.

Verwenden Sie die Funktion `IsProcessInJob`, um festzustellen, ob ein Prozess in einem Auftrag ausgeführt wird.

## <a name="next-steps"></a>Nächste Schritte

+ Weitere Hintergrundinformationen finden Sie in den Konzepten und Komponenten der [Erweiterbarkeits Architektur](../concepts/extensibility-framework.md) und der [Sicherheit](../concepts/security.md) .

+ Im Rahmen der Funktions Installation sind Sie möglicherweise bereits mit der Datenzugriffs Steuerung für Endbenutzer vertraut, aber falls nicht, finden Sie weitere Informationen unter [Erteilen von Benutzerberechtigungen für SQL Server Machine Learning](../security/user-permission.md) . 

+ Erfahren Sie, wie Sie die Systemressourcen für berechnungsintensive Machine Learning-Workloads anpassen. Weitere Informationen finden Sie unter [How to Create a Resource Pool (Erstellen eines Ressourcenpools](../administration/how-to-create-a-resource-pool.md)).
