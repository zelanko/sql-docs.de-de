---
title: Benutzerdefinierte R-Funktionen unter Verwendung von rxExec
description: Erfahren Sie, wie Sie die Ausführung einer benutzerdefinierten R-Funktion auf einem Remoteserver veranschaulichen.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: b8f03c64dc86e6d23113f3a35ae669f216b66489
ms.sourcegitcommit: cfa04a73b26312bf18d8f6296891679166e2754d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2020
ms.locfileid: "92195152"
---
# <a name="run-custom-r-functions-on-sql-server-using-rxexec-sql-server-and-revoscaler-tutorial"></a>Ausführen von benutzerdefinierten R-Funktionen auf SQL Server mithilfe von rxExec (SQL Server- und RevoScaleR-Tutorial)
[!INCLUDE [SQL Server 2016 and later](../../includes/applies-to-version/sqlserver2016.md)]

Bei diesem Tutorial handelt es sich um das 14. Tutorial der [Tutorialreihe zu RevoScaleR](deepdive-data-science-deep-dive-using-the-revoscaler-packages.md). In diesem Tutorial erfahren Sie, wie Sie [RevoScaleR-Funktionen](/machine-learning-server/r-reference/revoscaler/revoscaler) mit SQL Server verwenden.

In diesem Tutorial verwenden Sie simulierte Daten, um die Ausführung einer benutzerdefinierten R-Funktion auf einem Remoteserver zu veranschaulichen.

Sie können benutzerdefinierte R-Funktionen im Kontext von SQL Server ausführen, indem Sie die Funktion über [rxExec](/machine-learning-server/r-reference/revoscaler/rxexec) übergeben. Dabei wird davon ausgegangen, dass alle für das Skript erforderlichen Bibliotheken auf dem Server installiert sind und diese Bibliotheken mit der R-Basisverteilung kompatibel sind. 

Die **rxExec**-Funktion in **RevoScaleR** bietet einen Mechanismus zum Ausführen beliebiger R-Skripts. Darüber hinaus kann **rxExec** Workloads explizit auf mehrere Kerne auf einem einzelnen Server verteilen und die Skalierung von Skripts erhöhen, die andernfalls auf die Ressourceneinschränkungen der nativen R-Engine beschränkt sind.

## <a name="prerequisites"></a>Voraussetzungen

+ [SQL Server Machine Learning Services (mit R)](../install/sql-machine-learning-services-windows-install.md) oder [SQL Server 2016 R Services (datenbankintern)](../install/sql-r-services-windows-install.md)
  
+ [Datenbankberechtigungen](../security/user-permission.md) und eine Benutzeranmeldung für SQL Server-Datenbank

+ [Eine Entwicklungsarbeitsstation mit den RevoScaleR-Bibliotheken](../r/set-up-a-data-science-client.md)

Die R-Verteilung auf der Clientarbeitsstation bietet ein integriertes **Rgui**-Tool, das Sie zum Ausführen des R-Skripts in diesem Tutorial verwenden können. Sie können auch eine IDE wie RStudio oder R Tools für Visual Studio verwenden.

## <a name="create-the-remote-compute-context"></a>Erstellen des Remotecomputekontexts

Führen Sie die folgenden R-Befehle auf einer Clientarbeitsstation aus. Wenn Sie z. B. den Befehl **Rgui** verwenden, starten Sie diesen von dem folgenden Speicherort aus: C:\Programme\Microsoft\R Client\R_SERVER\bin\x64\.

1. Geben Sie die Verbindungszeichenfolge für die SQL Server-Instanz an, in der die Berechnungen durchgeführt werden sollen. Der Server muss für die R-Integration konfiguriert sein. Der Datenbankname wird in dieser Übung nicht verwendet, die Verbindungszeichenfolge erfordert jedoch eine Datenbank. Wenn Sie über eine Test- oder Beispieldatenbank verfügen, können Sie diese verwenden.

    **Verwenden einer SQL-Anmeldung**

    ```R
    sqlConnString <- "Driver=SQL Server;Server=<SQL-Server-instance-name>; Database=<database-name>;Uid=<SQL-user-name>;Pwd=<password>"
    ```

    **Verwenden der Windows-Authentifizierung**

    ```R
    sqlConnString <- "Driver=SQL Server;Server=<SQL-Server-instance-name>;Database=<database-name>;Trusted_Connection=True"
    ```

2. Erstellen Sie einen Remotecomputekontext für die SQL Server-Instanz, auf die in der Verbindungszeichenfolge verwiesen wird.

    ```R
    sqlCompute <- RxInSqlServer(connectionString = sqlConnString)
    ```

3. Aktivieren Sie den Computekontext, und geben Sie dann die Objektdefinition als Bestätigungsschritt zurück. Die Eigenschaften des Computekontextobjekts sollten angezeigt werden.

    ```R
    rxSetComputeContext(sqlCompute)
    rxGetComputeContext()
    ```

## <a name="create-the-custom-function"></a>Erstellen der benutzerdefinierten Funktion

In dieser Übung erstellen Sie eine benutzerdefinierte R-Funktion, die ein klassisches Kasinospiel mit zwei Würfeln simuliert. Die folgenden Regeln legen fest, mit welchen Augenzahlen Sie gewinnen oder verlieren:

+ Wenn Sie beim ersten Wurf eine 7 oder 11 würfeln, haben Sie gewonnen.
+ Wenn Sie eine 2, 3 oder 12 würfeln, haben Sie verloren.
+ Wenn Sie eine 4, 5, 6, 8, 9 oder 10 würfeln, wird die gewürfelte Zahl zu Ihrem Point, und Sie würfeln weiter, bis Sie entweder noch einmal Ihren Point würfeln (dann gewinnen Sie) oder eine 7 würfeln, was bedeutet, dass Sie verlieren.

Das Spiel wird in R einfach simuliert, indem Sie eine benutzerdefinierte Funktion erstellen und diese anschließend mehrmals ausführen.

1.  Erstellen Sie die benutzerdefinierte Funktion mit dem folgenden R-Code:
  
    ```R
    rollDice <- function()
    {
        result <- NULL
        point <- NULL
        count <- 1
            while (is.null(result))
            {
                roll <- sum(sample(6, 2, replace=TRUE))
  
                if (is.null(point))
                { point <- roll }
                if (count == 1 && (roll == 7 || roll == 11))
                {  result <- "Win" }
                else if (count == 1 && (roll == 2 || roll == 3 || roll == 12))
                { result <- "Loss" }
                else if (count > 1 && roll == 7 )
                { result <- "Loss" }
                else if (count > 1 && point == roll)
                { result <- "Win" }
                else { count <- count + 1 }
            }
            result
    }
    ```
  
2.  Führen Sie die Funktion aus, um ein einzelnes Würfelspiel zu simulieren.
  
    ```R
    rollDice()
    ```
  
    Haben Sie gewonnen oder verloren?
  
Sie verfügen nun über ein operationales Skript. Sehen wir uns an, wie Sie die Funktion **rxExec** mehrmals ausführen können, um eine Simulation zu erstellen, die dabei hilft, die Wahrscheinlichkeit eines Gewinns zu bestimmen.

## <a name="pass-rolldice-in-rxexec"></a>Übergeben von rollDice() in rxExec

Um eine beliebige Funktion im Kontext einer SQL Server-Remoteinstanz auszuführen, rufen Sie die **rxExec**-Funktion auf.

1. Rufen Sie die benutzerdefinierte Funktion als Argument für **rxExec** und einige andere Parameter auf, die die Simulation ändern.
  
    ```R
    sqlServerExec <- rxExec(rollDice, timesToRun=20, RNGseed="auto")
    length(sqlServerExec)
    ```
  
    + Verwenden Sie das *timesToRun* -Argument, um anzugeben, wie oft die Funktion ausgeführt werden soll.  In diesem Fall würfeln Sie 20 Mal.
  
    + Die Argumente *RNGseed* und *RNGkind* können dazu verwendet werden, die Generierung von Zufallszahlen zu steuern. Wenn *RNGseed* auf **automatisch**festgelegt ist, wird ein paralleler Stream von Zufallszahlen auf jedem Worker initialisiert.
  
2. Die Funktion **rxExec** erstellt bei jeder Ausführung eine Liste mit einem Element, es passiert jedoch nicht viel, bis die Liste vollständig ist. Wenn alle Iterationen abgeschlossen sind, gibt die Zeile, die mit **length** beginnt, einen Wert zurück.
  
    Sie können anschließend den nächsten Schritt ausführen, um eine Zusammenfassung Ihrer Bilanz aus gewonnenen und verlorenen Spielen abzurufen.
  
3. Konvertieren Sie die zurückgegebene Liste mithilfe der **unlist** -Funktion von R zu einem Vektor, und fassen Sie die Ergebnisse mithilfe der **table** -Funktion zusammen.
  
    ```R
    table(unlist(sqlServerExec))
    ```
  
    Ihre Ergebnisse sollten in etwa wie folgt aussehen:
  
     *Loss  Win* *12  8*

## <a name="conclusion"></a>Zusammenfassung

Obwohl diese Übung einfach ist, veranschaulicht sie einen wichtigen Mechanismus zur Integration beliebiger R-Funktionen in R-Skripts, die auf SQL Server ausgeführt werden. Im Folgenden finden Sie eine Zusammenfassung der wichtigsten Voraussetzungen für diese Technik:

+ SQL Server muss für Machine Learning und die R-Integration konfiguriert werden: [SQL Server Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) mit der R-Funktion oder [SQL Server 2016 R Services (datenbankintern)](../install/sql-r-services-windows-install.md).

+ Die in der Funktion verwendeten Open-Source- oder Drittanbieterbibliotheken, einschließlich aller Abhängigkeiten, müssen auf SQL Server installiert sein. Weitere Informationen finden Sie unter [Installieren neuer R-Pakete](../package-management/install-additional-r-packages-on-sql-server.md).

+ Durch das Verschieben eines Skripts aus einer Entwicklungsumgebung in eine festgeschriebene Produktionsumgebung können Firewall- und Netzwerkbeschränkungen auftreten. Führen Sie sorgfältige Tests durch, um sicherzustellen, dass das Skript wie erwartet ausgeführt werden kann.

## <a name="next-steps"></a>Nächste Schritte

Ein komplexeres Beispiel für die Verwendung von **rxExec** finden Sie im folgenden Artikel: [Undifferenzierte Parallelität mit foreach und rxExec](https://blog.revolutionanalytics.com/2015/04/coarse-grain-parallelism-with-foreach-and-rxexec.html)