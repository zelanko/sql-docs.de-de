---
title: MSSQLSERVER_17887 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17887 (Database Engine error)
ms.assetid: ad0806e6-3296-4c32-b103-fccf0f8a8d3d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b889779da7f48ffd52d55c63e2ddb0742c065e59
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/21/2020
ms.locfileid: "86553505"
---
# <a name="mssqlserver_17887"></a>MSSQLSERVER_17887
    
## <a name="details"></a>Details  
  
|attribute|Wert|  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|17887|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|SRV_IO_COMP_LISTENER_NONYIELDING|  
|Meldungstext|E/A-Abschlussüberwachung (0x%lx) Arbeitsthread 0x%p stellt im Knoten %ld kein Ergebnis bereit. Ungefähre CPU-Belegung: Kernel %I64d Millisek., Benutzer %I64d Millisek., Intervall: %I64d.|  
  
## <a name="explanation"></a>Erklärung  
 Kennzeichnet ein mögliches Problem mit der E/A-Abschlussportüberwachung an dem spezifischen Knoten, wenn die E/A-Abschlussroutine für ein Netzwerk-Lese-/Schreibereignis ausgeführt wird. Dieser Fehler wird behoben, wenn die E/A-Abschlussportüberwachung nach der Ausführung der E/A-Abschlussroutine zurückgegeben wird.  
  
## <a name="user-action"></a>Benutzeraktion  
 Wenden Sie sich an den Microsoft-Kundendienst (Customer Support Services, CSS).  
  
  
