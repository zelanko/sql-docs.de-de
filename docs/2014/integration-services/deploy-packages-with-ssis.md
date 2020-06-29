---
title: 'SSIS-Tutorial: Bereitstellen von Paketen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- deployment tutorial [Integration Services]
- deploying packages [Integration Services]
- SSIS, tutorials
- Integration Services, tutorials
- deploying packages [Integration Services], installing
- SQL Server Integration Services, tutorials
- walkthroughs [Integration Services]
- deployment utility [Integration Services]
- deploying packages [Integration Services], configurations
ms.assetid: de18468c-cff3-48f4-99ec-6863610e5886
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a2f5103c093666d59fb36b978e17dff5b51a0cdc
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85429767"
---
# <a name="ssis-tutorial-deploying-packages"></a>SSIS-Tutorial: Bereitstellen von Paketen
  [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] bietet Tools zum einfachen Bereitstellen von Paketen auf anderen Computern. Von den Bereitstellungstools werden auch mögliche Abhängigkeiten wie vom Paket benötigte Konfigurationen und Dateien verwaltet. In diesem Lernprogramm lernen Sie, wie Sie diese Tools verwenden, um Pakete und ihre Abhängigkeiten auf einem Zielrechner zu installieren.

 Zuerst führen Sie Aufgaben aus, um die Bereitstellung vorzubereiten. Sie erstellen zunächst ein neues [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] und fügen diesem vorhandene Pakete und Datendateien hinzu. Sie erstellen keine neuen Pakete. Stattdessen arbeiten Sie nur mit fertigen Paketen, die speziell für dieses Lernprogramm erstellt wurden. Sie nehmen in diesem Lernprogramm keine Änderung der Funktionalität der Pakete vor. Nachdem Sie die Pakete dem Projekt hinzugefügt haben, sollten Sie sie jedoch im [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer öffnen und ihren Inhalt überprüfen. Durch Untersuchen der Pakete erhalten Sie Informationen zu Paketabhängigkeiten wie Protokolldateien und weiteren interessanten Funktionen der Pakete.

 Bei der Vorbereitung der Bereitstellung aktualisieren Sie die Pakete auch, um Konfigurationen zu verwenden. Durch die Konfigurationen können die Eigenschaften von Paketen und Paketobjekten zur Laufzeit aktualisiert werden. In diesem Lernprogramm verwenden Sie Konfigurationen, um die Verbindungszeichenfolgen der Protokoll- und Textdateien und die Speicherorte der XML- und XSD-Dateien, die vom Paket verwendet werden, zu aktualisieren. Weitere Informationen zu Konfigurationen finden Sie unter [Paketkonfigurationen](../../2014/integration-services/package-configurations.md) und [Erstellen von Paketkonfigurationen](../../2014/integration-services/create-package-configurations.md).

 Nachdem Sie überprüft haben, ob die Pakete erfolgreich in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]ausgeführt werden, erstellen Sie die Bereitstellungsgruppe, um die Pakete zu installieren. Die Bereitstellungsgruppe besteht aus den Paketdateien und weiteren Elementen, die Sie dem [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt hinzugefügt haben, den Paketabhängigkeiten, die [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] automatisch enthält, und dem von Ihnen erstellten Bereitstellungshilfsprogramm. Weitere Informationen finden Sie unter [Create a Deployment Utility](../../2014/integration-services/create-a-deployment-utility.md).

 Sie kopieren dann die Bereitstellungsgruppe zum Zielrechner und führen den Paketinstallations-Assistenten aus, um die Pakete und Paketabhängigkeiten zu installieren. Die Pakete werden in der SQL Server-Datenbank msdb installiert, und die Unterstützungs- und Hilfsdateien werden im Dateisystem installiert. Da die bereitgestellten Pakete Konfigurationen verwenden, aktualisieren Sie die Konfiguration zur Verwendung neuer Werte, damit die Pakete erfolgreich in der neuen Umgebung ausgeführt werden können.

 Schließlich führen Sie die Pakete in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] mithilfe des Paketausführungshilfsprogramms aus.

 Es ist Ziel dieses Lernprogramms, die Komplexität von Bereitstellungsproblemen zu simulieren, die in der Praxis auftreten können. Wenn Sie die Pakete nicht auf einem anderen Computer bereitstellen können, können Sie dieses Lernprogramm dennoch ausführen. Dazu müssen Sie die Pakete in der msdb-Datenbank einer lokalen Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]installieren und dann von [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] auf derselben Instanz ausführen.

## <a name="what-you-will-learn"></a>Lernziele
 Die beste Möglichkeit, sich mit den neuen Tools, Steuerelementen und Features vertraut zu machen, die in verfügbar [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] sind, besteht darin, Sie zu verwenden. Dieses Lernprogramm führt Sie schrittweise durch die Erstellung eines [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekts und das anschließende Hinzufügen der Pakete und weiterer erforderlicher Dateien zum Projekt. Wenn das Projekt vollständig ist, erstellen Sie ein Bereitstellungspaket, kopieren es zum Zielcomputer und installieren dann die Pakete auf dem Zielcomputer.

## <a name="requirements"></a>Anforderungen
 Dieses Tutorial richtet sich an Benutzer, die bereits mit grundlegenden Dateisystem Vorgängen vertraut sind, aber nur über begrenzte Kenntnisse in Bezug auf die in verfügbaren neuen Features verfügen [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Um die grundlegenden Konzepte besser zu verstehen, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] die Sie in diesem Tutorial verwenden werden, ist es möglicherweise hilfreich, zunächst die folgenden [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Tutorials [auszuführen: Ausführen des SQL Server-Import/Export-Assistenten](import-export-data/start-the-sql-server-import-and-export-wizard.md) und [SSIS-Tutorial: Erstellen eines einfachen ETL-Pakets](../integration-services/ssis-how-to-create-an-etl-package.md).

 **Quellcomputer.** Auf dem Computer, auf dem Sie das Bereitstellungspaket erstellen, müssen die folgenden Komponenten installiert sein:

-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] mit der AdventureWorks-Datenbank. Aus Sicherheitsgründen werden die Beispieldatenbanken standardmäßig nicht installiert. Sie können die Beispieldatenbank von [codeplex](https://msftdbprodsamples.codeplex.com/releases/view/125550)herunterladen.

-   Sie müssen die Berechtigung zum Erstellen und Löschen von Tabellen in AdventureWorks haben.

-   Dieses Lernprogramm erfordert auch Beispieldaten, fertige Pakete, Konfigurationen und eine Infodatei. Die Dateien für diese Elemente werden zusammen mit den Beispielen installiert. Wenn Sie die Beispieldaten nicht finden, kehren Sie zu der obigen Prozedur zurück, und schließen Sie die Installation wie beschrieben ab.

-   Die Business Intelligence-Entwicklungsumgebung, [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].

 **Zielcomputer.** Auf dem Computer, auf dem Sie die Pakete bereitstellen, müssen die folgenden Komponenten installiert sein:

-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] mit der AdventureWorks-Datenbank.

-   [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].

-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].

-   Sie müssen über die Berechtigungen zum Erstellen und Löschen von Tabellen in AdventureWorks und zum Ausführen von Paketen in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]verfügen.

-   Sie müssen über Lese-und Schreib Berechtigung für die sysssispackages-Tabelle in der msdb- [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Systemdatenbank verfügen.

 Wenn Sie die Pakete auf demselben Computer bereitstellen möchten wie dem, auf dem Sie das Bereitstellungspaket erstellen, muss dieser Computer die Anforderungen sowohl des Quell- als auch des Zielcomputers erfüllen.

 **Geschätzte Zeit zum Bearbeiten dieses Tutorials:** 2 Stunden

## <a name="lessons-in-this-tutorial"></a>Lektionen in diesem Lernprogramm
 [Lektion 1: Vorbereiten der Erstellung des Bereitstellungs Pakets](../integration-services/lesson-1-preparing-to-create-the-deployment-bundle.md) In dieser Lektion können Sie eine ETL-Lösung bereitstellen, indem Sie ein neues [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Projekt erstellen und dem Projekt die Pakete und andere erforderliche Dateien hinzufügen.

 [Lektion 2: Erstellen des Bereitstellungs Pakets](../integration-services/lesson-2-create-the-deployment-bundle-in-ssis.md) In dieser Lektion erstellen Sie ein Bereitstellungs Hilfsprogramm und überprüfen, ob das Bereitstellungs Paket die notwendigen Dateien enthält.

 [Lektion 3: Installieren von Paketen](../integration-services/lesson-3-install-ssis-package.md) In dieser Lektion kopieren Sie das Bereitstellungs Paket auf den Zielcomputer, installieren die Pakete und führen dann die Pakete aus.

![Integration Services Symbol (klein)](media/dts-16.gif "Integration Services (kleines Symbol)")immer auf**dem neuesten Stand bleiben mit Integration Services**  <br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.

