---
title: Mit Microsoft Azure Storage verbinden (Wiederherstellen) | Microsoft Dokumentation
description: In SQL Server können Sie über das Dialogfeld „Azure Storage-Konto“ eine Verbindung zu einem Azure-Speicherkonto angeben, um Dateispeicher in einem Azure-Konto zu erhalten.
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
ms.openlocfilehash: d3a46b4af5ef064c675f16f20278c7f91afc73c8
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85748441"
---
# <a name="connect-to-microsoft-azure-storage-restore"></a>Mit Microsoft Azure Storage verbinden (Wiederherstellen)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
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
  
  
