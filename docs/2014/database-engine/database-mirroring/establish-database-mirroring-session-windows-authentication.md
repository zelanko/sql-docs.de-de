---
title: Einrichten einer Datenbank-Spiegelungssitzung mithilfe der Windows-Authentifizierung (SQL Server Management Studio) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], sessions
ms.assetid: 7cb418d6-dce1-4a0d-830e-9c5ccfe3bd72
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 70d9b3f9d243531e13d3d5a46693c80288815881
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52520326"
---
# <a name="establish-a-database-mirroring-session-using-windows-authentication-sql-server-management-studio"></a>Einrichten einer Datenbank-Spiegelungssitzung mithilfe der Windows-Authentifizierung (SQL Server Management Studio)
    
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Verwenden Sie stattdessen [!INCLUDE[ssHADR](../../includes/sshadr-md.md)].  
  
 Verwenden Sie im Dialogfeld **Datenbankeigenschaften** die Seite für die **Spiegelung**, um eine Datenbank-Spiegelungssitzung festzulegen und die Eigenschaften der Datenbankspiegelung für eine Datenbank zu ändern. Bevor Sie die Seite für die **Spiegelung** zum Konfigurieren der Datenbankspiegelung verwenden, sollten Sie sicherstellen, dass die folgenden Anforderungen erfüllt sind:  
  
-   Die Prinzipalinstanz und die Spiegelserverinstanz müssen in der gleichen Edition von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt werden: entweder in der Standard-Edition oder in der Enterprise-Edition. Darüber hinaus wird die Ausführung auf vergleichbaren Systemen empfohlen, die identische Arbeitsauslastungen bewältigen können.  
  
    > [!NOTE]  
    >  Eine Zeugenserverinstanz ist nicht in jeder Edition von [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Eine Liste der Funktionen, die von den Editionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]unterstützt werden, finden Sie unter [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
-   Die Spiegeldatenbank muss vorhanden sein und sich auf dem neuesten Stand befinden.  
  
     Zum Erstellen einer Spiegeldatenbank muss auf der Spiegelserverinstanz eine aktuelle Sicherung der Prinzipaldatenbank (mit der Option WITH NORECOVERY) wiederhergestellt werden. Nach der vollständigen Sicherung müssen außerdem eine oder mehrere Protokollsicherungen erstellt und der Reihe nach auf der Spiegeldatenbank (mit der Option WITH NORECOVERY) wiederhergestellt werden. Weitere Informationen finden Sie unter [Prepare a Mirror Database for Mirroring &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md).  
  
-   Wenn die Serverinstanzen unter unterschiedlichen Domänenbenutzerkonten ausgeführt werden, ist für jede Instanz in der **master** -Datenbank der anderen Instanzen ein Anmeldename erforderlich. Sofern kein Anmeldename vorhanden ist, müssen Sie vor dem Konfigurieren der Spiegelung einen erstellen. Weitere Informationen finden Sie unter [Zulassen des Netzwerkzugriffs auf einen Datenbank-Spiegelungsendpunkt mithilfe der Windows-Authentifizierung &#40;SQL Server&#41;](../database-mirroring-allow-network-access-windows-authentication.md).  
  
### <a name="to-configure-database-mirroring"></a>So konfigurieren Sie eine Datenbankspiegelung  
  
1.  Nachdem Sie eine Verbindung mit der Prinzipalserverinstanz hergestellt haben, klicken Sie im Objekt-Explorer auf den Servernamen, um die Serverstruktur zu erweitern.  
  
2.  Erweitern Sie **Datenbanken**, und wählen Sie die zu spiegelnde Datenbank aus.  
  
3.  Klicken Sie mit der rechten Maustaste auf die Datenbank, wählen Sie **Tasks**aus, und klicken Sie dann auf **Spiegeln**. Dadurch wird die Seite **Spiegelung** im Dialogfeld **Datenbankeigenschaften** geöffnet.  
  
4.  Klicken Sie zum Konfigurieren der Spiegelung auf **Sicherheit konfigurieren** , um den Assistenten zum Konfigurieren der Sicherheit für die Datenbankspiegelung zu starten.  
  
    > [!NOTE]  
    >  Während einer Datenbank-Spiegelungssitzung können Sie mithilfe dieses Assistenten nur die Zeugenserverinstanz hinzufügen oder ändern.  
  
5.  Der Assistent zum Konfigurieren der Sicherheit für die Datenbankspiegelung erstellt automatisch auf jeder Serverinstanz den Endpunkt für die Datenbankspiegelung (sofern keiner vorhanden ist) und gibt die Server-Netzwerkadressen in das der Rolle der jeweiligen Serverinstanz entsprechende Feld ein (**Prinzipal**, **Spiegel**oder **Zeuge**).  
  
    > [!IMPORTANT]  
    >  Beim Erstellen eines Endpunkts verwendet der Assistent zum Konfigurieren der Sicherheit für die Datenbankspiegelung immer die Windows-Authentifizierung. Bevor Sie den Assistenten mit der zertifikatbasierten Authentifizierung verwenden können, muss der Spiegelungsendpunkt auf jeder der Serverinstanzen bereits für die Verwendung von Zertifikaten konfiguriert worden sein. Außerdem müssen alle Felder im Dialogfeld **Dienstkonten** des Assistenten leer bleiben. Informationen zum Erstellen eines Datenbank-Spiegelungsendpunkts für die Verwendung von Zertifikaten finden Sie unter [CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql).  
  
6.  Sie können optional den Betriebsmodus ändern. Die Verfügbarkeit von bestimmten Betriebsmodi hängt davon ab, ob Sie eine TCP-Adresse für einen Zeugen angegeben haben. Folgende Optionen stehen zur Verfügung:  
  
    |Option|Zeuge?|Erklärung|  
    |------------|--------------|-----------------|  
    |**Hohe Leistung (asynchron)**|NULL (falls vorhanden, wird er nicht verwendet, die Sitzung benötigt jedoch ein Quorum)|Um die Leistung zu steigern, befindet sich die Spiegeldatenbank immer in einem gewissen zeitlichen Abstand zur Prinzipaldatenbank und niemals auf dem tatsächlich aktuellen Stand. Die Lücke zwischen den beiden Datenbanken ist üblicherweise aber sehr klein. Der Verlust eines Partners hat folgenden Effekt:<br /><br /> Wenn die Spiegelserverinstanz ausfällt, bleibt die Prinzipalinstanz in Betrieb.<br /><br /> Falls die Prinzipalserverinstanz unverfügbar wird, wird der Spiegel beendet. Wenn aber die Sitzung keinen Zeugen hat (wie empfohlen) oder der Zeuge mit dem Spiegelserver verbunden ist, ist der Spiegelserver als betriebsbereiter Server verfügbar. Der Datenbankbesitzer kann die Spiegelserverinstanz zur Übernahme des Diensts zwingen, wobei es möglicherweise zu Datenverlusten kommt.<br /><br /> <br /><br /> Weitere Informationen finden Sie unter [Rollenwechsel während einer Datenbank-Spiegelungssitzung &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md)herunter.|  
    |**Hohe Sicherheit ohne automatisches Failover (synchron)**|Nein|Für alle Transaktionen, für die ein Commit ausgeführt wird, wird sichergestellt, dass sie auf den Datenträger auf dem Spiegelserver geschrieben werden.<br /><br /> Ein manuelles Failover ist möglich, wenn die Partner miteinander verbunden sind und die Datenbank synchronisiert ist. Der Verlust eines Partners hat folgenden Effekt:<br /><br /> Wenn die Spiegelserverinstanz ausfällt, bleibt die Prinzipalinstanz in Betrieb.<br /><br /> Wenn die Prinzipalserverinstanz nicht mehr zur Verfügung steht, wird der Spiegel beendet, ist aber als betriebsbereiter Server verfügbar. Der Datenbankbesitzer kann die Spiegelserverinstanz zur Übernahme des Diensts zwingen, wobei es möglicherweise zu Datenverlusten kommt.<br /><br /> Weitere Informationen finden Sie unter [Rollenwechsel während einer Datenbank-Spiegelungssitzung &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md)herunter.|  
    |**Hohe Sicherheit mit automatischem Failover (synchron)**|Ja (erforderlich)|Für alle Transaktionen, für die ein Commit ausgeführt wird, wird sichergestellt, dass sie auf den Datenträger auf dem Spiegelserver geschrieben werden. Die Verfügbarkeit wird durch Bereitstellen eine Zeugenserverinstanz zur Unterstützung des automatischen Failovers maximiert. Beachten Sie, dass die Auswahl der Option **Hohe Sicherheit mit automatischem Failover (synchron)** nur möglich ist, wenn Sie zuvor eine Zeugenserveradresse angegeben haben. Ein manuelles Failover ist möglich, wenn die Partner miteinander verbunden sind und die Datenbank synchronisiert ist.<br /><br /> In Anwesenheit eines Zeugen hat der Verlust eines Partners die folgende Auswirkung:<br /><br /> – Wenn die Prinzipalserverinstanz nicht mehr verfügbar ist, tritt ein automatisches Failover. Die Spiegelserverinstanz übernimmt die Rolle des Prinzipals und stellt ihre Datenbank als Prinzipaldatenbank zur Verfügung.<br /><br /> – Wenn die Spiegelserverinstanz ausfällt, wird der Prinzipal fortgesetzt.<br /><br /> Weitere Informationen finden Sie unter [Rollenwechsel während einer Datenbank-Spiegelungssitzung &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md)herunter.<br /><br /> **\*\* Wichtig \*\*** Wenn der Zeuge getrennt wird, müssen die Partner miteinander verbunden sein, damit die Datenbank verfügbar ist. Weitere Informationen finden Sie unter [Quorum: Auswirkungen eines Zeugen auf die Datenbankverfügbarkeit &#40;Datenbankspiegelung&#41;](quorum-how-a-witness-affects-database-availability-database-mirroring.md).|  
  
7.  Wenn alle folgenden Bedingungen vorhanden sind, klicken Sie auf **Spiegelung starten** , um die Spiegelung zu beginnen:  
  
    -   Sie sind aktuell mit der Prinzipalserverinstanz verbunden.  
  
    -   Die Sicherheit wurde ordnungsgemäß konfiguriert.  
  
    -   Die vollqualifizierten TCP-Adressen der Prinzipal- und Spiegelserverinstanz sind angegeben (im Abschnitt **Server-Netzwerkadressen** ).  
  
    -   Wenn der Betriebsmodus auf **Hohe Sicherheit mit automatischem Failover (synchron)** festgelegt ist, ist die vollqualifizierte TCP-Adresse der Zeugenserverinstanz ebenfalls angegeben.  
  
8.  Nach dem Beginn der Spiegelung können Sie den Betriebsmodus ändern und die Änderung speichern, indem Sie auf **OK**klicken. Beachten Sie, dass Sie nur in den Hochsicherheitsmodus mit automatischem Failover wechseln können, wenn Sie zuerst eine Zeugenserveradresse angegeben haben.  
  
    > [!NOTE]  
    >  Zum Entfernen des Zeugen löschen Sie seine Servernetzwerkadresse aus dem Feld **Zeuge** . Wenn Sie vom Modus für hohe Sicherheit mit automatischem Failover zum Modus zur hohe Leistung wechseln, wird das Feld **Zeuge** automatisch gelöscht.  
  
## <a name="see-also"></a>Siehe auch  
 [Rollenwechsel während einer Datenbank-Spiegelungssitzung &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md)   
 [Vorbereiten einer Spiegeldatenbank auf die Spiegelung &#40;SQL Server&#41;](prepare-a-mirror-database-for-mirroring-sql-server.md)   
 [Datenbankeigenschaften &#40;Seite wird gespiegelt&#41;](../../relational-databases/databases/database-properties-mirroring-page.md)   
 [Anhalten oder Fortsetzen einer Datenbank-Spiegelungssitzung (SQL Server)](pause-or-resume-a-database-mirroring-session-sql-server.md)   
 [Einrichten der TRUSTWORTHY-Eigenschaft für eine Spiegeldatenbank (Transact-SQL)](set-up-a-mirror-database-to-use-the-trustworthy-property-transact-sql.md)   
 [Entfernen der Datenbankspiegelung (SQL Server)](database-mirroring-sql-server.md)   
 [Verwaltung von Anmeldenamen und Aufträgen nach einem Rollenwechsel (SQL Server)](../../sql-server/failover-clusters/management-of-logins-and-jobs-after-role-switching-sql-server.md)   
 [Einrichten der Datenbankspiegelung &#40;SQL Server&#41;](setting-up-database-mirroring-sql-server.md)   
 [Verwalten von Metadaten beim Bereitstellen einer Datenbank auf einer anderen Serverinstanz &#40;SQL Server&#41;](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md)   
 [Hinzufügen oder Ersetzen eines Datenbank-Spiegelungszeugen &#40;SQL Server Management Studio&#41;](../database-mirroring/add-or-replace-a-database-mirroring-witness-sql-server-management-studio.md)  
  
  
