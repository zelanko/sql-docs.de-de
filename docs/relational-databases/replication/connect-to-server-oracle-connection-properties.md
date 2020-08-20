---
description: Verbindung mit Server herstellen (Oracle), Verbindungseigenschaften
title: Verbindung mit Server herstellen (Oracle), Verbindungseigenschaften | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.oracleconnection.connectionprops.f1
helpviewer_keywords:
- Connect to Server dialog box, replication
ms.assetid: 1bb7396f-cbb2-4f88-b82b-543287ed4172
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2d6a5c942305252f8e694042633651baf981032c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88455617"
---
# <a name="connect-to-server-oracle-connection-properties"></a>Verbindung mit Server herstellen (Oracle), Verbindungseigenschaften
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
   Mithilfe der Registerkarte **Verbindungseigenschaften** des Dialogfelds **Verbindung mit Server herstellen** können Sie eine Veröffentlichungsoption von **Gateway** oder **Vollständig** angeben. Nachdem ein Verleger identifiziert wurde, kann diese Option nicht mehr geändert werden, ohne dass der Verleger gelöscht und neu konfiguriert wird. Weitere Informationen finden Sie unter [Konfigurieren eines Oracle-Verlegers](../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md).  
  
## <a name="options"></a>Optionen  
 **Herausgebertyp**  
 Wählen Sie **Gateway** oder **Vollständig**aus. Mithilfe der Option **Vollständig** kann für Momentaufnahme- und Transaktionsveröffentlichungen der vollständige Satz an unterstützten Funktionen für Oracle-Veröffentlichungen verfügbar gemacht werden. Die Option **Gateway** bietet spezielle Designoptimierungen, um die Leistung in Fällen zu verbessern, in denen die Replikation als Gateway zwischen Systemen verwendet wird. Sie können die Option **Gateway** nicht verwenden, wenn Sie planen, dieselbe Tabelle in mehreren Transaktionsveröffentlichungen zu veröffentlichen. Wenn Sie **Gateway**auswählen, kann eine Tabelle höchstens in einer Transaktionsveröffentlichung und in einer beliebigen Zahl an Momentaufnahmeveröffentlichungen erscheinen.  
  
 **Timeouts**  
 Geben Sie an, wie lange der [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Verteiler versuchen soll, eine Verbindung mit dem Oracle-Verleger herzustellen, bevor ein Timeoutfehler auftritt.  
  
## <a name="see-also"></a>Siehe auch  
 [Begriffe im Zusammenhang mit dem Veröffentlichen von Oracle-Daten](../../relational-databases/replication/non-sql/glossary-of-terms-for-oracle-publishing.md)   
 [Leistungsoptimierung für Oracle-Verleger](../../relational-databases/replication/non-sql/performance-tuning-for-oracle-publishers.md)  
  
  
