---
title: Erweitern von Paketen mit benutzerdefinierten Objekten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
ms.assetid: 26616eb8-9e80-434d-b22a-ece1b00f449d
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: d7384fd52f28f52647c310f7c76eec994b8c8141
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62896208"
---
# <a name="extending-packages-with-custom-objects"></a>Erweitern von Paketen mit benutzerdefinierten Objekten
  Wenn die in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] bereitgestellten Komponenten nicht Ihren Anforderungen entsprechen, können Sie die Effektivität von [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] durch Codieren eigener Erweiterungen erhöhen. Ihnen stehen zwei unterschiedliche Optionen zur Erweiterung der Pakete zur Verfügung: Sie können Code in die leistungsstarken Wrapper schreiben, die vom Skripttask und der Skriptkomponente bereitgestellt werden, oder benutzerdefinierte [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Erweiterungen durch Ableitung von den Basisklassen, die im [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Objektmodell zur Verfügung stehen, vollständig neu erstellen.  
  
 In diesem Abschnitt wird die erweiterte der beiden Optionen beschrieben: das Erweitern von Paketen mit benutzerdefinierten Objekten.  
  
 Wenn die benutzerdefinierte [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Lösung mehr Flexibilität als das Skripttask und die Skriptkomponente erfordert, oder wenn Sie eine Komponente benötigen, die in mehreren Paketen wieder verwendet wird, dann ermöglicht Ihnen das [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Objektmodell, benutzerdefinierte Tasks, Datenflusskomponenten und andere Paketobjekte zu erstellen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Entwickeln benutzerdefinierter Objekte für Integration Services](developing-custom-objects-for-integration-services.md)  
 Erläutert die benutzerdefinierten Objekte, die für [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] erstellt werden können, und fasst die wesentlichen Schritte und Einstellungen zusammen.  
  
 [Beibehalten von benutzerdefinierten Objekten](persisting-custom-objects.md)  
 Erläutert die Standardpersistenz benutzerdefinierter Objekte sowie den Prozess der Implementierung von benutzerdefinierter Persistenz.  
  
 [Erstellen, Bereitstellen und Debuggen von benutzerdefinierten Objekten](building-deploying-and-debugging-custom-objects.md)  
 Erläutert die gebräuchlichen Verfahren des Erstellens, Bereitstellens und Testens der verschiedenen Typen benutzerdefinierter Objekte.  
  
 [Entwickeln eines benutzerdefinierten Tasks](task/developing-a-custom-task.md)  
 Beschreibt den Prozess des Codierens eines benutzerdefinierten Tasks.  
  
 [Entwickeln eines benutzerdefinierten Verbindungs-Managers](connection-manager/developing-a-custom-connection-manager.md)  
 Beschreibt den Prozess des Codierens eines benutzerdefinierten Verbindungs-Managers.  
  
 [Entwickeln eines benutzerdefinierten Protokollanbieters](log-provider/developing-a-custom-log-provider.md)  
 Beschreibt den Prozess des Codierens eines benutzerdefinierten Protokollanbieters.  
  
 [Entwickeln eines benutzerdefinierten ForEach-Enumerators](foreach-enumerator/developing-a-custom-foreach-enumerator.md)  
 Beschreibt den Prozess des Codierens eines benutzerdefinierten Enumerators.  
  
 [Entwickeln einer benutzerdefinierten Datenflusskomponente](data-flow/developing-a-custom-data-flow-component.md)  
 Erläutert die Programmierung benutzerdefinierter Datenflussquellen, Transformationen und Ziele.  
  
## <a name="reference"></a>Verweis  
 [Fehler- und Meldungsreferenz von Integration Services](../integration-services-error-and-message-reference.md)  
 Listet die vordefinierten [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Fehlercodes mit ihren symbolischen Namen und Beschreibungen auf.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Erweitern von Paketen mit Skripts](../extending-packages-scripting/extending-packages-with-scripting.md)  
 Beschreibt, wie die Ablaufsteuerung mithilfe des Skripttasks bzw. der Datenfluss mithilfe der Skriptkomponente erweitert werden können.  
  
 [Programmgesteuertes Erstellen von Paketen](../building-packages-programmatically/building-packages-programmatically.md)  
 Erläutert, wie [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Pakete programmgesteuert erstellt, konfiguriert, ausgeführt, geladen, gespeichert und verwaltet werden.  
  
![Integration Services Symbol (klein)](../media/dts-16.gif "Integration Services (kleines Symbol)")immer auf**dem neuesten Stand bleiben mit Integration Services**  <br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Vergleichen von Skript Lösungen und benutzerdefinierten Objekten](../extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md)   
 [SQL Server Integration Services](../sql-server-integration-services.md)  
  
  
