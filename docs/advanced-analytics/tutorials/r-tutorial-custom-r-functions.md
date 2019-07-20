---
title: Ausführen benutzerdefinierter R-Funktionen auf SQL Server mithilfe von revoscaler rxexec
description: 'Tutorial: Exemplarische Vorgehensweise zum Ausführen eines benutzerdefinierten R-Skripts auf SQL Server mithilfe von revoscaler-Funktionen.'
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: cfbd5417106d8e6ddd0ab5c76c2c05dae07c0605
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2019
ms.locfileid: "68345982"
---
# <a name="run-custom-r-functions-on-sql-server-using-rxexec"></a>Ausführen benutzerdefinierter R-Funktionen auf SQL Server mithilfe von rxexec
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Sie können benutzerdefinierte R-Funktionen im Kontext von SQL Server ausführen, indem Sie Ihre Funktion über [rxexec](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxexec)übergeben. dabei wird davon ausgegangen, dass alle Bibliotheken, die Ihr Skript erfordert, auch auf dem Server installiert sind und diese Bibliotheken mit der basisverteilung von R kompatibel sind. 

Die **rxexec** -Funktion in **revoscaler** bietet einen Mechanismus zum Ausführen beliebiger R-Skripts, die Sie benötigen. Darüber hinaus kann **rxexec** die Arbeit explizit auf mehrere Kerne auf einem einzelnen Server verteilen und so das Skalieren zu Skripts hinzufügen, die andernfalls auf die Ressourceneinschränkungen der systemeigenen R-Engine beschränkt sind.

In diesem Tutorial verwenden Sie simulierte Daten, um die Ausführung einer benutzerdefinierten R-Funktion, die auf einem Remote Server ausgeführt wird, zu veranschaulichen.

## <a name="prerequisites"></a>Vorraussetzungen

+ [SQL Server 2017 Machine Learning Services (mit R)](../install/sql-machine-learning-services-windows-install.md) oder [SQL Server 2016 R Services (in-Database)](../install/sql-r-services-windows-install.md)
  
+ [Daten Bank Berechtigungen](../security/user-permission.md) und eine SQL Server Datenbank-Benutzeranmeldung

+ [Eine entwicklungsarbeits Station mit den revoscaler-Bibliotheken](../r/set-up-a-data-science-client.md)

Die r-Verteilung auf der Client Arbeitsstation bietet ein integriertes **rgui** -Tool, das Sie zum Ausführen des r-Skripts in diesem Tutorial verwenden können. Sie können auch eine IDE wie rstudio oder R Tools für Visual Studio verwenden.

## <a name="create-the-remote-compute-context"></a>Erstellen des remotecomputekontexts

Führen Sie die folgenden R-Befehle auf einer Client Arbeitsstation aus. Wenn Sie z. b. **rgui**verwenden, starten Sie Sie von diesem Speicherort: C:\programme\microsoft\r Client\R_SERVER\bin\x64\.

1. Geben Sie die Verbindungs Zeichenfolge für die SQL Server Instanz an, in der Berechnungen ausgeführt werden. Der Server muss für die R-Integration konfiguriert sein. Der Datenbankname wird in dieser Übung nicht verwendet, die Verbindungs Zeichenfolge erfordert jedoch eine. Wenn Sie über eine Test-oder Beispieldatenbank verfügen, können Sie diese verwenden.

    **Verwenden einer SQL-Anmeldung**

    ```R
    sqlConnString <- "Driver=SQL Server;Server=<SQL-Server-instance-name>; Database=<database-name>;Uid=<SQL-user-name>;Pwd=<password>"
    ```

    **Verwenden der Windows-Authentifizierung**

    ```R
    sqlConnString <- "Driver=SQL Server;Server=<SQL-Server-instance-name>;Database=<database-name>;Trusted_Connection=True"
    ```

2. Erstellen Sie einen remotecomputekontext für die SQL Server Instanz, auf die in der Verbindungs Zeichenfolge verwiesen wird

    ```R
    sqlCompute <- RxInSqlServer(connectionString = sqlConnString)
    ```

3. Aktivieren Sie den computekontext, und geben Sie dann die Objektdefinition als Bestätigungs Schritt zurück. Die Eigenschaften des computecontext-Objekts sollten angezeigt werden.

    ```R
    rxSetComputeContext(sqlCompute)
    rxGetComputeContext()
    ```

## <a name="create-the-custom-function"></a>Erstellen der benutzerdefinierten Funktion

In dieser Übung erstellen Sie eine benutzerdefinierte R-Funktion, die ein gemeinsames Kasino simuliert, das aus einem Rollenpaar besteht. Die Regeln des Spiels bestimmen das Ergebnis von Gewinn oder Verlust:

+ Wenn Sie ein 7-oder 11-Rollback durchführen, gewinnen Sie einen Gewinn.
+ Rollup 2, 3 oder 12, gehen verloren.
+ Führen Sie einen Rollup für einen Wert von 4, 5, 6, 8, 9 oder 10 durch, und setzen Sie den Vorgang fort, bis Sie entweder einen erneuten Rollback für den Punkt (in diesem Fall "Win") oder ein Rollback für 7 ausführen. in diesem Fall verlieren Sie den Vorgang.

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
  
2.  Simulieren Sie ein einzelnes Würfelspiel, indem Sie die-Funktion ausführen.
  
    ```R
    rollDice()
    ```
  
    Haben Sie gewonnen oder verloren?
  
Nun, da Sie ein Betriebs Skript haben, sehen wir uns an, wie Sie **rxexec** verwenden können, um die Funktion mehrmals auszuführen, um eine Simulation zu erstellen, mit der die Wahrscheinlichkeit eines Gewinns bestimmt wird.

## <a name="pass-rolldice-in-rxexec"></a>Übergeben von rolldice () in rxexec

Um eine beliebige Funktion im Kontext einer Remote SQL Server auszuführen, müssen Sie die **rxexec** -Funktion aufzurufen.

1. Nennen Sie die benutzerdefinierte Funktion als Argument für **rxexec**sowie andere Parameter, die die Simulation ändern.
  
    ```R
    sqlServerExec <- rxExec(rollDice, timesToRun=20, RNGseed="auto")
    length(sqlServerExec)
    ```
  
    + Verwenden Sie das *timesToRun* -Argument, um anzugeben, wie oft die Funktion ausgeführt werden soll.  In diesem Fall würfeln Sie 20 Mal.
  
    + Die Argumente *RNGseed* und *RNGkind* können dazu verwendet werden, die Generierung von Zufallszahlen zu steuern. Wenn *RNGseed* auf **automatisch**festgelegt ist, wird ein paralleler Stream von Zufallszahlen auf jedem Worker initialisiert.
  
2. Die Funktion **rxExec** erstellt bei jeder Ausführung eine Liste mit einem Element, es passiert jedoch nicht viel, bis die Liste vollständig ist. Wenn alle Iterationen vollständig sind, gibt die Zeile, die mit **length** beginnt, einen Wert zurück.
  
    Sie können anschließend den nächsten Schritt ausführen, um eine Zusammenfassung Ihrer Bilanz aus gewonnenen und verlorenen Spielen abzurufen.
  
3. Konvertieren Sie die zurückgegebene Liste mithilfe der **unlist** -Funktion von R zu einem Vektor, und fassen Sie die Ergebnisse mithilfe der **table** -Funktion zusammen.
  
    ```R
    table(unlist(sqlServerExec))
    ```
  
    Ihre Ergebnisse sollten in etwa wie folgt aussehen:
  
     *Verlust gewinnen* *12 8*

## <a name="conclusion"></a>Schlussbemerkung

Obwohl diese Übung einfach ist, veranschaulicht Sie einen wichtigen Mechanismus zur Integration beliebiger r-Funktionen in R-Skripts, die auf SQL Server ausgeführt werden. Zusammenfassen der wichtigen Punkte, die diese Technik ermöglichen:

+ SQL Server müssen für die Machine Learning-und R-Integration konfiguriert werden: [SQL Server 2017 Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) mit der R-Funktion oder [SQL Server 2016 R Services (in-Database)](../install/sql-r-services-windows-install.md).

+ Open-Source-oder Drittanbieterbibliotheken, die in ihrer Funktion verwendet werden, einschließlich aller Abhängigkeiten, müssen auf SQL Server installiert werden. Weitere Informationen finden Sie unter [Installieren neuer R-Pakete](../r/install-additional-r-packages-on-sql-server.md).

+ Durch das Verschieben eines Skripts aus einer Entwicklungsumgebung in eine gehärtete Produktionsumgebung können Firewall-und Netzwerk Einschränkungen eingeführt werden. Testen Sie sorgfältig, um sicherzustellen, dass das Skript wie erwartet ausgeführt werden kann.

## <a name="next-steps"></a>Nächste Schritte

Ein komplexeres Beispiel für die Verwendung von **rxexec**finden Sie in diesem Artikel: [Grobe Parallelitäts Parallelität mit foreach und rxexec](https://blog.revolutionanalytics.com/2015/04/coarse-grain-parallelism-with-foreach-and-rxexec.html)
