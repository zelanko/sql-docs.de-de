---
title: Schnellstart zum Überprüfen von R ist in SQL Server vorhanden
description: Schnellstart zum Überprüfen, ob R und Machine Learning Services in SQL Server vorhanden sind.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
ms.openlocfilehash: 951ffc07a32434b2f8d333140445f12c2971b811
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2019
ms.locfileid: "68470614"
---
# <a name="quickstart-verify-r-exists-in-sql-server"></a>Schnellstart: Überprüfen der Verfügbarkeit von R in SQL Server 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

SQL Server beinhaltet die Unterstützung von R-Sprachen für Data Science Analysen auf Residenten SQL Server Daten. Das r-Skript kann aus Open Source-r-Funktionen, r-Bibliotheken von Drittanbietern oder integrierten Microsoft R-Bibliotheken wie [revoscaler](../r/revoscaler-overview.md) für Predictive Analytics skaliert bestehen.

Die Skriptausführung erfolgt mithilfe gespeicherter Prozeduren, wobei eine der folgenden Ansätze verwendet wird:

+ Integrierte gespeicherte Prozedur [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) , wobei R-Skript in als Eingabeparameter übergeben wird.
+ Wrappen Sie das R-Skript in einer von Ihnen erstellten [benutzerdefinierten gespeicherten Prozedur](sqldev-in-database-r-for-sql-developers.md) .

In dieser Schnellstartanleitung überprüfen Sie, ob [SQL Server 2017 Machine Learning Services](../what-is-sql-server-machine-learning.md) oder [SQL Server 2016 R Services](../r/sql-server-r-services.md) installiert und konfiguriert ist.

## <a name="prerequisites"></a>Vorraussetzungen

Diese Übung erfordert Zugriff auf eine Instanz von SQL Server mit einer der folgenden bereits installierten:

+ [SQL Server 2017 Machine Learning Services](../install/sql-machine-learning-services-windows-install.md)mit installierter R-Sprache
+ [SQL Server 2016 R-Dienste](../install/sql-r-services-windows-install.md)

Ihre SQL Server Instanz kann sich auf einem virtuellen Azure-Computer oder lokal befinden. Beachten Sie, dass das Feature für die externe Skripterstellung standardmäßig deaktiviert ist. Daher müssen Sie möglicherweise [externe Skripterstellung aktivieren](../install/sql-machine-learning-services-windows-install.md#bkmk_enableFeature) und überprüfen, ob **SQL Server-Launchpad-Dienst** ausgeführt wird, bevor Sie beginnen.

Außerdem benötigen Sie ein Tool zum Ausführen von SQL-Abfragen. Sie können die R-Skripts mit einem beliebigen Daten Bank Verwaltungs-oder Abfrage Tool ausführen, solange eine Verbindung mit einer SQL Server Instanz hergestellt und eine T-SQL-Abfrage oder eine gespeicherte Prozedur ausgeführt werden kann. In diesem Schnellstart wird [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms)verwendet.

## <a name="verify-r-exists"></a>Überprüfen von R vorhanden

Sie können überprüfen, ob Machine Learning Services (mit R) für Ihre SQL Server Instanz aktiviert ist und welche Version von R installiert ist. Führen Sie die folgenden Schritte aus.

1. Öffnen Sie SQL Server Management Studio, und stellen Sie eine Verbindung mit Ihrer SQL Server Instanz her

2. Führen Sie den folgenden Code aus. 

    ```SQL
    EXECUTE sp_execute_external_script
    @language =N'R',
    @script=N'print(version)';
    GO
    ```

3. Die R `print` -Funktion gibt die Version an das Fenster **Meldungen** zurück. In der folgenden Beispielausgabe sehen Sie, dass SQL Server in diesem Fall R-Version 3.3.3 installiert hat.

    **Ergebnisse**

    ```text
    platform       x86_64-w64-mingw32          
    arch           x86_64                      
    os             mingw32                     
    system         x86_64, mingw32             
    status                                     
    major          3                           
    minor          3.3                         
    year           2017                        
    month          03                          
    day            06                          
    svn rev        72310                       
    language       R                           
    version.string R version 3.3.3 (2017-03-06)
    nickname       Another Canoe               
    ```

Wenn Sie von dieser Abfrage Fehler erhalten, sollten Sie alle Installationsprobleme ausschließen. Die Konfiguration nach der Installation ist erforderlich, um die Verwendung externer Codebibliotheken zu aktivieren. Weitere Informationen finden Sie unter [Installieren von SQL Server 2017 Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) oder [Installieren von SQL Server 2016 R Services](../install/sql-r-services-windows-install.md). Stellen Sie auch sicher, dass der Launchpad-Dienst ausgeführt wird.

Je nach Umgebung kann es erforderlich sein, dass Sie die R-Workerkonten für die Verbindung mit SQL Server aktivieren, zusätzliche Netzwerkbibliotheken installieren, Remotecodeausführung zulassen oder die Instanz neu starten, nachdem alles konfiguriert wurde. Weitere Informationen finden Sie unter [FAQ zu Installation und Upgrade von R Services](../r/upgrade-and-installation-faq-sql-server-r-services.md).

## <a name="list-r-packages"></a>Auflisten von R-Paketen

Microsoft stellt eine Reihe von R-Paketen bereit, die mit Machine Learning Services in Ihrer SQL Server Instanz vorinstalliert sind. Führen Sie die folgenden Schritte aus, um eine Liste der installierten R-Pakete anzuzeigen, einschließlich Version, Abhängigkeiten, Lizenz und Bibliotheks Pfadinformationen.

1. Führen Sie das folgende Skript auf Ihrer SQL Server Instanz aus.

    ```SQL
    EXECUTE sp_execute_external_script @language = N'R'
    , @script = N'
    OutputDataSet <- data.frame(installed.packages()[,c("Package", "Version", "Depends", "License", "LibPath")]);'
    WITH result sets((Package NVARCHAR(255), Version NVARCHAR(100), Depends NVARCHAR(4000)
        , License NVARCHAR(1000), LibPath NVARCHAR(2000)));
    ```

2. Die Ausgabe erfolgt `installed.packages()` in R und wird als Resultset zurückgegeben.

    **Ergebnisse**

    ![Installierte Pakete in R](./media/rsql-installed-packages.png)

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie bestätigt haben, dass Ihre Instanz für die Arbeit mit r bereit ist, sollten Sie sich einen genaueren Blick auf die grundlegende R-Interaktion machen.

> [!div class="nextstepaction"]
> [Schnellstart: "Hello World" R-Skript in SQL Server](quickstart-r-run-using-tsql.md)
