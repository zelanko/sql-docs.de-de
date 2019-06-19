---
title: Festlegen von Verschlüsselungsoptionen auf Zielservern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, encryption
- target servers [SQL Server], encryption
- multiserver environments [SQL Server], setting encryption options on target servers
ms.assetid: 1a9fd539-e166-4ea8-9f21-ac400ca74dee
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b27dd81df572e289d182fdaa637a3af972b3d603
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63244975"
---
# <a name="set-encryption-options-on-target-servers"></a>Festlegen von Verschlüsselungsoptionen auf Zielservern
  Wenn Sie für die verschlüsselte SSL-Kommunikation (Secure Sockets Layer) zwischen Masterservern und einigen oder allen Zielservern kein Zertifikat verwenden können, aber den Kanal zwischen diesen verschlüsseln möchten, müssen Sie auf dem Zielserver die erforderliche Sicherheitsstufe konfigurieren.  
  
 Zum Konfigurieren der für einen bestimmten Kommunikationskanal zwischen einem Master- und einem Zielserver erforderlichen geeigneten Sicherheitsstufe legen Sie den Registrierungsunterschlüssel **\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\** \<*instance_name*> **\SQLServerAgent\MsxEncryptChannelOptions(REG_DWORD)** für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent auf dem Zielserver auf einen der folgenden Werte fest. Der Wert von \<*Instanz_Name*> ist **MSSQL.** _n_. Beispiel: **MSSQL.1** oder **MSSQL.3**.  
  
|Wert|Description|  
|-----------|-----------------|  
|**0**|Deaktiviert die Verschlüsselung zwischen diesem Zielserver und dem Masterserver. Wählen Sie diese Option nur aus, wenn der Kanal zwischen Zielserver und Masterserver auf andere Weise gesichert ist.|  
|**1**|Aktiviert nur die Verschlüsselung zwischen diesem Zielserver und dem Masterserver, eine Zertifikatüberprüfung ist jedoch nicht erforderlich.|  
|**2**|Aktiviert die vollständige SSL-Verschlüsselung und Zertifikatüberprüfung zwischen diesem Zielserver und dem Masterserver. Dies ist die Standardeinstellung. Es wird empfohlen, diesen Wert nicht zu ändern, es sei denn, dafür liegen spezifische Gründe vor.|  
  
 Wenn **1** oder **2** angegeben wird, muss SSL sowohl auf dem Master- als auch auf dem Zielserver aktiviert sein. Wenn **2** angegeben wird, muss außerdem auf dem Masterserver ein ordnungsgemäß signiertes Zertifikat vorhanden sein.  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../includes/ssnoteregistry-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Aktivieren von verschlüsselten Verbindungen zur Datenbank-Engine &#40;SQL Server-Konfigurations-Manager&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)  
  
  
