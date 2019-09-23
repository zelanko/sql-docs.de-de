---
title: SQL Server Management Studio (SSMS)
description: Hier wird beschrieben, was SQL Server Management Studio (SSMS) ist und welche Möglichkeiten es bietet.
ms.prod: sql
ms.technology: ssms
ms.topic: overview
author: markingmyname
ms.author: maghan
ms.reviewer: ''
f1_keywords:
- sql13.ssms.viewhelp.f1
helpviewer_keywords:
- SQL Server Management Studio
- SQL Server Management Studio for Integration Services
- SQL Server Management Studio for Reporting Services
- SQL Server Management Studio for Analysis Services
ms.custom: ''
ms.date: 09/11/2019
ms.openlocfilehash: a185d7506b23931787699b52fedddfddf21c1cb8
ms.sourcegitcommit: 059da40428ee9766b6f9b16b66c689b788c41df1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/17/2019
ms.locfileid: "71038854"
---
# <a name="what-is-sql-server-management-studio-ssms"></a>Was ist SQL Server Management Studio (SSMS)?

[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md.md](../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] (SSMS) ist eine integrierte Umgebung für die Verwaltung jeder SQL-Infrastruktur. Verwenden Sie SSMS, um auf alle Komponenten von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], Azure SQL-Datenbank und SQL Data Warehouse zuzugreifen und diese zu konfigurieren, zu verwalten und zu entwickeln. SSMS bietet ein einzelnes, umfassendes Hilfsprogramm, das eine Vielzahl grafischer Tools mit einer Reihe von Skript-Editoren mit großem Funktionsumfang kombiniert, um Entwicklern und Datenbankadministratoren mit unterschiedlichem Kenntnisstand den Zugriff auf [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] zu ermöglichen.

- [**Herunterladen von SQL Server Management Studio (SSMS)** ](download-sql-server-management-studio-ssms.md)
- [**Herunterladen von SQL Server Developer**](https://my.visualstudio.com/Downloads?q=SQL%20Server%20Developer)
- [**Herunterladen von Visual Studio**](https://www.visualstudio.com/downloads/)

![SSMS](media/sql-server-management-studio-ssms/ssms.png)

## <a name="sql-server-management-studio-components"></a>Komponenten von SQL Server Management Studio  
  
|und Beschreibung|Komponente|  
|---------------|---------|  
|Die Verwendung des **Objekt-Explorers** zum Anzeigen und Verwalten aller Objekte in mindestens einer Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].|[Objekt-Explorers](../ssms/object/object-explorer.md)|  
|So wird der **Vorlagen-Explorer** zum Erstellen und Verwalten von Dateien mit Textbausteinen verwendet, die Sie zum Beschleunigen der Entwicklung von Abfragen und Skripts verwenden.|[Template Explorer](../ssms/template/template-explorer.md)|  
|So wird der veraltete **Projektmappen-Explorer** zum Erstellen von Projekten verwendet, die zum Verwalten von Verwaltungselementen wie Skripts und Abfragen verwendet werden.|[Projektmappen-Explorer](../ssms/solution/solution-explorer.md)|  
|So werden die in [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]enthaltenen visuellen Entwurfstools verwendet.|[Visual Database Tools](../ssms/visual-db-tools/visual-database-tools.md)|  
|So werden die [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] -Spracheditoren zum interaktiven Erstellen und Debuggen von Abfragen und Skripts verwendet.|[Abfrage- und Text-Editoren](scripting/query-and-text-editors-sql-server-management-studio.md)

## <a name="sql-server-management-studio-for-business-intelligence"></a>SQL Server Management Studio für Business Intelligence

Verwenden Sie [!INCLUDE[ssASnoversion](../includes/ssasnoversion_md.md)] für den Zugriff auf und die Verwaltung von [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] und [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Obwohl alle drei Business Intelligence-Technologien auf [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]basieren, weichen die mit den jeweiligen Technologien verbundenen Verwaltungsaufgaben leicht voneinander ab.

> [!NOTE]
> Verwenden Sie zum Erstellen und Ändern von Projektmappen in [!INCLUDE[ssASnoversion](../includes/ssasnoversion_md.md)], [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]und [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull_md.md)]und nicht [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull_md.md)] ist eine Entwicklungsumgebung, die auf [!INCLUDE[msCoName](../includes/msconame_md.md)][!INCLUDE[vsprvs](../includes/vsprvs-md.md)]basiert.

### <a name="managing-analysis-services-solutions-using-sql-server-management-studio"></a>Verwalten von Analysis Services-Lösungen mit SQL Server Management Studio

[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ermöglicht es Ihnen, [!INCLUDE[ssASnoversion](../includes/ssasnoversion_md.md)] -Objekte zu verwalten, beispielsweise Ausführen von Sicherungen und Verarbeiten von Objekten.

[!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] bietet ein [!INCLUDE[ssASnoversion](../includes/ssasnoversion_md.md)] -Skriptprojekt, in dem Sie in Multidimensional Expressions (MDX), Data Mining Extensions (DMX) und XML for Analysis (XMLA) geschriebene Skripts entwickeln und speichern können. Sie verwenden [!INCLUDE[ssASnoversion](../includes/ssasnoversion_md.md)] -Skriptprojekte, um Verwaltungsaufgaben auszuführen oder Objekte wie Datenbanken oder Cubes in [!INCLUDE[ssASnoversion](../includes/ssasnoversion_md.md)] -Instanzen neu zu erstellen. Sie können beispielsweise ein XMLA-Skript in einem [!INCLUDE[ssASnoversion](../includes/ssasnoversion_md.md)] -Skriptprojekt entwickeln, das neue Objekte direkt auf einer vorhandenen [!INCLUDE[ssASnoversion](../includes/ssasnoversion_md.md)] -Instanz erstellt. Die [!INCLUDE[ssASnoversion](../includes/ssasnoversion_md.md)] -Skriptprojekte können als Teil einer Lösung gespeichert werden und mit dem Quellcodeverwaltungssystem integriert werden.
  
Weitere Informationen zur Verwendung von [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], finden Sie unter [Entwickeln und Implementieren mithilfe von SQL Server Management Studio](https://docs.microsoft.com/analysis-services/instances/analysis-services-scripts-project-in-sql-server-management-studio).
  
### <a name="managing-integration-services-solutions-using-sql-server-management-studio"></a>Verwalten von Integration Services-Lösungen mit SQL Server Management Studio

[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ermöglicht Ihnen die Verwendung des [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Diensts, mit dem Sie Pakete verwalten und ausgeführte Pakete überwachen können. Zudem können Sie [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] zur Organisation von Paketen in Ordnern, zum Ausführen von Paketen, zum Im- und Exportieren von Paketen, zum Migrieren von DTS-Paketen (Data Transformation Services) sowie zum Aktualisieren von [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Paketen verwenden.

### <a name="managing-reporting-services-projects-using-sql-server-management-studio"></a>Verwalten von Reporting Services-Projekten mit SQL Server Management Studio

Verwenden Sie SQL Server Management Studio zum Aktivieren von Reporting Services-Funktionen und zum Verwalten von Server und Datenbanken sowie von Rollen und Aufträgen.

Verwalten Sie freigegebene Zeitpläne mit dem Ordner Freigegebene Zeitpläne, und verwalten Sie Berichtsserver-Datenbanken (ReportServer, ReportServerTempdb). Sie können darüber hinaus eine RSExecRole-Rolle in der master-Systemdatenbank erstellen, wenn Sie eine Berichtsserver-Datenbank in eine neue oder andere SQL Server-Datenbank-Engine ([!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssDE](../includes/ssde_md.md)]) verschieben. Weitere Informationen zu diesen Aufgaben finden Sie in den folgenden Artikeln:  

- [Reporting Services in SSMS](../reporting-services/tools/reporting-services-in-sql-server-management-studio-ssrs.md)
- [Verwalten einer Berichtsserver-Datenbank](../reporting-services/report-server/administer-a-report-server-database-ssrs-native-mode.md)
- [Create the RSExecRole (Erstellen der Rolle RSExecRole)](../reporting-services/security/create-the-rsexecrole.md)

Zudem verwalten Sie den Server, indem Sie verschiedene Funktionen aktivieren und konfigurieren, Serverstandardwerte festlegen und Rollen und Aufträge verwalten. Weitere Informationen zu diesen Aufgaben finden Sie in den folgenden Artikeln:

- [Set Report Server Properties (Festlegen von Berichtsservereigenschaften)](../reporting-services/tools/set-report-server-properties-management-studio.md)
- [Erstellen, Löschen oder Ändern von Rollen](../reporting-services/security/role-definitions-create-delete-or-modify.md)
- [Aktivieren und Deaktivieren von clientseitigem Druck für Reporting Services](../reporting-services/report-server/enable-and-disable-client-side-printing-for-reporting-services.md)

## <a name="non-english-language-versions-of-sql-server-management-studio-ssms"></a>Nicht englischsprachige Versionen von SQL Server Management Studio (SSMS)

Das Einrichten gemischter Sprachen wird nicht mehr blockiert. Sie können die deutsche Version von SSMS unter der französischen Windows-Version installieren. Stimmt die Sprache des Betriebssystems nicht mit der Sprache von SSMS überein, muss der Benutzer die Sprache unter „Extras“ > „Optionen“ > „Internationale Einstellungen“ ändern. Andernfalls wird die englische Benutzeroberfläche von SSMS angezeigt.

Weitere Informationen zu verschiedenen Gebietsschemas bei früheren Versionen finden Sie unter [Installieren von nicht englischsprachigen Versionen von SSMS](install-other-languages.md).

## <a name="support-policy-for-ssms"></a>Supportrichtlinie für SSMS

- Ab SSMS 17.0 hat das SQL-Tools-Team die [Moderne Microsoft-Lebenszyklusrichtlinie](https://support.microsoft.com/help/30881/modern-lifecycle-policy) übernommen.
- Lesen die ursprüngliche [Ankündigung der modernen Lebenszyklusrichtlinie](https://support.microsoft.com/help/447912/announcing-microsoft-modern-lifecycle-policy). Weitere Informationen finden Sie unter [Häufig gestellte Fragen zur modernen Richtlinie](https://support.microsoft.com/help/30882/modern-lifecycle-policy-faq).
- Informationen zur Erfassung von Diagnosedaten und zur Featureverwendung finden Sie unter [Ergänzende Datenschutzbestimmungen zu SQL Server](https://docs.microsoft.com/sql/sql-server/sql-server-privacy).

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]

## <a name="next-steps"></a>Nächste Schritte

- [Installieren von nicht englischsprachigen Versionen von SSMS](install-other-languages.md)
- [Herstellen einer Verbindung mit und Abfragen von einer SQL Server-Instanz](tutorials/connect-query-sql-server.md)
- [Schreiben von Transact-SQL-Anweisungen](https://msdn.microsoft.com/2addc9be-67d0-423d-a457-192fe9d7d058)
- [Azure Data Studio](../azure-data-studio/what-is.md)

[!INCLUDE[contribute-to-content](../includes/paragraph-content/contribute-to-content.md)]
