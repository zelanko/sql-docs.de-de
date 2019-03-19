---
title: Versionshinweise (OLE DB-Treiber für SQL Server) | Microsoft-Dokumentation
ms.date: 02/13/2019
ms.prod: sql
ms.technology: connectivity
ms.topic: conceptual
ms.reviewer: genemi
author: mateusz-kmiecik
ms.author: v-makmie
ms.openlocfilehash: 2a1d6d216f4f7ec7fee0f5f9aa5810c78f1936e6
ms.sourcegitcommit: 03870f0577abde3113e0e9916cd82590f78a377c
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2019
ms.locfileid: "58161767"
---
# <a name="release-notes-for-the-microsoft-ole-db-driver-for-sql-server"></a>Versionshinweise zum OLE DB-Treiber für SQL Server

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../includes/driver_oledb_download.md)]

Auf dieser Seite wird erläutert, was in den einzelnen Versionen des Microsoft OLE DB-Treibers für SQL Server hinzugefügt wurde.

<!--
USE THE TABLE FORMAT!
Hello, from now on, please use the table-based format standard for all new Release Notes content.
See section "## 18.2.1" for a live example in this article.
Thank you. For questions, contact GeneMi. (2019/03/16)
-->

## <a name="1821"></a>18.2.1

<!--
USE THE TABLE FORMAT!
Hello, from now on, please use the table-based format standard for all new Release Notes content.
See section "## 18.2.1" for a live example in this article.
Thank you. For questions, contact GeneMi. (2019/03/16)
-->

Februar 2019

### <a name="features-added"></a>Funktionen, die hinzugefügt

| Feature hinzugefügt | Details |
| :------------ | :------ |
| Unterstützung für UTF-8-Codierung-Server. | &bull; &nbsp; [UTF-8-Unterstützung im OLE DB-Treiber für SQL Server](features/utf-8-support-in-oledb-driver-for-sql-server.md). |
| Unterstützung für die Azure Active Directory-Authentifizierung. | &bull; &nbsp; [Verwenden von Azure Active Directory](features/using-azure-active-directory.md). |
| &nbsp; | &nbsp; |

## <a name="1810"></a>18.1.0

Juli 2018

### <a name="features-added"></a>Funktionen, die hinzugefügt

| Feature hinzugefügt | Details |
| :------------ | :------ |
| Unterstützung für die `UseFMTONLY` Schlüsselwort für Verbindungszeichenfolgen, und für die `SSPROP_INIT_USEFMTONLY` -Eigenschaft zur datenquelleninitialisierung. | `UseFMTONLY` Steuert, wie die Metadaten abgerufen werden, bei der Verbindung [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] und höher.<br/><br/>&bull; &nbsp; [Verwenden von Verbindungszeichenfolgen-Schlüsselwörtern mit dem OLE DB-Treiber für SQL Server](applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md). |
| &nbsp; | &nbsp; |

### <a name="bugs-fixed"></a>Behobene Probleme

| Behobenes Problem | Details |
| :-------- | :------ |
| Feste falsche Version von der BCP-Formatdatei. | OLE DB-Treiber-18.0 legt fälschlicherweise die Version der BCP-Formatdatei zu 18.0, statt auf 11.0 fest.<br/><br/>Formatdateien, die vom OLE DB-Treiber-18.0 können nicht von der OLE DB-Treiber 18.1. gelesen werden.<br/><br/>Wenn Sie Dateien im Format generiert, indem Sie die vorherige Version des Treibers durch den neuen Treiber verwenden müssen, können Sie die Dateien, um die Version 11.0 ändern manuell bearbeiten. |
| &nbsp; | &nbsp; |

## <a name="1802"></a>18.0.2

### <a name="features-added"></a>Funktionen, die hinzugefügt

| Feature hinzugefügt | Details |
| :------------ | :------ |
| Unterstützung für die `MultiSubnetFailover` Schlüsselwort für Verbindungszeichenfolgen, und die `SSPROP_INIT_MULTISUBNETFAILOVER` -Eigenschaft zur datenquelleninitialisierung. | &bull; &nbsp; [OLE DB-Treiber für SQL Server-Unterstützung für Hochverfügbarkeit, Notfallwiederherstellung](features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).<br/><br/>&bull; &nbsp; [Verwenden von Verbindungszeichenfolgen-Schlüsselwörtern mit dem OLE DB-Treiber für SQL Server](applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md). |
| &nbsp; | &nbsp; |

## <a name="see-also"></a>Siehe auch

[Microsoft OLE DB-Treiber für SQL Server](oledb-driver-for-sql-server.md)
