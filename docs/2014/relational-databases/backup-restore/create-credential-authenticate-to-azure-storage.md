---
title: Erstellen von Anmeldeinformationen – Authentifizieren beim Azure-Speicher | Microsoft Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.backuptourl.createcred.f1
ms.assetid: 0622619d-27c5-4ff0-83e5-cde31648c27a
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 6de7b5c8f9cdc7162eb9c6a8ddd214d0486255c6
ms.sourcegitcommit: 3b1f873f02af8f4e89facc7b25f8993f535061c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2019
ms.locfileid: "70175953"
---
# <a name="create-credential---authenticate-to-azure-storage"></a>Erstellen von Anmeldeinformationen – Authentifizieren beim Azure-Speicher
  Im Dialogfeld **URL-Sicherung > Anmeldeinformationen erstellen** können Sie neue SQL-Anmeldeinformationen erstellen.  
  
 Wenn Sie dieses Dialogfeld verwenden, um Anmelde Informationen zu erstellen, müssen Sie ein Azure-Verwaltungs Zertifikat bereitstellen, das dem lokalen Zertifikat Speicher hinzugefügt wurde, oder ein Veröffentlichungs Profil, das auf Ihren Computer heruntergeladen wird, um das Abonnement und die Speicherkonto Informationen zu  
  
 **SQL-Anmeldeinformationen**  
 Geben Sie den Namen für die SQL-Anmeldeinformationen an, die Sie erstellen möchten.  
  
## <a name="azure-credentials"></a>Azure-Anmelde Informationen  
 **Verwaltungszertifikat**  
 Verwenden Sie diese Option, um ein Zertifikat aus dem lokalen Zertifikat Speicher anzugeben, das mit dem Verwaltungs Zertifikat von Azure übereinstimmt. Weitere Informationen zu Azure-Verwaltungs Zertifikaten finden Sie unter [Erstellen und Hochladen eines Verwaltungs Zertifikats für Azure](https://go.microsoft.com/fwlink/?LinkId=320781).  
  
 **Abonnement**  
 Wählen Sie Ihre Azure-Abonnement-ID aus dem lokalen Zertifikat Speicher aus, geben Sie Sie ein, oder fügen Sie Sie ein.  
  
 **Veröffentlichungsprofil**  
 Verwenden Sie diese Option, wenn ein Veröffentlichungsprofil auf Ihren Computer heruntergeladen wurde. Bei dieser Option werden die Abonnement-ID und das Zertifikat automatisch aufgefüllt.  
  
> [!CAUTION]  
>  SQL Server unterstützt derzeit die Version 2.0 des Veröffentlichungsprofils. Weitere Informationen zum Herunterladen der unterstützten Version des Veröffentlichungsprofils finden Sie unter [Herunterladen des Veröffentlichungsprofils 2.0](https://go.microsoft.com/fwlink/?LinkId=396421).  
  
## <a name="storage-account"></a>Speicherkonto  
 Geben Sie den Namen des Speicherkontos an, in dem die Sicherungsdateien gespeichert werden sollen.  
  
  
