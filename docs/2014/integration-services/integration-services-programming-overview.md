---
title: Übersicht über die Programmierung von Integration Services | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/25/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Integration Services, programming
- architecture [Integration Services]
- assemblies [Integration Services]
- SSIS, programming
- SQL Server Integration Services, programming
- run-time engine [Integration Services]
- packages [Integration Services], programming
- data flow engine [Integration Services]
- languages [Integration Services]
ms.assetid: 262babc6-eea5-4609-bc65-07d64cbcfee9
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 4bf90de7f1ebcadbc65b6f2ee7eaaacb6d52e0e1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "74683625"
---
# <a name="integration-services-programming-overview"></a>Übersicht über die Programmierung von 'Integration Services'
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] verfügt über eine Architektur, die die Daten Verschiebung und-Transformation von der Paket Ablauf Steuerung und-Verwaltung trennt. Diese Architektur wird durch zwei unterschiedliche Engines definiert, die bei der Programmierung von [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] automatisiert und erweitert werden können. Die Runtime-Engine implementiert die Infrastruktur der Ablaufsteuerung und Paketverwaltung, mit deren Hilfe Entwickler den Ausführungsprozess steuern und Optionen für die Protokollierung, Ereignishandler und Variablen festlegen können. Die Datenfluss-Engine ist eine spezialisierte Hochleistungs-Engine, die ausschließlich dem Extrahieren, Transformieren und Laden von Daten dient. Beim Programmieren von [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] programmieren Sie mit diesen beiden Engines.  
  
 Im folgenden Bild wird die Architektur von [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] dargestellt.  
  
 ![Integration Services-Architektur](media/mw-dts-01.gif "Integration Services-Architektur")  
  
## <a name="integration-services-run-time-engine"></a>Integration Services-Runtime-Engine  
 Das [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]-Runtime-Engine steuert durch die Implementierung der Infrastruktur, die die Ausführungsreihenfolge, Protokollierung, Variablen und die Ereignisbehandlung ermöglicht, die Verwaltung und Ausführung von Paketen. Durch die Programmierung der [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]-Runtime-Engine können Entwickler die Erstellung, Konfiguration und Ausführung von Paketen automatisieren sowie benutzerdefinierte Tasks und andere Erweiterungen erstellen.  
  
 Weitere Informationen finden Sie unter [Erweitern von Paketen mithilfe des Skripttasks](extending-packages-scripting/task/extending-the-package-with-the-script-task.md), [Entwickeln eines benutzerdefinierten Tasks](extending-packages-custom-objects/task/developing-a-custom-task.md) und [Programmgesteuertes Erstellen von Paketen](building-packages-programmatically/building-packages-programmatically.md).  
  
## <a name="integration-services-data-flow-engine"></a>Integration Services-Datenfluss-Engine  
 Die Datenfluss-Engine verwaltet den Datenflusstask. Dies ist ein spezialisierter Hochleistungstask, der dem Verschieben und Transformieren von Daten verschiedener Quellen dient. Im Gegensatz zu anderen Tasks enthält der Datenflusstask zusätzliche Objekte, die sogenannten Datenflusskomponenten, bei denen es sich um Quellen, Transformationen oder Ziele handeln kann. Diese Komponenten sind die wichtigsten verschiebbaren Teile des Tasks. Sie definieren die Bewegung und die Transformation von Daten. Durch die Programmierung der Runtime-Engine können Entwickler die Erstellung und Konfiguration der Komponenten in einem Datenflusstask automatisieren sowie benutzerdefinierte Komponenten erstellen.  
  
 Weitere Informationen finden Sie unter [Erweitern des Datenflusses mit der Skript Komponente] (Erweitern von Paketen-Scripting/Data-Flow-Script-Component/Extending-the-Data-Flow-with-the-Script-Component. MD, [Entwickeln einer benutzerdefinierten Datenfluss Komponente](extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)und [Programm](building-packages-programmatically/building-packages-programmatically.md)gesteuertes Erstellen von Paketen).  
  
## <a name="supported-languages"></a>Unterstützte Sprachen  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]unterstützt [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]vollständig. Dadurch können Entwickler [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] in ihren bevorzugten .NET-kompatiblen Sprachen programmieren. Obwohl die Runtime-Engine und die Datenfluss-Engine in einem systemeigenen Code geschrieben wurden, sind sie beide über ein vollständig verwaltetes Objektmodell verfügbar.  
  
 Sie können Pakete [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , benutzerdefinierte Tasks und Komponenten in [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] oder einem anderen Code-oder Text-Editor programmieren. 
  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] enthält viele Tools und Funktionen für Entwickler, die die iterativen Zyklen, bestehend aus Codierung, Debugging und Test, sowie vereinfachen und beschleunigen. Auch die Bereitstellung ist mit [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] einfacher. 
  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wird jedoch nicht benötigt, um [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]-Codeprojekte zu kompilieren und zu erstellen. Das [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]-SDK enthält die [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]- und [!INCLUDE[csprcs](../includes/csprcs-md.md)]-Compiler sowie zugehörige Tools.  
  
> [!IMPORTANT]  
>  Standardmäßg wird [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] mit [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]installiert, das [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] -SDK jedoch nicht. Die in diesem Abschnitt vorkommenden Links auf SDK-Inhalte funktionieren nur, wenn das SDK auf Ihrem Computer installiert und die SDK-Dokumentation in der Onlinedokumentation enthalten ist. Fügen Sie das SDK nach der Installation des [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] SDK zur Onlinedokumentation und dem Inhaltsverzeichnis hinzu, indem Sie die Anweisungen unter [Hinzufügen oder Entfernen der Produktdokumentation für SQL Server](../2014-toc/index.yml) befolgen.  
  
 Der [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Skript Task und die Skript Komponente [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] verwenden Tools for Applications (VSTA) als eingebettete Skript Umgebung. VSTA unterstützt [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual Basic und [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual C#.  
  
> [!NOTE]  
>  Die [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]-Anwendungsprogrammierschnittstellen sind mit COM-basierten Skriptsprachen, z. B. VBScript, nicht kompatibel.  
  
## <a name="locating-assemblies"></a>Suchen von Assemblys  
 In [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]wurden die [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Assemblys auf .NET 4.0 aktualisiert. Es gibt einen separaten globalen Assemblycache für .NET 4, der sich in * \<Laufwerk>* befindet: \WINDOWS\Microsoft.net\assembly. Normalerweise befinden sich alle [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Assemblys unter diesem Pfad im Ordner GAC_MSIL.  
  
 Wie in früheren Versionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]befinden sich die [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] zentralen Erweiterbarkeits-dll-Dateien auch unter * \<Laufwerk>*: \Programme\Microsoft SQL Server\100\SDK\Assemblies.  
  
## <a name="commonly-used-assemblies"></a>Häufig verwendete Assemblys  
 In der folgenden Tabelle sind die Assemblys, die häufig beim Programmieren von [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] mithilfe von [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] verwendet werden, aufgelistet.  
  
|Assembly|BESCHREIBUNG|  
|--------------|-----------------|  
|Microsoft.SqlServer.ManagedDTS.dll|Enthält die verwaltete Runtime-Engine.|  
|Microsoft.SqlServer.RuntimeWrapper.dll|Enthält die primäre Interopassembly (PIA) oder den Wrapper für die native Runtime-Engine.|  
|Microsoft.SqlServer.PipelineHost.dll|Enthält die verwaltete Datenfluss-Engine.|  
|Microsoft.SqlServer.PipelineWrapper.dll|Enthält die primäre Interopassembly (PIA) oder den Wrapper für die native Datenfluss-Engine.|  

![Integration Services Symbol (klein)](media/dts-16.gif "Integration Services (kleines Symbol)")immer auf**dem neuesten Stand bleiben mit Integration Services**  <br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.  
  
  
