---
title: Konfigurieren Sie sofortige Dateiinitialisierung - Analytics Platform System | Microsoft-Dokumentation
description: Sofortige Dateiinitialisierung in Analytics Platform System zu konfigurieren. Sofortige dateiinitialisierung ist eine SQL Server-Funktion, mit dem Daten-Dateivorgänge, schneller ausgeführt werden kann.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 27f716b5fc3668b78fd7e5728dc4a2cd640c7940
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67960734"
---
# <a name="instant-file-initialization-configuration"></a>Instant File Initialization-Konfiguration
Sofortige dateiinitialisierung ist eine SQL Server-Funktion, mit dem Daten-Dateivorgänge, schneller ausgeführt werden kann. Überprüfen das Kontrollkästchen, um die sofortige Dateiinitialisierung einschalten steigert die Leistung von SQL Server PDW. Aber wenn dies ein Sicherheitsrisiko Business für Sie darstellt, dann lassen Sie das Kontrollkästchen deaktiviert.  
  
> [!IMPORTANT]  
> Wenn die sofortige dateiinitialisierung aktiviert ist, werden SQL Server keine gelöschten Bits mit Nullen überschrieben.  Dieses Verhalten kann ein Sicherheitsrisiko erstellen, wenn nicht autorisierte Benutzer Zugriff auf gelöschte Daten erhalten. Allerdings verringert SQL Server PDW dieses Risiko, dass sichergestellt wird, dass die SQL Server-Datenbank und die Sicherungsdateien immer mit einer Instanz von SQL Server angefügt werden; nur das SQL Server-Dienstkonto und den lokalen Administrator können die gelöschten Daten in SQL Server PDW zugreifen.  
  
Die sofortige Dateiinitialisierung ist nicht verfügbar, wenn TDE aktiviert ist.  
  
## <a name="add-permission-for-the-backup-account"></a>Fügen Sie die Berechtigung für das Backup-Konto  
Der Sicherungsvorgang ist erforderlich, einen Netzwerkanmeldeinformationen (Windows-Benutzerkonto), auf den Speicherort der Sicherung zugreifen kann. Autorisieren Sie PDW Konto mithilfe der [Sp_pdw_add_network_credentials](../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md) Verfahren. Finden Sie unter [SICHERUNGSDATENBANK](../t-sql/statements/backup-database-parallel-data-warehouse.md) für den gesamten Sicherungsvorgang. Um die sofortige dateiinitialisierung zu verwenden, muss das sicherungskonto gewährt werden die `Perform volume maintenance tasks` Berechtigung.  
  
1.  Öffnen Sie auf den backup-Server, die **Local Security Policy** Anwendung (`secpol.msc`).  
  
2.  Erweitern Sie im linken Bereich **Lokale Richtlinien**, und klicken Sie dann auf **Zuweisen von Benutzerrechten**.  
  
3.  Doppelklicken Sie im rechten Bereich auf **Durchführen von Volumewartungsaufgaben**.  
  
4.  Klicken Sie auf **Benutzer oder Gruppe hinzufügen** , und fügen Sie alle Benutzerkonten hinzu, die für Sicherungen verwendet werden.  
  
5.  Klicken Sie auf **Übernehmen**, und schließen Sie dann alle Dialogfelder von **Lokale Sicherheitsrichtlinie** .  
  
## <a name="to-turn-instant-file-initialization-on-or-off"></a>Zum Aktivieren oder deaktivieren Sie die sofortige Dateiinitialisierung  
  
1.  Starten Sie den Konfigurations-Manager. Weitere Informationen finden Sie unter [Starten des Konfigurations-Managers &#40;Analytics Platform System&#41;](launch-the-configuration-manager.md).  
  
2.  Klicken Sie im linken Bereich des Konfigurations-Managers auf **sofortige Dateiinitialisierung**.  
  
3.  Um die sofortige dateiinitialisierung zu aktivieren, aktivieren das Kontrollkästchen neben **sofortige Dateiinitialisierung aktiviert, auf allen Knoten**. Um die sofortige dateiinitialisierung zu deaktivieren, deaktivieren Sie das Kontrollkästchen neben **sofortige Dateiinitialisierung aktiviert, auf allen Knoten**.  
  
    > [!WARNING]  
    > Wenn Sie sofortige dateiinitialisierung deaktivieren, gelten die Sicherheitsaspekte machen, die weiter oben erläuterten, für die Funktion möglicherweise immer noch für Dateien gelöscht werden, während die sofortige dateiinitialisierung aktiviert wurde.  
  
4.  Klicken Sie auf **Übernehmen**. Die Änderung wird das nächste Mal über die SQL Server-Instanzen für SQL Server PDW weitergegeben, das die Anwendung Dienste neu gestartet werden. Um die Anwendung Dienste neu zu starten, finden Sie unter [PDW-Dienststatus &#40;Analytics Platform System&#41;](pdw-services-status.md).  
  
5.  Möglicherweise möchten Sie die oben erläuterten Schritte wiederholen **Berechtigung hinzufügen, für das Konto für die Sicherung** So entfernen Sie die **Durchführen von Volumewartungsaufgaben** Berechtigung.  
  
![DWConfig PDW-Appliance Instant File Initialization](./media/instant-file-initialization-configuration/SQL_Server_PDW_DWConfig_ApplPDWInstant.png "SQL_Server_PDW_DWConfig_ApplPDWInstant")  
  
Weitere Informationen zur sofortigen dateiinitialisierung finden Sie unter [sofortige Dateiinitialisierung](https://technet.microsoft.com/library/ms175935(v=SQL.105).aspx).  
  
