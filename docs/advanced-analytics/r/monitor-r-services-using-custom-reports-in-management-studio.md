---
title: Überwachung von R Services mithilfe von benutzerdefinierten Berichten in Management Studio – SQL Server Machine Learning Services
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 55fcb4e145481f98b0cba065ddab75e7cfa0a538
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58510287"
---
# <a name="monitor-machine-learning-services-using-custom-reports-in-management-studio"></a>Überwachung von Machine Learning Services mithilfe von benutzerdefinierten Berichten in Management Studio
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Zum Verwalten der Instanz für Machine learning verwendeten zu erleichtern, hat das Produktteam eine Anzahl von benutzerdefinierten Beispielberichten bereitgestellt, die Sie für SQL Server Management Studio hinzufügen können. In diesen Berichten können Sie Details wie z. B. anzeigen:

- Aktive R oder Python-Sitzungen
- Konfigurationseinstellungen für die Instanz
- Ausführungsstatistiken für Machine Learning-Aufträge
- Erweiterte Ereignisse bei R Services
- R oder Python-Pakete, die für die aktuelle Instanz installiert

In diesem Artikel wird erläutert, wie zum Installieren und verwenden die benutzerdefinierten Berichte, die speziell für Computer Leaerning bereitgestellt wird. 

Eine allgemeine Einführung in Berichte in Management Studio, finden Sie unter [benutzerdefinierte Berichte in Management Studio](../../ssms/object/custom-reports-in-management-studio.md).

## <a name="how-to-install-the-reports"></a>So führen Sie die Installation von Berichten durch

Die Berichte wurden mithilfe von SQL Server Reporting Services erstellt, können aber direkt aus SQL Server Management Studio verwendet werden, selbst wenn Reporting Services nicht auf Ihrer Instanz installiert ist. 

So verwenden Sie die Berichte:

* Laden Sie die RDL-Dateien aus dem GitHub-Repository für SQL Server Produktbeispiele herunter.
* Fügen Sie die Dateien zum Ordner der benutzerdefinierten Berichten hinzu, der von SQL Server Management Studio verwendet wird.
* Öffnen Sie die Berichte in SQL Server Management Studio.


### <a name="step-1-download-the-reports"></a>Schritt 1: Herunterladen der Berichte

1. Öffnen Sie das GitHub-Repository, enthält [SQL Server-Produktbeispiele](https://github.com/Microsoft/sql-server-samples), und Laden Sie die Beispielberichte. 

    + [Benutzerdefinierte Berichte von SSMS](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/machine-learning-services/ssms-custom-reports)

    > [!NOTE]
    > Die Berichte können mit SQL Server 2017 Machiine Learning Services oder SQL Server 2016 R Services verwendet werden.

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

Klicken Sie im GitHub-Repository für Produktbeispiele enthält derzeit die folgenden Berichte:

+ **R Services - Active Sessions**

  Verwenden Sie diesen Bericht, um die Benutzer anzuzeigen, die derzeit mit der SQL Server-Instanz und den ausgeführten Machine learning-Aufträgen verbunden sind. 
  
+ **R Services - Configuration**

  Verwenden Sie diesen Bericht, um die Konfiguration für die externen Skript-Laufzeit und die zugehörigen Dienste anzuzeigen. Dieser Bericht gibt an, ob ein Neustart erforderlich ist, und sucht nach erforderlichen Netzwerkprotokollen. 
  
  Implizite Authentifizierung ist erforderlich für Machine Learning-Aufgaben, die in SQL Server als computekontext ausgeführt. Um sicherzustellen, dass die implizite Authentifizierung konfiguriert ist, überprüft der Bericht an, ob eine datenbankanmeldung für der Gruppe "SQLRUserGroup" vorhanden ist.

 + **R Services - Configure Instance** 

   Dieser Bericht dient zum Machine Learning konfigurieren. Sie können auch auf diesem Bericht können Sie die Korrektur von Konfigurationsfehlern finden Sie in dem vorhergehenden Bericht ausführen.
 
+ **R Services - Execution Statistics**

  Verwenden Sie diesen Bericht, um Ausführungsstatistiken für Machine Learning-Aufträge anzuzeigen. Sie können z.B. die Gesamtzahl der R-Skripts, die ausgeführt wurden, die Anzahl der parallelen Ausführungen und die am häufigsten verwendeten RevoScaleR-Funktionen anzeigen lassen. Klicken Sie auf **SQL-Skript anzeigen** um die vollständige T-SQL-Code hinter diesem Bericht zu erhalten.

  Der Bericht überwacht derzeit nur die Statistiken für Funktionen aus dem RevoScaleR-Paket.

+ **R Services - Extended Events**

  Verwenden Sie diesen Bericht, um eine Liste der erweiterten Ereignisse anzuzeigen, für die Überwachung von Aufgaben im Zusammenhang mit dem externen Skript-Laufzeiten verfügbar sind. Klicken Sie auf **SQL-Skript anzeigen** um die vollständige T-SQL-Code hinter diesem Bericht zu erhalten.

+ **R Services - Packages**

  Verwenden Sie diesen Bericht zum Anzeigen einer Liste der R oder Python-Pakete auf SQL Server-Instanz installiert.

+ **R Services - Resource Usage**

  Mithilfe dieses Berichts Verbrauch von CPU, Arbeitsspeicher und e/a-Ressourcen nach Ausführung des externen Skripts anzuzeigen. Sie können auch die Einstellung für den Speicher von externen Ressourcenpools anzeigen.

## <a name="see-also"></a>Siehe auch

[Überwachung von Diensten](managing-and-monitoring-r-solutions.md)

[Extended events for R Services (Erweiterte Ereignisse bei R Services)](extended-events-for-sql-server-r-services.md)
