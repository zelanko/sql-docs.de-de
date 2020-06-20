---
title: Datenbank sichern (Seite „Allgemein“) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.backupdatabase.general.f1
ms.assetid: 5c344dfd-1ad3-41cc-98cd-732973b4a162
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1c315c827e1c8b206b2098009510bf6468bd7d74
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84959631"
---
# <a name="back-up-database-general-page"></a>Datenbank sichern (Seite Allgemein)
  Verwenden Sie im Dialogfeld **Datenbank sichern** die Seite **Allgemein** , um die Einstellungen für einen Sicherungsvorgang der Datenbank anzuzeigen und zu ändern.  
  
 Weitere Informationen zu grundlegenden Sicherungskonzepten finden Sie unter [Übersicht über Sicherungen &#40;SQL Server&#41;](backup-overview-sql-server.md).  
  
> [!NOTE]  
>  Wenn Sie eine Sicherungsaufgabe mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]angeben, können Sie das entsprechende [!INCLUDE[tsql](../../includes/tsql-md.md)][BACKUP](/sql/t-sql/statements/backup-transact-sql) -Skript generieren, indem Sie auf die Schaltfläche **Skript** klicken und anschließend ein Ziel für das Skript auswählen.  
  
 **So verwenden Sie SQL Server Management Studio zum Erstellen einer Sicherung**  
  
-   [Erstellen einer vollständigen Datenbanksicherung &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md)  
  
-   [Erstellen einer differenziellen Datenbanksicherung &#40;SQL Server&#41;](create-a-differential-database-backup-sql-server.md)  
  
    > [!IMPORTANT]  
    >  Sie können einen Datenbank-Wartungsplan definieren, um Datenbanksicherungen zu erstellen. Weitere Informationen über [Datenbank-Wartungspläne](../maintenance-plans/maintenance-plans.md) finden Sie in der [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] -Onlinedokumentation.  
  
 **So erstellen Sie eine Teilsicherung**  
  
-   Für eine Teilsicherung müssen Sie die [BACKUP](/sql/t-sql/statements/backup-transact-sql)-Anweisung ([!INCLUDE[tsql](../../includes/tsql-md.md)]) mit der Option PARTIAL verwenden.  
  
## <a name="options"></a>Tastatur  
  
### <a name="source"></a>`Source`  
 Mithilfe der Optionen des Bereichs **Quelle** werden die Datenbank identifiziert und der Sicherungstyp und die Sicherungskomponente für den Sicherungsvorgang angegeben.  
  
 **Datenbank**  
 Wählen Sie die zu sichernde Datenbank aus.  
  
 **Wiederherstellungsmodell**  
 Zeigt das Wiederherstellungsmodell (SIMPLE, FULL oder BULK_LOGGED) für die ausgewählte Datenbank an.  
  
 **Sicherungstyp**  
 Wählen Sie den Sicherungstyp aus, der für die angegebene Datenbank ausgeführt werden soll.  
  
|Sicherungstyp|Verfügbar für|Beschränkungen|  
|-----------------|-------------------|------------------|  
|Vollständig|Datenbanken, Dateien und Dateigruppen|Bei der **master** -Datenbank sind nur vollständige Sicherungen möglich.<br /><br /> Beim einfachen Wiederherstellungsmodell sind Datei- und Dateigruppensicherungen nur für schreibgeschützte Dateigruppen verfügbar.|  
|Differenziell|Datenbanken, Dateien und Dateigruppen|Beim einfachen Wiederherstellungsmodell sind Datei- und Dateigruppensicherungen nur für schreibgeschützte Dateigruppen verfügbar.|  
|Transaktionsprotokoll|Transaktionsprotokolle|Transaktionsprotokollsicherungen sind beim einfachen Wiederherstellungsmodell nicht verfügbar.|  
  
 **Kopiesicherung**  
 Wählen Sie diese Option aus, um eine Kopiesicherung zu erstellen. Eine *Kopiesicherung* ist eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Sicherung, die unabhängig von der Sequenz von herkömmlichen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Sicherungen erstellt wird. Weitere Informationen finden Sie unter [Kopiesicherungen &#40;SQL Server&#41;](copy-only-backups-sql-server.md).  
  
> [!NOTE]  
>  Wenn die Option **Differenziell** aktiviert ist, können Sie keine Kopiesicherung erstellen.  
  
 **Sicherungskomponente**  
 Wählen Sie die zu sichernde Datenbankkomponente aus. Wenn in der Liste **Sicherungstyp** der Eintrag **Transaktionsprotokoll** ausgewählt wird, ist diese Option nicht aktiviert.  
  
 Wählen Sie eines der folgenden Optionsfelder aus:  
  
|||  
|-|-|  
|**Datenbank**|Gibt an, dass die gesamte Datenbank gesichert werden soll.|  
|**Dateien und Dateigruppen**|Gibt an, dass die angegebenen Dateien und/oder Dateigruppen gesichert werden sollen.<br /><br /> Durch das Auswählen dieser Option wird das Dialogfeld **Dateien und Dateigruppen auswählen** geöffnet. Nach dem Auswählen der zu sichernden Dateigruppen oder Dateien und dem Klicken auf **OK**wird die Auswahl im Feld **Dateien und Dateigruppen** angezeigt.|  
  
### <a name="destination"></a>Destination  
 Mit den Optionen des Bereichs **Ziel** können Sie den Typ des Sicherungsmediums für den Sicherungsvorgang angeben und ein vorhandenes logisches oder physisches Sicherungsmedium suchen.  
  
> [!NOTE]  
>  Informationen zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Sicherungsmedien finden Sie unter [Sicherungsmedien &#40;SQL Server&#41;](backup-devices-sql-server.md).  
  
 **Sichern auf**  
 Wählen Sie einen der folgenden Medientypen aus, auf denen gesichert werden soll. Die ausgewählten Ziele werden in der Liste **Sichern auf** angezeigt.  
  
|||  
|-|-|  
|**Datenträger**|Sicherung auf einem Datenträger. Hierbei kann es sich um eine Systemdatei oder ein datenträgerbasiertes logisches Sicherungsmedium handeln, das für die Datenbank erstellt wurde. Die aktuell ausgewählten Datenträger werden in der Liste **Sichern auf** angezeigt. Sie können bis zu 64 Datenträger für den Sicherungsvorgang auswählen.|  
|**Band**|Sicherung auf einem Band. Hierbei kann es sich um ein lokales Bandlaufwerk oder ein bandbasiertes logisches Sicherungsmedium handeln, das für die Datenbank erstellt wurde. Die aktuell ausgewählten Bänder werden in der Liste **Sichern auf** angezeigt. Es können maximal 64 Werte angegeben werden. Wenn keine Bandmedien mit dem Server verbunden sind, ist diese Option deaktiviert. Die ausgewählten Bänder werden in der Liste **Sichern auf** aufgeführt.<br /><br /> Hinweis: Die Unterstützung für Bandsicherungsgeräte wird in zukünftigen Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]entfernt. Nutzen Sie diese Funktionen bei Neuentwicklungen nicht mehr, und planen Sie die Änderung von Anwendungen, die diese Funktion zurzeit verwenden.|  
|**URL**|Sichert in Azure BLOB Storage.|  
  
 Welche Optionen als Nächstes angezeigt werden, ist abhängig vom Typ des ausgewählten Ziels. Wenn Sie einen Datenträger oder ein Band auswählen, werden die folgenden Optionen angezeigt:  
  
 **Add (Hinzufügen)**  
 Fügt der Liste **Sichern auf** eine Datei oder ein Medium hinzu. Sie können auf 64 Medien gleichzeitig auf einem lokalen Datenträger oder Remotedatenträger sichern. Verwenden Sie den vollqualifizierten UNC-Namen (Universal Naming Convention), um eine Datei auf einem Remotedatenträger anzugeben. Weitere Informationen finden Sie unter [Sicherungsmedien &#40;SQL Server&#41;](backup-devices-sql-server.md)aufgezeichnet wurde.  
  
 **Remove**  
 Entfernt mindestens ein aktuell ausgewähltes Medium aus der Liste **Sichern auf** .  
  
 **Contents**  
 Zeigt den Medieninhalt des ausgewählten Mediums an.  
  
 Wenn Sie eine URL als Sicherungsziel auswählen, werden die folgenden Optionen angezeigt:  
  
 **Dateiname**  
 Geben Sie den Namen der Sicherungsdatei an.  
  
 **SQL-Anmelde Informationen**  
 Wählen Sie SQL-Anmelde Informationen aus, die zum Authentifizieren bei Azure Storage verwendet werden. Wenn Sie über keine vorhandenen geeigneten SQL-Anmeldeinformationen verfügen, klicken Sie auf die Schaltfläche **Erstellen** , um neue SQL-Anmeldeinformationen zu erstellen.  
  
> [!IMPORTANT]  
>  Das Dialogfeld, das beim Klicken auf **Erstellen** geöffnet wird, erfordert ein Verwaltungszertifikat oder das Veröffentlichungsprofil für das Abonnement. Wenn Sie keinen Zugriff auf das Verwaltungszertifikat oder Veröffentlichungsprofil haben, können Sie SQL-Anmeldeinformationen erstellen, indem Sie den Namen des Speicherkontos und die Informationen zum Zugriffsschlüssel mithilfe von Transact-SQL oder SQL Server Management Studio angeben. Informationen zum Erstellen von Anmelde Informationen mithilfe von Transact-SQL finden Sie im Beispielcode im Thema [zum Erstellen](../security/authentication-access/create-a-credential.md#Credential) von Anmelde Informationen. Alternativ können Sie auf der Datenbank-Engine-Instanz in SQL Server Management Studio mit der rechten Maustaste auf **Sicherheit**klicken und **Neu**sowie **Anmeldeinformationen**auswählen. Geben Sie im Feld **Identität** den Namen des Speicherkontos und im Feld **Kennwort** den Zugriffsschlüssel an.  
  
 **Azure-Speichercontainer**  
 Geben Sie den Namen des Azure-Speichercontainers an.  
  
 **URL-Präfix:**  
 Wird automatisch entsprechend den Speicherkontoinformationen, die in den SQL-Anmeldeinformationen gespeichert sind, und dem Namen des Azure-Speichercontainers generiert. Es wird empfohlen, die Informationen in diesem Feld nur zu bearbeiten, wenn Sie eine Domäne verwenden, die ein anderes Format als ** \<storage account> . BLOB.Core.Windows.net**verwendet.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sichern eines Transaktionsprotokolls &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md)   
 [Sichern von Dateien und Dateigruppen &#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md)   
 [Definieren eines logischen Sicherungsmediums für eine Datenträgerdatei &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-disk-file-sql-server.md)   
 [Definieren eines logischen Sicherungsmediums für ein Bandlaufwerk &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-tape-drive-sql-server.md)   
 [Wiederherstellungsmodelle &#40;SQL Server&#41;](recovery-models-sql-server.md)  
  
  
