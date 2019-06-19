---
title: 'Gewusst wie: Installieren und Verwalten von Funktionserweiterungen | Microsoft-Dokumentation'
ms.custom:
- SSDT
ms.date: 04/26/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 9cdc8cd5-c36f-4bee-a191-87ed457803e7
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 3240bd208a13342782fefeb19532fbabed7e81e1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65099679"
---
# <a name="how-to-install-and-manage-feature-extensions"></a>Gewusst wie: Installieren und Verwalten von Funktionserweiterungen
Sie können Regeln zum Analysieren von Datenbankcode, Bedingungen für Datenbankkomponententests und Erstellungs-/Bereitstellungs-Contributors hinzufügen, um die Funktionalität von Visual Studio-Editionen, einschließlich SQL Server Data Tools, zu erweitern. Bevor eine Funktionserweiterung verwendet werden kann, muss sie jedoch installiert werden, unabhängig davon, ob die zu installierende Erweiterung von Ihnen oder einer anderen Person erstellt wurde.  
  
Wo Ihre Erweiterung installiert wird, hängt von Erweiterungstyp und dem beabsichtigten Einsatzort ab. In den neuesten Editionen von Visual Studio wurde der Installationsspeicherort einiger Komponenten vom SQL Server-Installationsverzeichnis in das Visual Studio-Verzeichnis verschoben. Dies erleichtert die Koexistenz mehrerer Versionen der Software, bringt jedoch mit sich, dass Sie Ihre Erweiterung möglicherweise an mehreren Speicherorten installieren müssen, wenn Sie sie in verschiedenen Versionen von SQL Server Data Tools sowie in der Befehlszeile verwenden möchten.  
  
### <a name="installing-extensions-for-use-inside-visual-studio"></a>Installieren von Erweiterungen für die interne Verwendung in Visual Studio  
  
|Erweiterungstyp|Installationsspeicherort|  
|------------------|--------------------|  
|Benutzerdefinierte Testbedingung für SQL Server-Komponententests|<Visual Studio Install Dir>\Common7\IDE\Extensions\\Microsoft\SQLDB\TestConditions|  
|Erstellungs-Contributors<br /><br />Bereitstellungs-Contributors<br /><br />Regeln für die statische Codeanalyse|<Visual Studio Install Dir>\Common7\IDE\Extensions\\Microsoft\SQLDB\DAC\120\Extensions|  
  
Das <Visual Studio Install Dir> unterscheidet sich je nach verwendeter Visual Studio-Version und dem gewählten Installationspfad. Bei Visual Studio 2012 befindet es sich in der Regel im Verzeichnis „C:\Programme (x86)\\MicrosoftVisual Studio 11.0“. Bei Visual Studio 2013 befindet es sich in der Regel im Verzeichnis „C:\Programme (x86)\\MicrosoftVisual Studio 12.0“.  
  
Erweiterungen können außerdem als Teil der Befehlszeilendienste ausgeführt werden:  
  
|Erweiterungstyp|Befehlszeilendienst|Installationsordner|  
|------------------|------------------------|------------------|  
|Benutzerdefinierte Testbedingung für SQL Server-Komponententests|MSBuild/MSTest kann zum Ausführen von Komponententests an der Developer-Eingabeaufforderung für Visual Studio 2013 und in ähnlichen Befehlszeilentools verwendet werden.|Gleich wie für die interne Ausführung in Visual Studio.|  
|Erstellungs-Contributors<br /><br />Bereitstellungs-Contributors|[SqlPackage.exe](../tools/sqlpackage.md) oder durch Verwendung von Deploy- oder Publish-Zielen von MSBuild beim Erstellen eines Datenbankprojekts.|MSBuild: Gleich wie für die interne Ausführung in Visual Studio.<br /><br />[SqlPackage.exe](../tools/sqlpackage.md): Gleich wie zuvor, sofern im Visual Studio-Verzeichnis gespeichert.<br /><br />Wenn sich „SqlPackage.exe“ und andere DACFx-DLLs außerhalb dieses Verzeichnisses befinden, sollten Erweiterungen entweder im gleichen Verzeichnis oder unter „C:\Programme (x86)\\MicrosoftSQL Server\120\DAC\bin\Extensions“ platziert werden.|  
|Regeln für die statische Codeanalyse|MSBuild kann zum Erstellen des Projekts und zum Ausführen der statischen Codeanalyse verwendet werden.<br /><br />Darüber hinaus können Sie die Codeanalyse mithilfe einer CodeAnalysisService-API aus eigenen Anwendungen heraus ausführen. Die Suchregeln für Erweiterungen funktionieren in diesem Fall genau wie bei der Verwendung von „SqlPackage.exe“.|Das gleiche gilt für Erstellungs- und Bereitstellung-Contributors|  
  
> [!NOTE]  
> Sie müssen über Administratorberechtigungen auf dem Computer verfügen, um auf die Installationsverzeichnisse unter dem Ordner „Programme“ zuzugreifen. Wenn Sie nicht über die entsprechenden Berechtigungen verfügen, wenden Sie sich an Ihren Netzwerkadministrator.  
  
**Überlegungen zur Sicherheit**  
  
Vor der Installation einer Erweiterung, die nicht von Ihnen erstellt wurde, sollten Sie sich die folgenden Risiken vergegenwärtigen:  
  
-   Das Installationsprogramm für die Erweiterung könnte Schadsoftware sein, die je nach Ihren Installationsberechtigungen Zugriff auf geschützte Ressourcen erlangen könnte.  
  
-   Auch die Erweiterung selbst kann schädlich sein und Kontrolle über geschützte Ressourcen erlangen, sofern der Benutzer, der die Erweiterung verwendet, über ausreichende Berechtigungen verfügt.  
  
Um das Risiko zu minimieren, sollten Sie nur Erweiterungen aus bekannten Quellen installieren. Falls Sie eine Erweiterung aus einer nicht vertrauenswürdigen Quelle erhalten, sollten Sie den Quellcode der Erweiterung sowie deren Installationsprogramm (falls vorhanden) vor der Installation und Verwendung der Erweiterung überprüfen.  
  
## <a name="to-install-a-custom-feature-extension"></a>So installieren Sie eine benutzerdefinierte Funktionserweiterung  
Kopieren Sie die signierte Assembly (.dll) in den richtigen Installationsordner. Schließen Sie Visual Studio, und öffnen Sie es wieder. Die Erweiterung sollte jetzt verfügbar sein.  
  
## <a name="see-also"></a>Weitere Informationen  
[Erweitern der Datenbankfunktionen](../ssdt/extending-the-database-features.md)  
  
