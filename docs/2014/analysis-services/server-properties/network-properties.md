---
title: Netzwerk Eigenschaften | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- LingerTimeout property
- EnableNagleAlgorithm property
- MinPendingAcceptExCount property
- MaxPendingSendCount property
- EnableBinaryXML property
- MinPendingReceiveCount property
- MaxCompletedReceiveCount property
- DisableNonblockingMode property
- RequestSizeThreshold property
- CompressionLevel property
- ReceiveBufferSize property
- EnableCompression property
- ServerSendTimeout property
- IPV4Support property
- MaxPendingReceiveCount property
- MaxPendingAcceptExCount property
- IPV6Support property
- MaxAllowedRequestSize property
- ServerReceiveTimeout property
- EnableLingerOnClose property
- InitialConnectTimeout property
- SendBufferSize property
- ScatterReceiveMultiplier property
- network properties [Analysis Services]
ms.assetid: ef4251e2-abe5-4c5b-9868-7549782d0244
author: minewiskan
ms.author: owend
ms.openlocfilehash: 31f648e31c736d502f84df71d080551db2bc495f
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84940632"
---
# <a name="network-properties"></a>Netzwerkeigenschaften
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] unterstützt die in den folgenden Tabellen aufgeführten Servereigenschaften. Weitere Informationen zu zusätzlichen Servereigenschaften und zum Festlegen dieser Eigenschaften finden Sie unter [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md).  
  
 **Gilt für:** mehrdimensionalen und Tabellenservermodus  
  
## <a name="general"></a>Allgemein  
 `ListenOnlyOnLocalConnections`  
 Eine boolesche Eigenschaft, die anzeigt, ob nur lokale Verbindungen, z. B. localhost, überwacht werden sollen.  
  
## <a name="listener"></a>Listener  
 `IPV4Support`  
 Eine ganze 32-Bit-Zahl mit Vorzeichen, die die Unterstützung für das IPv4-Protokoll definiert. Diese Eigenschaft hat einen der in der folgenden Tabelle aufgeführten Werte:  
  
|Value|BESCHREIBUNG|  
|-----------|-----------------|  
|*0*|IPv4 ist deaktiviert; Clients können keine Verbindung herstellen.|  
|*1*|(Standard) IPv4 ist erforderlich; Server startet nicht, wenn eine Überwachung von IPv4 nicht möglich ist.|  
|*2*|IPv4 ist optional; Server versucht, IPv4 zu überwachen, startet aber auch, wenn dies nicht möglich ist.|  
  
 `IPV6Support`  
 Eine ganze 32-Bit-Zahl mit Vorzeichen, die die Unterstützung für das IPv6-Protokoll definiert. Diese Eigenschaft hat einen der in der folgenden Tabelle aufgeführten Werte:  
  
|Value|BESCHREIBUNG|  
|-----------|-----------------|  
|*0*|IPv6 ist deaktiviert; Clients können keine Verbindung herstellen.|  
|*1*|(Standard) IPv6 ist erforderlich; Server startet nicht, wenn eine Überwachung von IPv6 nicht möglich ist.|  
|*2*|IPv6 ist optional; Server versucht, IPv6 zu überwachen, startet aber auch, wenn dies nicht möglich ist.|  
  
 `MaxAllowedRequestSize`  
 Eine erweiterte Eigenschaft, die nur mithilfe der Schritte in [!INCLUDE[msCoName](../../includes/msconame-md.md)] geändert werden sollte.  
  
 `RequestSizeThreshold`  
 Eine erweiterte Eigenschaft, die nur mithilfe der Schritte in [!INCLUDE[msCoName](../../includes/msconame-md.md)] geändert werden sollte.  
  
 `ServerReceiveTimeout`  
 Eine erweiterte Eigenschaft, die nur mithilfe der Schritte in [!INCLUDE[msCoName](../../includes/msconame-md.md)] geändert werden sollte.  
  
 `ServerSendTimeout`  
 Eine erweiterte Eigenschaft, die nur mithilfe der Schritte in [!INCLUDE[msCoName](../../includes/msconame-md.md)] geändert werden sollte.  
  
## <a name="requests"></a>Requests  
 `EnableBinaryXML`  
 Eine boolesche Eigenschaft, die angibt, ob der Server Anforderungen im Format Binary XML erkennt.  
  
 `EnableCompression`  
 Eine boolesche Eigenschaft, die angibt, ob für Anforderungen die Komprimierung aktiviert ist.  
  
## <a name="responses"></a>Antworten  
 `CompressionLevel`  
 Eine erweiterte Eigenschaft, die nur mithilfe der Schritte in [!INCLUDE[msCoName](../../includes/msconame-md.md)] geändert werden sollte.  
  
 `EnableBinaryXML`  
 Eine boolesche Eigenschaft, die angibt, ob der Server für Antworten im Format Binary XML aktiviert ist.  
  
 `EnableCompression`  
 Eine boolesche Eigenschaft, die angibt, ob für Antworten auf Clientanforderungen die Komprimierung aktiviert ist.  
  
## <a name="tcp"></a>TCP  
 `InitialConnectTimeout`  
 Eine erweiterte Eigenschaft, die nur mithilfe der Schritte in [!INCLUDE[msCoName](../../includes/msconame-md.md)] geändert werden sollte.  
  
 `MaxCompletedReceiveCount`  
 Eine erweiterte Eigenschaft, die nur mithilfe der Schritte in [!INCLUDE[msCoName](../../includes/msconame-md.md)] geändert werden sollte.  
  
 `MaxPendingAcceptExCount`  
 Eine erweiterte Eigenschaft, die nur mithilfe der Schritte in [!INCLUDE[msCoName](../../includes/msconame-md.md)] geändert werden sollte.  
  
 `MaxPendingReceiveCount`  
 Eine erweiterte Eigenschaft, die nur mithilfe der Schritte in [!INCLUDE[msCoName](../../includes/msconame-md.md)] geändert werden sollte.  
  
 `MaxPendingSendCount`  
 Eine erweiterte Eigenschaft, die nur mithilfe der Schritte in [!INCLUDE[msCoName](../../includes/msconame-md.md)] geändert werden sollte.  
  
 `MinPendingAcceptExCount`  
 Eine erweiterte Eigenschaft, die nur mithilfe der Schritte in [!INCLUDE[msCoName](../../includes/msconame-md.md)] geändert werden sollte.  
  
 `MinPendingReceiveCount`  
 Eine erweiterte Eigenschaft, die nur mithilfe der Schritte in [!INCLUDE[msCoName](../../includes/msconame-md.md)] geändert werden sollte.  
  
 `ScatterReceiveMultiplier`  
 Eine erweiterte Eigenschaft, die nur mithilfe der Schritte in [!INCLUDE[msCoName](../../includes/msconame-md.md)] geändert werden sollte.  
  
 `SocketOptions\ DisableNonblockingMode`  
 Eine erweiterte Eigenschaft, die nur mithilfe der Schritte in [!INCLUDE[msCoName](../../includes/msconame-md.md)] geändert werden sollte.  
  
 `SocketOptions\ EnableLingerOnClose`  
 Eine erweiterte Eigenschaft, die nur mithilfe der Schritte in [!INCLUDE[msCoName](../../includes/msconame-md.md)] geändert werden sollte.  
  
 `SocketOptions\EnableNagleAlgorithm`  
 Eine erweiterte Eigenschaft, die nur mithilfe der Schritte in [!INCLUDE[msCoName](../../includes/msconame-md.md)] geändert werden sollte.  
  
 `SocketOptions\ LingerTimeout`  
 Eine erweiterte Eigenschaft, die nur mithilfe der Schritte in [!INCLUDE[msCoName](../../includes/msconame-md.md)] geändert werden sollte.  
  
 `SocketOptions\ ReceiveBufferSize`  
 Eine erweiterte Eigenschaft, die nur mithilfe der Schritte in [!INCLUDE[msCoName](../../includes/msconame-md.md)] geändert werden sollte.  
  
 `SocketOptions\ SendBufferSize`  
 Eine erweiterte Eigenschaft, die nur mithilfe der Schritte in [!INCLUDE[msCoName](../../includes/msconame-md.md)] geändert werden sollte.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren von Server Eigenschaften in Analysis Services](server-properties-in-analysis-services.md)   
 [Bestimmen des Servermodus einer Analysis Services-Instanz](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
