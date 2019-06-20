---
title: Installieren und Deinstallieren von Berichts-Generator-Unterstützung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- administering Report Builder
ms.assetid: 2c9a5814-17bf-4947-8fb3-6269e7caa416
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d35f6c7d77a43fe35ba78a88824309ffd72a5a44
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66454599"
---
# <a name="install-uninstall-and-report-builder-support"></a>Installation, Deinstallation und Unterstützung des Berichts-Generators
  Der Berichts-Generator ist ein Berichterstellungstool, das Sie zum Erstellen, Aktualisieren und Freigeben von Berichten, Berichtsteilen und freigegebenen Datasets verwenden können. Der Berichts-Generator ist in zwei Versionen verfügbar: als eigenständige Version und als [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]-Version. Die eigenständige Version wird von Ihnen oder einem Administrator auf dem Computer installiert. Die [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] -Version wird automatisch mit [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] installiert und vom Berichts-Manager oder von einer in [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]integrierten SharePoint-Website auf den Computer heruntergeladen.  
  
 Die eigenständige Version des Berichts-Generators wird nicht mit [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]installiert. Sie muss separat unter [Microsoft® SQL Server® 2012 Berichts-Generator](https://go.microsoft.com/fwlink/?LinkId=401502)heruntergeladen und installiert werden.  
  
> [!NOTE]  
>  Der Berichts-Generator kann nicht auf Itanium-basierten Computern installiert werden. Dies betrifft die [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] -Version und die eigenständige Version des Berichts-Generators.  
  
 Ein Administrator installiert und konfiguriert in der Regel [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], er gewährt die Berechtigung zum Verwenden der [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] -Version des Berichts-Generators und verwaltet Ordner und Berechtigungen für auf dem Berichtsserver gespeicherte Berichte, Berichtsteile und freigegebene Datasets. Weitere Informationen zu [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Verwaltung finden Sie unter [Reporting Services-Berichtsserver &#40;im einheitlichen Modus&#41; ](report-server/reporting-services-report-server-native-mode.md) in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?LinkId=154888) auf "MSDN.Microsoft.com".  
  
##  <a name="Installing"></a> Installieren von Berichts-Generator  
 Der Berichts-Generator ist als eigenständige Version und als [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] -Version verfügbar. Die eigenständige Version wird von Ihnen oder vom Administrator heruntergeladen und auf dem Computer installiert, während die [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] -Version mit [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)]installiert wird. Sie können den Berichts-Generator auch aus dem [Microsoft Download Center](https://go.microsoft.com/fwlink/?LinkID=186083)herunterladen.  
  
> [!NOTE]  
>  Der Berichts-Generator kann nicht auf Itanium 64-basierten Computern installiert werden. Dies betrifft die [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] -Version und die eigenständige Version des Berichts-Generators.  
  
 Überprüfen Sie vor dem Installieren einer Version des Berichts-Generators die Systemanforderungen, und installieren Sie alle erforderlichen Komponenten.  
  
### <a name="system-requirements"></a>Systemanforderungen  
 Der Berichts-Generator erfordert die Installation von [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Version 3.5 auf dem lokalen Computer. Wenn [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] bei der Installation des Berichts-Generators nicht auf dem lokalen Computer installiert ist, werden Sie aufgefordert, es zu installieren, bevor Sie fortfahren und die Installation abschließen können.  
  
 .NET Framework 3.5 ist kostenlos. Sie können .NET Framework 3.5 aus dem [Microsoft Download Center](https://go.microsoft.com/fwlink/?LinkID=110520)herunterladen.  
  
 Sie können den Berichts-Generator unter jedem [!INCLUDE[msCoName](../includes/msconame-md.md)] Windows-Betriebssystem installieren, das [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 3.5 unterstützt. Sie können Berichts-Generator z. B. unter Windows Vista oder Windows 7 installieren.  
  
 Es wird empfohlen, dass die Computer, auf denen Berichts-Generator ausgeführt wird, über 512 MB RAM verfügen. Je nach Komplexität der ausgeführten Berichte kann weniger oder mehr RAM erforderlich sein.  
  
### <a name="installing-the-stand-alone-version-of-report-builder-directly-on-your-computer"></a>Direktes Installieren der eigenständigen Version des Berichts-Generators auf dem Computer  
 Sie installieren den Berichts-Generator von der Downloadsite, dem [Microsoft Download Center](https://go.microsoft.com/fwlink/?LinkID=186083), oder ein Administrator stellt die Datei "ReportBuilder3.msi" (das Windows Installer-Paket für den Berichts-Generator) auf einer Freigabe bereit, von der Sie sie installieren können.  
  
 Sie können auch eine Befehlszeileninstallation durchführen und Optionen wie die unbeaufsichtigte Installation und das Schreiben von Protokolldateien für die Installation angeben. Informationen zu den verfügbaren Optionen finden Sie in der Dokumentation zum Windows Installer für die Ausführung von MSI-Dateien.  
  
 Weitere Informationen finden Sie unter [Installieren der eigenständigen Version des Berichts-Generator &#40;Berichts-Generator&#41;](install-windows/install-report-builder.md).  
  
 Ein Administrator kann auch Software wie Microsoft Systeme Manager Server (SMS) verwenden, um das Programm mithilfe von Push auf den Computer zu übertragen. In der Dokumentation für die Software wird beschrieben, wie spezifische Software zur Installation von Berichts-Generator verwendet wird.   
  
### <a name="installing-the-clickonce-version-of-report-builder-on-your-computer"></a>Installieren der ClickOnce-Version des Berichts-Generators auf dem Computer  
 Die [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] -Version von Berichts-Generator wird mit [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)]installiert. Sie wird sowohl bei systemeigenen als auch integrierten SharePoint-Installationen von [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)]installiert.  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] ist eine Microsoft-Technologie für die Bereitstellung von Windows-Anwendungen. Mit [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] können Benutzer Windows-Anwendungen wie den Berichts-Generator installieren und ausführen, indem sie auf einen Link auf einer Webseite klicken. Weitere Informationen zum Bereitstellen von [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] -Anwendungen und [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung oder zum Ausführen [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendungen in der Internetzone finden Sie unter der "ClickOnce-Bereitstellung für Windows Forms-Anwendungen", "Sicherheit in Windows Forms Overview"oder"Trusted Application Deployment Overview"auf die Artikel der [!INCLUDE[msCoName](../includes/msconame-md.md)] Developer Network-Website unter [ https://developer.microsoft.com/ ](https://developer.microsoft.com/).  
  
 Die [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] -Version des Berichts-Generators befindet sich auf dem Berichtsserver und wird auf dem Computer installiert, wenn Sie im Berichts-Manager auf die **Berichts-Generator** -Schaltfläche oder in einer SharePoint-Bibliothek im Menü **Neues Dokument** auf **Berichts-Generator-Bericht** klicken.  
  
> [!NOTE]  
>  Wenn das Menü **Neues Dokument** die Optionen **Berichts-Generator-Bericht**, **Berichts-Generator-Modell**und **Berichtsdatenquelle** nicht enthält, müssen die entsprechenden Inhaltstypen der SharePoint-Bibliothek hinzugefügt werden.   
  
 Sie können den Berichts-Generator über den Berichts-Manager oder eine SharePoint-Bibliothek öffnen. Weitere Informationen zum Öffnen des Berichts-Generator finden Sie unter [Starten des Berichts-Generators &#40;Berichts-Generator&#41;](report-builder/start-report-builder.md).  
  
### <a name="report-builder-languages"></a>Sprachen des Berichts-Generators  
 Der Berichts-Generator ist auf Englisch und in 21 weiteren Sprachen verfügbar. Wenn Sie die eigenständige Version des Berichts-Generators herunterladen, wählen Sie die Sprachversion aus, die Sie installieren möchten. Der Download muss für jede gewünschte Sprachversion wiederholt werden.  
  
 Bei der [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] -Version werden alle Sprachversionen auf dem Berichtsserver installiert, wenn Sie [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)]installieren. Durch die Kultur des Benutzercomputers wird festgelegt, welche Sprachversion auf dem Computer installiert wird. Wenn die Kultur mit keiner der verfügbaren Berichts-Generator-Sprachen übereinstimmt, wird die englische Version installiert.  
  
 Die folgende Tabelle enthält Informationen über die verfügbaren Sprachversionen.  
  
|LCID|Sprache|Culture|  
|----------|--------------|-------------|  
|1028|Chinesisch (traditionell)|zh-TW|  
|1029|Tschechisch|cs-CZ|  
|1030|Dänisch|da-DK|  
|1031|Deutsch|de-DE|  
|1032|Griechisch|el-GR|  
|1033|Englisch|de-DE|  
|1035|Finnisch|fi-FI|  
|1036|Französisch|fr-FR|  
|1038|Ungarisch|hu-HU|  
|1040|Italienisch|it-IT|  
|1041|Japanisch|ja-JP|  
|1042|Koreanisch|ko-KR|  
|1043|Niederländisch|nl-NL|  
|1044|Norwegisch (Bokmal)|nb-NO|  
|1045|Polnisch|pl-PLl|  
|1046|Portugiesisch (Brasilien)|pt-BR|  
|1049|Russisch|ru-RU|  
|1053|Schwedisch|sv-SE|  
|1055|Türkisch|tr-TR|  
|2052|Chinesisch (vereinfacht)|zh-CN|  
|2070|Portugiesisch (Portugal)|pt-PT|  
|3082|Spanisch (Spanien)|es-ES|  
  
  
##  <a name="Uninstalling"></a> Deinstallieren von Berichts-Generator  
 Sie können die eigenständige Version des Berichts-Generators über die Systemsteuerung oder die Befehlszeile deinstallieren. Dies betrifft nur die eigenständige Version des Berichts-Generators. Die [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] -Version des Berichts-Generators kann nicht separat deinstalliert werden. Sie wird immer mit [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]installiert und deinstalliert.  
  
 Weitere Informationen finden Sie unter [Deinstallieren der eigenständigen Version des Berichts-Generator &#40;Berichts-Generator&#41;](install-windows/uninstall-report-builder.md).  
  
  
##  <a name="Supporting"></a> Unterstützen von Berichtsgenerator  
 Ein Administrator ist für das Verwalten von Ordnern, Berichten und berichtsbezogenen Elementen auf dem Berichtsserver zuständig, gewährt die Berechtigung für Ressourcen auf dem Berichtsserver und konfiguriert den Berichtsserver für den Zugriff, um Autoren von Berichten zu unterstützen.  
  
### <a name="folders-reports-and-report-related-items"></a>Ordner, Berichte und berichtsbezogene Elemente  
 Die folgenden Ordner, Berichte und berichtsbezogenen Elemente werden auf dem Berichtsserver verwaltet:  
  
-   Ordner, in denen Sie Berichte, freigegebene Datenquellen, Modelle usw. speichern  
  
-   "Meine Berichte", der private Ordner, in dem Sie Ihre Berichte und berichtsbezogenen Elemente speichern  
  
-   Freigegebene Datenquellen, die Berichtsautoren die Verwendung von außerhalb von Berichten gespeicherten Datenquellen ermöglichen  
  
-   Freigegebene Datasets, die direkt verwendbare abgefragte Daten zu mehreren Berichten für mehrere Benutzer bereitstellen können  
  
-   Berichtsteile wie Tabellen und Diagramme, die es Benutzern ermöglichen, von anderen Benutzern in einer Zusammenarbeitsumgebung erstellte Teile von Berichten zu erweitern und wieder zu verwenden  
  
-   Berichtsmodelle, die das Abrufen von Daten für Berichte aus komplexen Datenquellen vereinfachen  
  
-   Bilder (z. B. Hintergrundbilder und Logos), die in mehreren Berichten verwendet werden können und zur einfachen Wartung außerhalb von Berichten gespeichert werden  
  
 Weitere Informationen finden Sie unter [Verwalten von Berichtsserverinhalten &#40;einheitlicher SSRS-Modus&#41; ](report-server/report-server-content-management-ssrs-native-mode.md) in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?LinkId=154888) auf "MSDN.Microsoft.com".  
  
### <a name="permissions"></a>Berechtigungen  
 Der Administrator erteilt Berechtigungen für den Berichtsserver. Als Benutzer des Berichts-Generators benötigen Sie Berechtigungen für den Berichtsserver, bevor Sie auf den Inhalt und die Funktionen des Berichtsservers zugreifen können. Sie können z. B. auf dem Berichtsserver gespeicherte Berichtsteile verwenden, Berichte aktualisieren und erneut auf dem Berichtsserver speichern und Berichte im Berichts-Manager ausführen. Abhängig von Ihren Anforderungen und Aufgaben können niedrigere oder höhere Berechtigungen gewährt werden. Berechtigungen mit geringeren Privilegien werden z. B. Benutzern gewährt, die freigegebene Berichte nur öffnen, aber nicht ändern müssen.  
  
 Wenn [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] im einheitlichen Modus installiert wird, kann ein Administrator folgende Aktionen ausführen:  
  
-   Er kann die Funktion "Meine Berichte" aktivieren, damit ein privater Ordner für Sie bereitgestellt wird, in dem Sie Ihre eigenen Berichte erstellen und speichern können.  
  
-   Er kann die Rolle "Berichts-Generator" für öffentliche Ordner verwenden, damit Sie eine Kopie eines freigegebenen Berichts öffnen und dann eine geänderte Version in einem privaten Ordner speichern können.  
  
-   Er kann die Rolle "Verleger" verwenden, damit Sie Berichte und freigegebene Datenquellen in öffentlichen Ordnern verwalten können. Diese Rolle wird erfahrenen Benutzern zugewiesen.  
  
 Wenn [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] im integrierten SharePoint-Modus installiert ist, kann ein Administrator folgende Aktionen ausführen:  
  
-   Er kann Ihnen die Berechtigung "Lesen" erteilen (wird Besuchern standardmäßig gewährt), sodass Sie eine Kopie eines Berichts in einem öffentlichen Ordner öffnen und dann die geänderte Version des Berichts in einem privaten Ordner oder auf Ihrem Computer speichern können.  
  
-   Er kann Ihnen die Berechtigung "Teilnehmen" erteilen (wird den Mitgliedergruppen standardmäßig gewährt), damit Sie Berichte und freigegebene Datenquellen in öffentlichen Ordnern verwalten können. Diese Berechtigungsstufe wird erfahrenen Benutzern gewährt.  
  
 Allgemeine Informationen zu Berechtigungen und das Erstellen und Verwenden von Rollen, finden Sie unter den [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] Dokumentation in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?LinkId=154888) auf "MSDN.Microsoft.com".  
  
### <a name="configuration-of-report-server"></a>Konfiguration des Berichtsservers  
 Wenn Sie im Berichts-Generator Berichte erstellen und eine Verbindung mit einer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Instanz herstellen, die unter Windows Vista, Windows Server 2008 oder Windows 7 installiert ist, kann beim Versuch, einen Bericht auf dem Berichtsserver zu öffnen oder zu speichern, ein Zugriffsfehler auftreten. Dieser Fehler tritt auf, weil die Sicherheitsfunktion "Benutzerkontensteuerung" (User Account Control, UAC) in Windows Vista, Windows Server 2008 und Windows 7 die Verwendung erhöhter Berechtigungen einschränkt, indem Administratorberechtigungen beim Zugriff auf Anwendungen entfernt werden.  
  
 Durch eine zusätzliche Konfiguration ist der Berichtsserver jedoch für Benutzer des Berichts-Generators verfügbar. Sie können [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -URLs den vertrauenswürdigen Websites hinzufügen. Standardmäßig wird Internet Explorer 7.0 oder höher unter Windows Vista, Windows Server 2008 und Windows 7 im geschützten Modus ausgeführt. Der geschützte Modus ist eine Funktion, die verhindert, dass Browseranforderungen auf demselben Computer ausgeführte Prozesse auf hoher Ebene erreichen. Sie können den geschützten Modus für die Berichtsserveranwendungen deaktivieren, indem Sie sie als vertrauenswürdige Sites hinzufügen. Für diese Änderung benötigen Sie Administratorberechtigungen.  
  
 Weitere Informationen zum Konfigurieren von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], finden Sie unter [Konfigurations-Manager für Reporting Services &#40;del&#41; ](https://docs.microsoft.com/sql/sql-server/install/reporting-services-configuration-manager-native-mode) in die [Reporting Services-Dokumentation](https://go.microsoft.com/fwlink/?linkid=121312) auf "MSDN.Microsoft.com".  
  
  
##  <a name="SampleDatabases"></a> SQL Server-Beispieldatenbanken  
 Die Adventure Works-Familie von Beispieldatenbanken beinhaltet Daten, mit denen Sie die Berichterstellung erlernen und Beispielberichte schreiben können.  
  
 Die Datenbanken sind in den folgenden Versionen verfügbar:  
  
-   Die Adventure Works-OLTP-Datenbank unterstützt standardmäßige Online-Transaktionsverarbeitungsszenarien (Adventure Works Cycles) für einen fiktiven Fahrradhersteller. Zu den Szenarien zählen Fertigung, Vertrieb, Einkauf, Produktverwaltung, Kontaktverwaltung und Personalwesen.  
  
-   Die [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] -Datenbank veranschaulicht das Erstellen eines Data Warehouse.  
  
-   Das [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] -Projekt kann verwendet werden, um eine AS-Datenbank für Business Intelligence-Szenarien zu erstellen.  
  
 Die Beispieldatenbanken sind nicht in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] enthalten und werden bei der Installation von [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] oder der eigenständigen Version des Berichts-Generators nicht installiert. Laden Sie stattdessen Beispieldatenbanken aus [CodePlex](https://go.microsoft.com/fwlink/?LinkId=87843)herunter. Alle Versionen der Beispieldatenbanken werden zusammen heruntergeladen. Sie können auch frühere Datenbankversionen herunterladen, die mit [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]und [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]und [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]veröffentlicht wurden.  
  
 Die erforderlichen Komponenten und Anweisungen zum Herunterladen und Installieren der [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] -Beispieldatenbanken finden Sie in den Themen zu den [Installationsvoraussetzungen für die SQL Server 2008-Beispieldatenbanken](https://go.microsoft.com/fwlink/?LinkId=166648) und zum [Installieren von Beispieldatenbanken](https://go.microsoft.com/fwlink/?LinkId=166649) auf CodePlex.  
  
  
##  <a name="HowTo"></a> Themen zur Vorgehensweise  
 Dieser Abschnitt enthält Verfahren, in denen die Installation und Deinstallation des Berichts-Generators erläutert werden.  
  
 [Installieren der eigenständigen Version des Berichts-Generators &#40;Berichts-Generator&#41;](install-windows/install-report-builder.md)  
  
 [Deinstallieren der eigenständigen Version des Berichts-Generators &#40;Berichts-Generator&#41;](install-windows/uninstall-report-builder.md)  
  
 [Starten Sie Berichts-Generator &#40;Berichts-Generator&#41;](report-builder/start-report-builder.md)  
  
  
## <a name="see-also"></a>Siehe auch  
 [Berichts-Generator in SQL Server 2014](report-builder/report-builder-in-sql-server-2016.md)  
  
  
