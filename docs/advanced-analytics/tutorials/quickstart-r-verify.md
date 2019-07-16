---
title: Schnellstart für die Überprüfung von R ist in SQL Server vorhanden.
description: Schnellstart für das sicherstellen, dass R und Machine Learning Services in SQL Server vorhanden sind.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/04/2019
ms.topic: quickstart
author: dphansen
ms.author: davidph
ms.openlocfilehash: f294f5f12e3efd734d1e54ace3041702c39d390a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67961967"
---
# <a name="quickstart-verify-r-exists-in-sql-server"></a>Schnellstart: Überprüfen der Verfügbarkeit von R in SQL Server 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server umfasst die Unterstützung der Sprache R für Data Science-Analyse in residenten SQL Server-Daten. Ihr R-Skript kann der Open-Source-R-Funktionen, die R-Bibliotheken von Drittanbietern oder die integrierte Microsoft-R-Bibliotheken bestehen, z. B. [RevoScaleR](../r/revoscaler-overview.md) für predictive Analytics nach Maß.

Ausführung des Skripts wird mithilfe von gespeicherten Prozeduren, die mit einem der folgenden Methoden:

+ Integrierte [Sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) gespeicherte Prozedur, die R-Skript im als Eingabeparameter übergeben.
+ Umschließen von R-Skript in einem [benutzerdefinierte gespeicherte Prozedur](sqldev-in-database-r-for-sql-developers.md) , die Sie erstellen.

In diesem Schnellstart werden Sie sicherstellen, dass [SQL Server 2017-Machine Learning Services](../what-is-sql-server-machine-learning.md) oder [SQL Server 2016 R Services](../r/sql-server-r-services.md) installiert und konfiguriert ist.

## <a name="prerequisites"></a>Vorraussetzungen

In dieser Übung erfordert Zugriff auf eine Instanz von SQL Server mit einem der folgenden bereits installiert:

+ [SQL Server 2017-Machine Learning Services](../install/sql-machine-learning-services-windows-install.md), mit der installierten R-Sprache
+ [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md)

Ihre SQL Server-Instanz kann in einer Azure-VM oder lokal sein. Machen Sie sich bewusst, dass das Feature "external Skripterstellung" standardmäßig deaktiviert ist. Sie müssen möglicherweise [aktivieren externer Skripts](../install/sql-machine-learning-services-windows-install.md#bkmk_enableFeature) und überprüfen Sie, ob **SQL Server Launchpad-Dienst** ausgeführt wird, bevor Sie beginnen.

Sie benötigen außerdem ein Tool für die Ausführung von SQL-Abfragen. Sie alle datenbankverwaltung mit R-Skripts ausführen oder Tool Abfragen, solange es eine Verbindung mit SQL Server-Instanz herstellen kann, und führen Sie eine T-SQL-Abfrage oder gespeicherte Prozedur. Dieser Schnellstart verwendet [SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms).

## <a name="verify-r-exists"></a>Stellen Sie sicher, dass die R vorhanden ist.

Sie können bestätigen, dass Machine Learning Services (mit R) aktiviert ist, für Ihre SQL Server-Instanz und welche Version von R installiert ist. Führen Sie die folgenden Schritte aus.

1. Öffnen Sie SQL Server Management Studio, und Verbinden mit Ihrer SQL Server-Instanz.

2. Führen Sie den folgenden Code ein. 

    ```SQL
    EXECUTE sp_execute_external_script
    @language =N'R',
    @script=N'print(version)';
    GO
    ```

3. Die R `print` Funktionsergebnis ist die Version, die **Nachrichten** Fenster. In der folgenden Beispielausgabe sehen Sie, dass SQL Server in diesem Fall R Version 3.3.3 installiert sein.

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

Wenn Sie aus dieser Abfrage Fehler erhalten, Regel, die Sie alle Probleme bei der Installation. Konfiguration nach der Installation ist erforderlich, um die Verwendung externer Codebibliotheken zu aktivieren. Finden Sie unter [Installieren von SQL Server 2017-Machine Learning-Dienste](../install/sql-machine-learning-services-windows-install.md) oder [Installieren von SQL Server 2016 R Services](../install/sql-r-services-windows-install.md). Ebenso, stellen Sie sicher, dass der Launchpad-Dienst ausgeführt wird.

Je nach Umgebung kann es erforderlich sein, dass Sie die R-Workerkonten für die Verbindung mit SQL Server aktivieren, zusätzliche Netzwerkbibliotheken installieren, Remotecodeausführung zulassen oder die Instanz neu starten, nachdem alles konfiguriert wurde. Weitere Informationen finden Sie unter [R Services – Installation und Upgrade – häufig gestellte Fragen](../r/upgrade-and-installation-faq-sql-server-r-services.md).

## <a name="list-r-packages"></a>Liste von R-Pakete

Microsoft bietet eine Anzahl von R-Pakete vorinstalliert mit Machine Learning-Dienste in Ihrer SQL Server-Instanz. Führen Sie zum Anzeigen einer Liste von der, die r Pakete installiert werden, einschließlich Version, Abhängigkeiten, Lizenz und Pfadinformationen Bibliothek, die folgenden Schritte aus.

1. Führen Sie das folgende Skript für Ihre SQL Server-Instanz.

    ```SQL
    EXECUTE sp_execute_external_script @language = N'R'
    , @script = N'
    OutputDataSet <- data.frame(installed.packages()[,c("Package", "Version", "Depends", "License", "LibPath")]);'
    WITH result sets((Package NVARCHAR(255), Version NVARCHAR(100), Depends NVARCHAR(4000)
        , License NVARCHAR(1000), LibPath NVARCHAR(2000)));
    ```

2. Die Ausgabe stammt aus `installed.packages()` in R und als Resultset zurückgegebenen.

    **Ergebnisse**

    ![Installierte Pakete in R](./media/rsql-installed-packages.png)

## <a name="next-steps"></a>Nächste Schritte

Nun, da Sie bestätigt haben, dass die Instanz mit R arbeiten kann, nehmen Sie einen genaueren Blick auf eine grundlegende R-Interaktion.

> [!div class="nextstepaction"]
> [Schnellstart: "Hello World"-R-Skript in SQL Server](quickstart-r-run-using-tsql.md)
