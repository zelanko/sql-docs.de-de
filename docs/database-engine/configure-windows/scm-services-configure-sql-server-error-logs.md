---
title: SQL Server-Fehlerprotokolle konfigurieren (Seite Allgemein) | Microsoft-Dokumentation
description: Informationen zur Wiederverwendung des Fehlerprotokolls Hier erfahren Sie, wie Sie eine maximale Protokolldateigröße und die Anzahl der vorherigen Protokolldateien festlegen können, die SQL Server sichert und archiviert.
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
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 060b3828c772a030ab095ae1bea857dc8eaa3b5a
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85651373"
---
# <a name="scm-services---configure-sql-server-error-logs"></a>SCM-Dienste: Konfigurieren von SQL Server-Fehlerprotokollen

 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  In diesem Thema wird beschrieben, wie Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Fehlerprotokolle anzeigen oder deren Wiederverwendung ändern.  

## <a name="to-open-the-configure-sql-server-error-logs-dialog-box"></a>So öffnen Sie das Dialogfeld SQL Server-Fehlerprotokolle konfigurieren  

1. Erweitern Sie im Objekt-Explorer die SQL Server-Instanz und anschließend **Verwaltung**. Klicken Sie anschließend mit der rechten Maustaste auf **Server-Protokolle**, und klicken Sie anschließend auf **Konfigurieren**.

2. Wählen Sie im Dialogfeld **SQL Server-Fehlerprotokolle konfigurieren** zwischen den folgenden Optionen aus.

    a. Anzahl von Protokolldateien

      **Beschränken Sie die Anzahl der Fehlerprotokolldateien vor der Wiederverwendung**

      Überprüft die Anzahl der bereits erstellten Fehlerprotokolle, bevor diese wiederverwendet werden. Bei jedem Start einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird ein neues Fehlerprotokoll erstellt. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] behält Sicherungen der vorherigen sechs Protokolle bei, außer wenn Sie diese Option aktivieren und eine andere maximale Anzahl von Fehlerprotokolldateien angeben.  
  
      **Maximale Anzahl von Fehlerprotokolldateien**

      Gibt die maximale Anzahl der erstellten archivierten Fehlerprotokolldateien vor der Wiederverwendung an. Der Standardwert ist 6 (ohne den aktuellen Wert). Dieser Wert bestimmt die Anzahl der vorhergehenden Sicherungsprotokolle, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vor der Wiederverwendung beibehält.

    b. Größe der Protokolldatei

      **Maximale Größe der Fehlerprotokolldatei in KB**

      Sie können die Größe der einzelnen Dateien in KB festlegen. Wenn Sie den Wert 0 belassen, ist die Protokollgröße unbegrenzt.
