---
title: Konfigurationskomponenten | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bcf7d34f8faf70f57373ad1a5dae55261799145b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63198410"
---
# <a name="configuration-components"></a>Konfigurationskomponenten
> [!NOTE]  
>  Ab Windows XP und Windows Server 2003, ist ODBC in das Windows-Betriebssystem enthalten. Sie sollten nur explizit ODBC in früheren Versionen von Windows installieren.  
  
 Datenquellen werden vom Installationsprogramm-DLL, konfiguriert in aktivieren Aufrufe Treiber DLLs und die Translator-Setup-DLLs einrichten, wenn sie benötigt werden. Das Installationsprogramm-DLL ist entweder direkt über die Systemsteuerung aufgerufen oder geladen und aufgerufen, die von einem anderen Programm, bekannt als die *-Verwaltungsprogramm*. Die folgende Abbildung zeigt die Beziehung zwischen den Konfigurationskomponenten.  
  
 ![Beziehung zwischen Konfigurationskomponenten](../../../odbc/reference/install/media/pr30.gif "pr30")  
  
 Weitere Informationen zu diesen Komponenten finden Sie unter den folgenden Themen am Ende dieses Abschnitts.  
  
-   [Setupprogramm](../../../odbc/reference/install/setup-program.md)  
  
-   [Installationsprogramm-DLL](../../../odbc/reference/install/installer-dll.md)  
  
-   [Setup-DLL für Treiber](../../../odbc/reference/install/driver-setup-dll.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Installationskomponenten](../../../odbc/reference/install/installation-components.md)
