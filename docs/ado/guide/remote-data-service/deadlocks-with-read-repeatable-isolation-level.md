---
title: Deadlocks mit Lese wiederholbarer Isolationsstufe | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- deadlocks in RDS [ADO]
- read repeatable in RDS [ADO]
ms.assetid: 29f3683f-12f3-4304-8a54-fe133c25a423
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c8e4e59606f3b68fbd9ce272db8ea8a50ab53e88
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67922716"
---
# <a name="deadlocks-with-read-repeatable-isolation-level"></a>Deadlocks mit Read Repeatable-Isolationsstufe
Wenn ein benutzerdefiniertes Geschäftsobjekt die Isolationsstufe Read REPEATABLE verwendet, um auf einen SQL Server zuzugreifen, und das Geschäftsobjekt gleichzeitig von zwei Clients aufgerufen wird, die eine Abfrage senden und in derselben Transaktion aktualisieren, ist ein Deadlock möglich. Der Remote Data Service ist so konzipiert, dass einem der Prozesse ein Timeout für die Freigabe des Deadlocks ermöglicht wird, das Update für diesen Client jedoch fehlschlägt.  
  
 Verwenden Sie die dynamische Eigenschaft [Cursor Dienst](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md) **Command** Timeout, um die Länge des Timeouts zu ändern.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Grundlegendes zu RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)



