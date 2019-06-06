---
title: Sicherstellen der ausreichenden Speicherplatz in TempDB | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- TempDB space in RDS [ADO]
ms.assetid: 09130db1-6248-4234-a1e5-a9c8e1622c06
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: e6d558b64095a4071687ed8edd62d54985015c5d
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66699486"
---
# <a name="ensuring-sufficient-tempdb-space"></a>Sicherstellen, dass ausreichend TempDB-Speicherplatz vorhanden ist
Wenn Fehler, bei der Behandlung auftreten [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekte, die Verarbeitung von Speicherplatz auf der Microsoft SQL Server 6.5, müssen Sie möglicherweise die Größe der TempDB erhöhen. (Einige Abfragen erfordern der temporäre Verarbeitungsbereich; zum Beispiel eine Abfrage mit ORDER BY-Klausel erfordert eine Art von der **Recordset**, wofür einige vorläufige Speicherplatz.)  
  
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012, sind nicht mehr RDS-Server-Komponenten in das Windows-Betriebssystem enthalten (finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) Einzelheiten). RDS-Client-Komponenten werden in einer zukünftigen Version von Windows entfernt werden. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS zu migrieren sollten [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
> [!IMPORTANT]
>  Lesen Sie über dieses Verfahren, bevor Sie die Aktionen ausführen, da es nicht so einfach, ein Gerät zu verkleinern, nachdem es vergrößert wurde.  
  
> [!NOTE]
>  SQLServer 7.0 und höher, TempDB wird vom standardmäßigen InMicrosoft automatisch vergrößert, Bedarf festgelegt. Aus diesem Grund kann diese Prozedur nur auf Servern, die mit Versionen vor 7.0 erforderlich sein.  
  
### <a name="to-increase-the-tempdb-space-on-sql-server-65"></a>Um den TempDB-Speicherplatz auf SQL Server 6.5 zu erhöhen.  
  
1.  Starten Sie Microsoft SQL Server Enterprise Manager, öffnen Sie die Struktur für den Server, und öffnen Sie dann auf die Datenbankmedien-Struktur.  
  
2.  Wählen Sie einen (physischen) Geräts zu erweitern, z. B. Master, und doppelklicken Sie auf das Gerät geöffnet die **Datenbankmedium bearbeiten** Dialogfeld.  
  
     Dieses Dialogfeld zeigt, wie viel Speicherplatz, der die aktuellen Datenbanken verwenden.  
  
3.  In der **Größe** Feld, das Gerät auf die gewünschte Menge (z. B. 50 Megabyte (MB) der Speicherplatz auf dem Datenträger) zu erhöhen.  
  
4.  Klicken Sie auf **jetzt ändern** um die Menge des Speicherplatzes zu erhöhen, die (logische) TempDB erweitern kann.  
  
5.  Öffnen Sie die Struktur der Datenbanken auf dem Server, und doppelklicken Sie dann auf **TempDB** zum Öffnen der **Datenbank bearbeiten** Dialogfeld. Die **Datenbank** Registerkarte zeigt den Umfang an Speicherplatz in TempDB (**Datengröße**). Standardmäßig ist dies 2 MB.  
  
6.  Unter den **Größe** auf **erweitern**. Die Diagramme zeigen die verfügbaren und reservierten Speicherplatz auf jedem physischen Geräte. Die braunen Balken stellen Speicherplatz dar.  
  
7.  Wählen Sie eine **Log Gerät**, z. B. Master-, um die verfügbare Größe in anzuzeigen die **Größe (MB)** Feld.  
  
8.  Klicken Sie auf **jetzt erweitern** um, Platz für die TempDB-Datenbank.  
  
     Die **Datenbank bearbeiten** Dialogfeld zeigt die neue Größe für TempDB belegt.  
  
 Weitere Informationen zu diesem Thema suchen Sie die Hilfe zu Microsoft SQL Server Enterprise Manager-Datei für "Erweitern Sie im Dialogfeld Datenbank."  
  
## <a name="see-also"></a>Siehe auch  
 [Grundlegendes zu RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)


