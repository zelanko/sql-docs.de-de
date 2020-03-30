---
title: MSSQLSERVER_26014 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 26014 (Database Engine error)
ms.assetid: e2b0dfc7-0681-4e5d-8875-1d5f63534086
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 44ddcd07bfe284ea5200e585d49a0f17ba3b4839
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "68002010"
---
# <a name="mssqlserver_26014"></a>MSSQLSERVER_26014
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|26014|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|SNI_SSL_USER_CERT_FAILURE|  
|Meldungstext|Das vom Benutzer angegebene Zertifikat [Cert Hash(sha1) "%hs"] kann nicht geladen werden. Vom Server wird keine Verbindung akzeptiert. Überprüfen Sie, ob das Zertifikat richtig installiert ist. Lesen Sie "Konfigurieren eines Zertifikats zur Verwendung durch SSL" in der Onlinedokumentation.|  
  
## <a name="explanation"></a>Erklärung  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] hat versucht, das in der Meldung genannte Zertifikat zu laden, aber bei dem Vorgang ist ein Fehler aufgetreten. Dieses Problem muss behoben werden, bevor [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dieses Zertifikat verwenden kann.  
  
Zu den möglichen Ursachen für den Fehler zählen die folgenden:  
  
-   Möglicherweise wurde das Zertifikat verschoben oder gelöscht.  
  
-   Falls sich der von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendete Anmeldename geändert hat, verfügt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] möglicherweise nicht über die Berechtigung für den Zugriff auf das Zertifikat.  
  
-   Das Zertifikat ist möglicherweise abgelaufen.  
  
## <a name="user-action"></a>Benutzeraktion  
Stellen Sie sicher, dass das in der Meldung genannte Zertifikat im System vorhanden ist, dass darauf zugegriffen werden kann und dass es für die Verwendung zulässig ist.  
  
