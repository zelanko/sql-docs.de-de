---
title: Verbindung mit Azure Storage herstellen (Wiederherstellen) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.restore.connectstorage.f1
ms.assetid: c0b7d7c8-b878-4b7f-8120-d0c6917b583f
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 6fbb57fe629797e34cc7c61f224d65d46d4e66cd
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/29/2019
ms.locfileid: "70154775"
---
# <a name="connect-to-azure-storage-restore"></a>Verbindung mit Azure Storage herstellen (Wiederherstellen)
  Mit dem Dialogfeld können Sie die Verbindung mit den Azure-Speicherkonto Informationen angeben, um den Dateispeicher im Azure-Speicherkonto abzurufen. Nachdem Sie die erforderlichen Informationen angegeben haben, klicken Sie auf **verbinden** , um die Verbindung mit dem Azure-Speicher herzustellen.  
  
## <a name="azure-storage-account"></a>Azure-Speicherkonto  
 **Speicherkonto**  
 Wählen Sie den Namen des Azure-Speicher Kontos aus, das Sie verwenden möchten, oder geben Sie ihn ein. Im Dropdownfeld werden die zuvor verwendeten Konten aufgeführt.  
  
 **Kontoschlüssel**  
 Geben Sie den Zugriffsschlüssel des Azure-Speicher Kontos an.  
  
 **Sichere Endpunkte (HTTPS) verwenden** – Kontrollkästchen  
 Wählen Sie diese Option aus, um eine sichere Verbindung mit Azure Storage herzustellen: empfohlen.  
  
 **Kontoschlüssel speichern** – Kontrollkästchen  
 Aktivieren Sie dieses Kontrollkästchen, wenn SQL Server den Zugriffsschlüssel für dieses Speicherkonto speichern soll.  
  
### <a name="sql-credential"></a>SQL-Anmeldeinformationen  
 **Auswählen vorhandener Anmeldeinformationen**  
 Wählen Sie ein vorhandenes Objekt mit passenden SQL-Anmeldeinformationen für den Kontonamen und den Zugriffsschlüssel aus.  
  
 **Erstellen von neuen Anmeldeinformationen**  
 Wählen Sie diese Option aus, um neue Anmeldeinformationen auf Basis des Speicherkontos und des Kontoschlüssels zu erstellen. Geben Sie den Namen der neuen Anmeldeinformationen im **Anmeldeinformationsname** -Feld an.  
  
  
