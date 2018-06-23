---
title: Wählen eines Konfliktlösers | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- default conflict resolver
- articles [SQL Server replication], conflict resolution
- conflict resolution [SQL Server replication], merge replication
ms.assetid: b7dec3fa-d9d9-409d-b946-f9b9a3202829
caps.latest.revision: 32
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 6f3a256b58bb2bf93e99a25758bcae5e6abd8dd5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36149038"
---
# <a name="choose-a-resolver"></a>Auswählen von Resolvern
  Beim Auswählen eines Konfliktlösers sollten Sie die Bedeutung der Konfliktlösung in Ihrer Anwendung und die Frage berücksichtigen, ob der standardmäßige prioritätsbasierte Konfliktlöser verwendet werden kann oder ob ein Artikelkonfliktlöser verwendet werden muss.  
  
 Wenn die Daten partitioniert werden, ohne dass mehrere Benutzer in dieselben Partitionen schreiben, und die Replikationstopologie relativ einfach ist (ein Verleger und wenige Abonnenten) sollten Konflikte selten oder nie vorkommen. In diesen Umgebungen ist eine komplexe Konfliktauflösungsstrategie eher nicht notwendig. Es wird eine Strategie empfohlen, die die Standardeinstellungen für die Konfliktlösung, Clientabonnements und eine Richtlinie verwendet, bei der die erste Änderung gewinnt. Wenn die Topologie komplexer ist (z. B. weil Wiederveröffentlichungsabonnenten verwendet werden), sind Serverabonnements mit spezifischen Prioritäten möglicherweise geeigneter.  
  
 Die Verwendung eines Artikelkonfliktlösers wird empfohlen, wenn die Anforderungen in Ihrem Unternehmen eine genauer abgestimmte Lösung als die mit dem Standardkonfliktlöser verfügbare Lösung nötig machen. Wenn Sie sich für die Verwendung eines Artikelkonfliktlösers entscheiden, empfiehlt sich die Verwendung eines Geschäftslogikhandlers. Weitere Informationen finden Sie unter [Ausführen von Geschäftslogik während der Mergesynchronisierung](execute-business-logic-during-merge-synchronization.md).  
  
 Letztendlich sollte sich die Entscheidung, ob der Standardkonfliktlöser oder ein Artikelkonfliktlöser verwendet wird, nach den Daten und den Geschäftslogikanforderungen der Anwendung richten. Nehmen wir z. B. eine Firma, in der Mitarbeiter in eine Gruppe von nicht partitionierten Tabellen auf unterschiedlichen Abonnenten Kundeneinstufungsdaten eingeben. Die Mitarbeiter gehören unterschiedlichen Funktionskategorien (Filialleiter, Abteilungsleiter, Vertriebsmitarbeiter) an. Für die Entscheidung, welche Daten Priorität erhalten, soll die jeweilige Funktionskategorie herangezogen werden. In diesem Fall kann ein Artikelkonfliktlöser erstellt werden, der beim Auftreten eines Konflikts anhand der Funktionskategorie aus dem Artikel den Prioritätsgewinner bestimmt.  
  
 Wenn die Wahrscheinlichkeit von häufigen Konflikten relativ hoch ist, sollten Sie bei der Implementierung einer Konfliktauflösungsstrategie u. a. die folgenden Punkte berücksichtigen:  
  
|Konfliktlösungsproblem|Empfehlung|  
|-------------------------------|--------------------|  
|Verschiedene Kategorien von Benutzern erfordern verschiedene Prioritätswerte.|Verwenden Sie den Standardkonfliktlöser, und erstellen Sie Serverabonnements mit unterschiedlichen Prioritätswerten.<br /><br /> -Oder-<br /><br /> Verwenden Sie einen Artikelkonfliktlöser, der eine Spalte mit Autoritätswerten im Artikel erkennt und damit die Konfliktlösung vereinfacht.|  
|Lösung wird gewünscht, bei der die erste Änderung den Konflikt gewinnt.|Verwenden Sie den Standardkonfliktlöser, und erstellen Sie Clientabonnements.|  
|Mehrere Benutzer, die dieselbe Datenzeile ändern, sollen zulässig sein, sofern keine konfliktverursachenden Änderungen an derselben Spalte vorgenommen werden.|Verwenden Sie entweder den Standardkonfliktlöser oder einen Artikelkonfliktlöser mit aktivierter Nachverfolgung auf Spaltenebene.|  
|Mehrere Änderungen an einem Wert in einer Zeile sollen als Konflikt markiert werden.|Verwenden Sie entweder den Standardkonfliktlöser oder einen Artikelkonfliktlöser mit Nachverfolgung auf Zeilenebene.|  
|Mehrere Änderungen an einem Wert in einem logischen Datensatz sollen als Konflikt markiert werden.|Verwenden Sie den Standardkonfliktlöser mit Nachverfolgung auf der Ebene des logischen Datensatzes (bei Verwendung logischer Datensätze werden weder benutzerdefinierte Konfliktlöser noch Geschäftslogikhandler unterstützt).|  
|Die resultierenden Konfliktdaten müssen sich von den ursprünglichen Konfliktdaten unterscheiden.|Verwenden Sie einen Artikelkonfliktlöser, der neue Werte berechnet.|  
  
## <a name="see-also"></a>Siehe auch  
 [Ermitteln und Lösen von Konflikten in logischen Datensätzen](advanced-merge-replication-conflict-resolving-in-logical-record.md)   
 [Erweiterte Konflikterkennung und -lösung bei der Mergereplikation](advanced-merge-replication-conflict-detection-and-resolution.md)   
 [Erneutes Veröffentlichen von Daten](../republish-data.md)  
  
  