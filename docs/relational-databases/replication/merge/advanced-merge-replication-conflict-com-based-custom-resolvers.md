---
title: COM-basierte benutzerdefinierte Konfliktlöser | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- COM-based resolvers [SQL Server replication]
- custom resolvers [SQL Server replication]
ms.assetid: 94195797-ad7a-4962-a8e3-b259cd13aa38
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e6555af4448af4e9e1e4e14f2e4e23f1407f0681
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63028937"
---
# <a name="advanced-merge-replication-conflict---com-based-custom-resolvers"></a>Erweiterte Konflikten bei der Mergereplikation – COM-basierte benutzerdefinierte Konfliktlöser
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Benutzerdefinierte Konfliktlöser ermöglichen eine höhere Flexibilität als der Standardmechanismus für die Konfliktlösung. Darüber hinaus kann mit Ihnen Geschäftslogik implementiert werden, die von den Anwendungen benötigt wird, die die replizierten Daten verwenden. Ein COM-basierter benutzerdefinierter Konfliktlöser ist eine DLL (Dynamic Link Library), die die **ICustomResolver** -COM-Schnittstelle, deren Methoden und Eigenschaften sowie andere unterstützende Schnittstellen und Typdefinitionen implementiert, die speziell für die Konfliktlösung entworfen wurden.  
  
> [!NOTE]  
>  Es wird empfohlen, nach Möglichkeit einen Geschäftslogikhandler statt eines COM-basierten benutzerdefinierten Konfliktlösers zu verwenden. Weitere Informationen zu Geschäftslogikhandlern finden Sie unter [Ausführen der Geschäftslogik während der Mergesynchronisierung](../../../relational-databases/replication/merge/execute-business-logic-during-merge-synchronization.md).  
  
 Zum Erstellen eines benutzerdefinierten COM-Konfliktlösers können Sie die in der Datei replrec.dll bereitgestellte Typbibliothek verwenden. Standardmäßig wird diese Bibliothek unter [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]COM installiert.  
  
 Sie müssen Folgendes vor dem Schreiben eines benutzerdefinierten COM-Konfliktlösers entscheiden:  
  
-   Die Typen von Zeilenänderungen, die aufgelöst werden sollen (z. B. Updates, Einfügungen und Löschungen), und ob der Konfliktlöser beim Upload und/oder dem Download von Mergeänderungen aufgerufen werden soll. Sie können einen Änderungstyp, alle Änderungen oder eine beliebige Kombination daraus angeben. Der Standardkonfliktlöser für Mergeprozesse verarbeitet alle Konflikte, die nicht von einem benutzerdefinierten Konfliktlöser abgedeckt werden.  
  
-   Ob beim Lösen des Konflikts das Protokollieren auf Spaltenebene verwendet werden soll. Wenn das Protokollieren auf Spaltenebene aktiviert ist, werden nur Daten in den Spalten, in denen ein Konflikt vorhanden ist, als Konflikt markiert; anderenfalls werden die Daten zusammengeführt. Konflikte werden jedoch wie bei der Nachverfolgung auf Zeilenebene gelöst: Der Prioritätsgewinner überschreibt die gesamte Datenzeile (die Daten können jedoch eine Mischung aus Werten vom Verleger, Werten von den Abonnenten oder geänderten Werten sein, die weder vom Verleger noch von den Abonnenten stammen). Weitere Informationen finden Sie unter [Erkennen und Beseitigen von Konflikten bei der Mergereplikation](../../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md).  
  
 Informationen zum Implementieren eines COM-basierten benutzerdefinierten Konfliktlösers finden Sie unter [Implementieren eines benutzerdefinierten Konfliktlösers für einen Mergeartikel](../../../relational-databases/replication/implement-a-custom-conflict-resolver-for-a-merge-article.md)  
  
 Ein benutzerdefinierter Konfliktlöser wird für einen Artikel und nicht für eine vollständige Veröffentlichung angegeben. Derselbe Konfliktlöser kann mit mehreren Artikeln verwendet werden, jedoch bezieht sich die Logik in benutzerdefinierten Konfliktlösern häufig auf eine bestimmte Tabelle. Wenn der in einer Tabelle verwendete Artikel nach dem Erstellen des Konfliktlösers geändert wird (z. B. durch Umbenennen des bei der Konfliktlösung verwendeten Spaltennamens), muss der Konfliktlöser gegebenenfalls geändert und erneut kompiliert werden.  
  
 Informationen zum Angeben eines benutzerdefinierten Konfliktlösers finden Sie unter [Angeben eines Mergeartikelkonfliktlösers](../../../relational-databases/replication/publish/specify-a-merge-article-resolver.md).  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Erweiterte Konflikterkennung und -lösung der Mergereplikation](../../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [Microsoft-COM-basierte Konfliktlöser](../../../relational-databases/replication/merge/advanced-merge-replication-conflict-com-based-resolvers.md)  
  
  
