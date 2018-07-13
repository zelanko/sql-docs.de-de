---
title: Sofortige Datenbankdateiinitialisierung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- initializing files [SQL Server]
- instant file initializations [SQL Server]
- fast file initialization (SQL Server)
- file initialization [SQL Server]
ms.assetid: 1ad468f5-4f75-480b-aac6-0b01b048bd67
caps.latest.revision: 33
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: da60e00ce0162a553d9ecf68368edd3dde193a08
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37180100"
---
# <a name="database-instant-file-initialization"></a>Sofortige Datenbankdateiinitialisierung
  Daten- und Protokolldateien werden initialisiert, um vorhandene Daten zu überschreiben, die von zuvor gelöschten Dateien auf dem Datenträger zurückgelassen wurden. Daten- und Protokolldateien werden erstmals durch Ausfüllen der Dateien mit Nullen initialisiert, wenn Sie eine der folgenden Operationen ausführen:  
  
-   Erstellen einer Datenbank  
  
-   Hinzufügen von Dateien, Protokoll- oder Datendateien, zu einer vorhandenen Datenbank.  
  
-   Vergrößern einer vorhanden Datei (einschließlich Vorgängen zur automatischen Vergrößerung).  
  
-   Wiederherstellen einer Datenbank oder Dateigruppe  
  
 Die Dateiinitialisierung führt dazu, dass diese Vorgänge mehr Zeit benötigen. Aber wenn die Daten zum ersten Mal an die Dateien geschrieben werden, muss das Betriebssystem die Dateien nicht mit Nullen ausfüllen.  
  
## <a name="instant-file-initialization"></a>Sofortige Dateiinitialisierung  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]können Datendateien sofort initialisiert werden. Damit ist eine schnelle Ausführung der zuvor erwähnten Dateivorgänge möglich. Bei der sofortigen Dateiinitialisierung wird belegter Speicherplatz freigegeben, ohne diesen Speicherplatz mit Nullen auszufüllen. Stattdessen wird Datenträgerinhalt überschrieben, wenn neue Daten an die Dateien geschrieben werden. Protokolldateien können nicht sofort initialisiert werden.  
  
> [!NOTE]  
>  Die sofortige Dateiinitialisierung ist nur in [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[winxppro](../../includes/winxppro-md.md)] oder [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] oder höheren Versionen verfügbar.  
  
 Die sofortige Dateiinitialisierung ist nur verfügbar, wenn dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (MSSQLSERVER)-Servicekonto SE_MANAGE_VOLUME_NAME erteilt wurde. Mitglieder der Windows-Administratorengruppe verfügen über dieses Recht und können es anderen Benutzern erteilen, indem sie diese der Sicherheitsrichtlinie **Durchführen von Volumewartungsaufgaben** hinzufügen. Weitere Informationen zum Zuweisen von Benutzerrechten finden Sie in der Windows-Dokumentation.  
  
 Die sofortige Dateiinitialisierung ist nicht verfügbar, wenn TDE aktiviert ist.  
  
 So erteilen Sie einem Konto die Berechtigung `Perform volume maintenance tasks` :  
  
1.  Öffnen Sie auf dem Computer, in dem die Sicherungsdatei erstellt werden, die `Local Security Policy` Anwendung (`secpol.msc`).  
  
2.  Erweitern Sie im linken Bereich **Lokale Richtlinien**, und klicken Sie dann auf **Zuweisen von Benutzerrechten**.  
  
3.  Doppelklicken Sie im rechten Bereich auf **Durchführen von Volumewartungsaufgaben**.  
  
4.  Klicken Sie auf **Benutzer oder Gruppe hinzufügen** , und fügen Sie alle Benutzerkonten hinzu, die für Sicherungen verwendet werden.  
  
5.  Klicken Sie auf **übernehmen**, und schließen Sie dann alle `Local Security Policy` Dialogfelder.  
  
### <a name="security-considerations"></a>Überlegungen zur Sicherheit  
 Da der gelöschte Datenträgerinhalt nur überschrieben wird, wenn neue Daten an die Dateien geschrieben wird, kann ein nicht autorisierter Prinzipal möglicherweise auf den gelöschten Inhalt zugreifen. Während die Datenbankdatei an die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]angefügt ist, wird diese Bedrohung einer Offenlegung von Informationen durch die besitzerverwaltete Zugriffssteuerungsliste (Discretionary Access Control List, DACL) in der Datei verringert. Diese DACL gewährt den Dateizugriff nur für das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienstkonto und den lokalen Administrator. Wenn die Datei jedoch getrennt wird, kann möglicherweise ein Benutzer oder Dienst darauf zugreifen, der nicht über SE_MANAGE_VOLUME_NAME verfügt. Eine ähnliche Bedrohung besteht, wenn die Datenbank gesichert wird. Der gelöschte Inhalt kann für einen nicht autorisierten Benutzer oder Dienst verfügbar werden, wenn die Sicherungsdatei nicht mit einer entsprechenden DACL geschützt wird.  
  
 Wenn Sie sich Gedanken über eine potenzielle Offenlegung von Informationen machen, sollten Sie eine oder beide der folgenden Maßnahmen treffen:  
  
-   Stellen Sie immer sicher, dass alle angebundenen Daten- und Sicherungsdateien über restriktive DACLs verfügen.  
  
-   Deaktivieren Sie die sofortige Dateiinitialisierung für die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , indem Sie SE_MANAGE_VOLUME_NAME im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienstkonto widerrufen.  
  
> [!NOTE]  
>  Das Deaktivieren der sofortigen Dateiinitialisierung wirkt sich nur auf Dateien aus, die nach dem Widerrufen des Benutzerrechts erstellt oder vergrößert werden.  
  
## <a name="see-also"></a>Siehe auch  
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](/sql/t-sql/statements/create-database-sql-server-transact-sql)  
  
  
