---
title: 'Lektion 1: Erstellen von Windows Azure-Speicherobjekten | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: 74edd1fd-ab00-46f7-9e29-7ba3f1a446c5
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 449f86b80b93055bb23fe4cd32ace10e15724dbc
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56038341"
---
# <a name="lesson-1-create-windows-azure-storage-objects"></a>Lektion 1: Erstellen von Windows Azure-Speicherobjekten
  Bevor Sie [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Sicherungen im Cloudspeicher erstellen, müssen Sie zunächst ein Speicherkonto und dann einen BLOB-Container erstellen. Lektion 1 führt Sie durch die Schritte zur Protokollierung im Windows Azure-Verwaltungsportal. Dabei erstellen Sie ein Speicherkonto und einen BLOB-Container.  
  
## <a name="create-a-storage-account"></a>Erstellen eines Speicherkontos  
 Um ein Speicherkonto im Windows Azure-Verwaltungsportal zu erstellen, führen Sie die folgenden Schritte aus:  
  
1.  Melden Sie sich unter Ihrem Konto beim Windows Azure-Verwaltungsportal an. Wenn Sie ein Windows Azure-Konto keine [finden Sie auf Windows Azure-3-Monats-Testversion](https://go.microsoft.com/fwlink/?LinkId=271927).  
  
     ![Windows Azure Login Screen](../../2014/tutorials/media/windowazurelogin-backuptocloud.gif "Windows Azure Login Screen")  
  
2.  Verwenden Sie die Schritt-für-Schritt-Anweisungen, die detaillierte [hier](https://go.microsoft.com/fwlink/?LinkId=271926), um ein Speicherkonto zu erstellen.  
  
3.  Navigieren Sie zu dem Speicherkonto, das Sie im vorherigen Schritt erstellt haben. Klicken Sie auf unten in der Mitte der Webseite, auf **Schlüssel verwalten**. Die Kontoinformationen werden angezeigt. Kopieren Sie den Speicherkontonamen und die Zugriffsschlüssel. Diese Informationen sind erforderlich, um gespeicherte SQL-Anmeldeinformation zu erstellen. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] verwendet diese Informationen, um auf das Speicherkonto zuzugreifen und Sicherungen zu erstellen.  
  
     ![Screenshot des Windows Azure-Speicherkontoschlüssel](../../2014/tutorials/media/manageaccesskeys-backuptocloud.gif "Screenshot des Windows Azure-Speicherkontoschlüssel")  
  
    > [!NOTE]  
    >  Sie können ein Speicherkonto mithilfe von REST-APIs auch programmgesteuert erstellen. Weitere Informationen finden Sie unter [Create Storage Account](https://go.microsoft.com/fwlink/?LinkId=271928).  
  
### <a name="create-a-blob-container"></a>Erstellen eines BLOB-Containers  
 Ein Container stellt eine Gruppierung eines Blob-Satzes bereit. Alle BLOBs müssen sich in einem Container befinden. Die Anzahl der Container für ein Konto ist unbegrenzt, muss jedoch mindestens 1 betragen. In einem Container kann eine unbegrenzte Anzahl von BLOBs gespeichert werden.  
  
 Führen Sie die folgenden Schritte aus, um einen Container zu erstellen:  
  
1.  Wählen Sie das Speicherkonto aus, klicken Sie auf die **Container** Registerkarte, und klicken Sie auf **CONTAINER hinzufügen** am unteren Rand des Bildschirms wird ein neues Dialogfeld geöffnet.  
  
     ![Erstellen eines Containers im Verwaltungsportal](../../2014/tutorials/media/backuptocloud.gif "Erstellen eines Containers im Verwaltungsportal")  
  
2.  Geben Sie den Namen für den Container ein. Notieren Sie den eingegebenen Containernamen. Diese Informationen werden in der URL (Pfad der Sicherungsdatei) der T-SQL-Anweisungen in Lektion 3 und 4 verwendet.  
  
3.  Wählen Sie die Private für **Zugriffstyp**. Es wird empfohlen, zum Sichern der Sicherungsdateien private Container zu erstellen.  
  
     ![Erstellen eines neuen Blob-Containers](../../2014/tutorials/media/backuptocloud-newblobcontainer.gif "Erstellen eines neuen Blob-Containers")  
  
    > [!NOTE]  
    >  Sowohl Sicherungs- als auch Wiederherstellungsvorgänge in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] erfordern eine Authentifizierung beim Speicherkonto. Dies gilt auch, wenn Sie einen öffentlichen Container erstellen.  
    >   
    >  Container können mithilfe der REST-APIs auch programmgesteuert erstellt werden. Weitere Informationen finden Sie unter [-Container erstellen](https://go.microsoft.com/fwlink/?LinkId=271946).  
  
### <a name="next-lesson"></a>Nächste Lektion  
 [Lektion 2: Erstellen Sie eine SQL Server-Anmeldeinformation](../../2014/tutorials/lesson-2-create-a-sql-server-credential.md).  
  
  
