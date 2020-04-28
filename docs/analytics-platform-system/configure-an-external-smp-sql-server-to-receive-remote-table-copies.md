---
title: Konfigurieren von SQL Server für den Empfang von Remote Tabellen Kopien
description: Beschreibt, wie eine externe SMP-SQL Server-Instanz konfiguriert wird, um Remote Tabellen Kopien von parallelen Data Warehouse zu empfangen.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 3e5475e86582ede2e6fa7ca5a302bba7ee74faa3
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "74401326"
---
# <a name="configure-an-external-smp-sql-server-to-receive-remote-table-copies---parallel-data-warehouse"></a>Konfigurieren eines externen SMP-SQL Server zum Empfangen von Remote Tabellen Kopien-parallel Data Warehouse
Beschreibt, wie eine externe SQL Server Instanz so konfiguriert wird, dass Remote Tabellen Kopien von parallelen Data Warehouse empfangen werden.  

In diesem Thema wird einer der Konfigurationsschritte zum Konfigurieren der Remote Tabellen Kopie beschrieben. Eine Liste aller Konfigurationsschritte finden Sie unter Kopieren von [Remote Tabellen](remote-table-copy.md).  
  
## <a name="before-you-begin"></a>Vorbereitungen  
Bevor Sie die externe SQL Server konfigurieren können, müssen Sie folgende Schritte ausführen:  
  
-   Sie müssen über ein Windows-System mit SQL Server 2008 Enterprise Edition oder einer neueren Version verfügen, die installiert oder bereits installiert ist. Das Windows-System muss bereits gemäß den Anweisungen in [Konfigurieren eines externen Windows-Systems zum Empfangen von Remote Tabellen Kopien mithilfe von InfiniBand](configure-an-external-windows-system-to-receive-remote-table-copies-using-infiniband.md)konfiguriert werden.  
  
-   Ein Windows-Administrator Konto mit der Möglichkeit, die SQL Server Instanz und das Windows-System zu konfigurieren.  
  
-   Ein SQL Server-Anmelde Konto (wenn SQL Server bereits installiert ist) mit der Möglichkeit, Anmeldungen zu erstellen und Berechtigungen für die Zieldatenbank (en) zu erteilen.  
  
## <a name="configure-an-external-smp-sql-server-to-receive-remote-table-copies"></a><a name="HowToSQLServer"></a>Konfigurieren eines externen SMP-SQL Server zum Empfangen von Remote Tabellen Kopien  
Das Feature "Remote Tabellen Kopie" kopiert Tabellen aus der SQL Server PDW Appliance in eine externe SMP-SQL Server Datenbank, die auf einem Windows-System ausgeführt wird. Nachdem Sie das externe Windows-System für das Empfangen von Remote Tabellen Kopien konfiguriert haben, besteht der nächste Schritt darin, SQL Server auf dem Windows-System zu installieren und zu konfigurieren.  
  
Führen Sie die folgenden Schritte aus, um SQL Server zu konfigurieren:  
  
1.  Installieren Sie SQL Server 2008 Enterprise Edition oder eine höhere Version auf dem Windows-System. Dies wird als SMP-SQL Server bezeichnet.  
  
2.  Konfigurieren Sie SQL Server, um TCP/IP-Verbindungen an einem TCP-Port zu akzeptieren. Diese Konfiguration ist standardmäßig deaktiviert und muss aktiviert werden, damit SQL Server PDW eine Verbindung mit der SMP-SQL Server herstellen kann.  
  
3.  Deaktivieren Sie die Windows-Firewall, oder konfigurieren Sie den SMP-SQL Server TCP-Port so, dass er mit aktivierter Windows-Firewall funktioniert.  
  
4.  Konfigurieren Sie SQL Server, um SQL Server Authentifizierungsmodus zuzulassen. Der parallele Datenexport verwendet immer SQL Server Konten für die Authentifizierung.  
  
5.  Bestimmen Sie ein SQL Server Konto auf dem SMP-SQL Server, das für die Authentifizierung verwendet wird. Erteilen Sie diesem Konto die Berechtigung zum Erstellen, löschen und Einfügen von Daten in Tabellen in der Zieldatenbank für den parallelen Datenexport Vorgang.  
  
## <a name="best-practices-for-smp-sql-server-configuration-for-remote-table-copy"></a><a name="BPSQLConfig"></a>Bewährte Methoden für die Konfiguration von SMP-SQL Server für die Remote Tabellen Kopie  
Verwenden Sie beim Konfigurieren der SMP-SQL Server für den Empfang von Remote Tabellen Kopien die folgenden bewährten Methoden, um die Leistung zu verbessern.  
  
1.  Befolgen Sie die bewährten Methoden, wie in SQL Server Produktdokumentation dokumentiert. Aktivieren Sie z. b. die Datenverschlüsselung. Weitere Informationen zum Sichern von SQL Server finden Sie unter [Sichern von SQL Server](../relational-databases/security/securing-sql-server.md) auf MSDN.  
  
2.  Verwenden Sie das Massen protokollierte oder einfache Wiederherstellungs Modell.  
  
    Während der parallelen Datenexport Vorgänge werden Daten in die neu erstellte Ziel Tabelle Massen eingefügt. Legen Sie für die maximale Leistung während der Massen Einfügung fest, dass die Zieldatenbank das Massen protokollierte oder das einfache Wiederherstellungs Modell verwendet.  
  
3.  Verwenden Sie die Option batch_size, um Protokoll Speicher freizugeben.  
  
    Obwohl bei den Massen protokollierten oder einfachen Wiederherstellungs Modellen die minimale Protokollierung für die Massen eingefügten Daten verwendet wird, erfolgt immer noch eine Protokollierung. Um zu verhindern, dass die Protokolldateien zu groß werden, verwenden Sie die Option SQL Server batch_size, um in regelmäßigen Abständen Protokoll Speicher freizugeben.  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
