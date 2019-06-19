---
title: SQL Server-Fehlerprotokolle konfigurieren (Seite Allgemein) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql13.swb.configurelogs.configureerrorlogs.f1
ms.assetid: 03f0d463-9b0b-4af9-a853-da936d75e5af
author: MikeRayMSFT
ms.author: mikeray
manager: jroth
ms.openlocfilehash: b79da9d55f40f20608bf2de48b6df70e12a83911
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66771959"
---
# <a name="scm-services---configure-sql-server-error-logs"></a>SCM-Dienste: Konfigurieren von SQL Server-Fehlerprotokollen
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  In diesem Thema wird beschrieben, wie Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Fehlerprotokolle anzeigen oder deren Wiederverwendung ändern.  
  
## <a name="to-open-the-configure-sql-server-error-logs-dialog-box"></a>So öffnen Sie das Dialogfeld SQL Server-Fehlerprotokolle konfigurieren  
  
1.  Erweitern Sie im Objekt-Explorer die SQL Server-Instanz und anschließend **Verwaltung**. Klicken Sie anschließend mit der rechten Maustaste auf **Server-Protokolle**, und klicken Sie anschließend auf **Konfigurieren**.  
  
2.  Wählen Sie im Dialogfeld **SQL Server-Fehlerprotokolle konfigurieren** zwischen den folgenden Optionen aus.  
  
     **Beschränken Sie die Anzahl der Fehlerprotokolldateien vor der Wiederverwendung**  
     Überprüft die Anzahl der bereits erstellten Fehlerprotokolle, bevor diese wiederverwendet werden. Bei jedem Start einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird ein neues Fehlerprotokoll erstellt. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] behält Sicherungen der vorherigen sechs Protokolle bei, außer wenn Sie diese Option aktivieren und eine andere maximale Anzahl von Fehlerprotokolldateien angeben.  
  
     **Maximale Anzahl von Fehlerprotokolldateien**  
     Gibt die maximale Anzahl der erstellten Fehlerprotokolldateien vor der Wiederverwendung an. Der Standardwert ist 6. Dies entspricht der Anzahl der vorhergehenden Sicherungsprotokolle, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vor der Wiederverwendung beibehält.  
  
  
