---
title: Übersicht über die Microsoft-Treiber für PHP für SQL Server | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/27/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 66559249-34c0-409d-b919-9b5bf0c4c9ec
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1c8f5cbf011165b41b353a37d8973031f55c2db6
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80922813"
---
# <a name="overview-of-the-microsoft-drivers-for-php-for-sql-server"></a>Übersicht über die Microsoft-Treiber für PHP für SQL Server

[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] ist eine PHP-Erweiterung, die Datenzugriff auf SQL Server 2005 und höhere Versionen, einschließlich Azure SQL-Datenbank, ermöglicht. Die Erweiterung stellt eine prozedurale Schnittstelle mit dem SQLSRV-Treiber und eine objektorientierte Schnittstelle mit dem PDO_SQLSRV-Treiber für den Zugriff auf Daten in allen Versionen von SQL Server bereit, einschließlich Express, ab SQL Server 2005. Ab SQL Server 2008 wird die Version 3.1 und höher der Treiber unterstützt. Die [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] -API umfasst Unterstützung für Windows-Authentifizierung, Transaktionen, Parameterbindung, Streaming, Zugriff auf Metadaten und Fehlerbehandlung.  
  
Sie müssen über die richtige Version von SQL Server Native Client verfügen oder den Microsoft ODBC-Treiber auf demselben Computer installiert haben, auf dem PHP ausgeführt wird, um [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] verwenden zu können.  Weitere Informationen finden Sie unter [Systemanforderungen für die Microsoft-Treiber für PHP für SQL Server](../../connect/php/system-requirements-for-the-php-sql-driver.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|BESCHREIBUNG|  
|---------|---------------|  
| ![Download: eingekreister Pfeil nach unten](../../ssms/media/download-icon.png)[ Herunterladen von Microsoft-Treibern für PHP für SQL Server](download-drivers-php-sql-server.md) | Links zum Herunterladen von Microsoft-Treibern für PHP für SQL Server. |
|[Anmerkungen zu dieser Version für die Microsoft-Treiber für PHP für SQL Server](../../connect/php/release-notes-php-sql-driver.md)|Listet die Features auf, die für die Versionen 4.0, 3.2, 3.1, 3.0 und 2.0 hinzugefügt wurden.|  
|[Unterstützungsressourcen für Microsoft-Treiber für PHP für SQL Server](../../connect/php/support-resources-for-the-php-sql-driver.md)|Enthält Links zu Ressourcen, die hilfreich sein können, wenn Sie Anwendungen entwickeln, die [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]nutzen.|  
|[Informationen zu den Codebeispielen in der Dokumentation](../../connect/php/about-code-examples-in-the-documentation.md)|Enthält Informationen, die beim Ausführen der Codebeispiele in dieser Dokumentation hilfreich sind.|  
| &nbsp; | &nbsp; |

## <a name="reference"></a>Verweis

[API-Referenz für den SQLSRV-Treiber](../../connect/php/sqlsrv-driver-api-reference.md)  
[Referenz zum Treiber PDO_SQLSRV](../../connect/php/pdo-sqlsrv-driver-reference.md)  
[Konstanten &#40;Microsoft-Treiber für PHP für SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)  

## <a name="see-also"></a>Weitere Informationen

[Getting Started with the Microsoft Drivers for PHP for SQL Server (Erste Schritte mit dem Microsoft-Treiber für PHP für SQL Server)](../../connect/php/getting-started-with-the-php-sql-driver.md)

[Programmierhandbuch für die Microsoft-Treiber für PHP für SQL Server](../../connect/php/programming-guide-for-php-sql-driver.md)

[Beispielanwendung &#40;SQLSRV-Treiber&#41;](../../connect/php/example-application-sqlsrv-driver.md)
