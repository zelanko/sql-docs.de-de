---
title: Bereitstellen von Paketen mit SSIS | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/20/2018
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: quickstart
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
caps.latest.revision: 27
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f7f28ae86cab01c86aa7360618b080ec4ff124e2
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43028814"
---
# <a name="deploy-packages-with-ssis"></a>Bereitstellen von Paketen mit SSIS
[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] bietet Tools zum einfachen Bereitstellen von Paketen auf anderen Computern. Von den Bereitstellungstools werden auch mögliche Abhängigkeiten wie vom Paket benötigte Konfigurationen und Dateien verwaltet. In diesem Lernprogramm lernen Sie, wie Sie diese Tools verwenden, um Pakete und ihre Abhängigkeiten auf einem Zielrechner zu installieren.    
    
Zuerst führen Sie Aufgaben aus, um die Bereitstellung vorzubereiten. Sie erstellen zunächst ein neues [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] und fügen diesem vorhandene Pakete und Datendateien hinzu. Sie erstellen keine neuen Pakete. Stattdessen arbeiten Sie nur mit fertigen Paketen, die speziell für dieses Lernprogramm erstellt wurden. Sie nehmen in diesem Lernprogramm keine Änderung der Funktionalität der Pakete vor. Nachdem Sie die Pakete dem Projekt hinzugefügt haben, sollten Sie sie jedoch im [!INCLUDE[ssIS](../includes/ssis-md.md)] -Designer öffnen und ihren Inhalt überprüfen. Durch Untersuchen der Pakete erhalten Sie Informationen zu Paketabhängigkeiten wie Protokolldateien und weiteren interessanten Funktionen der Pakete.    
    
Bei der Vorbereitung der Bereitstellung aktualisieren Sie die Pakete auch, um Konfigurationen zu verwenden. Durch die Konfigurationen können die Eigenschaften von Paketen und Paketobjekten zur Laufzeit aktualisiert werden. In diesem Lernprogramm verwenden Sie Konfigurationen, um die Verbindungszeichenfolgen der Protokoll- und Textdateien und die Speicherorte der XML- und XSD-Dateien, die vom Paket verwendet werden, zu aktualisieren. Weitere Informationen zu Konfigurationen finden Sie unter [Paketkonfigurationen](../integration-services/packages/package-configurations.md) und [Erstellen von Paketkonfigurationen](../integration-services/packages/create-package-configurations.md).    
    
Nachdem Sie überprüft haben, ob die Pakete erfolgreich in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]ausgeführt werden, erstellen Sie die Bereitstellungsgruppe, um die Pakete zu installieren. Die Bereitstellungsgruppe besteht aus den Paketdateien und weiteren Elementen, die Sie dem [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt hinzugefügt haben, den Paketabhängigkeiten, die [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] automatisch enthält, und dem von Ihnen erstellten Bereitstellungshilfsprogramm. Weitere Informationen finden Sie unter [Create a Deployment Utility](../integration-services/packages/create-a-deployment-utility.md).    
    
Sie kopieren dann die Bereitstellungsgruppe zum Zielrechner und führen den Paketinstallations-Assistenten aus, um die Pakete und Paketabhängigkeiten zu installieren. Die Pakete werden in der SQL Server-Datenbank msdb installiert, und die Unterstützungs- und Hilfsdateien werden im Dateisystem installiert. Da die bereitgestellten Pakete Konfigurationen verwenden, aktualisieren Sie die Konfiguration zur Verwendung neuer Werte, damit die Pakete erfolgreich in der neuen Umgebung ausgeführt werden können.    
    
Schließlich führen Sie die Pakete in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] mithilfe des Paketausführungshilfsprogramms aus.    
    
Es ist Ziel dieses Lernprogramms, die Komplexität von Bereitstellungsproblemen zu simulieren, die in der Praxis auftreten können. Wenn Sie die Pakete nicht auf einem anderen Computer bereitstellen können, können Sie dieses Lernprogramm dennoch ausführen. Dazu müssen Sie die Pakete in der msdb-Datenbank einer lokalen Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]installieren und dann von [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] auf derselben Instanz ausführen.    

**Geschätzte Zeit zum Bearbeiten dieses Tutorials:** 2 Stunden

## <a name="what-you-learn"></a>Ihre Lernziele    
Die beste Möglichkeit, den Umgang mit den neuen Tools, Steuerelementen und Funktionen von [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] zu üben, besteht in ihrer Verwendung. Dieses Lernprogramm führt Sie schrittweise durch die Erstellung eines [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekts und das anschließende Hinzufügen der Pakete und weiterer erforderlicher Dateien zum Projekt. Wenn das Projekt vollständig ist, erstellen Sie ein Bereitstellungspaket, kopieren es zum Zielcomputer und installieren dann die Pakete auf dem Zielcomputer.    
    
## <a name="prerequisites"></a>Voraussetzungen    
Dieses Tutorial wendet sich an Benutzer, die bereits mit grundlegenden Dateisystemvorgängen vertraut sind, aber nur über begrenzte Kenntnisse in Bezug auf die neuen Funktionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]verfügen. Um die grundlegenden [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Konzepte besser zu verstehen, deren Sie sich in diesem Tutorial bedienen, sollten Sie zuerst die folgenden [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Tutorials ausführen: [SSIS-Tutorials: Erstellen eines einfachen ETL-Pakets](../integration-services/ssis-how-to-create-an-etl-package.md).    
    
### <a name="on-the-source-computer"></a>Auf dem Quellcomputer

Auf dem Computer, auf dem Sie das Bereitstellungspaket erstellen, **müssen die folgenden Komponenten installiert sein**:

- SQL Server. (Laden Sie eine kostenlosen Evaluierungs- oder Entwicklerversion von SQL Server Sie unter [SQL Server-Downloads](https://www.microsoft.com/sql-server/sql-server-downloads) herunter.)

- Beispieldaten, fertige Pakete, Konfigurationen und eine Infodatei. Informationen zum Download der Beispieldaten sowie der Lektionspakete als ZIP-Datei finden Sie unter [Tutorial für SQL Server Integration Services: Erstellen eines einfachen ETL-Pakets](https://www.microsoft.com/download/details.aspx?id=56827). Die meisten Dateien in der ZIP-Datei sind schreibgeschützt, um unbeabsichtigte Änderungen zu verhindern. Um die Ausgabe in eine Datei zu schreiben oder zu ändern, müssen Sie unter Umständen das Nur-Lese-Attribut in den Dateieigenschaften deaktivieren.

-   Die Beispieldatenbank **AdventureWorks2014**. Laden Sie `AdventureWorks2014.bak` von der GitHub-Website[AdventureWorks sample databases](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) herunter, und stellen Sie die Sicherung wieder her, um die Datenbank **AdventureWorks2014** herunterzuladen.  

-   Sie müssen die Berechtigung zum Erstellen und Löschen von Tabellen in der AdventureWorks-Datenbank haben.
    
-   [SQL Server Data Tools (SSDT)](../ssdt/download-sql-server-data-tools-ssdt.md)    
    
### <a name="on-the-destination-computer"></a>Auf dem Zielcomputer

Auf dem Computer, auf dem Sie die Pakete bereitstellen, **müssen die folgenden Komponenten installiert sein:**    
    
- SQL Server. (Laden Sie eine kostenlosen Evaluierungs- oder Entwicklerversion von SQL Server Sie unter [SQL Server-Downloads](https://www.microsoft.com/sql-server/sql-server-downloads) herunter.)

- Beispieldaten, fertige Pakete, Konfigurationen und eine Infodatei. Informationen zum Download der Beispieldaten sowie der Lektionspakete als ZIP-Datei finden Sie unter [Tutorial für SQL Server Integration Services: Erstellen eines einfachen ETL-Pakets](https://www.microsoft.com/download/details.aspx?id=56827). Die meisten Dateien in der ZIP-Datei sind schreibgeschützt, um unbeabsichtigte Änderungen zu verhindern. Um die Ausgabe in eine Datei zu schreiben oder zu ändern, müssen Sie unter Umständen das Nur-Lese-Attribut in den Dateieigenschaften deaktivieren.

-   Die Beispieldatenbank **AdventureWorks2014**. Laden Sie `AdventureWorks2014.bak` von der GitHub-Website[AdventureWorks sample databases](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) herunter, und stellen Sie die Sicherung wieder her, um die Datenbank **AdventureWorks2014** herunterzuladen.  
    
- [SQL Server Management Studio](../ssms/download-sql-server-management-studio-ssms.md).    
    
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Weitere Informationen zur Installation von SSIS finden Sie unter [Installieren von Integration Services](install-windows/install-integration-services.md).
    
-   Sie benötigen Berechtigungen zum Erstellen und Löschen von Tabellen in der AdventureWorks-Datenbank und zum Ausführen von SSIS-Paketen in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].    
    
-   Sie müssen über Lese- und Schreibberechtigung für die `sysssispackages`-Tabelle in der `msdb`-Systemdatenbank von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] verfügen.    
    
Wenn Sie die Pakete auf demselben Computer bereitstellen möchten wie dem, auf dem Sie das Bereitstellungspaket erstellen, muss dieser Computer die Anforderungen sowohl des Quell- als auch des Zielcomputers erfüllen.    
        
## <a name="lessons-in-this-tutorial"></a>Lektionen in diesem Lernprogramm    
[Lektion 1: Vorbereiten der Erstellung des Bereitstellungspakets](../integration-services/lesson-1-preparing-to-create-the-deployment-bundle.md)    
In dieser Lektion beginnen Sie mit der Bereitstellung einer ETL-Lösung, indem Sie ein neues [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Projekt erstellen und diesem die Pakete und weitere erforderliche Dateien hinzufügen.    
    
[Lektion 2: Erstellen des Bereitstellungspakets in SSIS](../integration-services/lesson-2-create-the-deployment-bundle-in-ssis.md)    
In dieser Lektion erstellen Sie ein Bereitstellungshilfsprogramm und überprüfen, ob das Bereitstellungspaket die notwendigen Dateien enthält.    
    
[Lektion 3: Installieren von SSIS-Paketen](../integration-services/lesson-3-install-ssis-packages.md)    
In dieser Lektion kopieren Sie das Bereitstellungspaket auf den Zielcomputer, installieren die Pakete und führen diese dann aus.    
    

