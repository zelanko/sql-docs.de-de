---
title: TCP - IP-Eigenschaften (Registerkarte Protokoll) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- TCP/IP [SQL Server], configuration options
ms.assetid: 007638fc-3a24-4460-adbe-545ded5d6f88
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b545fbe28e28739b5f66a7beca1ab7c0450ae08a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63150455"
---
# <a name="tcp---ip-properties-protocols-tab"></a>TCP - IP-Eigenschaften (Registerkarte Protokoll)
  Verwenden Sie das Dialogfeld **TCP/IP-Eigenschaften** zum Konfigurieren der Optionen für das TCP/IP-Protokoll. Klicken Sie im linken Bereich auf **TCP/IP**, um die einzelnen IP-Adresskonfigurationen im Detailbereich anzuzeigen.  
  
 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] muss neu gestartet werden, damit die Änderungen in Kraft treten.  
  
## <a name="options"></a>Optionen  
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
  
  
