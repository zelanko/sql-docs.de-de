---
title: TCP/IP-Eigenschaften (Registerkarte Protokoll)
ms.custom: seo-lt-2019
ms.date: 08/24/2016
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- TCP/IP [SQL Server], configuration options
ms.assetid: 007638fc-3a24-4460-adbe-545ded5d6f88
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 32054dfc368a358370abe4b3a5213305fe815afb
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "75307586"
---
# <a name="tcpip-properties-protocols-tab"></a>TCP/IP-Eigenschaften (Registerkarte Protokoll)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  Verwenden Sie das Dialogfeld **TCP/IP-Eigenschaften** zum Konfigurieren der Optionen für das TCP/IP-Protokoll. Klicken Sie im linken Bereich auf **TCP/IP** , um die einzelnen IP-Adresskonfigurationen im Detailbereich anzuzeigen.  
  
 Microsoft SQL Server muss neu gestartet werden, damit die Änderungen in Kraft treten.  
  
## <a name="options"></a>Tastatur  
 **Aktiviert**  
 Mögliche Werte sind **Yes** und **No**.  
  
 **Keep Alive**  
 Geben Sie das Intervall (in Millisekunden) an, in dem Erhaltungspakete übertragen werden, die die Verfügbarkeit des Computers an der Remoteseite der Verbindung sicherstellen.  
  
 **Listen All**  
 Specify whether SQL Server will listen on all the IP addresses that are bound to network cards on the computer. Wenn für diese Option **Nein**festgelegt ist, müssen Sie jede IP-Adresse einzeln mithilfe des Dialogfeldes „Eigenschaften“ für jede IP-Adresse konfigurieren. Wenn für diese Option **Ja**festgelegt ist, gelten die Einstellungen des Eigenschaftenfeldes **IPAll** für alle IP-Adressen. Der Standardwert ist **Ja**.  
  
 **No Delay**  
 SQL Server implementiert keine Änderungen an dieser Eigenschaft.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Auswählen eines Netzwerkprotokolls](https://msdn.microsoft.com/library/ms187892(v=sql.130).aspx)   
 [Erstellen einer gültigen Verbindungszeichenfolge mithilfe von TCP/IP](creating-a-valid-connection-string-using-tcp-ip.md)  
  
  
