---
title: 'Lektion 1: Erstellen Azure Storage Kontos und Containers | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: efdbd930-cde5-41b0-90ad-58a6cc68dddc
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 4c0f364b15053e589d87b715d124bae48a87461e
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85039873"
---
# <a name="lesson-1-create-azure-storage-account-and-container"></a>Lektion 1: Erstellen eines Azure Storage-Kontos und -Containers
  Bevor Sie SQL Server Datendateien in Azure Storage speichern können, müssen Sie zunächst ein Azure Storage Konto, einen BlobContainer und eine Shared Access Signature erstellen. Lektion 1 führt Sie durch die Schritte zum Anmelden beim Azure-Verwaltungsportal, zum Erstellen eines Speicher Kontos, eines BLOB-Containers und einer Shared Access Signature.  
  
 Standardmäßig kann nur der Besitzer des Speicherkontos auf BLOBs, Tabellen und Warteschlangen innerhalb dieses Kontos zugreifen. Um mithilfe dieser neuen SQL Server-Erweiterung ohne Freigabe des Speicherkonto-Zugriffsschlüssels auf diese Ressourcen zugreifen zu können, gehen Sie wie folgt vor:  
  
-   Legen Sie die Berechtigungen des Containers auf "Privat" fest.  
  
-   Erstellen Sie eine Shared Access Signature. Sie ermöglicht es Ihnen, den eingeschränkten Zugriff auf einen Container, ein BLOB, eine Tabelle oder Warteschlangenressource zu delegieren. Geben Sie dazu das Intervall, für das die Ressourcen verfügbar sind, und die entsprechenden Client-Berechtigungen an.  
  
-   Verwenden Sie eine gespeicherte Zugriffsrichtlinie, um Shared Access Signatures für einen Container oder seine BLOBs zu verwalten. Die gespeicherte Zugriffsrichtlinie bietet Ihnen zusätzliche Kontrolle über die Shared Access Signatures und stellt zudem eine einfache Methode dar, um sie aufzuheben.  
  
 Weitere Informationen finden Sie unter [Verwalten des Zugriffs auf Azure Storage Ressourcen](https://msdn.microsoft.com/library/windowsazure/ee393343.aspx).  
  
## <a name="create-storage-account"></a>Erstellen eines Speicherkontos  
 Führen Sie die folgenden Schritte aus, um ein Speicherkonto auf dem Azure-Verwaltungsportal zu erstellen:  
  
1.  Melden Sie sich mit Ihrem Konto beim [Azure-Verwaltungsportal](https://manage.windowsazure.com) an. Wenn Sie kein Azure-Konto haben, sollten Sie die Seite [Kostenlose einmonatige Testversion](https://www.windowsazure.com/pricing/free-trial/)besuchen.  
  
     ![SQL 14 CTP2](../../2014/tutorials/media/ss-was-tutlesson-1-1.gif "SQL 14 CTP2")  
  
2.  Verwenden Sie die Schritt-für-Schritt-Anleitung zum [Erstellen eines Speicher Kontos](https://azure.microsoft.com/documentation/articles/storage-create-storage-account/). Beachten Sie Folgendes: Wenn Sie ein Speicherkonto erstellen, das für die SQL Server Datendateien in Azure verwendet werden soll, sollten Sie die Auswahl der georeplikation deaktivieren bzw. deaktivieren. Dies liegt daran, dass für mehrere BLOBs der Georeplikation keine Schreibreihenfolge gewährleistet wird. Wenn für ein Speicherkonto Georeplikation ausgeführt wird und Wiederherstellung erforderlich ist, tritt eine Beschädigung auf.  
  
     ![SQL 14 CTP2](../../2014/tutorials/media/ss-was-tutlesson-1-2.gif "SQL 14 CTP2")  
  
## <a name="create-a-blob-container"></a>Erstellen eines BLOB-Containers  
 In Azure bietet ein Container eine Gruppierung eines Satzes von BLOB. Alle BLOBs müssen sich in einem Container befinden. Die Anzahl der Container für ein Speicherkonto ist unbegrenzt, muss jedoch mindestens 1 betragen. In einem Container kann eine unbegrenzte Anzahl von BLOBs gespeichert werden. Aktuelle Informationen zu Speichergrößen Limits finden Sie unter [Verwenden des Azure BLOB Storage-Dienstanbieter in .net](https://www.windowsazure.com/develop/net/how-to-guides/blob-storage/).  
  
 Um einen Container in Azure zu erstellen, führen Sie die folgenden Schritte aus:  
  
1.  Melden Sie sich beim [Azure-Verwaltungsportal](https://manage.windowsazure.com) an.  
  
2.  Wählen Sie das Speicherkonto aus, klicken Sie auf die Registerkarte **Container** , und klicken Sie unten auf dem Bildschirm auf **Container hinzufügen** , um ein neues Dialogfeld zu öffnen.  
  
3.  Geben Sie einen Namen für den Container ein.  
  
4.  Wählen Sie **Privat** als **Zugriffstyp**aus. Wenn Sie den Zugriff auf "Privat" festlegen, können die Container-und BLOB-Daten nur vom Besitzer des Azure-Kontos gelesen werden.  
  
     ![SQL 14 CTP2](../../2014/tutorials/media/ss-was-tutlesson-1-4.gif "SQL 14 CTP2")  
  
> [!NOTE]  
>  Um Container programmgesteuert zu erstellen, können Sie auch REST-APIs verwenden. Weitere Informationen finden Sie unter [Create Container](https://msdn.microsoft.com/library/windowsazure/dd179468.aspx) und [Azure Storage Services Rest-API-Referenz](https://msdn.microsoft.com/library/windowsazure/dd179355.aspx).  
  
 **Nächste Lektion:**  
  
 [Lektion 2. Erstellen einer Richtlinie für einen Container und Generieren einer Shared Access Signature &#40;SAS-&#41; Schlüssel](../relational-databases/lesson-1-create-stored-access-policy-and-shared-access-signature.md)  
  
