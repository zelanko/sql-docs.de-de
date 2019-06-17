---
title: 'Lektion 1: Erstellen von Windows Azure-Speicherkonto und Container | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: efdbd930-cde5-41b0-90ad-58a6cc68dddc
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 8a1f8cef9f29c856ab0bc02480221e583a0078f3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62676198"
---
# <a name="lesson-1-create-windows-azure-storage-account-and-container"></a>Lektion 1: Erstellen eines Microsoft Azure Storage-Kontos und -Containers
  Bevor Sie mit dem Speichern von SQL Server-Datendateien im Windows Azure-Speicher beginnen können, müssen Sie zunächst ein Windows Azure-Speicherkonto, einen BLOB-Container und eine Shared Access Signature erstellen. Lektion 1 führt Sie durch die Schritte zur Anmeldung beim Windows Azure-Verwaltungsportal. Dabei erstellen Sie ein Speicherkonto, einen BLOB-Container und eine Shared Access Signature.  
  
 Standardmäßig kann nur der Besitzer des Speicherkontos auf BLOBs, Tabellen und Warteschlangen innerhalb dieses Kontos zugreifen. Um mithilfe dieser neuen SQL Server-Erweiterung ohne Freigabe des Speicherkonto-Zugriffsschlüssels auf diese Ressourcen zugreifen zu können, gehen Sie wie folgt vor:  
  
-   Legen Sie die Berechtigungen des Containers auf "Privat" fest.  
  
-   Erstellen Sie eine Shared Access Signature. Sie ermöglicht es Ihnen, den eingeschränkten Zugriff auf einen Container, ein BLOB, eine Tabelle oder Warteschlangenressource zu delegieren. Geben Sie dazu das Intervall, für das die Ressourcen verfügbar sind, und die entsprechenden Client-Berechtigungen an.  
  
-   Verwenden Sie eine gespeicherte Zugriffsrichtlinie, um Shared Access Signatures für einen Container oder seine BLOBs zu verwalten. Die gespeicherte Zugriffsrichtlinie bietet Ihnen zusätzliche Kontrolle über die Shared Access Signatures und stellt zudem eine einfache Methode dar, um sie aufzuheben.  
  
 Weitere Informationen finden Sie unter [Verwalten des Zugriffs auf Azure-Speicherressourcen](https://msdn.microsoft.com/library/windowsazure/ee393343.aspx).  
  
## <a name="create-storage-account"></a>Erstellen eines Speicherkontos  
 Um ein Speicherkonto im Windows Azure-Verwaltungsportal zu erstellen, führen Sie die folgenden Schritte aus:  
  
1.  Melden Sie sich bei der [Windows Azure-Verwaltungsportal](https://manage.windowsazure.com) mit Ihrem Konto. Wenn Sie nicht über ein Windows Azure-Konto verfügen, besuchen Sie [kostenlose Windows Azure-Testversion](http://www.windowsazure.com/pricing/free-trial/).  
  
     ![SQL 14 CTP2](../../2014/tutorials/media/ss-was-tutlesson-1-1.gif "SQL 14 CTP2")  
  
2.  Verwenden Sie die Schritt-für-Schritt-Anweisungen, um [Erstellen eines Speicherkontos](http://azure.microsoft.com/documentation/articles/storage-create-storage-account/). Wenn Sie ein Speicherkonto erstellen, das für SQL Server-Datendateien in Windows Azure verwendet werden soll, sollten Sie die Auswahl der Georeplikation aufheben oder die Georeplikation deaktivieren. Dies liegt daran, dass für mehrere BLOBs der Georeplikation keine Schreibreihenfolge gewährleistet wird. Wenn für ein Speicherkonto Georeplikation ausgeführt wird und Wiederherstellung erforderlich ist, tritt eine Beschädigung auf.  
  
     ![SQL 14 CTP2](../../2014/tutorials/media/ss-was-tutlesson-1-2.gif "SQL 14 CTP2")  
  
## <a name="create-a-blob-container"></a>Erstellen eines BLOB-Containers  
 In Windows Azure stellt ein Container eine Gruppierung eines BLOB-Satzes bereit. Alle BLOBs müssen sich in einem Container befinden. Die Anzahl der Container für ein Speicherkonto ist unbegrenzt, muss jedoch mindestens 1 betragen. In einem Container kann eine unbegrenzte Anzahl von BLOBs gespeichert werden. Aktuelle Informationen zu Begrenzungen der Speichergröße finden Sie [Gewusst wie: Verwenden des Windows Azure-Blob-Speicherdiensts in .NET](http://www.windowsazure.com/develop/net/how-to-guides/blob-storage/).  
  
 Um einen Container in Windows Azure zu erstellen, führen Sie folgende Schritte aus:  
  
1.  Melden Sie sich bei der [Windows Azure-Verwaltungsportal](https://manage.windowsazure.com).  
  
2.  Wählen Sie das Speicherkonto aus, klicken Sie auf die **Container** Registerkarte, und klicken Sie auf **CONTAINER hinzufügen** am unteren Rand des Bildschirms, der ein neues Dialogfeld geöffnet wird.  
  
3.  Geben Sie einen Namen für den Container ein.  
  
4.  Wählen Sie **Private** für **Zugriffstyp**. Wenn Sie den Zugriff auf "Privat" festlegen, können die Container- und BLOB-Daten nur vom Windows Azure-Kontoeigentümer gelesen werden.  
  
     ![SQL 14 CTP2](../../2014/tutorials/media/ss-was-tutlesson-1-4.gif "SQL 14 CTP2")  
  
> [!NOTE]  
>  Um Container programmgesteuert zu erstellen, können Sie auch REST-APIs verwenden. Weitere Informationen finden Sie unter [-Container erstellen](https://msdn.microsoft.com/library/windowsazure/dd179468.aspx) sowie [Windows Azure Storage Services REST-API-Referenz](https://msdn.microsoft.com/library/windowsazure/dd179355.aspx).  
  
 **Nächste Lektion:**  
  
 [Lektion 2: Erstellen Sie eine Richtlinie für Container und Generieren einer Shared Access Signature &#40;SAS&#41; Schlüssel](../relational-databases/lesson-1-create-stored-access-policy-and-shared-access-signature.md)  
  
  
