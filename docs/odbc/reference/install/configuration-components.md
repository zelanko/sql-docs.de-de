---
title: Konfigurations Komponenten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], configuring
ms.assetid: 0b68ff48-12e4-41aa-b9e2-b39ed5023ea7
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 37c2518c3b18423c804631780ee4a18bff29d88b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81289011"
---
# <a name="configuration-components"></a>Konfigurationskomponenten
> [!NOTE]  
>  Ab Windows XP und Windows Server 2003 ist ODBC im Windows-Betriebssystem enthalten. Sie sollten ODBC nur in früheren Versionen von Windows explizit installieren.  
  
 Datenquellen werden von der Installer-DLL konfiguriert, die wiederum die DLLs für die Treiber Einrichtung und die Konvertierungs-Setup-DLLs bei Bedarf aufruft. Die Installationsprogramm-dll wird entweder direkt in der Systemsteuerung aufgerufen oder von einem anderen Programm geladen und aufgerufen, das als *Verwaltungs Programm*bezeichnet wird. Die folgende Abbildung zeigt die Beziehung zwischen den Konfigurations Komponenten.  
  
 ![Beziehung zwischen Konfigurationskomponenten](../../../odbc/reference/install/media/pr30.gif "pr30")  
  
 Weitere Informationen zu diesen Komponenten finden Sie in den folgenden Themen am Ende dieses Abschnitts.  
  
-   [Setupprogramm](../../../odbc/reference/install/setup-program.md)  
  
-   [Installationsprogramm-DLL](../../../odbc/reference/install/installer-dll.md)  
  
-   [Setup-DLL für Treiber](../../../odbc/reference/install/driver-setup-dll.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Installationskomponenten](../../../odbc/reference/install/installation-components.md)
