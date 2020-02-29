---
title: Installieren oder Deinstallieren des PowerPivot für SharePoint-Add-Ins (SharePoint 2013) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: fe13ce8b-9369-4126-928a-9426f9119424
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2350d00353188bf2551b00e53f815eeb4c7bc462
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/28/2020
ms.locfileid: "78174359"
---
# <a name="install-or-uninstall-the-powerpivot-for-sharepoint-add-in-sharepoint-2013"></a>Installieren oder Deinstallieren des PowerPivot für SharePoint-Add-Ins (SharePoint 2013)
  
  [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] ist eine Sammlung von Anwendungsserverkomponenten und Back-End-Diensten, die [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] -Datenzugriff in einer [!INCLUDE[SPS2013](../../../includes/sps2013-md.md)] -Farm ermöglichen. Das [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] für SharePoint-Add-In (**spPowerpivot.msi**) ist ein Installationspaket, mit dem die Anwendungsserverkomponenten installiert werden.

-   Für SharePoint 2010-Bereitstellungen ist das Add-In nicht erforderlich.

-   In einer einzelnen Serverbereitstellung, die SharePoint 2013 und [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] im SharePoint-Modus umfasst, ist das Add-In nicht erforderlich. Wenn Sie einen [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] -Server im SharePoint-Modus installieren, sind die durch das Add-In installierten Komponenten bereits enthalten. Diagramme zu Beispiel Bereitstellungen mit dem Add-in finden Sie unter [Deployment Topologien for SQL Server BI Features in SharePoint](../../../sql-server/install/deployment-topologies-for-sql-server-bi-features-in-sharepoint.md).

 **Hinweis:** In diesem Thema wird die [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] Installation von Projektmappendateien und [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] für das Konfigurationstool für SharePoint 2013 beschrieben. Nach der Installation finden Sie im folgenden Thema Informationen zum Konfigurationstool und zusätzlichen Features, zum Konfigurieren von Power Pivot und zum Bereitstellen von [Lösungen &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/configure-power-pivot-and-deploy-solutions-sharepoint-2013).

 Informationen zum Herunterladen von **spPowerPivot.msi**finden Sie unter [Microsoft® SQL Server® 2014 PowerPivot® für Microsoft SharePoint®](https://go.microsoft.com/fwlink/?LinkID=324854).

 **In diesem Thema:**

-   [Hintergrund](#bkmk_background)

-   [Installationsort von "sppowerpivot. msi"](#bkmk_where_to_install)

-   [Anforderungen und Voraussetzungen](#bkmk_prereq)

-   [So installieren Sie PowerPivot für SharePoint](#bkmk_install)

-   [Bereitstellen der SharePoint-Lösungsdateien mit dem PowerPivot für SharePoint 2013-Konfigurationstool](#bkmk_deploy_solution)

-   [Deinstallieren oder Reparieren des Add-ins](#bkmk_remove_addin)

##  <a name="bkmk_background"></a> Hintergrund

-   **Anwendungs Server:** [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] die Funktionalität in SharePoint 2013 umfasst die Verwendung von Arbeitsmappen als Datenquelle, die planmäßige [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] Datenaktualisierung und das-Management-Dashboard.

     [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)]ist ein [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows Installer Paket (**sppowerpivot. msi**), das Analysis Services Client Bibliotheken bereitstellt und [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] Installationsdateien auf den Computer kopiert. 
  [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)]-Funktionen in SharePoint werden vom Installationsprogramm nicht bereitgestellt oder konfiguriert. Die folgenden Komponenten sind standardmäßig installiert:

    -   
  [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] 2013. Diese Komponente enthält PowerShell-Skripts (PS1-Dateien), SharePoint-Lösungspakete (WSP) und das [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] 2013-Konfigurationstool zum Bereitstellen von [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] in einer SharePoint 2013-Farm.

    -   
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] OLE DB-Anbieter für Analysis Services (MSOLAP).

    -   ADOMD.NET-Datenanbieter.

    -   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Analysis Management Objects.

-   **Backend-Dienste:** Wenn Sie für [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] Excel verwenden, um Arbeitsmappen mit analytischen Daten zu erstellen, müssen Sie Excel Services mit einem BI-Server [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] konfigurieren, auf dem im SharePoint-Modus ausgeführt wird, um in einer Serverumgebung auf diese Daten zuzugreifen. Sie können SQL Server-Setup auf einem Computer ausführen, auf dem SharePoint Server 2013 installiert ist, oder auf einem anderen Computer, der keine SharePoint-Software enthält. Zwischen Analysis Services und SharePoint bestehen keine Abhängigkeiten.

     Weitere Informationen zum Installieren, Deinstallieren und Konfigurieren der Back-End-Dienste finden Sie unter:

    -   [PowerPivot for SharePoint 2013 Installation](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services-in-power-pivot-mode)

    -   [Deinstallieren von PowerPivot für SharePoint](../../../sql-server/install/uninstall-power-pivot-for-sharepoint.md)

##  <a name="bkmk_where_to_install"></a>Installationsort von "sppowerpivot. msi"
 Als bewährte Methode wird empfohlen, **spPowerPivot.msi** aus Konsistenzgründen auf allen Servern in der SharePoint-Farm zu installieren, einschließlich der Anwendungsserver und Web-Front-End-Server. Das Installationspaket schließt die Analysis Services-Datenanbieter sowie das [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] -Konfigurationstool ein. Bei der Installation von **spPowerPivot.msi** können Sie die Installation anpassen, indem Sie einzelne Komponenten ausschließen.

 **Datenanbieter:** Mehrere SharePoint-und SQL Server-Technologien verwenden die Analysis Services Datenanbieter, einschließlich Excel Services, PerformancePoint Services und Power View. Durch die Installation von **SpPowerPivot.msi** auf allen SharePoint-Servern wird sichergestellt, dass der vollständige Satz der Analysis Services-Datenanbieter und PowerPivot-Konnektivität durchgehend in der Farm verfügbar ist.

> [!NOTE]
>  Sie müssen die Analysis Services-Datenanbieter mit **spPowerPivot.msi**auf einem SharePoint 2013-Server installieren. Andere im [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] Feature Pack verfügbaren Installationspakete werden nicht unterstützt, da diese Pakete keine SharePoint 2013-Unterstützungsdateien enthalten, die von den Datenanbietern in dieser Umgebung benötigt werden.

 **Konfigurations Tool:** Das PowerPivot für SharePoint 2013-Konfigurationstool ist auf nur einem der SharePoint-Server erforderlich. Als bewährte Methode in Multiserverfarmen empfiehlt es sich, das Konfigurationstool auf mindestens zwei Servern zu installieren, damit Sie Zugriff auf das Konfigurationstool haben, wenn einer der beiden Server offline ist.

##  <a name="bkmk_prereq"></a>Anforderungen und Voraussetzungen

-   [!INCLUDE[msCoName](../../../includes/msconame-md.md)]SharePoint Server 2013.

-   " **sppowerpivot. msi** " ist nur 64-Bit, in Übereinstimmung mit den Anforderungen von SharePoint-Produkten und-Technologien.

-   Ein [!INCLUDE[ssASCurrent](../../../includes/ssascurrent-md.md)] -Server im PowerPivot-Modus. Excel Services verwenden die SQL Server Analysis Services-Instanz als PowerPivot-Server. Analysis Services können auf dem lokalen oder einem Remotecomputer ausgeführt werden.

-   **Berechtigungen:** Zur Installation [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)]von muss der aktuelle Benutzer ein Administrator auf dem Computer und eine Gruppe der SharePoint-Farm Administratoren sein.

-   Weitere Informationen zu [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] Anforderungen und Voraussetzungen finden Sie unter [Hardware-und Software Anforderungen für Analysis Services Server im SharePoint-Modus &#40;SQL Server 2014&#41;](../../../sql-server/install/hardware-software-requirements-analysis-services-server-sharepoint-mode.md).

##  <a name="bkmk_install"></a>So installieren Sie PowerPivot für SharePoint
 Das Installationspaket **spPowerpivot.msi** unterstützt sowohl eine grafische Benutzeroberfläche als auch einen Befehlszeilenmodus. Beide Installationsmethoden setzen voraus, dass die MSI-Datei mit Administratorrechten ausgeführt wird. Nach der Installation finden Sie im folgenden Thema Informationen zum Konfigurationstool und zusätzlichen Features, zum Konfigurieren von Power Pivot und zum Bereitstellen von [Lösungen &#40;SharePoint 2013&#41;](https://docs.microsoft.com/analysis-services/instances/install-windows/configure-power-pivot-and-deploy-solutions-sharepoint-2013).

### <a name="user-interface-installation"></a>Installation über die Benutzeroberfläche
 Um [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] über die grafische Benutzeroberfläche zu installieren, führen Sie die folgenden Schritte aus:

1.  Führen Sie **SpPowerPivot.msi**aus.

2.  Klicken Sie auf der Willkommensseite auf **Weiter**.

3.  Lesen und akzeptieren Sie den Lizenzvertrag, und klicken Sie auf **Weiter**.

4.  Auf der Seite **Funktionsauswahl** sind alle Funktionen standardmäßig ausgewählt.

5.  Klicken Sie auf **Weiter**.

6.  Klicken Sie auf **Installieren** , um die Installation abzuschließen.

### <a name="command-line-installation"></a>Installation über die Befehlszeile
 Öffnen Sie bei der Installation über die Befehlszeile eine Eingabeaufforderung mit Administratorberechtigungen, und führen Sie dann **spPowerPivot.msi**aus. Beispiel:

 `Msiexec.exe /i SpPowerPivot.msi`.

 Um ein Installationsprotokoll zu erstellen, verwenden Sie die Standardoptionen für die MsiExec-Protokollierung. Im folgenden Beispiel wird die Protokolldatei "Install_Log. txt" mit dem Schalter "v" ausführliche Logging erstellt.

```cmd
Msiexec.exe /i SpPowerPivot.msi /L v c:\test\Install_Log.txt
```

### <a name="quiet-command-line-installation-for-scripting"></a>Installation über die Befehlszeile im stillen Modus unter Verwendung eines Skripts
 Mithilfe der Schalter **/q** oder **/quiet** können Sie eine unbeaufsichtigte Installation ausführen, bei der keine Dialogfelder oder Warnungen angezeigt werden. Die stille Installation ist nützlich, wenn Sie für die Installation des Add-Ins ein Skript schreiben möchten.

> [!IMPORTANT]
>  Wenn Sie den Schalter **/q** für eine Befehlszeileninstallation im unbeaufsichtigten Modus verwenden, wird der Endbenutzer-Lizenzvertrag nicht angezeigt. Unabhängig von der Installationsmethode unterliegt die Verwendung dieser Software einem Lizenzvertrag, dessen Einhaltung in Ihrer Verantwortung liegt.

#### <a name="to-perform-a-quiet-installation"></a>So führen Sie eine stille Installation aus

1.  Öffnen Sie eine Eingabeaufforderung **mit Administrator Berechtigungen**.

2.  Führen Sie den folgenden Befehl aus:

    ```cmd
    Msiexec.exe /i spPowerPivot.msi /q
    ```

### <a name="command-line-installation-to-include-specific-components"></a>Installation über die Befehlszeile, um bestimmte Komponenten einzuschließen
 Das [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] -Konfigurationstool ist nicht auf jedem SharePoint-Server erforderlich, es wird jedoch empfohlen, das Konfigurationstool mindestens auf zwei Servern zu installieren, damit es bei Bedarf verfügbar ist.

 Bei der Installation von spPowerPivot.msi [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] können Sie anstelle des -Konfigurationstools die Befehlszeilenoptionen verwenden, um bestimmte Komponenten, wie die Datenanbieter, zu installieren. Die folgende Befehlszeile stellt ein Beispiel für die Installation aller Komponenten mit Ausnahme des Konfigurationstools dar:

```
Msiexec /i spPowerPivot.msi AGREETOLICENSE="yes" ADDLOCAL=" SQL_OLAPDM,SQL_ADOMD,SQL_AMO,SQLAS_SP_Common"
```

|Option|Beschreibung|
|------------|-----------------|
|Analysis_Server_SP_addin|PowerPivot-Konfiguration|
|SQL_OLAPDM|MSOLAP|
|SQL_ADOMD|ADOMD.NET-Anbieter|
|SQL_AMO|AMO-Anbieter|
|SQLAS_SP_Common|Allgemeine Analysis Services-Komponenten für SharePoint 2013|

##  <a name="bkmk_deploy_solution"></a>Bereitstellen der SharePoint-Lösungs Dateien mit dem Konfigurations Tool "PowerPivot für SharePoint 2013"
 Drei der Dateien, die von spPowerPivot.msi auf die Festplatte kopiert werden, sind SharePoint-Lösungsdateien. Eine Lösungsdatei bezieht sich auf die Webanwendungsebene, während sich die anderen Dateien auf die Farmebene beziehen. Die Dateien lauten:

-   `PowerPivotFarmSolution.wsp`

-   `PowerPivotFarm14Solution.wsp`

-   `PowerPivotWebApplicationSolution.wsp`

 Die Lösungsdateien werden in den folgenden Ordner kopiert:

 `C:\Program Files\Microsoft SQL Server\120\Tools\PowerPivotTools\SPAddinConfiguration\Resources`

 Nach Abschluss der MSI-Installation führen Sie das [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] -Konfigurationstool aus, um die Lösungen in der SharePoint-Farm zu konfigurieren und bereitzustellen.

### <a name="to-start-the-configuration-tool"></a>So starten Sie das Konfigurationstool 

 Geben Sie auf dem Windows-Start Bildschirm "Power" ein, und klicken Sie in den Suchergebnissen der apps auf **PowerPivot für SharePoint 2013-Konfiguration**. Beachten Sie, dass die Suchergebnisse u. U. zwei Links enthalten, weil [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Setup separate [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] -Konfigurationstools für SharePoint 2010 und SharePoint 2013 installiert. Stellen Sie sicher, dass Sie das [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] für SharePoint 2013-Konfigurationstool starten.

 ![zwei Power Pivot-Konfigurationstools](https://docs.microsoft.com/analysis-services/analysis-services/media/as-powerpivot-configtools-bothicons.gif "zwei Power Pivot-Konfigurationstools")

 **oder**

1.  Wechseln Sie zu **Start**, **Alle Programme**.

2.  Klicken Sie auf **Microsoft SQL Server 2014**.

3.  Klicken Sie auf **Konfigurationstools**.

4.  Klicken Sie auf **Konfiguration von PowerPivot für SharePoint 2013**.

 Weitere Informationen zum Konfigurationstool finden Sie unter [PowerPivot Configuration Tools](../../power-pivot-sharepoint/power-pivot-configuration-tools.md).

##  <a name="bkmk_remove_addin"></a>Deinstallieren oder Reparieren des Add-ins

> [!CAUTION]
>  Bei der Deinstallation von **spPowerPivot.msi** werden die Datenanbieter und das Konfigurationstool deinstalliert. Nach Deinstallation der Datenanbieter kann der Server keine Verbindung mit PowerPivot mehr herstellen.

 Sie können [!INCLUDE[ssGeminiShortvnext](../../../includes/ssgeminishortvnext-md.md)] mithilfe einer der folgenden Methoden deinstallieren oder reparieren:

1.  **Windows-Systemsteuerung:** Wählen Sie **Microsoft SQL Server 2012 PowerPivot für SharePoint 2013**aus. Klicken Sie entweder auf **Deinstallieren** oder auf **Reparieren**.

2.  Führen Sie spPowerPivot.msi aus, und wählen Sie die Option **Entfernen** oder **Reparieren** aus.

 **Befehlszeile:** Öffnen Sie eine Eingabeaufforderung **mit Administrator Berechtigungen** , und führen Sie einen der folgenden Befehle aus, um PowerPivot für SharePoint 2013 mit der Befehlszeile zu reparieren oder zu deinstallieren:

-   Zum Reparieren führen Sie den folgenden Befehl aus:

    ```cmd
    msiexec.exe /f spPowerPivot.msi
    ```

 oder

-   Zum Deinstallieren führen Sie den folgenden Befehl aus:

    ```cmd
    msiexec.exe /uninstall spPowerPivot.msi
    ```
