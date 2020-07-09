---
title: Serverkonfigurationsoptionen für den Zugriffsüberprüfungscache | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- access check cache option
- access check cache bucket count
- access check cache quota
ms.assetid: 0a992ea8-3ec6-4a4d-97b5-460ae7326247
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: feed895eeb7b11b4c41c51c4c26859a1057d2733
ms.sourcegitcommit: 21c14308b1531e19b95c811ed11b37b9cf696d19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/09/2020
ms.locfileid: "86158758"
---
# <a name="access-check-cache-server-configuration-options"></a>Serverkonfigurationsoptionen für den Zugriffsüberprüfungscache
Beim Zugriff auf Datenbankobjekte durch [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]wird die Zugriffsprüfung in einer internen Struktur zwischengespeichert, die als **access check result cache**bezeichnet wird. 
  
Mit der Option **Cache Anzahl für Zugriffs Überprüfung** wird die Anzahl der Hash-Bucket gesteuert, die für den Ergebnis Cache der Zugriffs Überprüfung verwendet werden. 

Die Option **Cache Kontingent für Zugriffs Überprüfung** steuert die Anzahl der Einträge, die im Ergebnis Cache für die Zugriffs Überprüfung gespeichert werden. Wenn die maximale Anzahl von Einträgen erreicht wird, werden die ältesten Einträge aus dem Ergebnis Cache für die Zugriffs Überprüfung entfernt.
  
Die Standardwerte 0 geben an, dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] diese Optionen verwaltet. Von [!INCLUDE[ssKatmai](../../includes/ssKatmai-md.md)] bis [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] werden die Standardwerte in die folgenden internen Konfigurationen übersetzt:
-   Bei der Bucketanzahl für den Zugriffs Check Cache legt der Wert 0 einen Standardwert von 256-Bucket für die x86-Architektur und 2.048-Bucket für x64-und IA-64-Architekturen fest.
-   Bei der Zugriffs Überprüfung des Cache Kontingents legt der Wert 0 einen Standardwert von 1.024 Einträge für die x86-Architektur und 28.192.048-Bucket für x64-und IA-64-Architekturen fest.

In seltenen Fällen kann die Leistung durch das Ändern dieser Optionen verbessert werden. Beispielsweise können Sie die Größe des Ergebnis Caches für die Zugriffs Überprüfung verringern, wenn zu viel Arbeitsspeicher verwendet wird. Sie können auch die Größe des Ergebnis Caches für die Zugriffs Überprüfung erhöhen, wenn Sie bei einer Neuberechnung der Berechtigungen eine hohe CPU-Auslastung erzielen.

> [!IMPORTANT]
> Microsoft empfiehlt, diese Optionen nur auf Anweisung des Microsoft-Kundendiensts zu ändern.
  
## <a name="see-also"></a>Weitere Informationen  
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
