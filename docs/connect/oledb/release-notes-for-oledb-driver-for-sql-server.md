---
title: Versionshinweise (OLE DB-Treiber für SQL Server) | Microsoft-Dokumentation
ms.date: 05/13/2019
ms.prod: sql
ms.technology: connectivity
ms.topic: conceptual
ms.reviewer: genemi
author: mateusz-kmiecik
ms.author: v-makmie
ms.openlocfilehash: 969caa46506c9fd19410c5ace753076b3ba02fbe
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65619987"
---
# <a name="release-notes-for-the-microsoft-ole-db-driver-for-sql-server"></a>Anmerkungen zu dieser Version vom OLE DB-Treiber für SQL Server

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../includes/driver_oledb_download.md)]

Auf dieser Seite wird erläutert, was in den einzelnen Versionen des Microsoft OLE DB-Treibers für SQL Server hinzugefügt wurde.

<!--
USE THE TABLE FORMAT!
Hello, from now on, please use the table-based format standard for all new Release Notes content.
See section "## 18.2.1" for a live example in this article.
Thank you. For questions, contact GeneMi. (2019/03/16)
-->

## <a name="1822"></a>18.2.2

Mai 2019

### <a name="bugs-fixed"></a>Behobene Probleme

| Behobenes Problem | Details |
| :-------- | :------ |
| Die nicht interaktive Azure Active Directory-Authentifizierung im Multithread-Apartment-Modus (MTA) wurde behoben. | Der OLE DB-Treiber Version 18.2.1 versucht fälschlicherweise das COM-Parallelitätsmodell für ein Apartment zu ändern, das zuvor als Multithread-Apartment (MTA) initialisiert wurde. Daher kann der Treiber in einer Anwendung, die vor dem Aufruf der Schnittstelle [IDBInitialize::Initialize](https://go.microsoft.com/fwlink/?linkid=2092522) mehr als einen nachfolgenden Aufruf von [CoInitialize](https://go.microsoft.com/fwlink/?linkid=2092520) oder [CoInitializeEx](https://go.microsoft.com/fwlink/?linkid=2092521) durchführt, keine Verbindung herstellen, wenn ein Azure Active Directory-Authentifizierungsmodus verwendet wird. |
| &nbsp; | &nbsp; |

## <a name="1821"></a>18.2.1

Februar 2019

### <a name="features-added"></a>Neue Features:

| Neues Feature | Details |
| :------------ | :------ |
| Unterstützung der UTF-8-Servercodierung | &bull; &nbsp; [UTF-8-Unterstützung im OLE DB-Treiber für SQL Server](features/utf-8-support-in-oledb-driver-for-sql-server.md). |
| Unterstützung für die Azure Active Directory-Authentifizierung. | &bull; &nbsp; [Verwenden von Azure Active Directory](features/using-azure-active-directory.md). |
| &nbsp; | &nbsp; |

## <a name="1810"></a>18.1.0

Juli 2018

### <a name="features-added"></a>Neue Features:

| Neues Feature | Details |
| :------------ | :------ |
| Unterstützung für das Schlüsselwort der `UseFMTONLY`-Verbindungszeichenfolge sowie für die Initialisierungseigenschaft `SSPROP_INIT_USEFMTONLY`. | `UseFMTONLY` steuert, wie Metadaten abgerufen wird, wenn eine Verbindung mit [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] und höher hergestellt wird.<br/><br/>&bull; &nbsp; [Verwenden von Verbindungszeichenfolgen-Schlüsselwörtern mit dem OLE DB-Treiber für SQL Server](applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md). |
| &nbsp; | &nbsp; |

### <a name="bugs-fixed"></a>Behobene Probleme

| Behobenes Problem | Details |
| :-------- | :------ |
| Die falsche Version der BCP-Formatdatei wurde korrigiert. | Der OLE DB-Treiber 18.0 legt fälschlicherweise die Version der BCP-Formatdatei auf 18.0 statt auf 11.0 fest.<br/><br/>Die Formatdateien, die vom OLE DB-Treiber 18.0 generiert wurden, können nicht vom OLE DB-Treiber 18.1 gelesen werden.<br/><br/>Wenn Sie mit dem neuen Treiber Formatdateien verwenden müssen, die von der vorherigen Treiberversion generiert wurden, können Sie diese Dateien manuell bearbeiten, um die Version in 11.0 zu ändern. |
| &nbsp; | &nbsp; |

## <a name="1802"></a>18.0.2

### <a name="features-added"></a>Neue Features:

| Neues Feature | Details |
| :------------ | :------ |
| Unterstützung für das Schlüsselwort der `MultiSubnetFailover`-Verbindungszeichenfolge sowie für die Initialisierungseigenschaft `SSPROP_INIT_MULTISUBNETFAILOVER`. | &bull; &nbsp; [OLE DB-Treiber für SQL Server-Unterstützung für Hochverfügbarkeit, Notfallwiederherstellung](features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).<br/><br/>&bull; &nbsp; [Verwenden von Verbindungszeichenfolgen-Schlüsselwörtern mit dem OLE DB-Treiber für SQL Server](applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md). |
| &nbsp; | &nbsp; |

## <a name="see-also"></a>Siehe auch

[Microsoft OLE DB-Treiber für SQL Server](oledb-driver-for-sql-server.md)
