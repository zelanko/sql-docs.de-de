---
title: Herunterladen von SQL Server Management Studio (SSMS) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: sstein
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
ms.date: 07/26/2019
ms.openlocfilehash: cb379078fe5d8c2436b220871d84d352a8619155
ms.sourcegitcommit: 2604e13627fbc9f3bda3926b67045fceb7b04e37
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/06/2019
ms.locfileid: "68823123"
---
# <a name="download-sql-server-management-studio-ssms"></a>Herunterladen von SQL Server Management Studio (SSMS)

[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md.md](../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

SQL Server Management Studio (SSMS) ist eine integrierte Umgebung zum Verwalten jeder beliebigen SQL-Infrastruktur, von SQL Server bis hin zur Azure SQL-Datenbank. SSMS stellt Tools zum Konfigurieren, Überwachen und Verwalten von Instanzen von SQL Server und Datenbanken zur Verfügung. Verwenden Sie SSMS, um Abfragen und Skripts zu erstellen sowie die Datenebenenkomponenten bereitzustellen, zu überwachen und zu aktualisieren, die von Ihren Anwendungen verwendet werden.

Verwenden Sie SSMS zum Abfragen, Entwerfen und Verwalten Ihrer Datenbanken und Data Warehouses, unabhängig davon, ob sich diese auf Ihrem lokalen Computer oder in der Cloud befinden.

SSMS ist kostenlos!

## <a name="download-ssms-182"></a>Herunterladen von SSMS 18.2

**SSMS 18.2 ist jetzt verfügbar und ist die neueste Version mit der allgemeinen Verfügbarkeit (GA) von *SQL Server Management Studio* mit Unterstützung für [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)].**

**[![Download](../ssdt/media/download.png) SQL Server Management Studio 18.2 herunterladen](https://go.microsoft.com/fwlink/?linkid=2099720)**

SSMS 18.2 ist die aktuelle Version von SSMS mit allgemeiner Verfügbarkeit (GA, General Availability). Wenn Sie eine frühere allgemein verfügbare Version von SSMS 18 installiert haben, wird diese durch die Installation von SSMS 18.2 aktualisiert. Wenn eine ältere *Vorschauversion* von SSMS 18.x installiert ist, müssen Sie diese vor der Installation von SSMS 18.2 deinstallieren.

**Versionsinformationen**

- Releasenummer: 18.2  
- Buildnummer: 15.0.18142.0  
- Releasedatum: 25. Juli 2019  

Wenn Sie Kommentare oder Vorschläge haben oder Probleme melden möchten, erreichen Sie das SSMS-Team am besten über [UserVoice](https://aka.ms/sqlfeedback).

Durch die Installation von SSMS 18.x erfolgt weder ein Upgrade noch eine Ersetzung der SSMS-Version 17.x oder früher Versionen. SSMS 18.x wird parallel zu früheren Versionen installiert, damit beide Versionen zur Verfügung stehen.

Wenn ein Computer parallele SSMS-Installationen enthält, sollten Sie sich vergewissern, dass Sie die richtige Version für Ihre speziellen Anforderungen starten. Die neueste Version heißt **Microsoft SQL Server Management Studio 18**.

## <a name="available-languages-ssms-182"></a>Verfügbare Sprachen (SSMS 18.2)

Diese Version von SSMS kann in folgenden Sprachen installiert werden:

SQL Server Management Studio 18.2:  
[Chinesisch (vereinfacht)](https://go.microsoft.com/fwlink/?linkid=2099720&clcid=0x804) | [Chinesisch (traditionell)](https://go.microsoft.com/fwlink/?linkid=2099720&clcid=0x404) | [Englisch (Vereinigte Staaten)](https://go.microsoft.com/fwlink/?linkid=2099720&clcid=0x409) | [Französisch](https://go.microsoft.com/fwlink/?linkid=2099720&clcid=0x40c) | [Deutsch](https://go.microsoft.com/fwlink/?linkid=2099720&clcid=0x407) | [Italienisch](https://go.microsoft.com/fwlink/?linkid=2099720&clcid=0x410) | [Japanisch](https://go.microsoft.com/fwlink/?linkid=2099720&clcid=0x411) | [Koreanisch](https://go.microsoft.com/fwlink/?linkid=2099720&clcid=0x412) | [Portugiesisch (Brasilien)](https://go.microsoft.com/fwlink/?linkid=2099720&clcid=0x416) | [Russisch](https://go.microsoft.com/fwlink/?linkid=2099720&clcid=0x419) | [Spanisch](https://go.microsoft.com/fwlink/?linkid=2099720&clcid=0x40a)

> [!NOTE]
> Das SQL Server PowerShell-Modul ist eine separate Installation über den PowerShell-Katalog. Weitere Informationen finden Sie unter [Download SQL Server PowerShell Module](download-sql-server-ps-module.md) (Herunterladen des SQL Server PowerShell-Moduls).

## <a name="new-in-this-release-ssms-182"></a>Neues in diesem Release (SSMS 18.2)

|  Neues Element  |  Details  |
|-------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Always Encrypted | Der Enclave-Anbieter wurde aktualisiert, um Azure Attestation zu unterstützen. |
| IntelliSense/Editor | Unterstützung für die Datenklassifizierung wurde hinzugefügt.  |
| OPTIMIZE_FOR_SEQUENTIAL_KEY | SSMS-Indexdialogfeld – neue Indexoption OPTIMIZE_FOR_SEQUENTIAL_KEY wurde hinzugefügt. |
| OPTIMIZE_FOR_SEQUENTIAL_KEY | IntelliSense-Unterstützung wurde hinzugefügt |
| Abfrageausführung oder Ergebnisse | In den Meldungen wurde eine „Abschlusszeit“ hinzugefügt, um nachzuverfolgen, wann die Ausführung einer bestimmten Abfrage abgeschlossen wurde. |
| Abfrageausführung oder Ergebnisse  | Ermöglicht, mehr Daten anzuzeigen (Ergebnis in Text) und in Zellen zu speichern (Ergebnis in Raster). SSMS erlaubt nun bis zu 2 Mio. Zeichen für beides (Steigerung von 256 bzw. 64 Tausend). Damit ist auch das Problem gelöst, dass Benutzer nicht in der Lage waren, mehr als 43.680 Zeichen aus den Zellen des Rasters abzurufen. |
| Showplan | In QueryPlan wurde ein neues Attribut hinzugefügt für den Fall, dass das Inlining benutzerdefinierter Skalarfunktionen aktiviert ist (ContainsInlineScalarTsqlUdfs). |
| SMO | Unterstützung für „Funktionseinschränkungen“ wurde hinzugefügt. Informationen zum Feature selbst finden Sie unter [Funktionsbezogene Einschränkungen](https://docs.microsoft.com/sql/relational-databases/security/feature-restrictions). Informationen zu Bewertungserweiterungen finden Sie in der [Einführung der SQL-Bewertungs-API](https://techcommunity.microsoft.com/t5/SQL-Server/Introducing-SQL-Assessment-API-Public-Preview/ba-p/778570). |
| Integration Services (SSIS) | Leistungsoptimierung für SSIS-Paketplaner in Azure |
|  |  |

Ausführliche Informationen zu Neuerungen in dieser Version finden Sie in den [SSMS-Versionshinweisen](release-notes-ssms.md).

## <a name="supported-sql-offerings-ssms-182"></a>Unterstützte SQL-Angebote (SSMS 18.2)

* Diese Version von SSMS funktioniert mit allen [unterstützten Versionen von SQL Server 2008 – [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]](https://support.microsoft.com/lifecycle?C2=1044) und bietet das höchste verfügbare Maß an Unterstützung für die Arbeit mit den neuesten Cloudfunktionen in Azure SQL-Datenbank und Azure SQL Data Warehouse.
* Zusätzlich kann SSMS 18.x parallel zu SSMS 17.x, SSMS 16.x oder SQL Server 2014 SSMS und früheren Versionen installiert werden.
* SQL Server Integration Services (SSIS): SSMS Version 17.x oder höher unterstützt das Herstellen von Verbindungen zum veralteten Dienst SQL Server Integration Services nicht. Verwenden Sie die Version von SSMS, die auf die Version von SQL Server ausgerichtet ist, um eine Verbindung zu einer früheren Version von Integration Services herzustellen. Verwenden Sie beispielsweise SSMS 16.x, um eine Verbindung zum veralteten Dienst SQL Server 2016 Integration Services herzustellen. SSMS 17.x und SSMS 16.x können parallel auf demselben Computer installiert sein. Seit dem Release von SQL Server 2012 wird empfohlen, Integration Services-Pakete mithilfe der SSIS-Katalogdatenbank (SSISDB) zu speichern, zu verwalten, auszuführen und zu überwachen. Weitere Informationen finden Sie unter [SSIS-Katalog](../integration-services/catalog/ssis-catalog.md).

## <a name="supported-operating-systems-ssms-182"></a>Unterstützte Betriebssysteme (SSMS 18.2)

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

## <a name="release-notes-ssms-182"></a>Versionshinweise (SSMS 18.2)

Es sind ein paar [Probleme](release-notes-ssms.md#known-issues-181) für dieses Release bekannt.

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
