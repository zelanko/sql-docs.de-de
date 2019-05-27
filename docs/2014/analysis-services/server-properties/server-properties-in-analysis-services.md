---
title: Konfigurieren von Servereigenschaften in Analysis Services | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- SSAS, configuration properties
- Analysis Services, configuration properties
- SQL Server Analysis Services, configuration properties
- configuration options [Analysis Services]
- server properties [Analysis Services]
- properties [Analysis Services], configuration
- properties [Analysis Services]
ms.assetid: 274b89cd-14ed-4666-bc13-eedf1de51e18
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 31c05bbc1be8376144eb191ff28a9cdc6eebdd8a
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66068902"
---
# <a name="configure-server-properties-in-analysis-services"></a>Konfigurieren von Servereigenschaften in Analysis Services
  Ein [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Administrator kann die standardmäßigen Serverkonfigurationseigenschaften für eine [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz ändern. Jede Instanz verfügt über eigene Konfigurationseigenschaften, die unabhängig von anderen Instanzen auf demselben Server festgelegt werden können.  
  
 Zum Festlegen der Servereigenschaften können Sie SQL Server Management Studio verwenden oder die Datei msmdsrv.ini einer bestimmten Instanz bearbeiten.  
  
 Dieses Thema enthält folgende Abschnitte:  
  
 [Konfigurieren von Servereigenschaften (Instanz)](#bkmk_config)  
  
 [Referenz zu Servereigenschaften](#bkmk_ref)  
  
##  <a name="bkmk_config"></a> Konfigurieren von Servereigenschaften (Instanz)  
 Die Eigenschaftenseiten in SQL Server Management Studio enthalten eine Teilmenge der verfügbaren Eigenschaften. Es werden nur die Eigenschaften angezeigt, die mit größerer Wahrscheinlichkeit geändert werden. Den vollständigen Eigenschaftensatz finden Sie in der Datei msmdsrv.ini.  
  
> [!NOTE]  
>  In diesem Thema werden die Bereitstellungskonfigurationseigenschaften in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]nicht dokumentiert. Weitere Informationen zur Bereitstellungskonfiguration finden Sie unter [angeben der Konfigurationseinstellungen für die Lösungsbereitstellung](../multidimensional-models/deployment-script-files-solution-deployment-config-settings.md).  
  
#### <a name="view-or-set-configuration-properties-in-management-studio"></a>Anzeigen oder Festlegen von Konfigurationseigenschaften in Management Studio  
  
1.  Stellen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]eine Verbindung mit einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz her.  
  
     Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf eine [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz, und klicken Sie anschließend auf **Eigenschaften**. Die Seite Allgemein mit den gebräuchlicheren Eigenschaften wird angezeigt.  
  
2.  Aktivieren Sie zum Anzeigen weiterer Eigenschaften unten auf der Seite das Kontrollkästchen **Erweiterte (alle) Eigenschaften anzeigen** .  
  
     Das Ändern von Servereigenschaften wird nur für Server im tabellarischen Modus und mehrdimensionalen Modus unterstützt. Wenn Sie [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]installiert haben, verwenden Sie immer die Standardwerte, es sei Sie denn, Sie werden von einem Techniker des Microsoft-Produktsupports aufgefordert, andere Werte festzulegen.  
  
     Anweisungen zum Behandeln von Funktions- oder Leistungsproblemen mithilfe von Servereigenschaften finden Sie im [SQL Server 2008 R2 Analysis Services-Vorgangshandbuch](https://go.microsoft.com/fwlink/?LinkID=225539).  
  
     Informationen zu Servereigenschaften (die in den letzten Versionen größtenteils unverändert geblieben sind) finden Sie auch im Microsoft-Whitepaper [SQL Server 2005 Analysis Services (SSAS) Server Properties](https://go.microsoft.com/fwlink/?LinkID=199102)(SQL Server 2005 Analysis Services-Servereigenschaften (SSAS)).  
  
    > [!NOTE]  
    >  Einige Eigenschaften können nur in der Datei msmdsrv.ini festgelegt werden. Wenn die gewünschte Eigenschaft auch nach dem Einblenden der erweiterten Eigenschaften nicht angezeigt wird, müssen Sie ggf. die Datei msmdsrv.ini direkt bearbeiten.  
  
#### <a name="view-or-edit-configuration-properties-in-the-msmdsrvini-file"></a>Anzeigen oder Bearbeiten der Konfigurationseigenschaften in der Datei "msmdsrv.ini"  
  
1.  Überprüfen Sie zuerst die **DataDir** -Eigenschaft auf der Eigenschaftenseite Allgemein in Management Studio, um den Speicherort der Analysis Services-Programmdateien zu bestätigen (einschließlich der Datei msmdsrv.ini). Durch die Überprüfung des Speicherorts der Programmdateien wird sichergestellt, dass Sie die richtige Datei bearbeiten.  
  
    > [!NOTE]  
    >  Bei einer Standardinstallation befindet sich die Datei im Ordner \Programme\Microsoft SQL Server\MSAS12.MSSQLSERVER\OLAP\Config.  
  
2.  Erstellen Sie eine Sicherung der Datei für den Fall, dass Sie die ursprüngliche Datei wiederherstellen müssen.  
  
3.  Verwenden Sie einen Text-Editor, um die Datei msmdsrv.ini anzuzeigen oder zu bearbeiten.  
  
4.  Nach dem Speichern der Datei muss der Dienst neu gestartet werden.  
  
##  <a name="bkmk_ref"></a> Referenz zu Servereigenschaften  
 Die Konfigurationseigenschaften von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] spielen bei der Optimierung des Systems eine wichtige Rolle. Wenn Sie z. B. das Verhalten des Abfrageprotokolls an Ihre Anforderungen anpassen möchten, können Sie entsprechende Eigenschaften festlegen.  
  
 In den folgenden Themen werden die verschiedenen Konfigurationseigenschaften von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] erläutert:  
  
|Thema|Description|  
|-----------|-----------------|  
|[Allgemeine Eigenschaften](general-properties.md)|Bei den allgemeinen Eigenschaften handelt es sich sowohl um grundlegende als auch um erweiterte Eigenschaften. Hierzu zählen Eigenschaften zum Definieren des Datenverzeichnisses, Sicherungsverzeichnisses und anderem Serververhalten.|  
|[Data Mining-Eigenschaften](data-mining-properties.md)|Die Data Mining-Eigenschaften steuern, welche Data Mining-Algorithmen aktiviert und welche deaktiviert sind. Standardmäßig sind alle Algorithmen aktiviert.|  
|DSO|DSO wird nicht mehr unterstützt. DSO-Eigenschaften werden ignoriert.|  
|[Funktionseigenschaften](feature-properties.md)|Die Funktionseigenschaften beziehen sich auf Produktfunktionen. Bei dem größten Teil dieser Eigenschaften handelt es sich um erweiterte Eigenschaften sowie um Eigenschaften zum Steuern der Verbindungen zwischen Serverinstanzen.|  
|[Dateispeichereigenschaften](filestore-properties.md)|Die Dateispeichereigenschaften sind nur für fortgeschrittene Benutzer gedacht. Hierzu zählen erweiterte Einstellungen für die Speicherverwaltung.|  
|[Eigenschaften des Sperren-Managers](lock-manager-properties.md)|Die Sperren-Manager-Eigenschaften definieren das Serververhalten in Bezug auf Sperrvorgänge und Timeouts. Die meisten dieser Eigenschaften sind nur für fortgeschrittene Benutzer gedacht.|  
|[Protokolleigenschaften](log-properties.md)|Die Protokolleigenschaften steuern, ob, wann und wie Ereignisse auf dem Server protokolliert werden. Hierzu zählen die Fehlerprotokollierung, die Ausnahmeprotokollierung, der Flight Recorder, die Abfrageprotokollierung und Ablaufverfolgungen.|  
|[Speichereigenschaften](memory-properties.md)|Die Speichereigenschaften steuern die Speicherverwendung durch den Server. Sie sind in erster Linie für fortgeschrittene Benutzer gedacht.|  
|[Netzwerkeigenschaften](network-properties.md)|Die Netzwerkeigenschaften steuern das Serververhalten in Bezug auf die Vernetzung und beinhalten Eigenschaften zum Steuern der Komprimierung und binärem XML. Die meisten dieser Eigenschaften sind nur für fortgeschrittene Benutzer gedacht.|  
|[OLAP-Eigenschaften](olap-properties.md)|Die OLAP-Eigenschaften steuern die Cube- und Dimensionsverarbeitung, die verzögerte Verarbeitung, die Datenzwischenspeicherung und das Abfrageverhalten. Hierzu zählen sowohl grundlegende als auch erweiterte Eigenschaften.|  
|[Sicherheitseigenschaften](security-properties.md)|Im Abschnitt Sicherheit sind sowohl grundlegende als auch erweiterte Eigenschaften zum Definieren von Zugriffsberechtigungen enthalten. Hierzu zählen Einstellungen für Administratoren und Benutzer.|  
|[Threadpooleigenschaften](thread-pool-properties.md)|Die Threadpooleigenschaften steuern, wie viele Threads der Server erstellt. Hierbei handelt es sich vor allem um erweiterte Eigenschaften.|  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services-Instanzverwaltung](../instances/analysis-services-instance-management.md)   
 [Angeben der Konfigurationseinstellungen für die Lösungsbereitstellung](../multidimensional-models/deployment-script-files-solution-deployment-config-settings.md)  
  
  
