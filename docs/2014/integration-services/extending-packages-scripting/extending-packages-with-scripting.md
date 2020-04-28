---
title: Erweitern von Paketen mit Skripts | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- SQL Server Integration Services, scripting
- SSIS, scripting
- scripts [Integration Services], about scripting
ms.assetid: 67fe18ef-f3aa-41d4-9b9d-5defd4618c4b
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: bb567bffe0c184907ca61bd583eb5666948a0f03
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "78176182"
---
# <a name="extending-packages-with-scripting"></a>Erweitern von Paketen mit Skripts
  Wenn die integrierten Komponenten in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Ihren Anforderungen nicht entsprechen, können Sie die Effektivität von [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] durch Codieren eigener Erweiterungen erhöhen. Ihnen stehen zwei unterschiedliche Optionen zur Erweiterung der Pakete zur Verfügung: Sie können Code in die leistungsstarken Wrapper schreiben, die vom Skripttask und der Skriptkomponente bereitgestellt werden, oder benutzerdefinierte [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Erweiterungen durch Ableitung von den Basisklassen, die im [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Objektmodell zur Verfügung stehen, vollständig neu erstellen.

 In diesem Abschnitt wird die einfachere der zwei Optionen beschrieben: das Erweitern von Paketen mit Skripts.

 Mit dem Skripttask und der Skriptkomponente können Sie sowohl die Ablaufsteuerung als auch den Datenfluss eines [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Pakets mit minimaler Codierung erweitern. Für beide Objekte werden die Entwicklungsumgebung von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) und die Programmiersprachen [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic oder [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# verwendet sowie alle Funktionen der [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]-Klassenbibliothek einschließlich benutzerdefinierter Assemblys. Mit dem Skripttask und der Skriptkomponente können Entwickler benutzerdefinierte Funktionen erstellen, ohne den kompletten Infrastrukturcode schreiben zu müssen, der normalerweise bei der Entwicklung einer benutzerdefinierten Aufgabe oder Datenflusskomponente erforderlich ist.

## <a name="in-this-section"></a>In diesem Abschnitt
 [Vergleichen des Skript Tasks und der Skript Komponente](../extending-packages-scripting/comparing-the-script-task-and-the-script-component.md) Erläutert die Ähnlichkeiten und Unterschiede zwischen dem Skript Task und der Skript Komponente.

 [Vergleichen von Skript Lösungen und benutzerdefinierten Objekten](comparing-scripting-solutions-and-custom-objects.md) Erläutert die Kriterien für die Auswahl zwischen einer Skript Erstellungs Lösung und der Entwicklung eines benutzerdefinierten Objekts.

 [Verweisen auf andere Assemblys in Skript Lösungen](referencing-other-assemblies-in-scripting-solutions.md) Erläutert die Schritte, die zum Verweisen auf und Verwenden externer Assemblys und Namespaces in einem Skript Projekt erforderlich sind.

 [Erweitern des Pakets mit dem Skript Task](../extending-packages-scripting/task/extending-the-package-with-the-script-task.md) Erläutert, wie benutzerdefinierte Tasks mit dem Skript Task erstellt werden. Ein Task wird normalerweise einmal pro Paketausführung aufgerufen oder einmal für jede Datenquelle, die ein Paket öffnet.

 [Erweitern des Datenflusses mit der Skript Komponente](data-flow-script-component/extending-the-data-flow-with-the-script-component.md) Erläutert, wie mithilfe der Skript Komponente benutzerdefinierte Datenfluss Quellen, Transformationen und Ziele erstellt werden. Eine Datenflusskomponente wird i. d. R. für jede verarbeitete Datenzeile einmal aufgerufen.

## <a name="reference"></a>Verweis
 [Fehler-und](../integration-services-error-and-message-reference.md) Meldungs Referenz für Integration Services Listet die vordefinierten [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Fehlercodes mit ihren symbolischen Namen und Beschreibungen auf.

## <a name="related-sections"></a>Verwandte Abschnitte
 [Erweitern von Paketen mit benutzerdefinierten Objekten](../extending-packages-custom-objects/extending-packages-with-custom-objects.md) Erläutert, wie benutzerdefinierte Programm Tasks, Datenfluss Komponenten und andere Paket Objekte für die Verwendung in mehreren Paketen erstellt werden.

 [Programm](../building-packages-programmatically/building-packages-programmatically.md) gesteuertes entwickeln von Paketen Hier wird beschrieben, wie Pakete Programm gesteuert erstellt, konfiguriert, ausgeführt, geladen [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , gespeichert und verwaltet werden.

![Integration Services Symbol (klein)](../media/dts-16.gif "Integration Services (kleines Symbol)")immer auf**dem neuesten Stand bleiben mit Integration Services**  <br /> Die neuesten Downloads, Artikel, Beispiele und Videos von [!INCLUDE[msCoName](../../includes/msconame-md.md)] sowie ausgewählte Lösungen aus der Community finden Sie auf der [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Seite auf MSDN:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.

## <a name="see-also"></a>Weitere Informationen
 [SQL Server Integration Services](../sql-server-integration-services.md)


