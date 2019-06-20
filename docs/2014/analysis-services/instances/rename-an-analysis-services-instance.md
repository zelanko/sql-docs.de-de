---
title: Umbenennen einer Analysis Services-Instanz | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- instances of Analysis Services, renaming
- renaming instances of Analysis Services
- names [Analysis Services], renaming instances
- names [Analysis Services]
ms.assetid: 87494741-4a2e-4fed-8061-418fd1e111c3
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3ef94fc86c78e896eab03bffb318b58e4b328245
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66079619"
---
# <a name="rename-an-analysis-services-instance"></a>Umbenennen einer Analysis Services-Instanz
  Sie können eine vorhandene Instanz von umbenennen [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] mithilfe der **Instanz umbenennen** Dialogfeld.  
  
> [!IMPORTANT]  
>  Das Tool zum Umbenennen von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanzen wird beim Umbenennen der Instanz mit erhöhten Rechten ausgeführt und aktualisiert den Windows-Dienstnamen, Sicherheitskonten und Registrierungseinträge, die dieser Instanz zugeordnet sind. Um sicherzustellen, dass diese Aktionen stattfinden, muss das Tool als lokaler Systemadministrator ausgeführt werden.  
  
 Das Tool zum Umbenennen von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanzen ändert nicht den Programmordner, der für die ursprüngliche Instanz erstellt wurde. Ändern Sie den Namen des Programmordners nicht entsprechend der umbenannten Instanz. Wenn Sie den Namen eines Programmordners ändern, kann dies dazu führen, dass Setup die Installation nicht reparieren oder deinstallieren kann.  
  
> [!NOTE]  
>  Das [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Tool zur Instanzumbenennung wird in einer Clusterumgebung nicht unterstützt.  
  
### <a name="to-rename-an-instance-of-analysis-services"></a>So benennen Sie eine Instanz von Analysis Services um  
  
1.  Starten Sie die **Instanzumbenennung** Tool **asinstancerename.exe**, von C:\Program Files\Microsoft SQL Server\110\Tools\Binn\ManagementStudio.  
  
2.  Wählen Sie im Dialogfeld **Instanz umbenennen** aus der Liste **Umzubenennende Instanz** die Instanz aus, die Sie umbenennen möchten.  
  
3.  Geben Sie in das Feld **Neuer Instanzname** den neuen Namen für die Instanz ein.  
  
4.  Überprüfen Sie den Benutzernamen und das Kennwort, und klicken Sie auf **Umbenennen**.  
  
     Die Analysis Services-Instanz wird im Rahmen der Namensänderung beendet und neu gestartet.  
  
### <a name="post-rename-checklist"></a>Prüfliste nach dem Umbenennen  
  
1.  Um wieder auf die Datenbanken auf der umbenannten Instanz zugreifen zu können, müssen Sie die Datenverbindungen in Excel oder anderen Clientanwendungen manuell aktualisieren. Überprüfen Sie auch alle vordefinierten Verbindungen, z. B. freigegebene Reporting Services-Datenquellen, Excel-ODC-Dateien oder BI Semantikmodell-Verbindungsdateien, die möglicherweise auf die umbenannte Instanz verweisen. Weitere Informationen finden Sie unter [Verbinden mit Analysis Services](connect-to-analysis-services.md).  
  
2.  Aktualisieren Sie PowerShell-Skripts oder AMO-Skripts, mit denen Sie routinemäßig Datenbanken sichern, synchronisieren oder verarbeiten.  
  
3.  Aktualisieren Sie die Projekteigenschaften für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekte, mit denen Sie in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]arbeiten. Für Serverinstanzen im tabellarischen Modus müssen die Eigenschaft Arbeitsbereichsserver für die Datei model.bim und die Eigenschaft Server für das Projekt aktualisiert werden.  
  
4.  Je nachdem, wie Sie das Dienstkonto angegeben haben, müssen Sie ggf. Datenbank-Anmeldenamen oder Dateiberechtigungen aktualisieren, die dem Dienst Datenzugriffsrechte gewähren (z. B., wenn Sie das Dienstkonto verwenden, um Daten zu verarbeiten oder auf verknüpfte Objekte auf einem anderen Server zuzugreifen).  
  
     Das Aktualisieren eines Datenbank-Anmeldenamens oder von Dateiberechtigungen ist erforderlich, wenn Sie ein virtuelles Konto zum Bereitstellen des Diensts verwendet haben. Virtuelle Konten basieren auf dem Instanznamen. Wenn Sie die Instanz umbenennen, wird daher gleichzeitig auch das virtuelle Konto aktualisiert. Dies bedeutet, dass alle vorherigen Anmeldenamen oder Berechtigungen, die Sie für die vorherige Instanz erstellt haben, nicht mehr gültig sind.  
  
     Dies wird im folgenden Beispiel veranschaulicht. Nehmen wir an, dass Sie einen Server im tabellarischen Modus als Instanz mit dem Namen "Tabular" mit dem virtuellen Standardkonto, was in der folgenden Konfiguration installiert:  
  
    1.  Instanzname = \<Server > \TABULAR  
  
    2.  Dienstname = MSOLAP$TABULAR  
  
    3.  Virtuelles Konto = NT-Dienst\ MSOLAP$TABULAR  
  
     Jetzt nehmen Sie die Instanz in "TAB2" umbenennen. Nach der Namensänderung würde die Konfiguration wie folgt aussehen:  
  
    1.  Instanzname = \<Server > \TAB2  
  
    2.  Dienstname = MSOLAP$TAB2  
  
    3.  Virtuelles Konto = NT-Dienst\ MSOLAP$TAB2  
  
     Wie Sie sehen können, sind Datenbank- und Dateiberechtigungen, die "NT-dienst\ MSOLAP$ TABULAR" zuvor gewährt wurden, nicht mehr gültig. Um sicherzustellen, dass Tasks und vom Dienst ausgeführten Vorgänge ausgeführt werden, wie zuvor, nun müssen "NT-dienst\ MSOLAP$ TAB2" neue Datenbank- und Dateiberechtigungen gewähren.  
  
  
