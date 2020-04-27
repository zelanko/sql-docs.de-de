---
title: SQL Server Native Client-Konfigurationseigenschaften (Registerkarte „Flags“) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 59af121d-c8b9-4faa-91a1-b664f2c9b441
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9bf95081d3c4657dd147e06ae54d413dd96c4c18
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63028298"
---
# <a name="sql-server-native-client-configuration-properties-flags-tab"></a>SQL Server Native Client-Konfigurationseigenschaften (Registerkarte Flags)
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Clients auf diesem Computer kommunizieren mithilfe der Protokolle der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-Bibliotheksdatei mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Servern. Mithilfe dieser Seite wird der Clientcomputer so konfiguriert, dass die Anforderung einer verschlüsselten Verbindung mit Secure Sockets Layer (SSL) möglich ist. Wenn keine verschlüsselte Verbindung hergestellt werden kann, führt dies zu einem Verbindungsfehler.  
  
 Der Anmeldeprozess ist immer verschlüsselt. Die unten genannten Optionen gelten nur für verschlüsselte Daten. Weitere Informationen zur Verschlüsselungsart der Kommunikation von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und zu Konfigurationsanweisungen für den Client, damit dieser die Stammzertifizierungsstelle des Serverzertifikats als vertrauenswürdig einstuft, finden Sie unter „Verschlüsseln von Verbindungen zu [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]“ und „Gewusst wie: Aktivieren von Verschlüsselungsverbindungen für [!INCLUDE[ssDE](../../includes/ssde-md.md)] ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager)“ in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Onlinedokumentation.  
  
## <a name="options"></a>Tastatur  
 **ForceEncryption**  
 Fordern Sie eine Verbindung über SSL an.  
  
 **TrustServerCertificate**  
 Wenn diese Option auf **Nein**festgelegt ist, versucht der Clientprozess, das Serverzertifikat zu überprüfen. Client und Server müssen jeweils über ein Zertifikat von einer öffentlichen Zertifizierungsstelle verfügen. Wenn dieses Zertifikat auf dem Clientcomputer nicht vorhanden ist oder bei der Überprüfung des Zertifikats ein Fehler erzeugt wird, wird die Verbindung beendet.  
  
 Wenn diese Option auf **Ja**festgelegt ist, überprüft der Client das Serverzertifikat nicht. Dadurch wird die Verwendung eines selbstsignierten Zertifikats ermöglicht.  
  
 Das**TrustServerCertificate** -Flag ist nur verfügbar, wenn das **ForceEncryption** -Flag auf **Ja**festgelegt ist.  
  
  
