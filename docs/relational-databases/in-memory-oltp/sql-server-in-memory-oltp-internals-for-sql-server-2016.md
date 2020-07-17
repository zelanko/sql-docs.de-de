---
title: Merkmale von SQL Server In-Memory OLTP
description: Hier erfahren Sie mehr über die Implementierung der SQL Server In-Memory OLTP-Technologie, die Tabellen als speicheroptimiert deklariert, um In-Memory OLTP-Funktionen zu ermöglichen.
ms.custom: seo-dt-2019
ms.date: 09/14/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: b14da361-a6b8-4d85-b196-7f2f13650f44
author: jodebrui
ms.author: jodebrui
ms.openlocfilehash: e13dc56d78a5305b8fb8221d5622d2cd49ade704
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85735002"
---
# <a name="sql-server-in-memory-oltp-internals-for-sql-server-2016"></a>Merkmale von SQL Server In-Memory-OLTP für SQL Server 2016
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

**Zusammenfassung:** In-Memory-OLTP, Codename „Hekaton“, wurde in SQL Server 2014 eingeführt.
Durch diese leistungsfähige Technologie können Sie den Vorteil großer Mengen an Arbeitsspeicher und vieler Dutzender Kerne nutzen, um die Leistung für OLTP-Vorgänge um bis zu 30 bis 40 Mal zu steigern! SQL Server 2016 investiert weiterhin in In-Memory-OLTP, indem viele Einschränkungen, die in SQL Server 2014 entdeckt wurden, entfernt und interne Verarbeitungsalgorithmen verbessert werden, damit In-Memory-OLTP noch größere Verbesserungen bieten kann. Dieses Whitepaper beschreibt die Implementierung der In-Memory OLTP-Technologie von SQL Server 2016 ab SQL Server 2016 RTM. Bei der Verwendung von In-Memory-OLTP können Tabellen als „speicheroptimiert“ deklariert werden, um die Funktionen von In-Memory-OLTP zu aktivieren. Speicheroptimierte Tabellen sind vollständig transaktional, und es kann mithilfe von Transact-SQL auf sie zugegriffen werden. Gespeicherte Prozeduren in Transact-SQL, Trigger und skalare UDFS (user defined functions, benutzerdefinierte Funktionen) können zur weiteren Leistungsverbesserung in speicheroptimierten Tabellen in Computercode kompiliert werden. Die Engine ist für hohe Parallelität ohne Blockieren vorgesehen.    
  
**Verfasser:** Kalen Delaney  
  
**Technische Reviewer:** Sunil Agarwal und Jos de Bruijn  
  
**Veröffentlicht:** Juni 2016  
  
**Anwendungsbereich:** SQL Server 2016  
  
Um das Dokument zu lesen, laden Sie das Dokument [SQL Server In-Memory OLTP Internals for SQL Server 2016 (Merkmale von SQL Server In-Memory-OLTP für SQL Server 2016)](https://download.microsoft.com/download/8/3/6/8360731A-A27C-4684-BC88-FC7B5849A133/SQL_Server_2016_In_Memory_OLTP_White_Paper.pdf) herunter.   
