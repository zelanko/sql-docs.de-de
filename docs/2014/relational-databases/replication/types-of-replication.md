---
title: Replikationstypen | Microsoft-Dokumentation
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
- replication [SQL Server], types
ms.assetid: c1655e8d-d14c-455a-a7f9-9d2f43e88ab4
caps.latest.revision: 36
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: dfef8f2b31953356eb6e592fc89ad4e999a36225
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36050287"
---
# <a name="types-of-replication"></a>Replikationstypen
  In[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stehen für die Verwendung in verteilten Anwendungen die folgenden Replikationstypen zur Verfügung:  
  
-   Transaktionsreplikation. Weitere Informationen finden Sie unter [Transaktionsreplikation](transactional/transactional-replication.md).  
  
-   Mergereplikation. Weitere Informationen finden Sie unter [Mergereplikation](merge/merge-replication.md).  
  
-   Momentaufnahmereplikation. Weitere Informationen finden Sie unter [Momentaufnahmereplikation](snapshot-replication.md).  
  
 Für welchen Replikationstyp Sie sich bei Ihrer konkreten Anwendung entscheiden sollten, hängt von vielen Faktoren ab. So müssen z. B. die physische Replikationsumgebung, die Art und Menge der zu replizierenden Daten und die Frage berücksichtigt werden, ob die Daten auf dem Abonnenten aktualisiert werden. Bei der physischen Umgebung sind die Anzahl und der Standort der Computer in Betracht zu ziehen, die in die Replikation mit einbezogen werden sollen. Außerdem muss berücksichtigt werden, ob es sich bei diesen Computern um Clients (Arbeitsstationen, Laptops bzw. Handhelds) oder Server handelt.  
  
 Unabhängig vom jeweiligen Typ beginnen alle Replikationen typischerweise mit einer Erstsynchronisierung der veröffentlichten Objekte auf dem Verleger und den Abonnenten. Diese Erstsynchronisierung kann durch eine Replikation mit einer *Momentaufnahme*ausgeführt werden. Die Momentaufnahme ist eine Kopie aller in einer Veröffentlichung enthaltenen Objekte und Daten. Diese Momentaufnahme wird an die Abonnenten weitergegeben. Bei einigen Anwendungen ist lediglich eine Momentaufnahmereplikation erforderlich. Bei anderen Anwendungstypen hingegen ist es wichtig, dass nachfolgende Datenänderungen inkrementell an den Abonnenten weitergeleitet werden. Es gibt auch Anwendungen, bei denen Änderungen vom Abonnenten zurück an den Verleger fließen müssen. Für solche Anwendungstypen bieten die Transaktionsreplikation und die Mergereplikation entsprechende Optionen.  
  
 Datenänderungen werden bei der Momentaufnahmereplikation nicht nachverfolgt, sodass jedes Mal, wenn eine Momentaufnahme angewendet wird, die vorhandenen Daten komplett überschrieben werden. Bei der Transaktionsreplikation werden Änderungen im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Transaktionsprotokoll nachverfolgt. Bei der Mergereplikation erfolgt die Änderungsnachverfolgung mithilfe von Triggern und Metadatentabellen.  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über Replikations-Agents](agents/replication-agents-overview.md)  
  
  