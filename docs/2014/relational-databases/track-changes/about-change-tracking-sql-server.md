---
title: Informationen zur Änderungsnachverfolgung (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- data changes [SQL Server]
- tracking data changes [SQL Server]
- change tracking [SQL Server], about change tracking
- change tracking [SQL Server]
- data [SQL Server], changing
ms.assetid: 5e0ef05a-8317-4c98-be20-b19d4cd78f12
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 23abfb7b5de5f319a15d8d255705929cc4d7293d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48220290"
---
# <a name="about-change-tracking-sql-server"></a>Informationen zur Änderungsnachverfolgung (SQL Server)
  Die Änderungsnachverfolgung ist eine einfache Lösung, die einen effizienten Änderungsnachverfolgungsmechanismus für Anwendungen bereitstellt. Normalerweise mussten Anwendungsentwickler benutzerdefinierte Mechanismen zur Änderungsnachverfolgung implementieren, damit die Anwendungen Änderungen an Daten in einer Datenbank abfragen und auf Informationen im Zusammenhang mit den Änderungen zugreifen konnten. Erstellung dieser Mechanismen war i. d. r. sehr viel Arbeit häufig verbunden und eine Kombination von Triggern, `timestamp` Spalten, neuen Tabellen zum Speichern von Nachverfolgungsinformationen und benutzerdefinierten cleanupprozessen.  
  
 Die Anforderungen an die Menge erforderlicher Informationen zu den Änderungen variieren je nach Anwendungstyp. Anwendungen können die Änderungsnachverfolgung verwenden, um die folgenden Fragen zu den an einer Benutzertabelle vorgenommenen Änderungen zu beantworten:  
  
-   Welche Zeilen wurden in einer Benutzertabelle geändert?  
  
    -   Es ist nur die Tatsache von Belang, dass eine Zeile geändert wurde, nicht jedoch, wie oft die Zeile geändert wurde oder welche Werte bei Zwischenänderungen festgelegt wurden.  
  
    -   Die aktuellen Daten können direkt aus der nachverfolgten Tabelle abgerufen werden.  
  
-   Wurde eine Zeile geändert?  
  
    -   Die Tatsache, dass eine Zeile geändert wurde, und Informationen zu der Änderung müssen verfügbar sein und zum Zeitpunkt der Änderung in derselben Transaktion aufgezeichnet werden.  
  
> [!NOTE]  
>  Wenn für eine Anwendung Informationen zu allen vorgenommenen Änderungen und die Zwischenwerte der geänderten Daten erforderlich sind, ist möglicherweise eher die Verwendung von Change Data Capture anstelle der Änderungsnachverfolgung zu empfehlen. Weitere Informationen finden Sie unter [Informationen zu Change Data Capture &#40;SQL Server&#41;](../track-changes/about-change-data-capture-sql-server.md).  
  
## <a name="one-way-and-two-way-synchronization-applications"></a>Unidirektionale und bidirektionale Synchronisierungsanwendungen  
 Anwendungen, die Daten mit einer Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] synchronisieren müssen, müssen in der Lage sein, Änderungen abzufragen. Die Änderungsnachverfolgung kann sowohl als Grundlage für unidirektionale als auch für bidirektionale Synchronisierungsanwendungen verwendet werden.  
  
### <a name="one-way-synchronization-applications"></a>Unidirektionale Synchronisierungsanwendungen  
 Es können unidirektionale Synchronisierungsanwendungen, z. B. ein Client oder eine Zwischenspeicherungsanwendung auf der mittleren Ebene, erstellt werden, die die Änderungsnachverfolgung verwenden. Wie in der folgenden Abbildung dargestellt, müssen für eine Zwischenspeicherungsanwendung Daten in [!INCLUDE[ssDE](../../includes/ssde-md.md)] gespeichert und in anderen Datenspeichern zwischengespeichert werden. Die Anwendung muss in der Lage sein, den Cache auf dem aktuellen Stand zu halten, indem dieser mit allen an den Datenbanktabellen vorgenommenen Änderungen aktualisiert wird. Es werden keine Änderungen zurück an [!INCLUDE[ssDE](../../includes/ssde-md.md)]übergeben.  
  
 ![Zeigt Anwendungen mit unidirektionaler Synchronisierung](../../database-engine/media/one-waysync.gif "Shows one-way synchronization applications")  
  
### <a name="two-way-synchronization-applications"></a>Bidirektionale Synchronisierungsanwendungen  
 Es können auch bidirektionale Synchronisierungsanwendungen erstellt werden, die die Änderungsnachverfolgung verwenden. In diesem Szenario werden die Daten in einer Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)] mit mindestens einem Datenspeicher synchronisiert. Die Daten in diesen Speichern können aktualisiert werden, und die Änderungen müssen wieder mit [!INCLUDE[ssDE](../../includes/ssde-md.md)]synchronisiert werden.  
  
 ![Zeigt Anwendungen mit bidirektionaler Synchronisierung](../../database-engine/media/two-waysync.gif "Shows two-way synchronization applications")  
  
 Ein gutes Beispiel für eine bidirektionale Synchronisierungsanwendung ist eine gelegentlich verbundene Anwendung. In einer Anwendung dieses Typs fragt eine Clientanwendung einen lokalen Speicher ab und aktualisiert diesen. Wenn eine Verbindung zwischen einem Client und einem Server verfügbar ist, führt die Anwendung die Synchronisierung mit einem Server aus, und geänderte Daten fließen in beide Richtungen.  
  
 Die bidirektionalen Synchronisierungsanwendungen müssen Konflikte erkennen können. Zu einem Konflikt kommt es, wenn in der Zeit zwischen zwei Synchronisierungen die gleichen Daten in beiden Datenspeichern geändert wurden. Wenn eine Anwendung über die Fähigkeit zum Erkennen von Konflikten verfügt, kann sichergestellt werden, dass keine Änderungen verloren werden.  
  
## <a name="how-change-tracking-works"></a>Funktionsweise der Änderungsnachverfolgung  
 Zum Konfigurieren der Änderungsnachverfolgung können Sie DDL-Anweisungen oder [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]verwenden. Weitere Informationen finden Sie unter [Aktivieren und Deaktivieren der Änderungsnachverfolgung &#40;SQL Server&#41;](../track-changes/enable-and-disable-change-tracking-sql-server.md). Zum Nachverfolgen von Änderungen muss die Änderungsnachverfolgung zuerst für die Datenbank und dann für die Tabellen, die in dieser Datenbank nachverfolgt werden sollen, aktiviert werden. Die Tabellendefinition muss in keiner Weise geändert werden, und es werden keine Trigger erstellt.  
  
 Nachdem die Änderungsnachverfolgung für eine Tabelle konfiguriert wurde, werden bei der Verwendung einer DML-Anweisung, die sich auf die Zeilen in der Tabelle auswirkt, Änderungsinformationen für jede geänderte Zeile aufgezeichnet. Zum Abfragen von geänderten Zeilen und Informationen zu den Änderungen können Sie [Änderungsnachverfolgungsfunktionen](/sql/relational-databases/system-functions/change-tracking-functions-transact-sql)verwenden.  
  
 Die Werte der Primärschlüsselspalte sind die einzigen Informationen aus der nachverfolgten Tabelle, die mit den Änderungsinformationen aufgezeichnet werden. Diese Werte identifizieren die Zeilen, die geändert wurden. Zum Abrufen der aktuellen Daten dieser Zeilen kann eine Anwendung die Werte der Primärschlüsselspalte verwenden, um die Quelltabelle mit der nachverfolgten Tabelle zu verknüpfen.  
  
 Informationen zu den an den einzelnen Zeilen vorgenommenen Änderungen können auch mithilfe der Änderungsnachverfolgung abgerufen werden. Dazu zählen z. B. der Typ des DML-Vorgangs, der die Änderung (Einfügung, Update oder Löschung) bewirkt hat, oder die Spalten, die im Rahmen eines Updatevorgangs geändert wurden.  
  
## <a name="see-also"></a>Siehe auch  
 [Aktivieren und Deaktivieren der Änderungsnachverfolgung &#40;SQL Server&#41;](../track-changes/enable-and-disable-change-tracking-sql-server.md)   
 [Verwenden der Änderungsnachverfolgung &#40;SQL Server&#41;](../track-changes/work-with-change-tracking-sql-server.md)   
 [Verwalten der Änderungsnachverfolgung &#40;SQL Server&#41;](../track-changes/manage-change-tracking-sql-server.md)   
 [Nachverfolgen von Datenänderungen &#40;SQL Server&#41;](../track-changes/track-data-changes-sql-server.md)  
  
  
