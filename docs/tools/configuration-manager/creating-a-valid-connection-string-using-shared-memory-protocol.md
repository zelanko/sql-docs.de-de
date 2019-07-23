---
title: Erstellen einer gültigen Verbindungszeichenfolge mithilfe des Shared Memory-Protokolls | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- connection strings [Database Engine], shared memory
- aliases [SQL Server], shared memory
ms.assetid: 5fff42e8-377f-4b40-b0c8-b02393f8a1af
author: markingmyname
ms.author: maghan
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: a3d1e40e1909b7ab3129f63fc89c8bc20f4873b3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68010168"
---
# <a name="creating-a-valid-connection-string-using-shared-memory-protocol"></a>Erstellen einer gültigen Verbindungszeichenfolge mithilfe des Shared Memory-Protokolls
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  Verbindungen mit [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von einem Client auf dem gleichen Computer verwenden das Shared Memory-Protokoll. Shared Memory verfügt über keine konfigurierbaren Eigenschaften. Es wird immer zuerst versucht, Shared Memory zu verwenden; es ist nicht möglich, dieses Protokoll von der obersten Position der Liste **Aktivierte Protokolle** in der Liste **Eigenschaften der Clientprotokolle** zu verschieben. Das Shared Memory-Protokoll kann deaktiviert werden, was insbesondere bei der Problembehandlung eines der anderen Protokolle nützlich ist.  
  
 Sie können keinen Alias mithilfe des Shared Memory-Protokolls erstellen. Allerdings wird bei aktiviertem Shared Memory über den namentlichen Verbindungsaufbau zu [!INCLUDE[ssDE](../../includes/ssde-md.md)] eine Shared Memory-Verbindung hergestellt. Für Shared Memory-Verbindungszeichenfolgen wird das Format `lpc:<servername>[\instancename]`verwendet.  
  
## <a name="connecting-to-the-local-server"></a>Herstellen einer Verbindung mit dem lokalen Server  
 Beim Herstellen einer Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , das auf dem gleichen Computer wie der Client ausgeführt wird, können Sie **(local)** als Servernamen verwenden. Aus Gründen der Mehrdeutigkeit wird dies nicht empfohlen, kann aber nützlich sein, wenn vom Client bekannt ist, dass er auf dem vorgesehenen Computer ausgeführt wird. Beim Erstellen einer Anwendung für mobile Benutzer mit getrennter Verbindung (beispielsweise für Verkaufspersonal, wobei [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf Laptops ausgeführt und zum Speichern von Projektdaten verwendet wird) würde beispielsweise die Verbindung eines Clients zu **(local)** immer zu dem auf dem Laptop ausgeführten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] hergestellt. Anstelle von **(local)** kann das Wort**localhost**oder ein Punkt ( **.** ) verwendet werden.  
  
## <a name="verifying-your-connection-protocol"></a>Überprüfen Ihres Verbindungsprotokolls  
 Von der folgenden Abfrage wird das Protokoll zurückgegeben, das für die aktuelle Verbindung verwendet wird.  
  
```  
SELECT net_transport   
FROM sys.dm_exec_connections   
WHERE session_id = @@SPID;  
  
```  
  
## <a name="examples"></a>Beispiele:  
 Die folgenden Namen werden mit dem lokalen Computer mithilfe des Shared Memory-Protokolls verbunden, falls dieses aktiviert ist:  
  
 `<servername>`  
  
 `<servername>\<instancename>`  
  
 `(local)`  
  
 `localhost`  
  
 Sie können keinen Alias für eine Shared Memory-Verbindung erstellen.  
  
> [!NOTE]  
>  Die Angabe einer IP-Adresse im Feld **Server** führt zu einer TCP/IP-Verbindung.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen einer gültigen Verbindungszeichenfolge mithilfe von TCP/IP](../../tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md)   
 [Erstellen einer gültigen Verbindungszeichenfolge mithilfe von Named Pipes](https://msdn.microsoft.com/library/90930ff2-143b-4651-8ae3-297103600e4f)   
 [Auswählen eines Netzwerkprotokolls](https://msdn.microsoft.com/library/6565fb7d-b076-4447-be90-e10d0dec359a)  
  
  
