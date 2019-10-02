---
title: Herunterladen von SQL Server Management Studio (SSMS) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: sstein, maghan
ms.technology: ssms
ms.topic: conceptual
keywords:
- Installieren von SSMS, Herunterladen von SSMS, neueste SSMS-Version
- SQL Server Management Studio
- ssms.exe
- sql man studio
- sql management studio
- sql management studio install
- download sql management studio
- ms sql management studio
- install sql management studio
- ssms download
- sql server ssms
- ssms express
ms.assetid: adafeeef-4255-4924-8042-02f503d599ca
author: dnethi
ms.author: dinethi
ms.custom: ''
ms.date: 09/24/2019
ms.openlocfilehash: 21678d69305cbe01e1fed3b254da627e00eb60f1
ms.sourcegitcommit: c4875c097e3aae1b76233777d15e0a0ec8e0d681
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71342047"
---
# <a name="download-sql-server-management-studio-ssms"></a>Herunterladen von SQL Server Management Studio (SSMS)

[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md.md](../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

SQL Server Management Studio (SSMS) ist eine integrierte Umgebung zum Verwalten jeder beliebigen SQL-Infrastruktur, von SQL Server bis hin zur Azure SQL-Datenbank. SSMS stellt Tools zum Konfigurieren, Überwachen und Verwalten von Instanzen von SQL Server und Datenbanken zur Verfügung. Verwenden Sie SSMS, um Abfragen und Skripts zu erstellen sowie die Datenebenenkomponenten bereitzustellen, zu überwachen und zu aktualisieren, die von Ihren Anwendungen verwendet werden.

Verwenden Sie SSMS zum Abfragen, Entwerfen und Verwalten Ihrer Datenbanken und Data Warehouses, unabhängig davon, ob sich diese auf Ihrem lokalen Computer oder in der Cloud befinden.

SSMS ist kostenlos!

## <a name="download-ssms-183"></a>Herunterladen von SSMS 18.3

**SSMS 18.3 ist jetzt verfügbar und ist die neueste Version mit der allgemeinen Verfügbarkeit (GA) von *SQL Server Management Studio* mit Unterstützung für [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)].**

**[![Download](../ssdt/media/download.png) SQL Server Management Studio 18.3 herunterladen](https://go.microsoft.com/fwlink/?linkid=2104251)**

SSMS 18.3 ist die aktuelle Version von SSMS mit allgemeiner Verfügbarkeit (GA, General Availability). Wenn Sie eine frühere allgemein verfügbare Version von SSMS 18 installiert haben, wird diese durch die Installation von SSMS 18.3 aktualisiert. Wenn eine ältere *Vorschauversion* von SSMS 18.x installiert ist, müssen Sie diese vor der Installation von SSMS 18.3 deinstallieren.

**Versionsinformationen**

- Releasenummer: 18.3  
- Buildnummer: 15.0.18178.0  
- Releasedatum: 23. September 2019  

Wenn Sie Kommentare oder Vorschläge haben oder Probleme melden möchten, erreichen Sie das SSMS-Team am besten über [UserVoice](https://aka.ms/sqlfeedback).

Durch die Installation von SSMS 18.x erfolgt weder ein Upgrade noch eine Ersetzung der SSMS-Version 17.x oder früher Versionen. SSMS 18.x wird parallel zu früheren Versionen installiert, damit beide Versionen zur Verfügung stehen.

Wenn ein Computer parallele SSMS-Installationen enthält, sollten Sie sich vergewissern, dass Sie die richtige Version für Ihre speziellen Anforderungen starten. Die neueste Version heißt **Microsoft SQL Server Management Studio 18**.

## <a name="available-languages-ssms-183"></a>Verfügbare Sprachen (SSMS 18.3)

Diese Version von SSMS kann in folgenden Sprachen installiert werden:

SQL Server Management Studio 18.2:  
[Chinesisch (vereinfacht)](https://go.microsoft.com/fwlink/?linkid=2104251&clcid=0x804) | [Chinesisch (traditionell)](https://go.microsoft.com/fwlink/?linkid=2104251&clcid=0x404) | [Englisch (Vereinigte Staaten)](https://go.microsoft.com/fwlink/?linkid=2104251&clcid=0x409) | [Französisch](https://go.microsoft.com/fwlink/?linkid=2104251&clcid=0x40c) | [Deutsch](https://go.microsoft.com/fwlink/?linkid=2104251&clcid=0x407) | [Italienisch](https://go.microsoft.com/fwlink/?linkid=2104251&clcid=0x410) | [Japanisch](https://go.microsoft.com/fwlink/?linkid=2104251&clcid=0x411) | [Koreanisch](https://go.microsoft.com/fwlink/?linkid=2104251&clcid=0x412) | [Portugiesisch (Brasilien)](https://go.microsoft.com/fwlink/?linkid=2104251&clcid=0x416) | [Russisch](https://go.microsoft.com/fwlink/?linkid=2104251&clcid=0x419) | [Spanisch](https://go.microsoft.com/fwlink/?linkid=2104251&clcid=0x40a)

> [!NOTE]
> Das SQL Server PowerShell-Modul ist eine separate Installation über den PowerShell-Katalog. Weitere Informationen finden Sie unter [Download SQL Server PowerShell Module](download-sql-server-ps-module.md) (Herunterladen des SQL Server PowerShell-Moduls).

## <a name="new-in-this-release-ssms-183"></a>Neues in diesem Release (SSMS 18.3)

| Neues Element | Details |
|---------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Datenklassifizierung | Hinzufügen von Datenklassifizierungsinformationen zur Spalteneigenschaften-Benutzeroberfläche (*Informationstyp*, *Informationstyp-ID*, *Vertraulichkeitsbezeichnung* und *Vertraulichkeitsbezeichnungs-ID* werden auf der Benutzeroberfläche von SSMS nicht verfügbar gemacht). |
| IntelliSense/Editor | Aktualisierte Unterstützung für Features, die SQL Server 2019 vor Kurzem hinzugefügt wurden (z.B. "ALTER SERVER CONFIGURATION"). |
| Integration Services | Fügen Sie ein neues Auswahlmenü „itemr `Tools > Migrate to Azure > Configure Azure-enabled DTExec`“ hinzu, das Ausführungen von SSIS-Paketen in der Azure-SSIS Integration Runtime als SSIS-Paket ausführen-Aktivitäten in ADF-Pipelines aufruft. |
| SMO/Skripterstellung | Hinzugefügte Unterstützung für Supportskripts der UNIQUE-Einschränkung von Azure SQL DW. |
| SMO/Skripterstellung | Datenklassifizierung: Hinzugefügte Unterstützung für SQL Version 10 (SQL 2008) und höher.  Neues Vertraulichkeitsattribut ‚rank‘ für SQL Version 15 (SQL 2019) und höher sowie Azure SQL DB. |

Ausführliche Informationen zu Neuerungen in dieser Version finden Sie in den [SSMS-Versionshinweisen](release-notes-ssms.md).

## <a name="supported-sql-offerings-ssms-183"></a>Unterstützte SQL-Angebote (SSMS 18.3)

- Diese Version von SSMS funktioniert mit allen [unterstützten Versionen von SQL Server 2008 – [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]](https://support.microsoft.com/lifecycle?C2=1044) und bietet das höchste verfügbare Maß an Unterstützung für die Arbeit mit den neuesten Cloudfunktionen in Azure SQL-Datenbank und Azure SQL Data Warehouse.
- Zusätzlich kann SSMS 18.x parallel zu SSMS 17.x, SSMS 16.x oder SQL Server 2014 SSMS und früheren Versionen installiert werden.
- SQL Server Integration Services (SSIS): SSMS Version 17.x oder höher unterstützt das Herstellen von Verbindungen zum veralteten Dienst SQL Server Integration Services nicht. Verwenden Sie die Version von SSMS, die auf die Version von SQL Server ausgerichtet ist, um eine Verbindung zu einer früheren Version von Integration Services herzustellen. Verwenden Sie beispielsweise SSMS 16.x, um eine Verbindung zum veralteten Dienst SQL Server 2016 Integration Services herzustellen. SSMS 17.x und SSMS 16.x können parallel auf demselben Computer installiert sein. Seit dem Release von SQL Server 2012 wird empfohlen, Integration Services-Pakete mithilfe der SSIS-Katalogdatenbank (SSISDB) zu speichern, zu verwalten, auszuführen und zu überwachen. Weitere Informationen finden Sie unter [SSIS-Katalog](../integration-services/catalog/ssis-catalog.md).

## <a name="supported-operating-systems-ssms-183"></a>Unterstützte Betriebssysteme (SSMS 18.3)

Dieses Release von SSMS unterstützt die folgenden 64-Bit-Plattformen, wenn sie mit dem aktuellen Service Pack ausgestattet sind:

- Windows 10 (64-Bit) <sup>*</sup>
- Windows 8.1 (64-Bit)
- Windows Server 2019 (64-Bit)
- Windows Server 2016 (64-Bit) <sup>*</sup>
- Windows Server 2012 R2 (64-Bit)
- Windows Server 2012 (64-Bit)
- Windows Server 2008 R2 (64-Bit)

<sup>*</sup> Erfordert Version 1607 (10.0.14393) oder höher

> [!NOTE]
> SSMS wird nur unter Windows ausgeführt. Wenn Sie ein Tool benötigen, das auf anderen Plattformen als Windows ausgeführt wird, sehen Sie sich Azure Data Studio an. Azure Data Studio ist ein neues plattformübergreifendes Tool, das unter macOS, Linux sowie Windows ausgeführt werden kann. Weitere Informationen finden Sie unter [Azure Data Studio](../azure-data-studio/what-is.md).

## <a name="release-notes-ssms-183"></a>Versionshinweise (SSMS 18.3)

Es sind ein paar [Probleme](release-notes-ssms.md#known-issues-183) für dieses Release bekannt.

Ausführliche Informationen zu diesem Release finden Sie in den [SSMS-Versionshinweisen](release-notes-ssms.md).

## <a name="previous-ssms-releases"></a>Vorgängerversionen von SSMS

[Vorgängerversionen von SQL Server Management Studio](../ssms/release-notes-ssms.md#previous-ssms-releases)

[!INCLUDE[get-help-sql-tools](../includes/paragraph-content/get-help-sql-tools.md)]

## <a name="see-also"></a>Siehe auch

- [Tutorial: SQL Server Management Studio](tutorials/tutorial-sql-server-management-studio.md)
- [Dokumentation zu SQL Server Management Studio](sql-server-management-studio-ssms.md)
- [Weitere Updates und Service Packs](https://technet.microsoft.com/sqlserver/ff803383.aspx)
- [Herunterladen von SQL Server Data Tools (SSDT)](../ssdt/download-sql-server-data-tools-ssdt.md)

[!INCLUDE[contribute-to-content](../includes/paragraph-content/contribute-to-content.md)]
