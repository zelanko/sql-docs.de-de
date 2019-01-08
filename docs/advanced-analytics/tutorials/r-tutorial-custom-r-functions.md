---
title: Ausführen von benutzerdefinierten R-Funktionen in SQL Server mithilfe von RevoScaleR RxExec - SQL Server-Machine Learning
description: Exemplarische Vorgehensweise im Lernprogramm zum Ausführen von benutzerdefinierten R-Skripts in SQL Server mithilfe der RevoScaleR-Funktionen.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/27/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 90790c2b96843ea1821b8b4ed05052a7611cdf74
ms.sourcegitcommit: 33712a0587c1cdc90de6dada88d727f8623efd11
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2018
ms.locfileid: "53596441"
---
# <a name="run-custom-r-functions-on-sql-server-using-rxexec"></a>Ausführen von benutzerdefinierten R-Funktionen in SQL Server mithilfe von rxExec
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Sie können benutzerdefinierte R-Funktionen im Kontext von SQL Server ausführen, übergeben Sie die Funktion über [RxExec](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxexec), vorausgesetzt, dass alle Bibliotheken, die Ihr Skript muss ebenfalls auf dem Server installiert und diese Bibliotheken kompatibel mit der Basis sind Verteilung von R. 

Die **RxExec** -Funktion in **RevoScaleR** bietet einen Mechanismus für die Ausführung eines R-Skripts, die Sie benötigen. Darüber hinaus **RxExec** kann explizit Verteilen von Arbeit auf mehrere Kerne in einem einzelnen Server, Skripts, die andernfalls die ressourceneinschränkungen der nativen R-Engine auf sind Skalierung hinzugefügt.

In diesem Tutorial verwenden Sie die simulierte Daten, um die Ausführung einer benutzerdefinierten R-Funktion zu veranschaulichen, die auf einem Remoteserver ausgeführt wird.

## <a name="prerequisites"></a>Erforderliche Komponenten

+ [SQL Server 2017-Machine-Learning-Dienste (mit R)](../install/sql-machine-learning-services-windows-install.md) oder [SQL Server 2016 R Services (Datenbankintern)](../install/sql-r-services-windows-install.md)
  
+ [Datenbankberechtigungen](../security/user-permission.md) und eine SQL Server-Datenbank-Benutzeranmeldung

+ [Eine Arbeitsstation mit den RevoScaleR-Bibliotheken](../r/set-up-a-data-science-client.md)

Die R-Distribution auf der Clientarbeitsstation bietet eine integrierte **Rgui** Tool, das Sie zum Ausführen des R-Skripts in diesem Tutorial verwenden können. Sie können auch eine IDE wie RStudio oder R-Tools für Visual Studio verwenden.

## <a name="create-the-remote-compute-context"></a>Erstellen Sie im remotecomputekontext

Führen Sie die folgenden R-Befehle auf einer Clientarbeitsstation ein. Verwenden Sie z. B. **Rgui**, starten Sie ihn von diesem Speicherort: C:\Programme\Microsoft Files\Microsoft\R Client\R_SERVER\bin\x64\.

1. Geben Sie die Verbindungszeichenfolge für SQL Server-Instanz, in dem Berechnungen ausgeführt werden. Der Server muss für die R-Integration konfiguriert werden. Der Name der Datenbank wird in dieser Übung nicht verwendet, aber die Verbindungszeichenfolge muss eine. Wenn Sie eine Test- oder Sample-Datenbank verfügen, können Sie, die verwenden.

    **Verwenden einer SQL-Anmeldung**

    ```R
    sqlConnString <- "Driver=SQL Server;Server=<SQL-Server-instance-name>; Database=<database-name>;Uid=<SQL-user-name>;Pwd=<password>"
    ```

    **Verwenden der Windows-Authentifizierung**

    ```R
    sqlConnString <- "Driver=SQL Server;Server=<SQL-Server-instance-name>;Database=<database-name>;Trusted_Connection=True"
    ```

2. Erstellen Sie einen remotecomputekontext mit der SQL Server-Instanz, die in der Verbindungszeichenfolge verwiesen wird.

    ```R
    sqlCompute <- RxInSqlServer(connectionString = sqlConnString)
    ```

3. Aktivieren Sie den computekontext, und dann zurück der Objektdefinition als Bestätigungsschritt zur. Daraufhin sollte die Eigenschaften der computekontext-Objekt.

    ```R
    rxSetComputeContext(sqlCompute)
    rxGetComputeContext()
    ```

## <a name="create-the-custom-function"></a>Die benutzerdefinierte Funktion erstellen

In dieser Übung erstellen Sie eine benutzerdefinierte R-Funktion, die eine allgemeine Casino bestehend aus parallelen Würfeln simuliert. Die Regeln des Spiels bestimmen ein Ergebnisses Gewinn oder Verlust:

+ Eine 7 oder 11 beim ersten Wurf zurücksetzen, Sie gewonnen haben.
+ Zurücksetzen von 2, 3 oder 12, Sie verlieren.
+ Zurücksetzen einer 4, 5, 6, 8, 9 oder 10, wird diese Zahl den Punkt, und Sie Würfeln weiter, bis Sie sich, die entweder Zurücksetzen noch einmal Ihren Point (in diesem Fall Sie gewinnen) oder ein Rollback auszuführen, die eine 7, in dem Sie Fall, verlieren.

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
  
2.  Simulieren Sie ein einzelnes Spiel Würfeln, indem Sie Ausführung der Funktion.
  
    ```R
    rollDice()
    ```
  
    Haben Sie gewonnen oder verloren?
  
Nun, da Sie ein operational Skript haben, sehen wir uns an Informationen zur Verwendung **RxExec** zum Ausführen der Funktion mehrere Male auf, um eine Simulation zu erstellen, die dabei hilft, die Wahrscheinlichkeit eines Gewinns zu bestimmen.

## <a name="pass-rolldice-in-rxexec"></a>Übergeben Sie rollDice() rxExec

Um eine beliebige Funktion im Kontext von einem Remotecomputer mit SQL Server auszuführen, rufen Sie die **RxExec** Funktion.

1. Rufen Sie die benutzerdefinierte Funktion als Argument an **RxExec**zusammen mit anderen Parametern, die die Simulation zu ändern.
  
    ```R
    sqlServerExec <- rxExec(rollDice, timesToRun=20, RNGseed="auto")
    length(sqlServerExec)
    ```
  
    + Verwenden Sie das *timesToRun* -Argument, um anzugeben, wie oft die Funktion ausgeführt werden soll.  In diesem Fall würfeln Sie 20 Mal.
  
    + Die Argumente *RNGseed* und *RNGkind* können dazu verwendet werden, die Generierung von Zufallszahlen zu steuern. Wenn *RNGseed* auf **automatisch**festgelegt ist, wird ein paralleler Stream von Zufallszahlen auf jedem Worker initialisiert.
  
2. Die Funktion **rxExec** erstellt bei jeder Ausführung eine Liste mit einem Element, es passiert jedoch nicht viel, bis die Liste vollständig ist. Wenn alle Iterationen abgeschlossen sind, die Zeile, beginnend mit **Länge** gibt einen Wert zurück.
  
    Sie können anschließend den nächsten Schritt ausführen, um eine Zusammenfassung Ihrer Bilanz aus gewonnenen und verlorenen Spielen abzurufen.
  
3. Konvertieren Sie die zurückgegebene Liste mithilfe der **unlist** -Funktion von R zu einem Vektor, und fassen Sie die Ergebnisse mithilfe der **table** -Funktion zusammen.
  
    ```R
    table(unlist(sqlServerExec))
    ```
  
    Ihre Ergebnisse sollten in etwa wie folgt aussehen:
  
     *Verlust – Gewinn* *12 8*

## <a name="conclusion"></a>Schlussbemerkung

Obwohl in dieser Übung stark Vereinfachend ist, wird einen wichtigen Mechanismus für die Integration von beliebiger R-Funktionen in R-Skript, die unter SQL Server veranschaulicht. Die wichtigsten Punkte zusammengefasst, die diese Technik zu ermöglichen:

+ SQL Server muss für Machine Learning und R-Integration konfiguriert werden: [SQL Server 2017-Machine Learning Services](../install/sql-machine-learning-services-windows-install.md) mit der R-Funktion oder [SQL Server 2016 R Services (Datenbankintern)](../install/sql-r-services-windows-install.md).

+ Open Source- oder Drittanbieter-Bibliotheken, die in Ihrer Funktion, einschließlich der Abhängigkeiten, verwendet, müssen auf SQL Server installiert werden. Weitere Informationen finden Sie unter [Installieren neuer R-Pakete](../r/install-additional-r-packages-on-sql-server.md).

+ Verschieben von Skripts aus einer bereitstellungsumgebung in einer mit verstärkter Sicherheit produktionsumgebung kann Einschränkungen für Firewall- und Netzwerkeinstellungen einführen. Testen Sie sorgfältig, um sicherzustellen, dass das Skript wie erwartet ausgeführt werden kann.

## <a name="next-steps"></a>Nächste Schritte

Ein komplexeres Beispiel der Verwendung von **RxExec**, finden Sie im Artikel: [Grob differenzierte Parallelität mit Foreach und rxExec](https://blog.revolutionanalytics.com/2015/04/coarse-grain-parallelism-with-foreach-and-rxexec.html)
