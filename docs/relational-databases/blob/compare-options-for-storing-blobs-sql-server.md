---
title: Vergleichen von Optionen zum Speichern von Blobs (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
ms.assetid: 6038697b-36a9-49e8-a02a-2ad9e2e60e5a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 68efb09a2b6d2a3ace441107ed9160fede154c8a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68085445"
---
# <a name="compare-options-for-storing-blobs-sql-server"></a>Vergleichen von Optionen zum Speichern von Blobs (SQL Server)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Erläutert und vergleicht die Optionen, die zum Speichern von Dateien und Dokumenten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verfügbar sind.

## <a name="Expectations"></a> Speichern von Dateien in der Datenbank: Vorteile und Erwartungen

Ein großer Prozentsatz der Unternehmensdaten ist unstrukturiert und wird in der Regel als Dateien und Dokumente in Dateisystemen gespeichert. Der Großteil dieser Daten wird von Anwendungen generiert, verwaltet und benötigt, die über Windows-APIs auf die Dateien zugreifen. Unternehmen speichern diese Daten in der Regel im Dateisystem, wohingegen die verwandten Metadaten für die Dateien in einer relationalen Datenbank gespeichert werden.

Die Integration unstrukturierter Daten in die relationale Datenbank bietet die folgenden Vorteile:

- Integrierte Speicher- und Datenverwaltungsfunktionen, z. B. Sicherungen.
- Integrierte Dienste, z. B. Volltextsuche und semantische Suche über Daten und Metadaten.
- Einfache Administration und Richtlinienverwaltung der unstrukturierten Daten.

Es war generell jedoch nicht zweckdienlich, unstrukturierte Daten in einer relationalen Datenbank zu speichern. Das erneute Schreiben etablierter Anwendungen (z.B. Microsoft Word oder Adobe Reader) zur Interaktion über relationale Datenbank-APIs hat sich nicht als praktisch erwiesen. Bei diesen Anwendungen wird erwartet, dass über Windows-APIs auf die Daten zugegriffen werden kann. Für die Anwendungen bestehen die folgenden Erwartungen:

- Für Windows-Anwendungen sind keine Datenbanktransaktionen erforderlich, und diese werden nicht berücksichtigt.
- Windows-Anwendungen erfordern für Datei- und Verzeichnisdaten Kompatibilität mit Dateisystem-APIs.

Vor vielen Jahren gab es in SQL Server keine Möglichkeit, unstrukturierte Daten in einer relationalen Datenbank zu speichern. Heute gibt es in SQL Server jedoch Möglichkeiten, unstrukturierte Daten zu speichern.

## <a name="Filestream"></a> FILESTREAM

In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gibt es das FILESTREAM-Feature bereits. Das FILESTREAM-Feature ermöglicht ein effizientes Speichern, Verwalten und Streamen unstrukturierter Daten, die als Dateien im Dateisystem gespeichert sind. Bei einer FILESTREAM-Lösung ist jedoch die benutzerdefinierte Programmierung erforderlich. Sie wird der oben beschriebenen Anforderung im Hinblick auf vollständige Windows-Anwendungskompatibilität nicht gerecht.

## <a name="FileTables"></a> FileTables

Das FileTable-Feature basiert auf den vorhandenen FILESTREAM-Funktionen. Das FileTable-Feature ermöglicht Unternehmenskunden, unstrukturierte Dateidaten sowie Verzeichnishierarchien in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank zu speichern. Das Feature richtet sich dabei an die Anforderungen für nicht transaktionalen Zugriff und die Kompatibilität von Windows-Anwendung mit dateibasierten Daten.

## <a name="CompareFileTable"></a> Vergleichen von FILESTREAM und FileTable

|Funktion|Dateiserver und Datenbanklösung|FILESTREAM-Lösung|FileTable-Lösung|
|:------|:--------------------------------|:------------------|:-----------------|
|**Einzelne Story für Verwaltungstasks**|Nein|Ja|**ja**|
|**Einzelner Satz von Diensten**: Suche, Berichterstellung, Abfrage usw.|Nein|Ja|**ja**|
|**Integriertes Sicherheitsmodell**|Nein|Ja|**Ja**|
|**Direkte Updates der FILESTREAM-Daten**|Ja|Nein|**ja**|
|**In der Datenbank beibehaltene Datei- und Verzeichnishierarchie**|Nein|Nein|**ja**|
|**Windows-Anwendungskompatibilität**|Ja|Nein|**Ja**|
|**Relationaler Zugriff auf Dateiattribute**|Nein|Nein|**ja**|

## <a name="CompareRBS"></a> Vergleichen von FILESTREAM und Remote BLOB-Speicher (RBS)

Eine weitere Option für das Speichern unstrukturierter Daten schließt einen Remote Blob Store (RBS) ein. Weitere Informationen finden Sie unter [Remote Blob Store (RBS) (SQL Server)](remote-blob-store-rbs-sql-server.md).

## <a name="more"></a> Weitere Informationen

[FILESTREAM &#40;SQL Server&#41;](../../relational-databases/blob/filestream-sql-server.md)  
[FileTables &#40;SQL Server&#41;](../../relational-databases/blob/filetables-sql-server.md)  
[Remoteblobspeicher &#40;RBS&#41; &#40;SQL Server&#41;](../../relational-databases/blob/remote-blob-store-rbs-sql-server.md)
