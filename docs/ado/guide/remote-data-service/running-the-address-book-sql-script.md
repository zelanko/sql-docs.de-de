---
title: Ausführen des Adressbuchs SQL-Skripts | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- address book application scenario [ADO]
- RDS scenarios [ADO]
ms.assetid: 409b3f8b-0ced-4867-acbe-b245dcdf6702
author: rothja
ms.author: jroth
ms.openlocfilehash: 133ff64f2c15fefac072ecfa28a7f772cea4f465
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82758976"
---
# <a name="running-the-address-book-sql-script"></a>Ausführen des Adress Book-SQL-Skripts
> [!IMPORTANT]
>  Ab Windows 8 und Windows Server 2012 sind RDS-Server Komponenten nicht mehr im Windows-Betriebssystem enthalten (weitere Details finden Sie unter Windows 8 und [Windows Server 2012 Compatibility Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). RDS-Client Komponenten werden in einer zukünftigen Version von Windows entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden. Anwendungen, die RDS verwenden, sollten zu [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)migriert werden.  
  
 Sie müssen entweder das Befehlszeilenprogramm isql/Query Analyzer oder den SQL Server Enterprise-Manager verwenden, um das enthaltene SQL-Skript (sampleemp. SQL) auszuführen, das Folgendes umfasst:  
  
-   Erstellt eine neue Datenbank, addrbookdb, auf dem Standardgerät.  
  
-   Stellt eine Verbindung mit der-Datenbank her, addrbookdb.  
  
-   Erstellt eine Employee-Tabelle.  
  
-   Füllt die Tabelle mit Beispiel Daten auf.  
  
-   Führt eine einfache SELECT-Anweisung aus, um die Auffüllung der Datenbanktabelle zu überprüfen.  
  
-   Richtet ein Benutzerkonto mit dem Namen "adcdemo" mit dem Kennwort "adcdemo" ein.  
  
#### <a name="to-run-the-sampleempsql-script-in-microsoft-sql-server-65"></a>So führen Sie das Skript "sampleemp. SQL" in Microsoft SQL Server 6,5 aus  
  
1.  Klicken Sie auf **Start**, zeigen Sie auf **Programme**, und zeigen Sie dann auf **Microsoft SQL Server 6,5**. Klicken Sie auf **SQL Enterprise Manager**.  
  
2.  Klicken Sie **im Menü** Extras auf **SQL-Abfrage Tool**.  
  
3.  Klicken Sie auf **SQL-Skript laden** , und navigieren Sie zu c:\platform sdk\samples\dataaccess\rds\addressbook.  
  
4.  Wählen Sie die Datei sampleemp. SQL aus. Klicken Sie auf **Öffnen**.  
  
5.  Klicken Sie auf die Schaltfläche **Abfrage ausführen** (der grüne Pfeil auf der Symbolleiste).  
  
6.  Schließen Sie nach der Ausführung die **Abfrage** und die Fenster von **Enterprise Manager** .  
  
#### <a name="to-run-the-sampleempsql-script-in-microsoft-sql-server-70"></a>So führen Sie das Skript "sampleemp. SQL" in Microsoft SQL Server 7,0 aus  
  
1.  Klicken Sie auf **Start**, zeigen Sie auf **Programme**, und zeigen Sie dann auf **Microsoft SQL Server 7,0**. Klicken Sie auf **Enterprise Manager**.  
  
2.  Stellen Sie sicher, dass die SQL Server, die Sie verwenden möchten, in der Liste der registrierten Server in Enterprise Manager ausgewählt ist.  
  
3.  Klicken Sie **im Menü** Extras auf **SQL Server Query Analyzer**.  
  
4.  Klicken Sie auf die Schaltfläche **SQL-Skript laden** (den Ordner öffnen auf der Symbolleiste), und navigieren Sie zu c:\platform sdk\samples\dataaccess\rds\addressbook.  
  
5.  Wählen Sie die Datei sampleemp. SQL aus. Klicken Sie auf **Öffnen**.  
  
6.  Klicken Sie auf die Schaltfläche **Abfrage ausführen** (grüner Pfeil auf der Symbolleiste) oder **F5**.  
  
7.  Schließen Sie nach der Ausführung die **Abfrage**, **Abfrage Analyse**und **Enterprise Manager** -Fenster.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausführen der Adress Book-Beispielanwendung](../../../ado/guide/remote-data-service/running-the-address-book-sample-application.md)


