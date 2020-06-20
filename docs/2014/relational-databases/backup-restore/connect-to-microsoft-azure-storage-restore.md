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
ms.openlocfilehash: 9fb4a8943c237e37ca612bf367abe99d47c8eb08
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84958785"
---
# <a name="connect-to-azure-storage-restore"></a>Verbinden mit Azure Storage (Wiederherstellen)
  Über das Dialogfeld können Sie die Verbindung zum Azure-Speicherkonto angeben, um den Dateispeicher im Azure-Speicherkonto abzurufen. Nachdem Sie die erforderlichen Informationen angegeben haben, klicken Sie auf **Verbinden**, um die Verbindung zum Azure-Speicher herzustellen.  
  
## <a name="azure-storage-account"></a>Azure Storage-Konto  
 **Speicherkonto**  
 Geben Sie den Namen des Azure-Speicherkontos an, das Sie verwenden möchten. Im Dropdownfeld werden die zuvor verwendeten Konten aufgeführt.  
  
 **Kontoschlüssel**  
 Geben Sie den Zugriffsschlüssel für das Azure-Speicherkonto an.  
  
 **Sichere Endpunkte (HTTPS) verwenden** – Kontrollkästchen  
 Wählen Sie diese Option, um eine sichere Verbindung zu Azure Storage herzustellen (empfohlen).  
  
 **Kontoschlüssel speichern** – Kontrollkästchen  
 Aktivieren Sie dieses Kontrollkästchen, wenn SQL Server den Zugriffsschlüssel für dieses Speicherkonto speichern soll.  
  
### <a name="sql-credential"></a>SQL-Anmeldeinformationen  
 **Auswählen vorhandener Anmeldeinformationen**  
 Wählen Sie ein vorhandenes Objekt mit passenden SQL-Anmeldeinformationen für den Kontonamen und den Zugriffsschlüssel aus.  
  
 **Erstellen von neuen Anmeldeinformationen**  
 Wählen Sie diese Option aus, um neue Anmeldeinformationen auf Basis des Speicherkontos und des Kontoschlüssels zu erstellen. Geben Sie den Namen der neuen Anmeldeinformationen im **Anmeldeinformationsname** -Feld an.  
  
  
