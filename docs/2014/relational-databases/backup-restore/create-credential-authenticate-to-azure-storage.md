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
ms.openlocfilehash: 5f76a455637e28c06e967b0609cea19a874d7967
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84958590"
---
# <a name="create-credential---authenticate-to-azure-storage"></a>Erstellen von Anmeldeinformationen – Authentifizieren beim Azure-Speicher
  Im Dialogfeld **URL-Sicherung > Anmeldeinformationen erstellen** können Sie neue SQL-Anmeldeinformationen erstellen.  
  
 Wenn Sie die Anmeldeinformationen mithilfe dieses Dialogfelds erstellen, müssen Sie ein Azure-Verwaltungszertifikat bereitstellen, das dem lokalen Zertifikatspeicher hinzugefügt wurde, oder ein Veröffentlichungsprofil angeben, das auf den Computer heruntergeladen wurde, um das Abonnement und die Speicherkontoinformationen zu überprüfen.  
  
 **SQL-Anmeldeinformationen**  
 Geben Sie den Namen für die SQL-Anmeldeinformationen an, die Sie erstellen möchten.  
  
## <a name="azure-credentials"></a>Azure-Anmeldeinformationen  
 **Verwaltungszertifikat**  
 Mit dieser Option geben Sie ein Zertifikat aus dem lokalen Zertifikatspeicher an, das mit dem Verwaltungszertifikat von Azure übereinstimmt. Weitere Informationen zu Azure-Verwaltungszertifikaten finden Sie unter [Erstellen und Hochladen eines Verwaltungszertifikats für Azure](https://go.microsoft.com/fwlink/?LinkId=320781).  
  
 **Abonnement**  
 Wählen Sie die zugehörige Azure-Abonnement-ID für das Verwaltungszertifikat aus dem lokalen Zertifikatspeicher, oder geben bzw. fügen Sie sie ein.  
  
 **Veröffentlichungsprofil**  
 Verwenden Sie diese Option, wenn ein Veröffentlichungsprofil auf Ihren Computer heruntergeladen wurde. Bei dieser Option werden die Abonnement-ID und das Zertifikat automatisch aufgefüllt.  
  
> [!CAUTION]  
>  SQL Server unterstützt derzeit die Version 2.0 des Veröffentlichungsprofils. Weitere Informationen zum Herunterladen der unterstützten Version des Veröffentlichungsprofils finden Sie unter [Herunterladen des Veröffentlichungsprofils 2.0](https://go.microsoft.com/fwlink/?LinkId=396421).  
  
## <a name="storage-account"></a>Speicherkonto  
 Geben Sie den Namen des Speicherkontos an, in dem die Sicherungsdateien gespeichert werden sollen.  
  
  
