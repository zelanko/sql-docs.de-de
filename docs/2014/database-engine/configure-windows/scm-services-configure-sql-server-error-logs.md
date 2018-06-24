---
title: SQL Server-Fehlerprotokolle konfigurieren (Seite Allgemein) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.configurelogs.configureerrorlogs.f1
ms.assetid: 03f0d463-9b0b-4af9-a853-da936d75e5af
caps.latest.revision: 17
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 0ef024a0697fe8f3b1e4ce5d165343b7d653a3d0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36059428"
---
# <a name="configure-sql-server-error-logs"></a>Konfigurieren von SQL Server-Fehlerprotokollen
  In diesem Thema wird beschrieben, wie Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Fehlerprotokolle anzeigen oder deren Wiederverwendung ändern.  
  
## <a name="to-open-the-configure-sql-server-error-logs-dialog-box"></a>So öffnen Sie das Dialogfeld SQL Server-Fehlerprotokolle konfigurieren  
  
1.  Erweitern Sie im Objekt-Explorer die SQL Server-Instanz und anschließend **Verwaltung**. Klicken Sie anschließend mit der rechten Maustaste auf **Server-Protokolle**, und klicken Sie anschließend auf **Konfigurieren**.  
  
2.  Wählen Sie im Dialogfeld **SQL Server-Fehlerprotokolle konfigurieren** zwischen den folgenden Optionen aus.  
  
     **Beschränken Sie die Anzahl der Fehlerprotokolldateien vor der Wiederverwendung**  
     Überprüft die Anzahl der bereits erstellten Fehlerprotokolle, bevor diese wiederverwendet werden. Bei jedem Start einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird ein neues Fehlerprotokoll erstellt. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] behält Sicherungen der vorherigen sechs Protokolle bei, außer wenn Sie diese Option aktivieren und eine andere maximale Anzahl von Fehlerprotokolldateien angeben.  
  
     **Maximale Anzahl von Fehlerprotokolldateien**  
     Gibt die maximale Anzahl der erstellten Fehlerprotokolldateien vor der Wiederverwendung an. Der Standardwert ist 6. Dies entspricht der Anzahl der vorhergehenden Sicherungsprotokolle, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vor der Wiederverwendung beibehält.  
  
  