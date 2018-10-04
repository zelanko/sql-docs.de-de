---
title: Protokolldatei-Speicherplatz minimieren | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- log file space in RDS [ADO]
ms.assetid: 669662a0-e20f-483e-ab28-53f66c524c98
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 39daf1dd4b3f97628bed17377e7d11f7ecc9c725
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47714468"
---
# <a name="minimizing-log-file-space-usage"></a>Minimieren des Verbrauchs an Protokolldatei-Speicherplatz
Eine Protokolldatei kann schnell füllen (daher den Server verlangsamen) Wenn eine große Anzahl von Aktivitäten auf einer SQL Server-Datenbank vorhanden ist. Legen Sie die Protokolldatei auf **Protokoll bei Prüfpunkt abschneiden** erheblich die Lebensdauer der Protokolldatei für eine Datenbank zu erweitern.  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/en-us/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
### <a name="to-enable-truncate-on-checkpoint-in-microsoft-sql-server-65"></a>Protokoll bei Prüfpunkt in Microsoft SQL Server 6.5 Abschneiden aktivieren  
  
1.  Starten Sie Microsoft SQL Server Enterprise Manager, öffnen Sie die Struktur für den Server, und öffnen Sie dann auf die Datenbankmedien-Struktur.  
  
2.  Doppelklicken Sie auf den Namen der Datenbank, auf der dieses Feature aktiviert wird.  
  
3.  Von der **Datenbank** Registerkarte **Truncate**.  
  
4.  Von der **Optionen** Registerkarte **Protokoll bei Prüfpunkt abschneiden**, und klicken Sie dann auf **OK**.  
  
### <a name="to-enable-truncate-on-checkpoint-in-microsoft-sql-server-70"></a>Um Truncate bei Prüfpunkt in Microsoft SQL Server 7.0 zu aktivieren.  
  
1.  Starten Sie Microsoft SQL Server Enterprise Manager, öffnen Sie die Struktur für den Server, und öffnen Sie dann die Struktur der Datenbanken.  
  
2.  Mit der rechten Maustaste in des Namens der Datenbank auf dem dieses Feature wird aktiviert, und wählen Sie **Eigenschaften**.  
  
3.  Von der **Optionen** Registerkarte **Protokoll bei Prüfpunkt abschneiden**, und klicken Sie dann auf **OK**.  
  
 Weitere Informationen zu den **Protokoll bei Prüfpunkt abschneiden** feature, finden Sie in der Microsoft SQL Server-Dokumentation.  
  
## <a name="see-also"></a>Siehe auch  
 [Grundlegendes zu RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)


