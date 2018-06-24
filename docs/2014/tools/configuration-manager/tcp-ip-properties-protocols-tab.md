---
title: TCP - IP-Eigenschaften (Registerkarte "Protokolle") | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- configmgr-client
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- TCP/IP [SQL Server], configuration options
ms.assetid: 007638fc-3a24-4460-adbe-545ded5d6f88
caps.latest.revision: 36
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 57b3bd32574aadbd42b25b626756cc20369d9b8a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36049596"
---
# <a name="tcp---ip-properties-protocols-tab"></a>TCP - IP-Eigenschaften (Registerkarte "Protokolle")
  Verwenden Sie das Dialogfeld **TCP/IP-Eigenschaften** zum Konfigurieren der Optionen für das TCP/IP-Protokoll. Klicken Sie im linken Bereich auf **TCP/IP**, um die einzelnen IP-Adresskonfigurationen im Detailbereich anzuzeigen.  
  
 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] muss neu gestartet werden, damit die Änderungen in Kraft treten.  
  
## <a name="options"></a>Tastatur  
 **Enabled**  
 Mögliche Werte sind **Yes** und **No**.  
  
 **Keep Alive**  
 Geben Sie das Intervall (in Millisekunden) an, in dem Erhaltungspakete übertragen werden, die die Verfügbarkeit des Computers an der Remoteseite der Verbindung sicherstellen.  
  
 **Listen All**  
 Specify whether SQL Server will listen on all the IP addresses that are bound to network cards on the computer. Wenn für diese Option **Nein**festgelegt ist, müssen Sie jede IP-Adresse einzeln mithilfe des Dialogfeldes „Eigenschaften“ für jede IP-Adresse konfigurieren. Wenn für diese Option **Ja**festgelegt ist, gelten die Einstellungen des Eigenschaftenfeldes **IPAll** für alle IP-Adressen. Der Standardwert ist **Ja**.  
  
 **No Delay**  
 Von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] werden keine Änderungen an dieser Eigenschaft implementiert.  
  
## <a name="see-also"></a>Siehe auch  
 [Auswählen eines Netzwerkprotokolls](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)   
 [Erstellen einer gültigen Verbindungszeichenfolge mithilfe von TCP/IP](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md)  
  
  