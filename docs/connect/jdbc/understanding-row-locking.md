---
title: Grundlegendes zu Zeilensperren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 63c76a2f-f2b9-461f-8904-acbda0169ac3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e2bb0038320ccefe0e143ca7c18fbf7e117c4a75
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47719658"
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
