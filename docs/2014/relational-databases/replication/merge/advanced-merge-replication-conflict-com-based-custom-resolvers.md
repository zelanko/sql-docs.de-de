---
title: COM-basierte benutzerdefinierte Konfliktlöser | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- COM-based resolvers [SQL Server replication]
- custom resolvers [SQL Server replication]
ms.assetid: 94195797-ad7a-4962-a8e3-b259cd13aa38
caps.latest.revision: 35
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9809787b2a674b176bd7ef21a1091aecdd106d6d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37271166"
---
# <a name="com-based-custom-resolvers"></a>COM-Based Custom Resolvers
  Benutzerdefinierte Konfliktlöser ermöglichen eine höhere Flexibilität als der Standardmechanismus für die Konfliktlösung. Darüber hinaus kann mit Ihnen Geschäftslogik implementiert werden, die von den Anwendungen benötigt wird, die die replizierten Daten verwenden. Ein COM-basierter benutzerdefinierter Konfliktlöser ist eine DLL (Dynamic Link Library), die die **ICustomResolver** -COM-Schnittstelle, deren Methoden und Eigenschaften sowie andere unterstützende Schnittstellen und Typdefinitionen implementiert, die speziell für die Konfliktlösung entworfen wurden.  
  
> [!NOTE]  
>  Es wird empfohlen, nach Möglichkeit einen Geschäftslogikhandler statt eines COM-basierten benutzerdefinierten Konfliktlösers zu verwenden. Weitere Informationen zu Geschäftslogikhandlern finden Sie unter [Ausführen der Geschäftslogik während der Mergesynchronisierung](execute-business-logic-during-merge-synchronization.md).  
  
 Zum Erstellen eines benutzerdefinierten COM-Konfliktlösers können Sie die in der Datei replrec.dll bereitgestellte Typbibliothek verwenden. Standardmäßig wird diese Bibliothek unter [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]COM installiert.  
  
 Sie müssen Folgendes vor dem Schreiben eines benutzerdefinierten COM-Konfliktlösers entscheiden:  
  
-   Die Typen von Zeilenänderungen, die aufgelöst werden sollen (z. B. Updates, Einfügungen und Löschungen), und ob der Konfliktlöser beim Upload und/oder dem Download von Mergeänderungen aufgerufen werden soll. Sie können einen Änderungstyp, alle Änderungen oder eine beliebige Kombination daraus angeben. Der Standardkonfliktlöser für Mergeprozesse verarbeitet alle Konflikte, die nicht von einem benutzerdefinierten Konfliktlöser abgedeckt werden.  
  
-   Ob beim Lösen des Konflikts das Protokollieren auf Spaltenebene verwendet werden soll. Wenn das Protokollieren auf Spaltenebene aktiviert ist, werden nur Daten in den Spalten, in denen ein Konflikt vorhanden ist, als Konflikt markiert; anderenfalls werden die Daten zusammengeführt. Konflikte werden jedoch wie bei der Nachverfolgung auf Zeilenebene gelöst: Der Prioritätsgewinner überschreibt die gesamte Datenzeile (die Daten können jedoch eine Mischung aus Werten vom Verleger, Werten von den Abonnenten oder geänderten Werten sein, die weder vom Verleger noch von den Abonnenten stammen). Weitere Informationen finden Sie unter [Detect and Resolve Merge Replication Conflicts](advanced-merge-replication-resolve-merge-replication-conflicts.md).  
  
 Informationen zum Implementieren eines COM-basierten benutzerdefinierten Konfliktlösers finden Sie unter [Implement a Custom Conflict Resolver for a Merge Article](../implement-a-custom-conflict-resolver-for-a-merge-article.md).  
  
 Ein benutzerdefinierter Konfliktlöser wird für einen Artikel und nicht für eine vollständige Veröffentlichung angegeben. Derselbe Konfliktlöser kann mit mehreren Artikeln verwendet werden, jedoch bezieht sich die Logik in benutzerdefinierten Konfliktlösern häufig auf eine bestimmte Tabelle. Wenn der in einer Tabelle verwendete Artikel nach dem Erstellen des Konfliktlösers geändert wird (z. B. durch Umbenennen des bei der Konfliktlösung verwendeten Spaltennamens), muss der Konfliktlöser gegebenenfalls geändert und erneut kompiliert werden.  
  
 Informationen zum Angeben eines benutzerdefinierten Konfliktlösers finden Sie unter [Specify a Merge Article Resolver](../publish/specify-a-merge-article-resolver.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Advanced Merge Replication Conflict Detection and Resolution](advanced-merge-replication-conflict-detection-and-resolution.md)   
 [Microsoft COM-Based Resolvers](advanced-merge-replication-conflict-com-based-resolvers.md)  
  
  
