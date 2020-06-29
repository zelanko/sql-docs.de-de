---
title: Entwickeln eines benutzerdefinierten Tasks | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom tasks [Integration Services], about custom tasks
- Task class
- custom tasks [Integration Services]
- SSIS custom tasks
- SSIS custom tasks, about custom tasks
- IDtsTaskUI interface
- DtsTaskAttribute attribute
- tasks [Integration Services], custom
- TaskHost object
ms.assetid: dcbd8615-fa6d-4ddb-b8a5-0b19dddd6239
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b4257d883b1f39e918f0f8a6eb8135e25b784a79
ms.sourcegitcommit: 04ba0ed3d860db038078609d6e348b0650739f55
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2020
ms.locfileid: "85469285"
---
# <a name="developing-a-custom-task"></a>Entwickeln eines benutzerdefinierten Tasks
  [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] nutzt Tasks, um Arbeitseinheiten auszuführen, die das Extrahieren, Umwandeln und Laden von Daten unterstützen. [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] beinhaltet verschiedene Tasks, durch die häufig auftretende Aktionen ausgeführt werden, z. B. das Ausführen von SQL-Anweisungen oder das Herunterladen einer Datei von einer FTP-Site. Wenn die enthaltenen Tasks und unterstützten Aktionen Ihre Anforderungen nicht vollständig erfüllen, können Sie einen benutzerdefinierten Task erstellen.  
  
 Zum Erstellen eines benutzerdefinierten Tasks müssen Sie eine Klasse erstellen, die von der Basisklasse [Microsoft. SqlServer. DTS. Runtime. Task](/dotnet/api/microsoft.sqlserver.dts.runtime.task) erbt, das- <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> Attribut auf die neue Klasse anwenden und die wichtigen Methoden und Eigenschaften der Basisklasse, einschließlich der-Methode, überschreiben <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A> .  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 In diesem Abschnitt wird beschrieben, wie Sie einen benutzerdefinierten Task und seine optionale benutzerdefinierte Benutzeroberfläche erstellen, konfigurieren und codieren.  
  
 [Erstellen eines benutzerdefinierten Tasks](creating-a-custom-task.md)  
 Beschreibt den ersten Schritt, durch den der benutzerdefinierte Task erstellt wird.  
  
 [Codieren eines benutzerdefinierten Tasks](coding-a-custom-task.md)  
 Beschreibt, wie die Hauptmethoden eines benutzerdefinierten Tasks codiert werden.  
  
 [Herstellen einer Verbindung mit Datenquellen in einem benutzerdefinierten Task](connecting-to-data-sources-in-a-custom-task.md)  
 Beschreibt, wie Sie einen benutzerdefinierten Task mit einer Datenquelle verbinden können.  
  
 [Auslösen und Definieren von Ereignissen in einem benutzerdefinierten Task](raising-and-defining-events-in-a-custom-task.md)  
 Beschreibt, wie Ereignisse ausgelöst und benutzerdefinierte Ereignisse in dem benutzerdefinierten Task definiert werden.  
  
 [Bereitstellen von Unterstützung für das Debuggen in einem benutzerdefinierten Task](adding-support-for-debugging-in-a-custom-task.md)  
 Beschreibt, wie Breakpointziele in dem benutzerdefinierten Task erstellt werden.  
  
 [Entwickeln einer Benutzeroberfläche für einen benutzerdefinierten Task](developing-a-user-interface-for-a-custom-task.md)  
 Beschreibt, wie eine Benutzeroberfläche erstellt wird, die im [!INCLUDE[ssIS](../../../includes/ssis-md.md)]-Designer angezeigt wird, um Eigenschaften für den benutzerdefinierten Task zu konfigurieren.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
  
### <a name="information-common-to-all-custom-objects"></a>Informationen, die für alle benutzerdefinierten Objekte gelten  
 Informationen zu allen Arten benutzerdefinierter Objekte, die Sie in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] erstellen können, finden Sie in den folgenden Themen:  
  
 [Entwickeln benutzerdefinierter Objekte für Integration Services](../developing-custom-objects-for-integration-services.md)  
 Beschreibt die grundlegenden Schritte bei der Implementierung aller Arten von benutzerdefinierten Objekten in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].  
  
 [Beibehalten von benutzerdefinierten Objekten](../persisting-custom-objects.md)  
 Beschreibt die benutzerdefinierte Persistenz und erklärt, wann diese notwendig ist.  
  
 [Erstellen, Bereitstellen und Debuggen von benutzerdefinierten Objekten](../building-deploying-and-debugging-custom-objects.md)  
 Beschreibt die Techniken für das Erstellen, Signieren, Bereitstellen und Debuggen von benutzerdefinierten Objekten.  
  
### <a name="information-about-other-custom-objects"></a>Informationen zu anderen benutzerdefinierten Objekten  
 Informationen zu den anderen Arten benutzerdefinierter Objekte, die Sie in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] erstellen können, finden Sie in den folgenden Themen:  
  
 [Entwickeln eines benutzerdefinierten Verbindungs-Managers](../connection-manager/developing-a-custom-connection-manager.md)  
 Erläutert die Programmierung benutzerdefinierter Verbindungs-Manager.  
  
 [Entwickeln eines benutzerdefinierten Protokollanbieters](../log-provider/developing-a-custom-log-provider.md)  
 Erläutert die Programmierung benutzerdefinierter Protokollanbieter.  
  
 [Entwickeln eines benutzerdefinierten ForEach-Enumerators](../foreach-enumerator/developing-a-custom-foreach-enumerator.md)  
 Erläutert die Programmierung benutzerdefinierter Enumeratoren.  
  
 [Entwickeln einer benutzerdefinierten Datenflusskomponente](../data-flow/developing-a-custom-data-flow-component.md)  
 Erläutert die Programmierung benutzerdefinierter Datenflussquellen, Transformationen und Ziele.  
  
![Integration Services Symbol (klein)](../../media/dts-16.gif "Integration Services (kleines Symbol)")immer auf**dem neuesten Stand bleiben mit Integration Services**  <br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweitern des Pakets mit dem Skript Task](../../extending-packages-scripting/task/extending-the-package-with-the-script-task.md)   
 [Vergleichen von Skriptlösungen und benutzerdefinierten Objekten](../../extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md)  
  
  
