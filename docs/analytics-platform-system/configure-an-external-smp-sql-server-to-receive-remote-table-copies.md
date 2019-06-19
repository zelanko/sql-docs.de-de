---
title: Konfigurieren von SQL Server zum Empfangen von remotetabellenkopien - Parallel Data Warehouse | Microsoft-Dokumentation
description: Beschreibt, wie eine externe SMP-SQL Server-Instanz zum Empfangen von remotetabellenkopien von Parallel Data Warehouse zu konfigurieren.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: ae6799d468d57dec04046b443c613823c0a8cb8c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63224683"
---
# <a name="configure-an-external-smp-sql-server-to-receive-remote-table-copies---parallel-data-warehouse"></a>Konfigurieren einer externen SMP-SQL-Server zum Empfangen von remotetabellenkopien - Parallel Data Warehouse
Beschreibt, wie eine externe Instanz von SQL Server zum Empfangen von remotetabellenkopien von Parallel Data Warehouse zu konfigurieren.  

Dieses Thema beschreibt eine Konfigurationsschritte für die Konfiguration von remote-Tabelle kopieren. Eine Liste der alle Konfigurationsschritte, finden Sie unter [Remotetabellenkopie](remote-table-copy.md).  
  
## <a name="before-you-begin"></a>Vorbereitungen  
Bevor Sie den externen SQL Server konfigurieren können, müssen Sie folgende Schritte ausführen:  
  
-   Haben Sie ein Windows-System mit SQL Server 2008 Enterprise Edition oder eine höhere Version installiert oder noch installiert werden kann. Das Windows-System muss bereits konfiguriert sein, gemäß der Anleitung in [konfigurieren Sie eine externe Windows System zu empfangen Remote Tabelle kopiert mithilfe von InfiniBand](configure-an-external-windows-system-to-receive-remote-table-copies-using-infiniband.md).  
  
-   Ein Windows-Admin-Konto mit der Möglichkeit zum Konfigurieren von SQL Server-Instanz und das Windows-System.  
  
-   Ein SQL Server Anmeldekonto (falls es sich um eine SQL Server bereits installiert ist) mit der Möglichkeit zum Erstellen von Anmeldungen, und Erteilen von Berechtigungen für die Ziel-Datenbanken.  
  
## <a name="HowToSQLServer"></a>Konfigurieren eines externen SMP-SQL-Servers zum Empfangen von Remotetabellenkopien  
Die remotetabellenkopie-Features kopiert Tabellen aus der SQL Server-PDW-Appliance mit einer externen SMP-SQL Server-Datenbank, die auf einem Windows-System ausgeführt wird. Nach dem Konfigurieren der externen Windows-Systems zum Empfangen von remotetabellenkopien, ist im nächste Schritt zum Installieren und Konfigurieren von SQL Server auf dem Windows-System.  
  
Verwenden Sie die folgenden Schritte aus, um SQL Server zu konfigurieren:  
  
1.  Installieren Sie SQL Server 2008 Enterprise Edition oder höher auf dem Windows-System an. Dies wird als der SMP-SQL-Server bezeichnet.  
  
2.  Konfigurieren Sie SQL Server für die TCP/IP-Verbindungen über einen festen TCP-Port zu akzeptieren. Diese Konfiguration ist standardmäßig deaktiviert und muss aktiviert sein, um SQL Server PDW für die Verbindung mit dem SMP-SQL-Server zu ermöglichen.  
  
3.  Konfigurieren Sie Windows-Firewall bzw. deaktivieren Sie den SMP-SQL Server TCP-Port, damit es bei aktivierter Windows-Firewall funktioniert.  
  
4.  Konfigurieren Sie SQL Server für SQL Server-Authentifizierungsmodus zu. Die parallele Datenexport immer verwendet SQL Server-Konten für die Authentifizierung.  
  
5.  Bestimmen Sie eine SQL Server-Dienstkonto auf dem SMP-SQL-Server, die für die Authentifizierung verwendet werden. Erteilen Sie diesem Konto die Berechtigung zum Erstellen, löschen und Einfügen von Daten in Tabellen in der Zieldatenbank für den Exportvorgang parallel Daten.  
  
## <a name="BPSQLConfig"></a>Bewährte Methoden für die SMP-SQL Server-Konfiguration für Remotetabellenkopie  
Wenn Sie den SMP-SQL-Server zum Empfangen von remotetabellenkopien konfigurieren zu können, verwenden Sie die folgenden bewährten Methoden zur Verbesserung der Leistung.  
  
1.  Befolgen Sie die bewährten Methoden, wie in SQL Server-Produktdokumentation beschrieben. Aktivieren Sie z. B. Data Encryption. Weitere Informationen zum Sichern von SQL Server finden Sie unter [Sichern von SQL Server](../relational-databases/security/securing-sql-server.md) auf MSDN.  
  
2.  Verwenden Sie das massenprotokollierte oder einfache Wiederherstellungsmodell.  
  
    Exportieren bei der parallelen Vorgänge, die beim Massenkopieren in die neu erstellte Zieltabelle eingefügt. Legen Sie für maximale Leistung während der masseneinfügung die Zieldatenbank mit dem massenprotokollierten oder einfachen Wiederherstellungsmodell.  
  
3.  Verwenden Sie die Batch_size-Option, um wieder Protokollspeicherplatz freizugeben.  
  
    Obwohl die massenprotokollierte oder einfache Wiederherstellung verwenden, die minimale Protokollierung für die Masseneinfügen Daten modelliert, tritt auf, noch einige Protokollierung. Um zu verhindern, dass die Protokolldateien zu groß, verwenden Sie die SQL Server-Batch_size-Option, um in regelmäßigen Abständen wieder Protokollspeicherplatz freizugeben.  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
