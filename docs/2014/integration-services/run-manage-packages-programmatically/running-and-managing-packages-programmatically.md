---
title: Programmgesteuerte Ausführung und Verwaltung von Paketen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
ms.assetid: 1a08c75e-ce8c-45ee-81bd-32248bbdb2b2
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: ecbaa54a723fae6a3c5fd11363bf42f1f2a57da0
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2019
ms.locfileid: "58376468"
---
# <a name="running-and-managing-packages-programmatically"></a>Programmgesteuerte Ausführung und Verwaltung von Paketen
  Wenn Sie [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Pakete außerhalb der Entwicklungsumgebung verwalten und ausführen müssen, können Sie Pakete programmgesteuert ändern. Dieser Ansatz bietet Ihnen eine Reihe von Optionen:  
  
-   Laden und Ausführen eines vorhandenen Pakets ohne Änderung  
  
-   Laden, Neukonfigurieren (z. B. für eine andere Datenquelle) und Ausführen eines vorhandenen Pakets  
  
-   Erstellen eines neuen Pakets, Hinzufügen und Konfigurieren von Komponenten Objekt um Objekt und Eigenschaft um Eigenschaft, Speichern und Ausführen des Pakets  
  
 Sie können auch ein vorhandenes Paket von einer Clientanwendung aus laden und ausführen, indem Sie nur einige Zeilen Code schreiben.  
  
 In diesem Abschnitt wird beschrieben und veranschaulicht, wie ein vorhandenes Paket programmgesteuert ausgeführt wird und wie auf die Ausgabe des Datenflusses anderer Anwendungen zugegriffen werden kann. Als erweiterte Programmieroption können Sie Zeile für Zeile ein [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Paket programmgesteuert erstellen, wie im Thema [Programmgesteuertes Erstellen von Paketen](../building-packages-programmatically/building-packages-programmatically.md) beschrieben.  
  
 In diesem Abschnitt werden auch weitere administrative Tasks behandelt, die Sie programmgesteuert ausführen können, um gespeicherte und ausgeführte Pakete sowie Paketrollen zu verwalten.  
  
## <a name="running-packages-on-the-integration-services-server"></a>Ausführen von Paketen auf dem Integration Services-Server  
 Wenn Sie Pakete auf dem [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Server bereitstellen, können Sie die Pakete programmgesteuert unter Verwendung des <xref:Microsoft.SqlServer.Management.IntegrationServices>-Namespaces ausführen. Die Microsoft.SqlServer.Management.IntegrationServices-Assembly wird mit .NET Framework 3.5 kompiliert. Wenn Sie eine .NET Framework 4.0-Anwendung erstellen, müssen Sie der Projektdatei den Assemblyverweis möglicherweise direkt hinzufügen.  
  
 Sie können auch den Namespace verwenden, um [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Projekte auf dem [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Server bereitzustellen und zu verwalten. Eine Übersicht über den Namespace und die Codeausschnitte finden Sie im Blogeintrag [Ein Blick auf das verwaltete Objektmodell des SSIS-Katalogs](https://go.microsoft.com/fwlink/?LinkId=253122) (Überblick über das SSIS-Katalogmodell verwalteter Objekte) auf blogs.msdn.com.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Grundlegendes zu den Unterschieden zwischen der lokalen und der Remoteausführung](../run-manage-packages-programmatically/understanding-the-differences-between-local-and-remote-execution.md)  
 Erläutert wichtige Unterschiede zwischen der Ausführung eines Pakets in der lokalen Umgebung oder auf dem Server.  
  
 [Programmgesteuertes Laden und Ausführen eines lokalen Pakets](../run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md)  
 Beschreibt, wie ein vorhandenes Paket von einer Clientanwendung auf dem lokalen Computer ausgeführt wird.  
  
 [Programmgesteuertes Laden und Ausführen eines Remotepakets](../run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md)  
 Beschreibt die Ausführung eines vorhandenes Pakets von einer Clientanwendung und wie sichergestellt wird, dass das Paket auf dem Server ausgeführt wird.  
  
 [Laden der Ausgabe eines lokalen Pakets](../run-manage-packages-programmatically/loading-the-output-of-a-local-package.md)  
 Beschreibt, wie ein Paket auf dem lokalen Computer ausgeführt und die Ausgabe des Datenflusses unter Verwendung des DataReader-Ziels und des DtsClient-Namespaces in eine Clientanwendung geladen wird.  
  
 [Programmgesteuertes Auflisten verfügbarer Pakete](../run-manage-packages-programmatically/enumerating-available-packages-programmatically.md)  
 Beschreibt, wie verfügbare Pakete, die vom [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Dienst verwaltet werden, ermittelt werden.  
  
 [Programmgesteuerte Verwaltung von Paketen und Ordnern](../run-manage-packages-programmatically/managing-packages-and-folders-programmatically.md)  
 Beschreibt das Erstellen, Umbenennen und Löschen von Paketen und Ordnern.  
  
 [Programmgesteuerte Verwaltung von ausgeführten Paketen](../run-manage-packages-programmatically/managing-running-packages-programmatically.md)  
 Beschreibt, wie Pakete, die gerade ausgeführt werden, aufgelistet werden, wie ihre Eigenschaften untersucht werden und wie ein ausgeführtes Paket beendet werden kann.  
  
 [Programmgesteuertes Verwalten von Paketrollen &#40;SSIS-Dienst&#41;](../run-manage-packages-programmatically/managing-package-roles-programmatically-ssis-service.md)  
 Beschreibt, wie Informationen über die einem Paket oder einem Ordner zugewiesenen Rollen abgerufen oder festgelegt werden können.  
  
## <a name="reference"></a>Referenz  
 [Fehler- und Meldungsreferenz von Integration Services](../integration-services-error-and-message-reference.md)  
 Listet die vordefinierten [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Fehlercodes mit ihren symbolischen Namen und Beschreibungen auf.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Erweitern von Paketen mit Skripts](../extending-packages-scripting/extending-packages-with-scripting.md)  
 Erläutert, wie die Ablaufsteuerung mithilfe des Skripttasks und der Datenfluss mithilfe der Skriptkomponente erweitert werden können.  
  
 [Erweitern von Paketen mit benutzerdefinierten Objekten](../extending-packages-custom-objects/extending-packages-with-custom-objects.md)  
 Beschreibt, wie benutzerdefinierte Tasks, Datenflusskomponenten und andere Paketobjekte für die Verwendung in mehreren Paketen erstellt und programmiert werden.  
  
 [Programmgesteuertes Erstellen von Paketen](../building-packages-programmatically/building-packages-programmatically.md)  
 Erläutert, wie [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Pakete programmgesteuert erstellt, konfiguriert und gespeichert werden können.  
  
![Integration Services (kleines Symbol)](../media/dts-16.gif "Integration Services (kleines Symbol)")**bleiben oben, um das Datum mit Integration Services**<br /> Die neuesten Downloads, Artikel, Beispiele und Videos von [!INCLUDE[msCoName](../../includes/msconame-md.md)] sowie ausgewählte Lösungen aus der Community finden Sie auf der [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Seite auf MSDN:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server Integration Services](../sql-server-integration-services.md)  
  
  
