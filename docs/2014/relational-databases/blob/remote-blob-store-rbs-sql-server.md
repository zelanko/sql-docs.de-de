---
title: Remote Blob Store (RBS) (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.technology: filestream
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Remote Blob Store (RBS) [SQL Server]
- RBS (Remote Blob Store) [SQL Server]
ms.assetid: 31c947cf-53e9-4ff4-939b-4c1d034ea5b1
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 4379e0ff3ca534acd6ae130cbdf0f8acd2b6a81f
ms.sourcegitcommit: 45a9d7ffc99502c73f08cb937cbe9e89d9412397
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2019
ms.locfileid: "66009850"
---
# <a name="remote-blob-store-rbs-sql-server"></a>Remote Blob Store (RBS) (SQL Server)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Remote BLOB-Speicher (RBS) ist eine optionale Add-On-Komponente, mit der Datenbankadministratoren Binary Large Objects in Speicherlösungen statt direkt auf dem Hauptdatenbankserver speichern können.  
  
 RBS ist nicht auf den [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Installationsmedien enthalten. Er wird auch nicht über das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setupprogram installiert.  
  
 Weitere Informationen zu RBS finden Sie in diesem Thema unter [RSB-Ressourcen](#rbsresources) .  
  
## <a name="benefits-of-rbs"></a>Vorteile von RBS  
 RBS bietet die folgenden Vorteile:  
  
### <a name="optimized-database-storage-and-performance"></a>Optimierte Datenbankspeicher und optimierte Datenbankleistung  
 Durch das Speichern von BLOBs in der Datenbank können große Mengen an Dateispeicherplatz sowie teure Serverressourcen belegt werden. RBS überträgt auf effiziente Weise BLOBs auf eine dedizierte Speicherlösung Ihrer Wahl und speichert Verweise auf diese in der Datenbank. Dadurch werden Serverspeicher für strukturierte Daten und Serverressourcen für Datenbankoperationen freigegeben.  
  
### <a name="efficient-management-of-blobs"></a>Effiziente Verwaltung von BLOBs  
 Mehrere RBS-Funktionen unterstützen die bequeme Verwaltung von gespeicherten BLOBs:  
  
-   BLOBs werden mithilfe von ACID-Transaktionen (atomic consistency isolation durable; Unteilbarkeit, Konsistenz, Isolation, Dauerhaftigkeit) verwaltet.  
  
-   BLOBs sind in Auflistungen unterteilt.  
  
-   Automatische Speicherbereinigung, Konsistenzüberprüfung und andere Wartungsfunktionen sind enthalten.  
  
### <a name="standardized-api"></a>Standardisierte API  
 RBS definiert einen Satz von APIs, die ein standardisiertes Programmiermodell für Anwendungen bereitstellen, um auf BLOB-Speicher zuzugreifen und zu ändern. Jeder BLOB-Speicher kann eine eigene Anbieterbibliothek angeben, die an die RBS-Clientbibliothek angeschlossen wird und angibt, wie BLOBs gespeichert werden und auf sie zugegriffen wird.  
  
 Eine Reihe von Speicherlösungen von Drittanbietern haben RBS-Anbieter entwickelt, die diesen Standard-APIs entsprechen und BLOB-Speicherung auf verschiedenen Speicherplattformen unterstützen.  
  
## <a name="rbs-requirements"></a>RSB-Anforderungen  
 RSB erfordert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise für den Hauptdatenbankserver, in dem die BLOB-Metadaten gespeichert werden. Wenn Sie jedoch den bereitgestellten FILESTREAM-Anbieter verwenden, können Sie die BLOBs selbst auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Standard speichern.  
  
 RBS beinhaltet einen FILESTREAM-Anbieter, mit dem Sie BLOBs mithilfe von RBS auf einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]speichern können. Wenn Sie BLOBs mithilfe von RBS in einer anderen Speicherlösung speichern möchten, müssen Sie einen für diese Speicherlösung entwickelten RSB-Anbieter eines Drittanbieters verwenden oder einen benutzerdefinierten RBS-Anbieter mithilfe der RBS-API entwickeln. Ein Beispielanbieter, der BLOBs im NTFS-Dateisystem speichert, steht als Lernressource auf [Codeplex](https://go.microsoft.com/fwlink/?LinkId=210190)zur Verfügung.  
  
## <a name="rbs-security"></a>RSB-Sicherheit  
 Wenn Sie einen benutzerdefinierten Anbieter verwenden, um BLOBs außerhalb von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zu speichern, stehen diese möglicherweise auch anderen Prozessen, die das[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Sicherheitssystem umgehen, zur Verfügung. Stellen Sie sicher, dass die gespeicherten BLOBs anhand von Berechtigungen und Verschlüsselungsoptionen geschützt sind, die für das vom benutzerdefinierten Anbieter verwendete Speichermedium geeignet sind.  
  
##  <a name="rbsresources"></a> RSB-Ressourcen  
 **RBS-Dokumentation**  
 Die RBS-Dokumentation ist im Windows Installer-Paket enthalten. Wenn Sie die RBS-Dokumentation durchlesen möchten, ohne RBS zu installieren, können Sie die [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] -Version der Dokumentation auch [online in der MSDN Library](https://go.microsoft.com/fwlink/?LinkId=210192)anzeigen.  
  
 **RSB-Whitepaper**  
 Das Whitepaper [Remote BLOB Storage](https://go.microsoft.com/fwlink/?LinkId=210422), das als Microsoft Word-Dokument in englischer Sprache zum Download zur Verfügung steht, bietet ausführliche Informationen zur Installation und Konfiguration von RBS.  
  
 **RSB-Beispiele**  
 In den auf [CodePlex](https://go.microsoft.com/fwlink/?LinkId=210190) verfügbaren RSB-Beispielen wird veranschaulicht, wie Sie eine RBS-Anwendung entwickeln und einen benutzerdefinierten RBS-Anbieter installieren.  
  
 **RBS-Blog**  
 Der [RBS-Blog](https://go.microsoft.com/fwlink/?LinkId=210315) bietet zusätzliche Informationen, durch die Sie RBS besser verstehen, bereitstellen und verwalten können.  
  
  
