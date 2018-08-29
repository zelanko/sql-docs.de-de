---
title: Grundlegendes zu Zeilensperren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 63c76a2f-f2b9-461f-8904-acbda0169ac3
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c860f4e89517631048f0929b5a6014aa83fd48bf
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2018
ms.locfileid: "42783922"
---
# <a name="understanding-row-locking"></a>Grundlegendes zu Zeilensperren

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] verwendet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Zeilensperren. Diese implementieren die Parallelitätssteuerungen zwischen mehreren Benutzern, die gleichzeitig Änderungen an einer Datenbank vornehmen. Standardmäßig werden Transaktionen und Sperren pro Verbindung verwaltet. Wenn eine Anwendung beispielsweise zwei JDBC-Verbindungen öffnet, können von einer Verbindung erhaltene Sperren nicht mit einer anderen Verbindung gemeinsam verwendet werden. Keine der Verbindungen kann Sperren erhalten, die zu Konflikten mit den Sperren der anderen Verbindung führen.

> [!NOTE]  
> Wenn Zeilensperren verwendet werden, werden alle Zeilen im Fetchpuffer gesperrt. Das Festlegen eines großen Werts für die Fetchgröße kann daher Auswirkungen auf die Parallelität haben.

Sperren werden verwendet, um Transaktionsintegrität und Datenbankkonsistenz zu gewährleisten. Sperren verhindern, dass Benutzer Daten lesen, die von anderen Benutzern geändert werden, und dass mehrere Benutzer gleichzeitig die gleichen Daten ändern. Wenn keine Sperren verwendet werden, kann dies dazu führen, dass die Daten in der Datenbank logisch falsch sind. Die für diese Daten ausgeführten Abfragen können dann unerwartete Ergebnisse zurückgeben.

> [!NOTE]  
> Weitere Informationen zu Zeilensperren in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] finden Sie unter „Sperren in [!INCLUDE[ssDE](../../includes/ssde_md.md)]“ in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation.

## <a name="see-also"></a>Weitere Informationen finden Sie unter

[Verwalten von Resultsets mit dem JDBC-Treiber](../../connect/jdbc/managing-result-sets-with-the-jdbc-driver.md)
