---
title: Tutorial für Data Scientists, die mit der Sprache R – SQL Server-Machine Learning
description: Dieses Tutorial zeigt, wie eine End-to-End-R-Lösung für in-Database-Analyse zu erstellen.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/26/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 0b1820e15975ca027af7b51e809ba920af3ffc82
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58511301"
---
# <a name="tutorial-sql-development-for-r-data-scientists"></a>Tutorial: SQL-Datenbankentwicklung R Data scientists die Aufgabe
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Erfahren Sie in diesem Tutorial für Data Scientists, wie zum Erstellen von End-to-End-Lösung für die vorhersagemodellierung basierend auf der Unterstützung von R-Funktionen in SQL Server 2016 oder SQL Server 2017. Dieses Tutorial verwendet ein [NYCTaxi_sample](demo-data-nyctaxi-in-sql.md) Datenbank auf SQL Server. 

Sie verwenden eine Kombination aus R-Code [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Daten und benutzerdefinierten SQL-Funktionen ein klassifizierungsmodells des Typs zu erstellen, der die Wahrscheinlichkeit angibt, dass der Treiber ein Trinkgeld für eine bestimmte taxifahrt erhalten kann. Sie wird auch Ihr R-Modell zum Bereitstellen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und Server-Daten zum Generieren von Bewertungen auf Grundlage des Modells verwenden.

In diesem Beispiel kann auf alle möglichen realen Probleme, z. B. Vorhersagen der Kundenreaktionen auf Verkaufsaktionen oder die Vorhersage der Ausgaben oder die Teilnahme an Ereignisse erweitert werden. Da das Modell aus einer gespeicherten Prozedur aufgerufen werden kann, können Sie einfach in eine Anwendung einbetten.

Die exemplarische Vorgehensweise ist darauf ausgelegt, R-Entwicklern eine Einführung [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], R wird verwendet, wo immer dies möglich. Dies bedeutet jedoch nicht, dass R unbedingt das beste Tool für jede Aufgabe ist. In vielen Fällen stellt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eine bessere Leistung bereit, besonders für Aufgaben wie Datenaggregation und Featureentwicklung.  Solche Aufgaben profitieren besonders von neuen Funktionen in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], wie z.B. von speicheroptimierten Columnstore-Indizes. Wir versuchen, nebenbei auf mögliche Optimierungen hinweisen.

## <a name="prerequisites"></a>Erforderliche Komponenten

+ [SQL Server 2017 Machine Learning Services, Integration in R](../install/sql-machine-learning-services-windows-install.md#verify-installation) oder [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md)

+ [Datenbankberechtigungen](../security/user-permission.md) und eine SQL Server-Datenbank-Benutzeranmeldung

+ [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)

+ [NYC Taxi-Demo-Datenbank](demo-data-nyctaxi-in-sql.md)

+ Eine R-IDE wie RStudio oder des integrierten RGUI-Tools, die in R enthalten ist

Es wird empfohlen, dass Sie in dieser exemplarischen Vorgehensweise auf einer Clientarbeitsstation ausführen. Sie müssen möglicherweise, sich im selben Netzwerk, eine Verbindung mit einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Computer mit SQL Server und die R-Sprache aktiviert. Anweisungen zur Konfiguration von Workstation, finden Sie unter [richten Sie eine Data Science-Client für R-Entwicklungstools](../r/set-up-a-data-science-client.md).

Alternativ können Sie die exemplarische Vorgehensweise ausführen, auf einem Computer, die beides aufweist [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und ein R-Entwicklungsumgebung, aber es wird nicht empfohlen, diese Konfiguration für eine produktionsumgebung. Wenn Sie Client und Server auf demselben Computer platzieren möchten, achten Sie darauf, dass Sie einen zweiten Satz von Microsoft R-Bibliotheken für das Senden von R-Skript von einem "remote" Client installieren. Verwenden Sie nicht die R-Bibliotheken, die in die Programmdateien des SQL Server-Instanz installiert sind. Insbesondere wenn Sie einen Computer verwenden, sollten Sie die RevoScaleR-Bibliothek in beiden der folgenden Speicherorte auf Client- und Servervorgänge zu unterstützen.

+ C:\Programme\Microsoft Files\Microsoft\R Client\R_SERVER\library\RevoScaleR 
+ C:\Programme\Microsoft c:\Programme\Microsoft SQL Server\MSSQL14. MSSQLSERVER\R_SERVICES\library\RevoScaleR

<a name="add-packages"></a>

## <a name="additional-r-packages"></a>Zusätzliche R-Pakete

Diese exemplarische Vorgehensweise erfordert einige R-Bibliotheken, die nicht standardmäßig, als Teil des installiert sind [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]. Sie müssen die Pakete jeweils auf dem Client installieren, wo Sie die Lösung entwickeln und auf die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Computer, in dem Sie die Lösung bereitstellen.

### <a name="on-a-client-workstation"></a>Auf einer Clientarbeitsstation

Klicken Sie in Ihrer R-Umgebung Kopieren Sie die folgenden Zeilen, und führen Sie den Code in einem Konsolenfenster (Rgui oder eine IDE). Einige Pakete installieren ferner erforderlichen Pakete. Insgesamt sind etwa 32 Pakete installiert. Sie benötigen eine Internetverbindung, um diesen Schritt abzuschließen.
    
  ```R
  # Install required R libraries, if they are not already installed.
  if (!('ggmap' %in% rownames(installed.packages()))){install.packages('ggmap')}
  if (!('mapproj' %in% rownames(installed.packages()))){install.packages('mapproj')}
  if (!('ROCR' %in% rownames(installed.packages()))){install.packages('ROCR')}
  if (!('RODBC' %in% rownames(installed.packages()))){install.packages('RODBC')}
  ```

### <a name="on-the-server"></a>Auf dem server

Sie haben mehrere Optionen zum Installieren von Paketen auf SQL Server. Z. B. SQL Server bietet [R-paketverwaltung](../r/install-additional-r-packages-on-sql-server.md) -Feature, können Datenbankadministratoren, erstellen Sie ein paketrepository, und weisen Sie Benutzer die Rechte, um ihre eigenen Pakete zu installieren. Jedoch wenn Sie ein Administrator auf dem Computer sind, können Sie neue Pakete, die mithilfe von R, installieren, solange Sie in der richtigen Bibliothek installieren.

> [!NOTE]
> Auf dem Server **nicht** in einer Benutzerbibliothek installieren, auch wenn Sie dazu aufgefordert werden. Wenn Sie in einer Benutzerbibliothek installieren, SQL Server-Instanz nicht gefunden, oder führen Sie die Pakete. Weitere Informationen finden Sie unter [Installieren neuer R-Pakete auf SQL Server](../r/install-additional-r-packages-on-sql-server.md).

1. Öffnen Sie auf dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Computer **als Administrator** RGui.exe.  Wenn Sie SQL Server R Services unter Verwendung der Standardeinstellungen installiert haben, können Rgui.exe in C:\Program Files\Microsoft SQL Server\MSSQL13 gefunden werden. MSSQLSERVER\R_SERVICES\bin\x64).

2. Führen Sie an einer R-Eingabeaufforderung die folgenden R-Befehle aus:
  
  ```R
  install.packages("ggmap", lib=grep("Program Files", .libPaths(), value=TRUE)[1])
  install.packages("mapproj", lib=grep("Program Files", .libPaths(), value=TRUE)[1])
  install.packages("ROCR", lib=grep("Program Files", .libPaths(), value=TRUE)[1])
  install.packages("RODBC", lib=grep("Program Files", .libPaths(), value=TRUE)[1])
  ```
  Dieses Beispiel verwendet die "GREP"-Funktion von R, suchen den Vektor der verfügbaren Pfade aus, und suchen Sie den Pfad an, der "Program Files" enthält. Weitere Informationen finden Sie unter [ https://www.rdocumentation.org/packages/base/functions/grep ](https://www.rdocumentation.org/packages/base/functions/grep).

  Sollten Sie die Pakete bereits installiert haben, überprüfen Sie die Liste der installierten Pakete mit `installed.packages()`.

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Untersuchen und Zusammenfassen von Daten](walkthrough-view-and-summarize-data-using-r.md)