---
title: Herunterladen des Microsoft OLE DB-Treibers für SQL Server | Microsoft-Dokumentation
description: Laden Sie den Microsoft OLE DB-Treiber für SQL Server herunter, um native Windows-Anwendungen zu entwickeln, die eine Verbindung mit SQL Server und Azure SQL-Datenbank herstellen.
ms.date: 05/25/2020
ms.prod: sql
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4424f11e4b8d31c964d024b3ecaf90bec0cd7c21
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2020
ms.locfileid: "91727341"
---
# <a name="download-microsoft-ole-db-driver-for-sql-server"></a>Herunterladen des Microsoft OLE DB-Treibers für SQL Server

[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

Der OLE DB-Treiber für SQL Server ist eine eigenständige Datenzugriffs-API (Anwendungsprogrammierschnittstelle), die für OLE DB verwendet wird. Der OLE DB-Treiber für SQL Server ist für Windows verfügbar und stellt den SQL OLE DB-Treiber in einer Dynamic Link Library (DLL) bereit.

## <a name="download"></a>Download

Das weitervertreibbare Installationsprogramm für den Microsoft OLE DB-Treiber für SQL Server installiert die Clientkomponenten, die während der Laufzeit erforderlich sind, um neuere SQL Server-Features nutzen zu können. Ab Version 18.3 schließt das Installationsprogramm auch die Microsoft Active Directory-Authentifizierungsbibliothek (ADAL.dll) mit ein und installiert sie.

Der Microsoft OLE DB-Treiber 18.4 für SQL Server ist die aktuelle allgemein verfügbare Version. Wenn Sie eine frühere Version des Microsoft OLE DB-Treibers 18 für SQL Server installiert haben, können Sie durch Installieren der Version 18.4 ein Upgrade auf Version 18.4 durchführen.

**[![Download](../../ssms/media/download-icon.png) Herunterladen des Microsoft OLE DB-Treibers für SQL Server (x64)](https://go.microsoft.com/fwlink/?linkid=2129954)**  
**[![Download](../../ssms/media/download-icon.png) Herunterladen des Microsoft OLE DB-Treibers für SQL Server (x86)](https://go.microsoft.com/fwlink/?linkid=2131003)**  

### <a name="version-information"></a>Versionsinformationen

- Releasenummer: 18.4.0
- Veröffentlichung: 30. Mai 2020

> [!Note]
> Wenn Sie von einer nicht englischsprachigen Version auf diese Seite zugreifen und den neuesten Inhalt anzeigen möchten, besuchen Sie die [US-englische Version der Website](). Sie können verschiedene Sprachen von der US-englischen Website herunterladen, indem Sie [available languages](#available-languages) (verfügbare Sprachen) auswählen.

## <a name="available-languages"></a>Verfügbare Sprachen

Dieses Release des Microsoft OLE DB-Treibers für SQL Server kann in den folgenden Sprachen installiert werden:

Microsoft OLE DB-Treiber 18.4 für SQL Server (x64):  
[Chinesisch (vereinfacht)](https://go.microsoft.com/fwlink/?linkid=2129954&clcid=0x804) | [Chinesisch (traditionell)](https://go.microsoft.com/fwlink/?linkid=2129954&clcid=0x404) | [Englisch (Vereinigte Staaten)](https://go.microsoft.com/fwlink/?linkid=2129954&clcid=0x409) | [Französisch](https://go.microsoft.com/fwlink/?linkid=2129954&clcid=0x40c) | [Deutsch](https://go.microsoft.com/fwlink/?linkid=2129954&clcid=0x407) | [Italienisch](https://go.microsoft.com/fwlink/?linkid=2129954&clcid=0x410) | [Japanisch](https://go.microsoft.com/fwlink/?linkid=2129954&clcid=0x411) | [Koreanisch](https://go.microsoft.com/fwlink/?linkid=2129954&clcid=0x412) | [Portugiesisch (Brasilien)](https://go.microsoft.com/fwlink/?linkid=2129954&clcid=0x416) | [Russisch](https://go.microsoft.com/fwlink/?linkid=2129954&clcid=0x419) | [Spanisch](https://go.microsoft.com/fwlink/?linkid=2129954&clcid=0x40a)

Microsoft OLE DB-Treiber 18.4 für SQL Server (x86):  
[Chinesisch (vereinfacht)](https://go.microsoft.com/fwlink/?linkid=2131003&clcid=0x804) | [Chinesisch (traditionell)](https://go.microsoft.com/fwlink/?linkid=2131003&clcid=0x404) | [Englisch (Vereinigte Staaten)](https://go.microsoft.com/fwlink/?linkid=2131003&clcid=0x409) | [Französisch](https://go.microsoft.com/fwlink/?linkid=2131003&clcid=0x40c) | [Deutsch](https://go.microsoft.com/fwlink/?linkid=2131003&clcid=0x407) | [Italienisch](https://go.microsoft.com/fwlink/?linkid=2131003&clcid=0x410) | [Japanisch](https://go.microsoft.com/fwlink/?linkid=2131003&clcid=0x411) | [Koreanisch](https://go.microsoft.com/fwlink/?linkid=2131003&clcid=0x412) | [Portugiesisch (Brasilien)](https://go.microsoft.com/fwlink/?linkid=2131003&clcid=0x416) | [Russisch](https://go.microsoft.com/fwlink/?linkid=2131003&clcid=0x419) | [Spanisch](https://go.microsoft.com/fwlink/?linkid=2131003&clcid=0x40a)

## <a name="release-notes"></a>Versionshinweise

Ausführliche Informationen zu diesem Release finden Sie in den [Versionshinweisen](release-notes-for-oledb-driver-for-sql-server.md).

## <a name="previous-releases"></a>Vorgängerversionen

[Frühere Releases des Microsoft OLE DB-Treibers für SQL Server](release-notes-for-oledb-driver-for-sql-server.md#previous-releases)

## <a name="see-also"></a>Weitere Informationen

[Versionsanmerkungen für Microsoft OLE DB Driver for SQL Server](release-notes-for-oledb-driver-for-sql-server.md)  
[Systemanforderungen für den OLE DB-Treiber für SQL Server](system-requirements-for-oledb-driver-for-sql-server.md)  
[Unterstützungsrichtlinien des OLE DB-Treibers für SQL Server](applications\support-policies-for-oledb-driver-for-sql-server.md)  
[Verwendung des OLE DB-Treibers für SQL Server](when-to-use-oledb-driver-for-sql-server.md)  
[Installation des OLE DB-Treibers für SQL Server](applications/installing-oledb-driver-for-sql-server.md)