---
title: Mit Microsoft Azure Storage verbinden | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/12/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.swb.windowsazurestorage.connect.f1
- SQL13.SWB.WINDOWSAZURESTORAGE.CONNECT.F1
ms.assetid: ''
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 2c4381ddbbe0a218b6fc53d8e054017b66068b59
ms.sourcegitcommit: 944af0f6b31bf07c861ddd4d7960eb7f018be06e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/31/2019
ms.locfileid: "66454552"
---
# <a name="connect-to-microsoft-azure-storage"></a>Mit Microsoft Azure Storage verbinden
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Verwenden Sie das Dialogfeld **Windows Azure Storage-Verbindung** , um ein Speicherkonto anzugeben und die Verbindung mit Windows Azure zu überprüfen.  
  
## <a name="options"></a>enthalten  
Geben Sie die folgenden Informationen zum Windows Azure-Konto an, und klicken Sie dann auf **Weiter** , um fortzufahren.  
  
1.  **Speicherkonto** – Geben Sie den Speicherkontonamen an.

   >[!NOTE]
   > Sie können nur Verbindungen zu [allgemeinen Speicherkonten](https://docs.microsoft.com/azure/storage/storage-introduction#azure-storage-services) herstellen. Die Verbindungserstellung zu anderen Arten von Speicherkonten kann zu einem Fehler wie dem folgenden führen:
   >
   >  The value for one of the HTTP headers is not in the correct format. (Das Format von einem der Werte des HTTP-Headers ist nicht korrekt.) (Microsoft.SqlServer.StorageClient).
   >
   >  The remote server returned an error: (400) Bad Request (400 (Ungültige Anforderung)). (System)

2.  **Kontoschlüssel** – Geben Sie den Kontoschlüssel für das angegebene Speicherkonto an.  
  
3.  **Sichere Endpunkte verwenden (HTTPS)** : Bei Aktivierung dieser Option wird die Kommunikation verschlüsselt, und für Netzwerkwebserver wird eine sichere Identifikation verwendet.  
  
4.  **Kontoschlüssel speichern** – Bei Aktivierung dieser Option wird das Kennwort in einer verschlüsselten Datei gespeichert.  
  
