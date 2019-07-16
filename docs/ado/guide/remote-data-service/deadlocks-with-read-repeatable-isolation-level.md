---
title: Deadlocks mit Read Repeatable-Isolationsstufe | Microsoft-Dokumentation
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67922716"
---
# <a name="deadlocks-with-read-repeatable-isolation-level"></a>Deadlocks mit Read Repeatable-Isolationsstufe
Wenn ein benutzerdefiniertes Geschäftsobjekt eine Isolationsstufe repeatable Read, verwendet um den Zugriff auf eine SQL-Server und das Geschäftsobjekt, das gleichzeitig von zwei Clients, die eine Abfrage senden und aktualisieren Sie in der gleichen Transaktion aufgerufen wird, ist ein Deadlock möglich. Remote Data Service wurde entwickelt, um einen der Prozesse zu einem Timeout, um den Deadlock zu ermöglichen, aber das Update für diesen Client fehl.  
  
 Verwenden der [Cursordiensts](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md) **Befehlstimeout** dynamischen Eigenschaft, die die Länge der das Timeout zu ändern.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="see-also"></a>Siehe auch  
 [Grundlegendes zu RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)



