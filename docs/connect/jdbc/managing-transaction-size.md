---
title: Verwalten des Transaktionsumfangs | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 82900342-bc80-445f-98a4-468a303aae1e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 22ef6f66c6a0f1685b824c9c89689465c53f4d2d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47810598"
---
# <a name="managing-transaction-size"></a>Verwalten des Transaktionsumfangs
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Wenn Sie mit Transaktionen arbeiten, ist es wichtig, die Transaktionen so kurz wie möglich zu halten. Der Standardmodus von „auto-commit“, den Sie mithilfe der [setAutoCommit](../../connect/jdbc/reference/setautocommit-method-sqlserverconnection.md)-Methode aktivieren und deaktivieren können, führt einen Commit für jede Aktion aus. Dies ist der Modus, mit dem die meisten Entwickler am bequemsten arbeiten können.  
  
 Wenn Sie manuelle Transaktionen verwenden, stellen Sie sicher, dass im Code so schnell wie möglich ein Commit für die Transaktion ausgeführt wird. Durch das Offenhalten einer Transaktion wird blockiert, dass andere Benutzer auf die Daten zugreifen können. Es ist beispielsweise ein gutes Programmierverfahren, einen rollback-Aufruf im catch-Block und einen commit-Aufruf im finally-Block einzufügen. Dies ist jedoch vom Entwurf der Anwendung abhängig.  
  
 Wenn der Umfang der Transaktionen klein gehalten wird, führt dies zu einer besseren Parallelität. Wenn Sie beispielsweise eine manuelle Transaktion beginnen und 10.000 Zeilen in einer Tabelle mit 20.000 Zeilen ändern, ist die Hälfte der Tabelle für alle anderen Benutzer blockiert, auch wenn sie die Daten nur lesen. Durch das Reduzieren der Änderungen auf 2.000 Zeilen bleiben 90 Prozent der Tabelle verfügbar.  
  
 Stellen Sie außerdem sicher, dass Sie die Timeouteinstellung für Sperren verwenden, wenn die Anwendung Probleme mit Sperren erwartet und hierfür Timeouts benötigt. Dies kann auf einfache Weise mithilfe der [setLockTimeout](../../connect/jdbc/reference/setlocktimeout-method-sqlserverdatasource.md)-Methode ausgeführt werden. Der Standardwert für das Sperrtimeout ist -1. Dies bedeutet, dass beim Warten auf die Sperre unendlich lang blockiert wird. Sie können das Sperrtimeout auf 30 Sekunden festlegen. So tritt bei der gesperrten Verbindung nach 30 Sekunden ein Timeout auf, wenn eine Blockierung durch eine andere Verbindung vorliegt.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Verbessern von Leistung und Zuverlässigkeit mit dem JDBC-Treiber](../../connect/jdbc/improving-performance-and-reliability-with-the-jdbc-driver.md)  
  
  
