---
title: Servereigenschaften in Analysis Services | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d70f58bfb5dba352d154f18b4c3db675b69147ad
ms.sourcegitcommit: 6e55a0a7b7eb6d455006916bc63f93ed2218eae1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2018
ms.locfileid: "35238820"
---
# <a name="server-properties-in-analysis-services"></a>Servereigenschaften in Analysis Services
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  Ein [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Administrator kann die Standard-Serverkonfigurationseigenschaften einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz ändern. Jede Instanz verfügt über eigene Konfigurationseigenschaften, die unabhängig von anderen Instanzen auf demselben Server festgelegt werden.  
  
 Konfigurieren Sie den Server, SQL Server Management Studio verwenden oder bearbeiten Sie die Datei "Msmdsrv.ini" einer bestimmten SQL Server Analysis Services-Instanz.  
 
Eigenschaftenseiten in SQL Server Management Studio zeigen eine Teilmenge der Eigenschaften, die wahrscheinlich geändert werden sollen. Den vollständigen Eigenschaftensatz finden Sie in der Datei „msmdsrv.ini“.   
  
> [!NOTE]  
>  In einer Standardinstallation von SQL Server Analysis Services kann "Msmdsrv.ini" im \Programme\Microsoft SQL Server\MSAS13 gefunden werden. MSSQLSERVER\OLAP\Config-Ordner.
> 
> Zu anderen Eigenschaften, die die Serverkonfiguration beeinflussen, gehören Bereitstellungskonfigurationseigenschaften in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Weitere Informationen zu diesen Eigenschaften finden Sie unter [Angeben der Konfigurationseinstellungen für die Lösungsbereitstellung](../../analysis-services/multidimensional-models/deployment-script-files-solution-deployment-config-settings.md).
 
##  <a name="bkmk_config"></a> Konfigurieren von Eigenschaften in Management Studio 
  
1.  Stellen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]eine Verbindung mit einer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz her.  
  
2. Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf eine [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanz, und klicken Sie anschließend auf **Eigenschaften**. Die Seite Allgemein mit den gebräuchlicheren Eigenschaften wird angezeigt.  

3.  Aktivieren Sie zum Anzeigen weiterer Eigenschaften unten auf der Seite das Kontrollkästchen **Erweiterte (alle) Eigenschaften anzeigen** .  
  
     Das Ändern von Servereigenschaften wird nur für Server im tabellarischen Modus und mehrdimensionalen Modus unterstützt. Wenn Sie [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]installiert haben, verwenden Sie, sofern vom Microsoft-Support nicht anders angegeben, immer die Standardwerte.  
  
     Anweisungen zum Behandeln von Funktions- oder Leistungsproblemen mithilfe von Servereigenschaften finden Sie im [SQL Server 2008 R2 Analysis Services-Vorgangshandbuch](http://go.microsoft.com/fwlink/?LinkID=225539).  
  
     Informationen zu Servereigenschaften (die in den letzten Versionen größtenteils unverändert geblieben sind) finden Sie auch im Microsoft-Whitepaper [SQL Server 2005 Analysis Services (SSAS) Server Properties](http://go.microsoft.com/fwlink/?LinkID=199102)(SQL Server 2005 Analysis Services-Servereigenschaften (SSAS)).    
  
##  <a name="bkmk_msmdsrvini"></a> Konfigurieren von Eigenschaften in „msmdsrv.ini“
  Einige Eigenschaften können nur in der Datei msmdsrv.ini festgelegt werden. Wenn die gewünschte Eigenschaft auch nach dem Einblenden der erweiterten Eigenschaften nicht angezeigt wird, müssen Sie ggf. die Datei msmdsrv.ini direkt bearbeiten.
  
1.  Überprüfen Sie die **DataDir** -Eigenschaft auf der Eigenschaftenseite „Allgemein“ in Management Studio, um den Speicherort der Analysis Services-Programmdateien zu bestätigen (einschließlich der Datei „msmdsrv.ini“).

     Auf einem Server, der über mehrere Instanzen verfügt, wird durch die Überprüfung des Programmdateispeicherorts sichergestellt, dass Sie die richtige Datei bearbeiten.  
  
2.  Navigieren Sie zum Ordner **config** am Speicherort des Ordners mit Programmdateien.

3. Erstellen Sie eine Sicherung der Datei für den Fall, dass Sie die ursprüngliche Datei wiederherstellen müssen.  
  
4.  Verwenden Sie einen Text-Editor, um die Datei msmdsrv.ini anzuzeigen oder zu bearbeiten.  
  
5.  Speichern Sie die Datei, und starten Sie den Dienst erneut.  
  
##  <a name="bkmk_ref"></a> Referenz zu Servereigenschaften  
  
 In den folgenden Themen werden die verschiedenen Konfigurationseigenschaften von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] beschrieben:  
  
|Thema|Description|  
|-----------|-----------------|  
|[Allgemeine Eigenschaften](../../analysis-services/server-properties/general-properties.md)|Bei den allgemeinen Eigenschaften handelt es sich sowohl um grundlegende als auch um erweiterte Eigenschaften. Hierzu zählen Eigenschaften zum Definieren des Datenverzeichnisses, Sicherungsverzeichnisses und anderem Serververhalten.|  
|[Data Mining-Eigenschaften](../../analysis-services/server-properties/data-mining-properties.md)|Die Data Mining-Eigenschaften steuern, welche Data Mining-Algorithmen aktiviert und welche deaktiviert sind. Standardmäßig sind alle Algorithmen aktiviert.| 
|[DAX-Eigenschaften](../../analysis-services/server-properties/dax-properties.md)|Definiert Eigenschaften, die im Zusammenhang mit DAX-Abfragen stehen.|
|DSO|DSO wird nicht mehr unterstützt. DSO-Eigenschaften werden ignoriert.|  
|[Funktionseigenschaften](../../analysis-services/server-properties/feature-properties.md)|Die Funktionseigenschaften beziehen sich auf Produktfunktionen. Bei dem größten Teil dieser Eigenschaften handelt es sich um erweiterte Eigenschaften sowie um Eigenschaften zum Steuern der Verbindungen zwischen Serverinstanzen.|  
|[Dateispeichereigenschaften](../../analysis-services/server-properties/filestore-properties.md)|Die Dateispeichereigenschaften sind nur für fortgeschrittene Benutzer gedacht. Hierzu zählen erweiterte Einstellungen für die Speicherverwaltung.|  
|[Eigenschaften des Sperren-Managers](../../analysis-services/server-properties/lock-manager-properties.md)|Die Sperren-Manager-Eigenschaften definieren das Serververhalten in Bezug auf Sperrvorgänge und Timeouts. Die meisten dieser Eigenschaften sind nur für fortgeschrittene Benutzer gedacht.|  
|[Protokolleigenschaften](../../analysis-services/server-properties/log-properties.md)|Die Protokolleigenschaften steuern, ob, wann und wie Ereignisse auf dem Server protokolliert werden. Hierzu zählen die Fehlerprotokollierung, die Ausnahmeprotokollierung, der Flight Recorder, die Abfrageprotokollierung und Ablaufverfolgungen.|  
|[Speichereigenschaften](../../analysis-services/server-properties/memory-properties.md)|Die Speichereigenschaften steuern die Speicherverwendung durch den Server. Sie sind in erster Linie für fortgeschrittene Benutzer gedacht.|  
|[Netzwerkeigenschaften](../../analysis-services/server-properties/network-properties.md)|Die Netzwerkeigenschaften steuern das Serververhalten in Bezug auf die Vernetzung und beinhalten Eigenschaften zum Steuern der Komprimierung und binärem XML. Die meisten dieser Eigenschaften sind nur für fortgeschrittene Benutzer gedacht.|  
|[OLAP-Eigenschaften](../../analysis-services/server-properties/olap-properties.md)|Die OLAP-Eigenschaften steuern die Cube- und Dimensionsverarbeitung, die verzögerte Verarbeitung, die Datenzwischenspeicherung und das Abfrageverhalten. Hierzu zählen sowohl grundlegende als auch erweiterte Eigenschaften.|  
|[Sicherheitseigenschaften](../../analysis-services/server-properties/security-properties.md)|Im Abschnitt Sicherheit sind sowohl grundlegende als auch erweiterte Eigenschaften zum Definieren von Zugriffsberechtigungen enthalten. Hierzu zählen Einstellungen für Administratoren und Benutzer.|  
|[Threadpooleigenschaften](../../analysis-services/server-properties/thread-pool-properties.md)|Die Threadpooleigenschaften steuern, wie viele Threads der Server erstellt. Hierbei handelt es sich vor allem um erweiterte Eigenschaften.|  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services-Instanzverwaltung](../../analysis-services/instances/analysis-services-instance-management.md)   
 [Angeben der Konfigurationseinstellungen für die Lösungsbereitstellung](../../analysis-services/multidimensional-models/deployment-script-files-solution-deployment-config-settings.md)  
  
  
