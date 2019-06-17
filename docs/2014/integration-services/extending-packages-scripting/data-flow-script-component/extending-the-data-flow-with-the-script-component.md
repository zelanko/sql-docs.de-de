---
title: Erweitern des Datenflusses mit der Skriptkomponente | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- data flow task [Integration Services], components
- data flow [Integration Services], extending
- debugging [Integration Services], components
- code design mode [Integration Services]
- metadata [Integration Services]
- scripts [Integration Services], extending data flow
- data flow components [Integration Services], Script component
- components [Integration Services], data flow
- Script component [Integration Services], about Script component
- Script component [Integration Services]
- data flow [Integration Services], components
ms.assetid: 072bc4b8-363a-4131-87c3-240338e2fa5c
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 051f2ed14e8218a3909a43052f08e0e339138dab
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62894804"
---
# <a name="extending-the-data-flow-with-the-script-component"></a>Erweitern des Datenflusses mit der Skriptkomponente
  Die Skriptkomponente erweitert die Datenflussfunktionen von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]-Paketen durch benutzerdefinierten Code, der in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic oder [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# geschrieben ist und zur Laufzeit des Pakets kompiliert und ausgeführt wird. Die Skriptkomponente vereinfacht die Entwicklung von benutzerdefinierten Datenflussquellen, -transformationen oder -zielen, falls die in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] enthaltenen Quellen, Transformationen und Ziele Ihre Anforderungen nicht voll erfüllen. Nach Konfiguration der Komponente mit den erwarteten Eingaben und Ausgaben schreibt sie den nötigen Infrastrukturcode für Sie, damit Sie sich vollständig auf den Code konzentrieren können, der für die benutzerdefinierte Verarbeitung erforderlich ist.  
  
 Eine Skriptkomponente interagiert mit dem entsprechenden Paket und dem Datenfluss über die automatisch erzeugten Klassen in den Projektelementen `ComponentWrapper` und `BufferWrapper`, die jeweils Instanzen der <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent>-Klasse und der <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer>-Klasse sind. Diese Klassen machen Verbindungen, Variablen und andere Paketelemente als typisierte Objekte verfügbar und verwalten Eingaben und Ausgaben. Die Skriptkomponente kann außerdem den [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]-Namespace und die [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]-Klassenbibliothek sowie benutzerdefinierte Assemblys zum Implementieren benutzerdefinierter Funktionen verwenden.  
  
 Die Skriptkomponente und der Infrastrukturcode, den sie generieren, erleichtern Ihnen die Entwicklung benutzerdefinierter Datenflusskomponenten deutlich. Um die Funktionsweise der Skriptkomponente zu verstehen, kann es jedoch hilfreich sein, den Abschnitt [Entwickeln einer benutzerdefinierten Datenflusskomponente](../../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md) zu lesen. Dort werden die Schritte erläutert, die bei der Entwicklung einer benutzerdefinierten Datenflusskomponente durchlaufen werden.  
  
 Wenn Sie eine Quelle, Transformation oder ein Ziel erstellen, das Sie in mehreren Paketen wiederverwenden möchten, sollten Sie keine Skriptkomponente verwenden, sondern eine benutzerdefinierte Komponente entwickeln. Weitere Informationen finden Sie unter [Entwickeln einer benutzerdefinierten Datenflusskomponente](../../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 In den folgenden Themen werden weitere Informationen zur Skriptkomponente bereitgestellt.  
  
 [Konfigurieren der Skriptkomponente im Skriptkomponenten-Editor](configuring-the-script-component-in-the-script-component-editor.md)  
 Eigenschaften, die Sie im **Transformations-Editor für Skripterstellung** konfigurieren, wirken sich auf die Funktionen und die Leistung des Codes in der Skriptkomponente aus.  
  
 [Coding and Debugging the Script Component] (coding-and-debugging-the-script-component.md  
 Die [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications-Entwicklungsumgebung (VSTA) wird zum Entwickeln der in der Skriptkomponente enthaltenen Skripts verwendet.  
  
 [Grundlegendes zum Skript-Komponentenobjektmodell](understanding-the-script-component-object-model.md)  
 Ein neues Skriptkomponentenprojekt enthält drei Projektelemente mit mehreren Klassen sowie automatisch generierten Eigenschaften und Methoden.  
  
 [Verwenden von Variablen in der Skriptkomponente](using-variables-in-the-script-component.md)  
 Das `ComponentWrapper`-Projektelement enthält Accessoreigenschaften mit starker Typbindung für Paketvariablen.  
  
 [Herstellen einer Verbindung zu Datenquellen in der Skriptkomponente](connecting-to-data-sources-in-the-script-component.md)  
 Das `ComponentWrapper`-Projektelement enthält auch Accessoreigenschaften mit starker Typbindung für im Paket definierte Verbindungen.  
  
 [Auslösen von Ereignissen in der Skriptkomponente](raising-events-in-the-script-component.md)  
 Sie können Ereignisse auslösen, um die Benachrichtigung von Problemen und Fehlern sicherzustellen.  
  
 [Protokollieren in der Skriptkomponente](logging-in-the-script-component.md)  
 Sie können Informationen für im Paket aktivierte Protokollanbieter protokollieren.  
  
 [Entwickeln bestimmter Arten von Skriptkomponenten](../../extending-packages-scripting-data-flow-script-component-types/developing-specific-types-of-script-components.md)  
 Diese einfachen Beispiele erläutern und veranschaulichen, wie mithilfe der Skriptkomponente benutzerdefinierte Datenflussquellen, Transformationen und Ziele entwickelt werden.  
  
 [Zusätzliche Skriptkomponentenbeispiele](../../extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md)  
 In diesen einfachen Beispielen werden einige mögliche Verwendungsbereiche für die Skriptkomponente erklärt und veranschaulicht.  
  
![Integration Services (kleines Symbol)](../../media/dts-16.gif "Integration Services (kleines Symbol)")**bleiben oben, um das Datum mit Integration Services**<br /> Die neuesten Downloads, Artikel, Beispiele und Videos von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] sowie ausgewählte Lösungen aus der Community finden Sie auf der [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]-Seite auf MSDN:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.  
  
## <a name="see-also"></a>Siehe auch  
 [Skriptkomponente](../../data-flow/transformations/script-component.md)   
 [Vergleich zwischen Skripttask und Skriptkomponente](../comparing-the-script-task-and-the-script-component.md)  
  
  
