---
title: Tutorial für Datenanalysten mit R-Sprache
description: Tutorial, das zeigt, wie Sie eine End-to-End-R-Lösung für Daten bankübergreifende Analysen erstellen.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/26/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 45a1352b60574304a124af88226cc2a9d7f1a804
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2019
ms.locfileid: "68345800"
---
# <a name="tutorial-sql-development-for-r-data-scientists"></a>Tutorial: SQL-Entwicklung für R-Datenanalysten
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In diesem Tutorial für Datenanalysten erfahren Sie, wie Sie eine End-to-End-Lösung für die Vorhersage Modellierung erstellen, die auf der Unterstützung von R-Features in SQL Server 2016 oder SQL Server 2017 basiert. In diesem Tutorial wird eine [NYCTaxi_sample](demo-data-nyctaxi-in-sql.md) -Datenbank auf SQL Server verwendet. 

Sie verwenden eine Kombination aus R- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Code, Daten und benutzerdefinierten SQL-Funktionen, um ein Klassifizierungs Modell zu erstellen, das die Wahrscheinlichkeit angibt, dass der Treiber einen Tipp für eine bestimmte Taxifahrt erhält. Außerdem stellen Sie das R-Modell [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in bereit und verwenden Serverdaten zum Generieren von Bewertungen basierend auf dem Modell.

Dieses Beispiel kann auf alle Arten von realen Problemen erweitert werden, wie z. b. das Vorhersagen von Kunden Antworten auf Verkaufskampagnen oder das Vorhersagen von Ausgaben oder Anwesenheits Veranstaltungen. Da das Modell aus einer gespeicherten Prozedur aufgerufen werden kann, können Sie es problemlos in eine Anwendung einbetten.

Da die exemplarische Vorgehensweise entworfen wurde, um r [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]-Entwickler in einzuführen, wird r nach Möglichkeit verwendet. Dies bedeutet jedoch nicht, dass R notwendigerweise das beste Tool für jede Aufgabe ist. In vielen Fällen stellt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eine bessere Leistung bereit, besonders für Aufgaben wie Datenaggregation und Featureentwicklung.  Solche Aufgaben profitieren besonders von neuen Funktionen in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], wie z.B. von speicheroptimierten Columnstore-Indizes. Wir versuchen, auf mögliche Optimierungen zu verweisen.

## <a name="prerequisites"></a>Vorraussetzungen

+ [SQL Server 2017 Machine Learning Services mit r-Integration](../install/sql-machine-learning-services-windows-install.md#verify-installation) oder [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md)

+ [Daten Bank Berechtigungen](../security/user-permission.md) und eine SQL Server Datenbank-Benutzeranmeldung

+ [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)

+ [NYC Taxi Demo-Datenbank](demo-data-nyctaxi-in-sql.md)

+ Eine r-IDE wie rstudio oder das integrierte rgui-Tool, das in R enthalten ist

Es wird empfohlen, diese exemplarische Vorgehensweise auf einer Client Arbeitsstation auszuführen. Sie müssen in der Lage sein, im gleichen Netzwerk eine Verbindung mit einem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Computer herzustellen, auf dem SQL Server und die R-Sprache aktiviert sind. Anweisungen zur Arbeitsstations Konfiguration finden [Sie unter Einrichten eines Data Science Clients für die R-Entwicklung](../r/set-up-a-data-science-client.md).

Alternativ können Sie die exemplarische Vorgehensweise auf einem Computer ausführen, der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sowohl als auch eine R-Entwicklungsumgebung hat, aber wir empfehlen diese Konfiguration nicht für eine Produktionsumgebung. Wenn Sie Client und Server auf demselben Computer platzieren müssen, achten Sie darauf, dass Sie einen zweiten Satz von Microsoft r-Bibliotheken zum Senden eines R-Skripts von einem Remote Client installieren. Verwenden Sie die R-Bibliotheken nicht, die in den Programmdateien der SQL Server Instanz installiert sind. Insbesondere, wenn Sie einen Computer verwenden, benötigen Sie die revoscaler-Bibliothek an beiden Speicherorten, um Client-und Server Vorgänge zu unterstützen.

+ C:\programme\microsoft\r Client\R_SERVER\library\RevoScaleR 
+ C:\Programme\Microsoft SQL server\mssql14. MSSQLSERVER\R_SERVICES\library\RevoScaleR

<a name="add-packages"></a>

## <a name="additional-r-packages"></a>Zusätzliche R-Pakete

Diese exemplarische Vorgehensweise erfordert einige R-Bibliotheken, die nicht standardmäßig als [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]Teil von installiert werden. Sie müssen die Pakete auf dem Client installieren, auf dem Sie die Lösung entwickeln, und auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dem Computer, auf dem Sie die Lösung bereitstellen.

### <a name="on-a-client-workstation"></a>Auf einer Client Arbeitsstation

Kopieren Sie in Ihrer R-Umgebung die folgenden Zeilen, und führen Sie den Code in einem Konsolenfenster (rgui oder IDE) aus. Bei einigen Paketen werden auch erforderliche Pakete installiert. Insgesamt werden ungefähr 32 Pakete installiert. Sie müssen über eine Internetverbindung verfügen, um diesen Schritt abzuschließen.
    
  ```R
  # Install required R libraries, if they are not already installed.
  if (!('ggmap' %in% rownames(installed.packages()))){install.packages('ggmap')}
  if (!('mapproj' %in% rownames(installed.packages()))){install.packages('mapproj')}
  if (!('ROCR' %in% rownames(installed.packages()))){install.packages('ROCR')}
  if (!('RODBC' %in% rownames(installed.packages()))){install.packages('RODBC')}
  ```

### <a name="on-the-server"></a>Auf dem Server

Sie haben mehrere Optionen für die Installation von Paketen auf SQL Server. SQL Server stellt beispielsweise die [R-Paket Verwaltungs](../r/install-additional-r-packages-on-sql-server.md) Funktion bereit, mit der Datenbankadministratoren ein Paketrepository erstellen und Benutzern die Rechte zuweisen können, um Ihre eigenen Pakete zu installieren. Wenn Sie jedoch ein Administrator auf dem Computer sind, können Sie neue Pakete mithilfe von R installieren, solange Sie in der richtigen Bibliothek installieren.

> [!NOTE]
> Installieren Sie auf dem-Server nicht in einer Benutzer Bibliothek, auch wenn **Sie** dazu aufgefordert werden. Wenn Sie in einer Benutzer Bibliothek installieren, kann die SQL Server Instanz die Pakete nicht finden oder ausführen. Weitere Informationen finden Sie unter [Installieren neuer R-Pakete auf SQL Server](../r/install-additional-r-packages-on-sql-server.md).

1. Öffnen Sie auf dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Computer **als Administrator** RGui.exe.  Wenn Sie SQL Server R Services mithilfe der Standardeinstellungen installiert haben, finden Sie "rgui. exe" unter "c:\Programme\Microsoft SQL server\mssql13.". MSSQLSERVER\R_SERVICES\bin\x64).

2. Führen Sie an einer R-Eingabeaufforderung die folgenden R-Befehle aus:
  
  ```R
  install.packages("ggmap", lib=grep("Program Files", .libPaths(), value=TRUE)[1])
  install.packages("mapproj", lib=grep("Program Files", .libPaths(), value=TRUE)[1])
  install.packages("ROCR", lib=grep("Program Files", .libPaths(), value=TRUE)[1])
  install.packages("RODBC", lib=grep("Program Files", .libPaths(), value=TRUE)[1])
  ```
  In diesem Beispiel wird die R grep-Funktion verwendet, um den Vektor der verfügbaren Pfade zu durchsuchen und den Pfad zu finden, der "Programmdateien" enthält. Weitere Informationen finden [https://www.rdocumentation.org/packages/base/functions/grep](https://www.rdocumentation.org/packages/base/functions/grep)Sie unter.

  Wenn Sie der Ansicht sind, dass die Pakete bereits installiert sind, überprüfen Sie die `installed.packages()`Liste der installierten Pakete durch Ausführen von.

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Untersuchen und Zusammenfassen der Daten](walkthrough-view-and-summarize-data-using-r.md)