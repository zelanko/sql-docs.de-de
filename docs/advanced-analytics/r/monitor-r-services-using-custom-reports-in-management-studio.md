---
title: Überwachen von R Services mithilfe von benutzerdefinierten Berichten in Management Studio
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: a7ab7a4ccd4956bd1752be398b25a6ff9fd92ce5
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715083"
---
# <a name="monitor-machine-learning-services-using-custom-reports-in-management-studio"></a>Überwachung von Machine Learning Services mithilfe von benutzerdefinierten Berichten in Management Studio
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Um die Verwaltung der für Machine Learning verwendeten Instanz zu vereinfachen, hat das Produktteam eine Reihe von benutzerdefinierten Beispiel Berichten bereitgestellt, die Sie SQL Server Management Studio hinzufügen können. In diesen Berichten können Sie Details wie die folgenden anzeigen:

- Aktive R-oder python-Sitzungen
- Konfigurationseinstellungen für die Instanz
- Ausführungs Statistik für Machine Learning-Aufträge
- Erweiterte Ereignisse für R Services
- Auf der aktuellen Instanz installierte R-oder python-Pakete

In diesem Artikel wird erläutert, wie Sie die benutzerdefinierten Berichte installieren und verwenden, die speziell für Machine Learning bereitgestellt werden 

Eine allgemeine Einführung in die Berichte in Management Studio finden Sie unter [benutzerdefinierte Berichte in Management Studio](../../ssms/object/custom-reports-in-management-studio.md).

## <a name="how-to-install-the-reports"></a>So führen Sie die Installation von Berichten durch

Die Berichte wurden mithilfe von SQL Server Reporting Services erstellt, können aber direkt aus SQL Server Management Studio verwendet werden, selbst wenn Reporting Services nicht auf Ihrer Instanz installiert ist. 

So verwenden Sie die Berichte:

* Laden Sie die RDL-Dateien aus dem GitHub-Repository für SQL Server Produktbeispiele herunter.
* Fügen Sie die Dateien zum Ordner der benutzerdefinierten Berichten hinzu, der von SQL Server Management Studio verwendet wird.
* Öffnen Sie die Berichte in SQL Server Management Studio.


### <a name="step-1-download-the-reports"></a>Schritt 1: Herunterladen der Berichte

1. Öffnen Sie das GitHub-Repository, das [SQL Server Produktbeispiele](https://github.com/Microsoft/sql-server-samples)enthält, und laden Sie die Beispiel Berichte herunter. 

    + [Benutzerdefinierte SSMS-Berichte](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/machine-learning-services/ssms-custom-reports)

    > [!NOTE]
    > Die Berichte können entweder mit den SQL Server 2017-maschinallerndiensten oder mit SQL Server 2016 R-Diensten verwendet werden.

2. Sie können sich auch in GitHub anmelden, und eine lokale Verzweigung der Beispiele erstellen, um die Beispiele herunterzuladen. 

### <a name="step-2-copy-the-reports-to-management-studio"></a>Schritt 2: Kopieren der Berichte in Management Studio

3. Suchen Sie den Ordner der benutzerdefinierten Berichte, der von SQL Server Management Studio verwendet wird. Standardmäßig werden benutzerdefinierte Berichte in diesem Ordner gespeichert:
    
   `C:\Users\user_name\Documents\SQL Server Management Studio\Custom Reports`

   Sie können jedoch einen anderen Ordner angeben, oder einen Unterordner erstellen.

4. Kopieren Sie die *.RDL-Dateien in den Ordner der benutzerdefinierten Berichte.


### <a name="step-3-run-the-reports"></a>Schritt 3: Ausführen der Berichte

5. Klicken Sie in Management Studio mit der rechten Maustaste auf den Knoten **Datenbanken** der Instanz, auf der Sie die Berichte ausführen möchten.
6. Klicken Sie auf **Berichte**, und klicken Sie dann auf **Benutzerdefinierte Berichte**.
7. Suchen Sie im Dialogfeld **Datei öffnen** den Ordner mit den benutzerdefinierten Berichten.
8. Wählen Sie eine der RDL-Dateien aus, die Sie heruntergeladen haben, und klicken Sie dann auf **Öffnen**.

> [!IMPORTANT]
> Diese Berichte können bei manchen Remotedesktopsitzungen oder auf manchen Computern nicht verwendet werden, z.B. auf Computern mit Anzeigegeräten mit hohem DPI-Wert oder einer höheren Auflösung als 1080p. Es gibt einen Fehler im Berichtanzeige-Steuerelement in SSMS, der den Bericht abstürzen lässt.

## <a name="report-list"></a>Berichtsliste

Das produktbeispielrepository in GitHub enthält derzeit die folgenden Berichte:

+ **R Services - Active Sessions**

  Verwenden Sie diesen Bericht, um die Benutzer anzuzeigen, die derzeit mit der SQL Server Instanz verbunden sind und Machine Learning-Aufträge ausführen. 
  
+ **R Services - Configuration**

  Verwenden Sie diesen Bericht, um die Konfiguration der externen Skript Laufzeit und zugehöriger Dienste anzuzeigen. Dieser Bericht gibt an, ob ein Neustart erforderlich ist, und sucht nach erforderlichen Netzwerkprotokollen. 
  
  Die implizite Authentifizierung ist für Machine Learning-Aufgaben erforderlich, die in SQL Server als computekontext ausgeführt werden. Um zu überprüfen, ob die implizite Authentifizierung konfiguriert ist, überprüft der Bericht, ob eine Daten Bank Anmeldung für die Gruppe sqlrusergroup vorhanden ist.

 + **R Services - Configure Instance** 

   Dieser Bericht soll Ihnen helfen, Machine Learning zu konfigurieren. Sie können diesen Bericht auch ausführen, um die im vorherigen Bericht gefundenen Konfigurationsfehler zu beheben.
 
+ **R Services - Execution Statistics**

  Verwenden Sie diesen Bericht, um Ausführungs Statistiken für Machine Learning-Aufträge anzuzeigen. Sie können z.B. die Gesamtzahl der R-Skripts, die ausgeführt wurden, die Anzahl der parallelen Ausführungen und die am häufigsten verwendeten RevoScaleR-Funktionen anzeigen lassen. Klicken Sie auf **SQL-Skript anzeigen** , um den gesamten T-SQL-Code für diesen Bericht zu erhalten.

  Der Bericht überwacht derzeit nur die Statistiken für Funktionen aus dem RevoScaleR-Paket.

+ **R Services - Extended Events**

  Verwenden Sie diesen Bericht, um eine Liste der erweiterten Ereignisse anzuzeigen, die für die Überwachung von Aufgaben im Zusammenhang mit externen Skript Laufzeiten verfügbar sind. Klicken Sie auf **SQL-Skript anzeigen** , um den gesamten T-SQL-Code für diesen Bericht zu erhalten.

+ **R Services - Packages**

  Verwenden Sie diesen Bericht, um eine Liste der R-oder python-Pakete anzuzeigen, die auf der SQL Server Instanz installiert sind.

+ **R Services - Resource Usage**

  Verwenden Sie diesen Bericht, um den Verbrauch von CPU-, Arbeitsspeicher-und e/a-Ressourcen durch die externe Skriptausführung anzuzeigen. Sie können auch die Einstellung für den Speicher von externen Ressourcenpools anzeigen.

## <a name="see-also"></a>Siehe auch

[Überwachen von Diensten](managing-and-monitoring-r-solutions.md)

[Extended events for R Services (Erweiterte Ereignisse bei R Services)](extended-events-for-sql-server-r-services.md)
