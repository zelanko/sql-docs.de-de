---
title: Herstellen einer Verbindung mit einem Microsoft Azure-Abonnement | Microsoft Dokumentation
description: Registrieren Sie einen Azure-Blobcontainer bei Ihrer SQL Server-Instanz, die eine Shared Access Signature, eine gespeicherte Zugriffsrichtlinie und SQL Server-Anmeldeinformationen erstellt.
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: cca5a270-643f-4677-8802-98464f19f82a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a017eb6d2f9267408387413782a83488fa39d542
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85748451"
---
# <a name="connect-to-a-microsoft-azure-subscription"></a>Herstellen einer Verbindung mit einem Microsoft Azure-Abonnement
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
Verwenden Sie **Mit einem Microsoft-Abonnement verbinden** , um einen vorhandenen Azure-Blobcontainer bei Ihrer Instanz von SQL Server zu registrieren.  Das Dialogfeld erstellt eine SAS und die gespeicherte Zugriffsrichtlinie für einen Azure-Blobcontainer und dann SQL Server-Anmeldeinformationen.  Dieses Dialogfeld wird angezeigt, wenn die Sicherungs- oder Wiederherstellungsaufgabe von SQL Server Management Studio verwendet wird, und der Vorgang ein URL-Medium einbezieht.

## <a name="limitation"></a>Einschränkung
**Mit einem Microsoft-Abonnement verbinden** funktioniert nur mit einem Azure Storage-Konto, das über das Dienstverwaltungs-Bereitstellungsmodell (klassisch) erstellt wurde.  Weitere Informationen zu Azure-Bereitstellungsmodellen finden Sie unter [Azure Resource Manager-Bereitstellung im Vergleich zur klassischen Bereitstellung: Grundlegendes zu Bereitstellungsmodellen und zum Status von Ressourcen](https://azure.microsoft.com/documentation/articles/resource-manager-deployment-model/).

## <a name="options"></a>Tastatur
**Anmelden**     
Melden Sie sich mit dem entsprechenden Azure-Konto an.

**Zu verwendendes Abonnement auswählen**      
Wählen Sie das gewünschte Abonnement aus der Dropdownliste.

**Speicherkonto auswählen**  
Wählen Sie aus der Dropdownliste das gewünschte Speicherkonto aus.

**Blobcontainer auswählen**   
Wählen Sie den gewünschten Blobcontainer aus der Dropdownliste.

**Ablauf der Richtlinie für den gemeinsamen Zugriff**   
Die SAS-Richtlinie läuft an diesem Datum ab.  Die Standardgültigkeitsdauer beträgt ein Jahr ab der Erstellung.  Ändern Sie es nach Bedarf.

**Generierte Shared Access Signature**   
Das Rich-Text-Feld zeigt die generierte SAS an.

**Anmeldeinformationen erstellen**   
Über diese Schaltfläche wird eine gespeicherte Zugriffsrichtlinie sowie eine SAS generiert, und dann werden SQL Server-Anmeldeinformationen erstellt.
