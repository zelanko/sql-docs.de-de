---
title: Sofortige Datei Initialisierung konfigurieren
description: Konfigurieren Sie die sofortige Datei Initialisierung auf dem Analytics Platform System. Die sofortige Datei Initialisierung ist ein SQL Server Feature, mit dem Datendatei Vorgänge schneller ausgeführt werden können.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 83ed373fd4fdd38ae5ddd391678b74e3d2e168c9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "74401117"
---
# <a name="instant-file-initialization-configuration"></a>Konfiguration der sofortigen Datei Initialisierung
Die sofortige Datei Initialisierung ist ein SQL Server Feature, mit dem Datendatei Vorgänge schneller ausgeführt werden können. Wenn Sie das Kontrollkästchen aktivieren, um die sofortige Datei Initialisierung zu aktivieren, wird die Leistung von SQL Server PDW verbessert. Wenn dies jedoch ein Sicherheitsrisiko für Ihr Unternehmen darstellt, lassen Sie das Kontrollkästchen deaktiviert.  
  
> [!IMPORTANT]  
> Wenn die sofortige Datei Initialisierung aktiviert ist, überschreibt SQL Server gelöschte Bits mit Nullen nicht.  Dieses Verhalten kann zu einem Sicherheitsrisiko führen, wenn nicht autorisierte Benutzer Zugriff auf gelöschte Daten erhalten. SQL Server PDW jedoch das Risiko verringert, indem sichergestellt wird, dass die SQL Server Datenbank und die Sicherungsdateien immer an eine Instanz von SQL Server angefügt werden. nur das SQL Server-Dienst Konto und der lokale Administrator können auf die gelöschten Daten auf SQL Server PDW zugreifen.  
  
Die sofortige Dateiinitialisierung ist nicht verfügbar, wenn TDE aktiviert ist.  
  
## <a name="add-permission-for-the-backup-account"></a>Berechtigung für das Sicherungs Konto hinzufügen  
Der Sicherungs Vorgang erfordert Netzwerk Anmelde Informationen (Windows-Benutzerkonto), die auf den Speicherort der Sicherung zugreifen können. Sie autorisieren PDW, das Konto mithilfe des [sp_pdw_add_network_credentials](../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md) Verfahrens zu verwenden. Weitere Informationen finden Sie unter [Backup Database](../t-sql/statements/backup-database-parallel-data-warehouse.md) für den gesamten Sicherungs Vorgang. Damit die sofortige Datei Initialisierung verwendet werden kann, muss dem Sicherungs Konto `Perform volume maintenance tasks` die Berechtigung erteilt werden.  
  
1.  Öffnen Sie auf dem Sicherungs Server die Anwendung **lokale Sicherheitsrichtlinie** (`secpol.msc`).  
  
2.  Erweitern Sie im linken Bereich **Lokale Richtlinien**, und klicken Sie dann auf **Zuweisen von Benutzerrechten**.  
  
3.  Doppelklicken Sie im rechten Bereich auf **Durchführen von Volumewartungsaufgaben**.  
  
4.  Klicken Sie auf **Benutzer oder Gruppe hinzufügen** , und fügen Sie alle Benutzerkonten hinzu, die für Sicherungen verwendet werden.  
  
5.  Klicken Sie auf **Übernehmen**, und schließen Sie dann alle Dialogfelder von **Lokale Sicherheitsrichtlinie** .  
  
## <a name="to-turn-instant-file-initialization-on-or-off"></a>So aktivieren oder deaktivieren Sie die sofortige Datei Initialisierung  
  
1.  Starten Sie die Configuration Manager. Weitere Informationen finden Sie unter [Start the Configuration Manager &#40;Analytics Platform System&#41;](launch-the-configuration-manager.md).  
  
2.  Klicken Sie im linken Bereich des Configuration Manager auf **sofortige Datei Initialisierung**.  
  
3.  Aktivieren Sie das Kontrollkästchen neben **sofortige Datei Initialisierung auf allen Knoten aktivieren**, um die sofortige Datei Initialisierung zu aktivieren. Deaktivieren Sie das Kontrollkästchen neben **sofortige Datei Initialisierung auf allen Knoten aktivieren**, um die sofortige Datei Initialisierung zu deaktivieren.  
  
    > [!WARNING]  
    > Wenn Sie die sofortige Datei Initialisierung deaktivieren, kann die oben beschriebene Sicherheits Überlegung für das Feature weiterhin auf Dateien angewendet werden, die während der Aktivierung der sofortigen Datei Initialisierung gelöscht wurden.  
  
4.  Klicken Sie auf **Anwenden**. Die Änderung wird durch die SQL Server Instanzen auf SQL Server PDW weitergegeben, wenn die Geräte Dienste das nächste Mal neu gestartet werden. Informationen zum Neustarten der Geräte Dienste finden Sie unter [PDW-Dienst Status &#40;Analytics Platform System&#41;](pdw-services-status.md).  
  
5.  Möglicherweise möchten Sie die oben beschriebenen Schritte als **Berechtigung hinzufügen für das Sicherungs Konto** wiederholen, um die Berechtigung zum **Ausführen von volumewartungstasks** zu entfernen.  
  
![DWConfig-Anwendung, PDW – Sofortige Dateiinitialisierung](./media/instant-file-initialization-configuration/SQL_Server_PDW_DWConfig_ApplPDWInstant.png "SQL_Server_PDW_DWConfig_ApplPDWInstant")  
  
Weitere Informationen zur sofortigen Datei Initialisierung finden Sie unter [sofortige Datei Initialisierung](https://technet.microsoft.com/library/ms175935(v=SQL.105).aspx).  
  
