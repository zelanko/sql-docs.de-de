---
title: Clientprotokolle - TCP- und IP-Eigenschaften (Registerkarte Protokoll) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- TCP/IP [SQL Server], client protocols
- client protocols [SQL Server]
ms.assetid: d04f1bce-069c-4a02-b561-c87c3282be36
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: ec3c433c1ce16e35f064910083e7ab9959e4c3bb
ms.sourcegitcommit: ca9b5cb6bccfdba4cdbe1697adf5c673b4713d6c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/18/2019
ms.locfileid: "56407570"
---
# <a name="client-protocols---tcp-and-ip-properties-protocol-tab"></a>Clientprotokolle – TCP- und IP-Eigenschaften (Registerkarte „Protokoll“)
  Verwenden Sie im Konfigurations-Manager von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im Dialogfeld **Eigenschaften von TCP/IP** die Registerkarte **Protokoll** , um die folgenden Optionen anzuzeigen oder anzugeben. Zum Herstellen einer Verbindung mit einem anderen Port geben Sie die Portnummer im Dialogfeld **Standardport** ein. Weitere Informationen zu Verbindungszeichenfolgen finden Sie unter [Erstellen einer gültigen Verbindungszeichenfolge mithilfe von TCP/IP](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md).  
  
## <a name="options"></a>Optionen  
 **Standardport**  
 Gibt den Standardport an, der von der TCP/IP-Netzwerkbibliothek zum Herstellen einer Verbindung mit der Zielinstanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verwendet wird. Der Standardport ist 1433.  
  
 Beim Verbinden mit einer Standardinstanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)]verwendet der Client diesen Wert. Wenn die Standardinstanz zur Überwachung eines anderen Ports konfiguriert wurde, ändern Sie diesen Wert in diese Portnummer.  
  
 Beim Herstellen einer Verbindung mit einer benannten Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)]versucht der Client, die Portnummer vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browser-Dienst zu erhalten, der auf dem Servercomputer ausgeführt wird. Wenn der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browser-Dienst nicht ausgeführt wird, muss die Portnummer über diese Einstellung oder in der Verbindungszeichenfolge angegeben werden.  
  
 **Enabled**  
 Mögliche Werte sind **Yes** und **No**.  
  
 **Keep Alive**  
 Dieser Parameter steuert, wie oft (in Millisekunden) TCP durch das Senden eines **KEEPALIVE** -Pakets zu überprüfen versucht, ob eine Verbindung im Leerlauf noch reagiert. Der Standardwert beträgt 30000 Millisekunden.  
  
 **Erhaltungsintervall**  
 Dieser Parameter bestimmt das Intervall (in Millisekunden), das **KEEPALIVE** -Pakete voneinander trennt, bis eine Antwort erhalten wird. Der Standardwert beträgt 1.000 Millisekunden.  
  
## <a name="see-also"></a>Siehe auch  
 [Auswählen eines Netzwerkprotokolls](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)   
 [Neuer Alias &#40;Registerkarte „Alias“&#41;](../../../2014/tools/configuration-manager/new-alias-alias-tab.md)   
 [&#60;Alias&#62;-Eigenschaften &#40;Registerkarte „Alias“&#41;](../../../2014/tools/configuration-manager/alias-properties-alias-tab.md)  
  
  
