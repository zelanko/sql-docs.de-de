---
title: Analysis Services-Netzwerkeigenschaften | Microsoft-Dokumentation
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3b9bb77c5139b299a25fbd75bc30a58790ee0c30
ms.sourcegitcommit: 8a64c59c5d84150659a015e54f8937673cab87a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/08/2018
ms.locfileid: "53072357"
---
# <a name="network-properties"></a>Netzwerkeigenschaften
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] unterstützt die in den folgenden Tabellen aufgeführten Servereigenschaften. Weitere Informationen zu zusätzlichen Servereigenschaften und zum Festlegen dieser Eigenschaften finden Sie unter [Servereigenschaften in Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md).  
  
 **Gilt für:** Mehrdimensionaler und tabellarischer Servermodus  
  
## <a name="general"></a>Allgemein  
 **ListenOnlyOnLocalConnections**  
 Eine boolesche Eigenschaft, die anzeigt, ob nur lokale Verbindungen, z. B. localhost, überwacht werden sollen.  
  
## <a name="listener"></a>Listener  
 **IPV4Support**  
 Eine ganze 32-Bit-Zahl mit Vorzeichen, die die Unterstützung für das IPv4-Protokoll definiert. Diese Eigenschaft hat einen der in der folgenden Tabelle aufgeführten Werte:  
  
|Wert|Description|  
|-----------|-----------------|  
|*0*|IPv4 ist deaktiviert; Clients können keine Verbindung herstellen.|  
|*1*|(Standard) IPv4 ist erforderlich; Server startet nicht, wenn eine Überwachung von IPv4 nicht möglich ist.|  
|*2*|IPv4 ist optional; Server versucht, IPv4 zu überwachen, startet aber auch, wenn dies nicht möglich ist.|  
  
 **IPV6Support**  
 Eine ganze 32-Bit-Zahl mit Vorzeichen, die die Unterstützung für das IPv6-Protokoll definiert. Diese Eigenschaft hat einen der in der folgenden Tabelle aufgeführten Werte:  
  
|Wert|Description|  
|-----------|-----------------|  
|*0*|IPv6 ist deaktiviert; Clients können keine Verbindung herstellen.|  
|*1*|(Standard) IPv6 ist erforderlich; Server startet nicht, wenn eine Überwachung von IPv6 nicht möglich ist.|  
|*2*|IPv6 ist optional; Server versucht, IPv6 zu überwachen, startet aber auch, wenn dies nicht möglich ist.|  
  
 **MaxAllowedRequestSize**  
 Eine erweiterte Eigenschaft, die nur mithilfe der Schritte in [!INCLUDE[msCoName](../../includes/msconame-md.md)] geändert werden sollte.  
  
 **RequestSizeThreshold**  
 Eine erweiterte Eigenschaft, die nur mithilfe der Schritte in [!INCLUDE[msCoName](../../includes/msconame-md.md)] geändert werden sollte.  
  
 **ServerReceiveTimeout**  
 Eine erweiterte Eigenschaft, die nur mithilfe der Schritte in [!INCLUDE[msCoName](../../includes/msconame-md.md)] geändert werden sollte.  
  
 **ServerSendTimeout**  
 Eine erweiterte Eigenschaft, die nur mithilfe der Schritte in [!INCLUDE[msCoName](../../includes/msconame-md.md)] geändert werden sollte.  
  
## <a name="requests"></a>Anforderungen  
 **EnableBinaryXML**  
 Eine boolesche Eigenschaft, die angibt, ob der Server Anforderungen im Format Binary XML erkennt.  
  
 **EnableCompression**  
 Eine boolesche Eigenschaft, die angibt, ob für Anforderungen die Komprimierung aktiviert ist.  
  
## <a name="responses"></a>Antworten  
 **CompressionLevel**  
 Eine erweiterte Eigenschaft, die nur mithilfe der Schritte in [!INCLUDE[msCoName](../../includes/msconame-md.md)] geändert werden sollte.  
  
 **EnableBinaryXML**  
 Eine boolesche Eigenschaft, die angibt, ob der Server für Antworten im Format Binary XML aktiviert ist.  
  
 **EnableCompression**  
 Eine boolesche Eigenschaft, die angibt, ob für Antworten auf Clientanforderungen die Komprimierung aktiviert ist.  
  
## <a name="tcp"></a>TCP  
 **InitialConnectTimeout**  
 Eine erweiterte Eigenschaft, die nur mithilfe der Schritte in [!INCLUDE[msCoName](../../includes/msconame-md.md)] geändert werden sollte.  
  
 **MaxCompletedReceiveCount**  
 Eine erweiterte Eigenschaft, die nur mithilfe der Schritte in [!INCLUDE[msCoName](../../includes/msconame-md.md)] geändert werden sollte.  
  
 **MaxPendingAcceptExCount**  
 Eine erweiterte Eigenschaft, die nur mithilfe der Schritte in [!INCLUDE[msCoName](../../includes/msconame-md.md)] geändert werden sollte.  
  
 **MaxPendingReceiveCount**  
 Eine erweiterte Eigenschaft, die nur mithilfe der Schritte in [!INCLUDE[msCoName](../../includes/msconame-md.md)] geändert werden sollte.  
  
 **MaxPendingSendCount**  
 Eine erweiterte Eigenschaft, die nur mithilfe der Schritte in [!INCLUDE[msCoName](../../includes/msconame-md.md)] geändert werden sollte.  
  
 **MinPendingAcceptExCount**  
 Eine erweiterte Eigenschaft, die nur mithilfe der Schritte in [!INCLUDE[msCoName](../../includes/msconame-md.md)] geändert werden sollte.  
  
 **MinPendingReceiveCount**  
 Eine erweiterte Eigenschaft, die nur mithilfe der Schritte in [!INCLUDE[msCoName](../../includes/msconame-md.md)] geändert werden sollte.  
  
 **ScatterReceiveMultiplier**  
 Eine erweiterte Eigenschaft, die nur mithilfe der Schritte in [!INCLUDE[msCoName](../../includes/msconame-md.md)] geändert werden sollte.  
  
 **SocketOptions\ DisableNonblockingMode**  
 Eine erweiterte Eigenschaft, die nur mithilfe der Schritte in [!INCLUDE[msCoName](../../includes/msconame-md.md)] geändert werden sollte.  
  
 **SocketOptions\ EnableLingerOnClose**  
 Eine erweiterte Eigenschaft, die nur mithilfe der Schritte in [!INCLUDE[msCoName](../../includes/msconame-md.md)] geändert werden sollte.  
  
 **SocketOptions\EnableNagleAlgorithm**  
 Eine erweiterte Eigenschaft, die nur mithilfe der Schritte in [!INCLUDE[msCoName](../../includes/msconame-md.md)] geändert werden sollte.  
  
 **SocketOptions\ LingerTimeout**  
 Eine erweiterte Eigenschaft, die nur mithilfe der Schritte in [!INCLUDE[msCoName](../../includes/msconame-md.md)] geändert werden sollte.  
  
 **SocketOptions\ ReceiveBufferSize**  
 Eine erweiterte Eigenschaft, die nur mithilfe der Schritte in [!INCLUDE[msCoName](../../includes/msconame-md.md)] geändert werden sollte.  
  
 **SocketOptions\ SendBufferSize**  
 Eine erweiterte Eigenschaft, die nur mithilfe der Schritte in [!INCLUDE[msCoName](../../includes/msconame-md.md)] geändert werden sollte.  
  
## <a name="see-also"></a>Siehe auch  
 [Servereigenschaften in Analysis Services](../../analysis-services/server-properties/server-properties-in-analysis-services.md)   
 [Bestimmen des Servermodus einer Analysis Services-Instanz](../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
