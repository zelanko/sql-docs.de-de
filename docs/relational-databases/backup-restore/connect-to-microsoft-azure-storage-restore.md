---
title: Mit Microsoft Azure Storage verbinden (Wiederherstellen) | Microsoft Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql13.swb.restore.connectstorage.f1
ms.assetid: c0b7d7c8-b878-4b7f-8120-d0c6917b583f
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 7be978540b673578fb9ca401f25dfab053f4f7e3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47854173"
---
# <a name="connect-to-microsoft-azure-storage-restore"></a>Mit Microsoft Azure Storage verbinden (Wiederherstellen)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Über das Dialogfeld können Sie die Verbindung zum Windows Azure-Speicherkonto angeben, um den Dateispeicher im Windows Azure-Speicherkonto abzurufen. Nachdem Sie die erforderlichen Informationen angegeben haben, klicken Sie auf **Verbinden** , um die Verbindung zum Windows Azure-Speicher herzustellen.  
  
## <a name="windows-azure-storage-account"></a>Windows Azure-Speicherkonto  
 **Speicherkonto**  
 Geben Sie den Namen des Windows Azure-Speicherkontos an, das Sie verwenden möchten. Im Dropdownfeld werden die zuvor verwendeten Konten aufgeführt.  
  
 **Kontoschlüssel**  
 Geben Sie den Windows Azure-Speicherkonto-Zugriffsschlüssel an.  
  
 **Sichere Endpunkte (HTTPS) verwenden** – Kontrollkästchen  
 Wählen Sie diese Option, um eine sichere Verbindung zum Windows Azure-Speicher herzustellen (empfohlen).  
  
 **Kontoschlüssel speichern** – Kontrollkästchen  
 Aktivieren Sie dieses Kontrollkästchen, wenn SQL Server den Zugriffsschlüssel für dieses Speicherkonto speichern soll.  
  
### <a name="sql-credential"></a>SQL-Anmeldeinformationen  
 **Auswählen vorhandener Anmeldeinformationen**  
 Wählen Sie ein vorhandenes Objekt mit passenden SQL-Anmeldeinformationen für den Kontonamen und den Zugriffsschlüssel aus.  
  
 **Erstellen von neuen Anmeldeinformationen**  
 Wählen Sie diese Option aus, um neue Anmeldeinformationen auf Basis des Speicherkontos und des Kontoschlüssels zu erstellen. Geben Sie den Namen der neuen Anmeldeinformationen im **Anmeldeinformationsname** -Feld an.  
  
  
