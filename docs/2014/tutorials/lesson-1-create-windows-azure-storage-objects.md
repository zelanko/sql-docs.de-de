---
title: 'Lektion 1: Erstellen von Azure Storage Objekten | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: 74edd1fd-ab00-46f7-9e29-7ba3f1a446c5
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 9f580b1b7c6cb1127ac9feecf5e767c467e710bd
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85039974"
---
# <a name="lesson-1-create-azure-storage-objects"></a>Lektion 1: Erstellen von Azure Storage-Objekten
  Bevor Sie [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Sicherungen im Cloudspeicher erstellen, müssen Sie zunächst ein Speicherkonto und dann einen BLOB-Container erstellen. Lektion 1 führt Sie durch die Schritte zum Anmelden beim Azure-Verwaltungsportal und zum Erstellen eines Speicher Kontos und eines BLOB-Containers.  
  
## <a name="create-a-storage-account"></a>Erstellen eines Speicherkontos  
 Führen Sie die folgenden Schritte aus, um ein Speicherkonto aus dem Azure-Verwaltungsportal zu erstellen:  
  
1.  Melden Sie sich unter Ihrem Konto beim Azure-Verwaltungsportal an. Wenn Sie nicht über ein Azure-Konto verfügen, besuchen Sie die [Kostenlose Azure-Testversion für 3 Monate](https://go.microsoft.com/fwlink/?LinkId=271927).  
  
     ![Azure-Anmeldebildschirm](../../2014/tutorials/media/windowazurelogin-backuptocloud.gif "Azure-Anmeldebildschirm")  
  
2.  Führen Sie die [hier](https://go.microsoft.com/fwlink/?LinkId=271926)beschriebenen schrittweisen Anweisungen aus, um ein Speicherkonto zu erstellen.  
  
3.  Navigieren Sie zu dem Speicherkonto, das Sie im vorherigen Schritt erstellt haben. Klicken Sie unten in der Mitte der Webseite auf **Schlüssel verwalten**. Die Kontoinformationen werden angezeigt. Kopieren Sie den Speicherkontonamen und die Zugriffsschlüssel. Diese Informationen sind erforderlich, um gespeicherte SQL-Anmeldeinformation zu erstellen. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] verwendet diese Informationen, um auf das Speicherkonto zuzugreifen und Sicherungen zu erstellen.  
  
     ![Screenshot der Azure Storage Kontoschlüssel](../../2014/tutorials/media/manageaccesskeys-backuptocloud.gif "Screenshot der Azure Storage Kontoschlüssel")  
  
    > [!NOTE]  
    >  Sie können ein Speicherkonto mithilfe von REST-APIs auch programmgesteuert erstellen. Weitere Informationen finden Sie unter [Erstellen eines Speicher Kontos](https://go.microsoft.com/fwlink/?LinkId=271928).  
  
### <a name="create-a-blob-container"></a>Erstellen eines BLOB-Containers  
 Ein Container stellt eine Gruppierung eines Blob-Satzes bereit. Alle BLOBs müssen sich in einem Container befinden. Die Anzahl der Container für ein Konto ist unbegrenzt, muss jedoch mindestens 1 betragen. In einem Container kann eine unbegrenzte Anzahl von BLOBs gespeichert werden.  
  
 Führen Sie die folgenden Schritte aus, um einen Container zu erstellen:  
  
1.  Wählen Sie das Speicherkonto aus, klicken Sie auf die Registerkarte **Container** , und klicken Sie am unteren Bildschirmrand auf **Container hinzufügen** , um ein neues Dialogfeld zu öffnen.  
  
     ![Erstellen eines Containers im Verwaltungsportal](../../2014/tutorials/media/backuptocloud.gif "Erstellen eines Containers im Verwaltungsportal")  
  
2.  Geben Sie den Namen für den Container ein. Notieren Sie den eingegebenen Containernamen. Diese Informationen werden in der URL (Pfad der Sicherungsdatei) der T-SQL-Anweisungen in Lektion 3 und 4 verwendet.  
  
3.  Wählen Sie privat als **Zugriffstyp**aus. Es wird empfohlen, zum Sichern der Sicherungsdateien private Container zu erstellen.  
  
     ![Erstellen eines neuen BLOB-Containers](../../2014/tutorials/media/backuptocloud-newblobcontainer.gif "Erstellen eines neuen BLOB-Containers")  
  
    > [!NOTE]  
    >  Sowohl Sicherungs- als auch Wiederherstellungsvorgänge in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] erfordern eine Authentifizierung beim Speicherkonto. Dies gilt auch, wenn Sie einen öffentlichen Container erstellen.  
    >   
    >  Container können mithilfe der REST-APIs auch programmgesteuert erstellt werden. Weitere Informationen finden Sie unter [Create Container](https://go.microsoft.com/fwlink/?LinkId=271946).  
  
### <a name="next-lesson"></a>Nächste Lektion  
 [Lektion 2: Erstellen eines SQL Server](../../2014/tutorials/lesson-2-create-a-sql-server-credential.md)Anmelde Informationen.  
  
  
