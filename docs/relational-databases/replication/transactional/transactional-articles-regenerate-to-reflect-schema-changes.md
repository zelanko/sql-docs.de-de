---
title: Erneutes Generieren von benutzerdefinierten Prozeduren für Schemaänderungen (transaktionsbasiert)
description: Hier wird erläutert, wie Sie benutzerdefinierte gespeicherte Transaktionsprozeduren erneut generieren, um Schemaänderungen bei der Transaktionsreplikation widerzuspiegeln.
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- custom procedures [SQL Server replication]
- transactional replication, replicating schema changes
- schemas [SQL Server replication], replicating changes
ms.assetid: ccf68a13-e748-4455-8168-90e6d2868098
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 9616c11a1d17f2634ef0b525dd23ac8b31203ddc
ms.sourcegitcommit: 21c14308b1531e19b95c811ed11b37b9cf696d19
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/09/2020
ms.locfileid: "86159388"
---
# <a name="transactional-articles---regenerate-to-reflect-schema-changes"></a>Transaktionsartikel – Regenerieren zur Wiedergabe von Schemaänderungen
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../../includes/applies-to-version/sql-asdbmi.md)]
  Änderungen von Daten auf den Abonnenten werden bei der Transaktionsreplikation standardmäßig mithilfe von gespeicherten Prozeduren vorgenommen, die durch interne Prozeduren für jeden Tabellenartikel in der Veröffentlichung generiert werden. Die drei Prozeduren (eine für Einfügungen, eine für Updates und eine für Löschungen) werden auf den Abonnenten kopiert und ausgeführt, wenn eine Einfügung, ein Update oder eine Löschung auf den Abonnenten repliziert wird. Wenn bei einer Tabelle auf einem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Verleger eine Schemaänderung vorgenommen wird, werden diese Prozeduren bei der Replikation automatisch erneut generiert, indem derselbe Satz interner Skriptprozeduren aufgerufen wird, damit die neuen Prozeduren dem neuen Schema entsprechen (die Replikation von Schemaänderungen wird bei Oracle-Verlegern nicht unterstützt).  
  
 Es ist auch möglich, benutzerdefinierte Prozeduren anzugeben, die an die Stelle einer oder mehrerer Standardprozedur(en) treten. Benutzerdefinierte Prozeduren müssen immer dann geändert werden, wenn sich die Schemaänderung auf die jeweilige Prozedur auswirkt. Wenn eine Prozedur z. B. auf eine Spalte verweist, die in einer Schemaänderung gelöscht wurde, müssen die Verweise auf diese Spalte aus der Prozedur entfernt werden. Für die Weitergabe einer neuen benutzerdefinierten Prozedur an Abonnenten durch Replikation gibt es die folgenden beiden Möglichkeiten:  
  
-   Die erste Möglichkeit besteht in der Verwendung einer benutzerdefinierten Skriptprozedur zum Ersetzen der von der Replikation verwendeten Standardprozeduren:  
  
    1.  Stellen Sie beim Ausführen von [sp_addarticle &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) sicher, dass für das `@schema_option`-0x02-Bit **TRUE** festgelegt ist.  
  
    2.  Führen Sie [sp_register_custom_scripting &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-register-custom-scripting-transact-sql.md) aus, und geben Sie für den `@type`-Parameter „insert“, „update“ oder „delete“ und für den `@value`-Parameter den Namen der benutzerdefinierten Skriptprozedur an.  
  
     Wenn das nächste Mal eine Schemaänderung vorgenommen wird, ruft die Replikation diese gespeicherte Prozedur auf, um die Definition für die neue benutzerdefinierte gespeicherte Prozedur auszugeben. Anschließend wird die Prozedur an die einzelnen Abonnenten weitergegeben.  
  
-   Die zweite Möglichkeit besteht darin, ein Skript zu verwenden, das eine neue benutzerdefinierte Prozedurdefinition enthält:  
  
    1.  Legen Sie bei der Ausführung von [sp_addarticle &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) für das `@schema_option`-0x02-Bit den Wert **FALSE** fest, damit die Replikation nicht automatisch benutzerdefinierte Prozeduren auf dem Abonnenten generiert.  
  
    2.  Erstellen Sie vor jeder Schemaänderung eine neue Skriptdatei, und registrieren Sie das Skript bei der Replikation, indem Sie [sp_register_custom_scripting &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-register-custom-scripting-transact-sql.md) ausführen. Geben Sie für den `@type`-Parameter den Wert „custom_script“ und für den Parameter `@value` den Pfad zum Skript auf dem Verleger an.  
  
     Bei der nächsten relevanten Schemaänderung wird dieses Skript innerhalb derselben Transaktion wie der DDL-Befehl auf allen Abonnenten ausgeführt. Nach Abschluss der Schemaänderung wird die Registrierung des Skripts aufgehoben. Damit das Skript bei einer weiteren Schemaänderung wieder ausgeführt wird, müssen Sie es erneut registrieren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Angeben der Weitergabemethode für Änderungen bei Transaktionsartikeln](../../../relational-databases/replication/transactional/transactional-articles-specify-how-changes-are-propagated.md)   
 [Vornehmen von Schemaänderungen in Veröffentlichungsdatenbanken](../../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md)  
  
  
