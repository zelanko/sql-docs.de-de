---
title: Verbindung mit Server herstellen (Oracle), Verbindungseigenschaften | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.oracleconnection.connectionprops.f1
helpviewer_keywords:
- Connect to Server dialog box, replication
ms.assetid: 1bb7396f-cbb2-4f88-b82b-543287ed4172
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4c76a3058283a098357701a44de48efff917acd7
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85010952"
---
# <a name="connect-to-server-oracle-connection-properties"></a>Verbindung mit Server herstellen (Oracle), Verbindungseigenschaften
  Mithilfe der Registerkarte **Verbindungseigenschaften** des Dialogfelds **Verbindung mit Server herstellen** können Sie eine Veröffentlichungsoption von **Gateway** oder **Vollständig**angeben. Nachdem ein Verleger identifiziert wurde, kann diese Option nicht mehr geändert werden, ohne dass der Verleger gelöscht und neu konfiguriert wird. Weitere Informationen finden Sie unter [Konfigurieren eines Oracle-Verlegers](non-sql/configure-an-oracle-publisher.md).  
  
## <a name="options"></a>Tastatur  
 **Herausgebertyp**  
 Wählen Sie **Gateway** oder **Vollständig**aus. Mithilfe der Option **Vollständig** kann für Momentaufnahme- und Transaktionsveröffentlichungen der vollständige Satz an unterstützten Funktionen für Oracle-Veröffentlichungen verfügbar gemacht werden. Die Option **Gateway** bietet spezielle Designoptimierungen, um die Leistung in Fällen zu verbessern, in denen die Replikation als Gateway zwischen Systemen verwendet wird. Sie können die Option **Gateway** nicht verwenden, wenn Sie planen, dieselbe Tabelle in mehreren Transaktionsveröffentlichungen zu veröffentlichen. Wenn Sie **Gateway**auswählen, kann eine Tabelle höchstens in einer Transaktionsveröffentlichung und in einer beliebigen Zahl an Momentaufnahmeveröffentlichungen erscheinen.  
  
 **Timeouts**  
 Geben Sie an, wie lange der [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Verteiler versuchen soll, eine Verbindung mit dem Oracle-Verleger herzustellen, bevor ein Timeoutfehler auftritt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Begriffe im Zusammenhang mit dem Veröffentlichen von Oracle-Daten](non-sql/glossary-of-terms-for-oracle-publishing.md)   
 [Leistungsoptimierung für Oracle-Verleger](non-sql/performance-tuning-for-oracle-publishers.md)  
  
  
