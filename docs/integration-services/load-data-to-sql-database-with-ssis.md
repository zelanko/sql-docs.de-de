---
title: Laden von Daten in Azure SQL-Datenbank mit SQL Server Integration Services (SSIS) | Microsoft-Dokumentation
description: In diesem Artikel wird erläutert, wie ein SQL Server Integration Services-Paket (SSIS) erstellt wird, um Daten aus einer Vielzahl von Datenquellen in Azure SQL-Datenbank zu verschieben.
documentationcenter: NA
ms.prod: sql
ms.prod_service: integration-services
ms.suite: sql
ms.technology: integration-services
ms.devlang: NA
ms.topic: conceptual
ms.tgt_pltfrm: NA
ms.custom: loading
ms.date: 08/14/2018
ms.author: douglasl
author: douglaslMS
manager: craigg-msft
ms.openlocfilehash: ed87e5a83e992ba5de6289d72465d92c94126748
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2018
ms.locfileid: "40175022"
---
# <a name="load-data-into-azure-sql-database-with-sql-server-integration-services-ssis"></a>Laden von Daten in Azure SQL-Datenbank mit SQL Server Integration Services

Erstellen Sie ein SQL Server Integration Services-Paket (SSIS), um Daten in [Azure SQL-Datenbank](/azure/sql-database/) zu verschieben. Sie können die Daten optional umstrukturieren, transformieren und bereinigen, während diese den SSIS-Datenfluss durchlaufen.

Dieser Artikel enthält Anleitungen für folgende Aktionen:

* Erstellen Sie ein neues Integration Services-Projekt in Visual Studio.
* Entwerfen Sie ein SSIS-Paket, das Daten aus der Quelle in das Ziel lädt.
* Führen Sie das SSIS-Paket aus, um die Daten zu laden.

## <a name="basic-concepts"></a>Grundlegende Konzepte

Ein Paket ist die grundlegende Bereitstellungseinheit in SSIS. Zugehörige Pakete werden in Projekten gruppiert. Sie erstellen Projekte und entwerfen Pakete in Visual Studio mit SQL Server Data Tools. Der Entwurfsprozess ist ein visueller Prozess, bei dem Sie Komponenten per Drag & Drop aus der Toolbox auf die Entwurfsoberfläche ziehen, diese verbinden und ihre Eigenschaften festlegen. Wenn Sie ein Paket fertiggestellt haben, können Sie es ausführen und zur umfassenden Verwaltung, Überwachung und Sicherheit optional in SQL Server oder SQL-Datenbank bereitstellen.

Eine ausführliche Einführung in SSIS würde den Rahmen dieses Artikels sprengen. Weitere Informationen erhalten Sie in den folgenden Artikeln:

- [SQL Server Integration Services](sql-server-integration-services.md)

- [Erstellen eines einfachen ETL-Pakets](ssis-how-to-create-an-etl-package.md)

## <a name="about-the-solution"></a>Informationen zur Projektmappe

Die Projektmappe besteht aus einem normalen Paket, das einen Datenflusstask verwendet, der eine Quelle und ein Ziel enthält. Durch diesen Ansatz werden eine Vielzahl von Datenquellen unterstützt, einschließlich SQL Server und Azure SQL-Datenbank.

In diesem Tutorial wird SQL Server als Datenquelle verwendet. SQL Server wird auf einem lokalen Computer oder auf einem virtuellen Azure-Computer ausgeführt.

Um eine Verbindung zu SQL Server und SQL-Datenbank herzustellen, können Sie den ADO.NET-Verbindungs-Manager und dazu Quelle und Ziel verwenden. Alternativ können Sie den OLE DB-Verbindungs-Manager mit Quelle und Ziel verwenden. Dieses Tutorial verwendet ADO NET, da darin die wenigsten Konfigurationsoptionen enthalten sind. OLE DB stellt möglicherweise eine geringfügig bessere Leistung als ADO .NET bereit.

Um das Verfahren abzukürzen, können Sie den SQL Server-Import/Export-Assistenten verwenden, um das einfache Paket zu erstellen. Speichern Sie das Paket anschließend, und öffnen Sie es in Visual Studio oder SSDT, um es anzuzeigen und anzupassen. Weitere Informationen finden Sie unter [Importieren und Exportieren von Daten mit dem SQL Server-Import/Export-Assistenten](import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md).

## <a name="prerequisites"></a>Voraussetzungen
Zum Abschließen dieses Tutorials benötigen Sie Folgendes:

1. **SQL Server Integration Services (SSIS)**. SSIS ist eine Komponente von SQL Server und erfordert eine lizenzierte Version oder die Entwickler- oder Evaluierungsversion von SQL Server. Informationen darüber, wie Sie eine Evaluierungsversion von SQL Server erhalten, finden Sie im [Evaluation Center für SQL Server](https://www.microsoft.com/evalcenter/evaluate-sql-server-2017-rtm).
2. **Visual Studio** (optional). Die kostenlose Visual Studio Community Edition können Sie unter [Visual Studio Community][Visual Studio Community] abrufen. Wenn Sie Visual Studio nicht installieren möchten, können Sie auch nur SQL Server Data Tools (SSDT) installieren. Mit SSDT wird auch eine Version von Visual Studio mit eingeschränkter Funktionalität installiert.
3. **SQL Server Data Tools for Visual Studio (SSDT)**. Informationen zum Installieren von SQL Server Data Tools for Visual Studio finden Sie unter [Herunterladen von SQL Server Data Tools (SSDT)][Download SQL Server Data Tools (SSDT)].
4. **Eine Datenbank von Azure SQL-Datenbank und Berechtigungen**. In diesem Tutorial stellen Sie eine Verbindung mit einer Instanz von SQL-Datenbank her und laden Daten in diese. Sie benötigen Berechtigungen für eine Verbindung, zum Erstellen einer Tabelle und zum Laden von Daten.
5. **Beispieldaten**. Dieses Tutorial verwendet als Quelldaten zum Laden in SQL Data Warehouse Beispieldaten, die in der AdventureWorks-Beispieldatenbank in SQL-Datenbank gespeichert sind. Weitere Informationen zum Abrufen der AdventureWorks-Beispieldatenbank finden Sie in den [AdventureWorks-Beispieldatenbanken][AdventureWorks 2014 Sample Databases].
6. **Eine Firewallregel**. Sie müssen eine Firewallregel für SQL-Datenbank mit der IP-Adresse Ihres lokalen Computers erstellen, bevor Sie Daten in SQL-Datenbank hochladen können.

## <a name="create-a-new-integration-services-project"></a>Erstellen eines neuen SQL Server Integration Services-Projekts
1. Starten Sie Visual Studio.
2. Wählen Sie im Menü **Datei** die Option **Neu | Projekt** aus.
3. Navigieren Sie zu den Projekttypen **Installiert | Vorlagen | Business Intelligence | Integration Services**.
4. Wählen Sie ein **Integration Services-Projekt** aus. Geben Sie Werte für **Name** und **Speicherort** ein, und klicken Sie dann auf **OK**.

Visual Studio wird geöffnet und erstellt ein neues Integration Services-Projekt (SSIS). Dann öffnet Visual Studio den Designer für das neue SSIS-Paket (Package.dtsx) im Projekt. Die folgenden Bildschirmbereiche werden angezeigt:

* Auf der linken Seite befindet sich die **Toolbox** der SSIS-Komponenten.
* In der Mitte befindet sich die Entwurfsoberfläche mit mehreren Registerkarten. In der Regel verwenden Sie mindestens die Registerkarten **Ablaufsteuerung** und **Datenfluss**.
* Auf der rechten Seite befinden sich die Bereiche **Projektmappen-Explorer** und **Eigenschaften**.
  
    ![][01]

## <a name="create-the-basic-data-flow"></a>Erstellen des grundlegenden Datenflusses
1. Ziehen Sie einen Datenflusstask aus der Toolbox in die Mitte der Entwurfsoberfläche (auf der Registerkarte **Ablaufsteuerung**).
   
    ![][02]
2. Doppelklicken Sie auf den Datenflusstask, um zur Registerkarte „Datenfluss“ zu wechseln.
3. Ziehen Sie aus der Liste „Andere Quellen“ in der Toolbox eine ADO.NET-Quelle auf die Entwurfsoberfläche. Ändern Sie mit noch ausgewähltem Quelladapter den Namen im Bereich **Eigenschaften** in **SQL Server-Quelle**.
4. Ziehen Sie aus der Liste „Andere Ziele“ in der Toolbox ein ADO.NET-Ziel auf die Entwurfsoberfläche unter der ADO NET-Quelle. Ändern Sie mit noch ausgewähltem Zieladapter den Namen im Bereich **Eigenschaften** in **SQL DB-Ziel**.
   
    ![][09]

## <a name="configure-the-source-adapter"></a>Konfigurieren des Quelladapters
1. Doppelklicken Sie auf den Quelladapter, um den **ADO.NET-Quellen-Editor** zu öffnen.
   
    ![][03]
2. Klicken Sie im **ADO.NET-Quellen-Editor** auf der Registerkarte **Verbindungs-Manager** auf die Schaltfläche **Neu** neben der Liste **ADO.NET-Verbindungs-Manager**, um das Dialogfeld **ADO.NET-Verbindungs-Manager konfigurieren** zu öffnen. Nehmen Sie dann Verbindungseinstellungen für die SQL Server-Datenbank vor, von der in diesem Tutorial Daten geladen werden.
   
    ![][04]
3. Klicken Sie im Dialogfeld **ADO.NET-Verbindungs-Manager konfigurieren** auf die Schaltfläche **Neu**, um das Dialogfeld **Verbindungs-Manager** zu öffnen, und erstellen Sie eine neue Datenverbindung.
   
    ![][05]
4. Führen Sie im Dialogfeld **Verbindungs-Manager** folgende Schritte durch:
   
   1. Wählen Sie als **Anbieter** den SqlClient-Datenanbieter aus.
   2. Geben Sie für **Servernamen** den SQL Server-Namen ein.
   3. Wählen Sie im Abschnitt **Beim Server anmelden** die Authentifizierungsinformationen aus, oder geben Sie sie ein.
   4. Wählen Sie im Abschnitt **Mit Datenbank verbinden** die AdventureWorks-Beispieldatenbank aus.
   5. Klicken Sie auf **Verbindung testen**.
      
       ![][06]
   6. Klicken Sie im Dialogfeld, in dem die Ergebnisse des Verbindungstests gemeldet werden, auf **OK**, um zum Dialogfeld **Verbindungs-Manager** zurückzukehren.
   7. Klicken Sie im Dialogfeld **Verbindungs-Manager** auf **OK**, um zum Dialogfeld **ADO.NET-Verbindungs-Manager konfigurieren** zurückzukehren.
5. Klicken Sie im Dialogfeld **ADO.NET-Verbindungs-Manager konfigurieren** auf **OK**, um zum **ADO.NET-Quellen-Editor** zurückzukehren.
6. Wählen Sie im **ADO.NET-Quellen-Editor** in der Liste **Name der Tabelle oder Sicht** die Tabelle **Sales.SalesOrderDetail** aus.
   
    ![][07]
7. Klicken Sie auf **Vorschau**, um die ersten 200 Datenzeilen in der Quelltabelle im Dialogfeld **Vorschau der Abfrageergebnisse anzeigen** anzuzeigen.
   
    ![][08]
8. Klicken Sie im Dialogfeld **Vorschau der Abfrageergebnisse anzeigen** auf **Schließen**, um zum **ADO.NET-Quellen-Editor** zurückzukehren.
9. Klicken Sie im **ADO.NET-Quellen-Editor** auf **OK**, um die Konfiguration der Datenquelle abzuschließen.

## <a name="connect-the-source-adapter-to-the-destination-adapter"></a>Herstellen einer Verbindung zwischen dem Quell- und Zieladapter
1. Wählen Sie den Quelladapter auf der Entwurfsoberfläche aus.
2. Wählen Sie den blauen Pfeil aus, der vom Quelladapter ausgeht, und ziehen Sie ihn zum Ziel-Editor, bis dieser fest positioniert ist.
   
    ![][10]
   
    Bei einem typischen SSIS-Paket verwenden Sie eine Reihe von anderen Komponenten von der SSIS-Toolbox zwischen Quelle und Ziel, um Ihre Daten beim Durchlaufen durch den SSIS-Datenfluss umzustrukturieren, zu transformieren und zu bereinigen. Um dieses Beispiel so einfach wie möglich zu halten, stellen wir eine direkte Verbindung zwischen Quelle und Ziel her.

## <a name="configure-the-destination-adapter"></a>Konfigurieren des Zieladapters
1. Doppelklicken Sie auf den Zieladapter, um den **ADO.NET-Ziel-Editor** zu öffnen.
   
    ![][11]
2. Klicken Sie im **ADO.NET-Ziel-Editor** auf der Registerkarte **Verbindungs-Manager** auf die Schaltfläche **Neu** neben der Liste **Verbindungs-Manager**, um das Dialogfeld **ADO.NET-Verbindungs-Manager konfigurieren** zu öffnen. Nehmen Sie dann Verbindungseinstellungen für die Datenbank von Azure SQL-Datenbank vor, in die in diesem Tutorial Daten geladen werden.
3. Klicken Sie im Dialogfeld **ADO.NET-Verbindungs-Manager konfigurieren** auf die Schaltfläche **Neu**, um das Dialogfeld **Verbindungs-Manager** zu öffnen, und erstellen Sie eine neue Datenverbindung.
4. Führen Sie im Dialogfeld **Verbindungs-Manager** folgende Schritte durch:
   1. Wählen Sie als **Anbieter** den SqlClient-Datenanbieter aus.
   2. Geben Sie für **Servername** den Namen von SQL-Datenbank an.
   3. Wählen Sie im Abschnitt **Beim Server anmelden** die Option **SQL Server-Authentifizierung verwenden** aus, und geben Sie die Authentifizierungsinformationen ein.
   4. Wählen Sie im Abschnitt **Mit Datenbank verbinden** eine vorhandene Datenbank von SQL-Datenbank aus.
   5. Klicken Sie auf **Verbindung testen**.
   6. Klicken Sie im Dialogfeld, in dem die Ergebnisse des Verbindungstests gemeldet werden, auf **OK**, um zum Dialogfeld **Verbindungs-Manager** zurückzukehren.
   7. Klicken Sie im Dialogfeld **Verbindungs-Manager** auf **OK**, um zum Dialogfeld **ADO.NET-Verbindungs-Manager konfigurieren** zurückzukehren.
5. Klicken Sie im Dialogfeld **ADO.NET-Verbindungs-Manager konfigurieren** auf **OK**, um zum **ADO.NET-Ziel-Editor** zurückzukehren.
6. Klicken Sie im **ADO.NET-Ziel-Editor** neben der Liste **Tabelle oder Sicht verwenden** auf **Neu**, um das Dialogfeld **Tabelle erstellen** zu öffnen, um eine neue Zieltabelle mit einer Spaltenliste zu erstellen, die der Quelltabelle entspricht.
   
    ![][12a]
7. Führen Sie im Dialogfeld **Tabelle erstellen** die folgenden Schritte aus:
   
   1. Ändern Sie den Namen der Zieltabelle in **SalesOrderDetail**.
      
       ![][12b]

   2. Klicken Sie auf **OK**, um die Tabelle zu erstellen und zum **ADO.NET-Ziel-Editor** zurückzukehren.
8. Wählen Sie im **ADO.NET-Ziel-Editor** die Registerkarte **Zuordnungen** aus, um festzustellen, wie Spalten in der Quelle denen im Ziel zugeordnet werden.
   
    ![][13]
9. Klicken Sie auf **OK**, um die Konfiguration des Ziels abzuschließen.

## <a name="run-the-package-to-load-the-data"></a>Ausführen des Pakets zum Laden der Daten
Führen Sie das Paket aus, indem Sie auf der Symbolleiste auf die Schaltfläche **Starten** klicken oder im Menü **Debuggen** eine der Optionen **Ausführen** auswählen.

In den folgenden Abschnitten wird beschrieben, was Sie sehen, wenn Sie das Paket mit der zweiten Option, die in diesem Artikel dargestellt ist, erstellt haben, also mit dem Datenfluss, der eine Quelle und ein Ziel enthält.

Wenn die Paketausführung beginnt, sehen Sie gelbe sich drehende Räder, die auf laufende Aktivität hinweisen, sowie die Anzahl der bisher verarbeiteten Zeilen.

![][14]

Wenn die Ausführung des Pakets abgeschlossen ist, sehen Sie grüne Häkchen, die auf ihre erfolgreiche Ausführung hinweisen, sowie die Gesamtanzahl der Datenzeilen, die von der Quelle in das Ziel geladen wurden.

![][15]

Gratulation! Sie haben mit SQL Server Integration Services erfolgreich Daten in Azure SQL-Datenbank geladen.

## <a name="next-steps"></a>Nächste Schritte

- Erfahren Sie mehr über das Debuggen und Behandeln von Problemen mit Ihren Paketen direkt in der Entwurfsumgebung. Legen Sie hiermit los: [Tools zur Problembehandlung für die Paketentwicklung][Troubleshooting Tools for Package Development].

- Erfahren Sie, wie Sie Ihre SSIS-Projekte und -Pakete in Integration Services Server oder an einem anderen Speicherort bereitstellen. Legen Sie hiermit los: [Bereitstellung von Projekten und Paketen][Deployment of Projects and Packages].

<!-- Image references -->
[01]:  ./media/load-data-to-sql-database-with-ssis/ssis-designer-01.png
[02]:  ./media/load-data-to-sql-database-with-ssis/ssis-data-flow-task-02.png
[03]:  ./media/load-data-to-sql-database-with-ssis/ado-net-source-03.png
[04]:  ./media/load-data-to-sql-database-with-ssis/ado-net-connection-manager-04.png
[05]:  ./media/load-data-to-sql-database-with-ssis/ado-net-connection-05.png
[06]:  ./media/load-data-to-sql-database-with-ssis/test-connection-06.png
[07]:  ./media/load-data-to-sql-database-with-ssis/ado-net-source-07.png
[08]:  ./media/load-data-to-sql-database-with-ssis/preview-data-08.png
[09]:  ./media/load-data-to-sql-database-with-ssis/source-destination-09.png
[10]:  ./media/load-data-to-sql-database-with-ssis/connect-source-destination-10.png
[11]:  ./media/load-data-to-sql-database-with-ssis/ado-net-destination-11.png
[12a]: ./media/load-data-to-sql-database-with-ssis/destination-query-before-12a.png
[12b]: ./media/load-data-to-sql-database-with-ssis/destination-query-after-12b.png
[13]:  ./media/load-data-to-sql-database-with-ssis/column-mapping-13.png
[14]:  ./media/load-data-to-sql-database-with-ssis/package-running-14.png
[15]:  ./media/load-data-to-sql-database-with-ssis/package-success-15.png

<!-- Article references -->

<!-- MSDN references -->
[Download SQL Server Data Tools (SSDT)]: ../ssdt/download-sql-server-data-tools-ssdt.md
[Data Flow]: ./data-flow/data-flow.md
[Troubleshooting Tools for Package Development]: ./troubleshooting/troubleshooting-tools-for-package-development.md
[Deployment of Projects and Packages]: ./packages/deploy-integration-services-ssis-projects-and-packages.md

<!--Other Web references-->
[Microsoft SQL Server 2017 Integration Services Feature Pack for Azure]: https://www.microsoft.com/download/details.aspx?id=54798
[SQL Server Evaluations]: https://www.microsoft.com/evalcenter/evaluate-sql-server-2017
[Visual Studio Community]: https://www.visualstudio.com/products/visual-studio-community-vs.aspx
[AdventureWorks 2014 Sample Databases]: https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks
