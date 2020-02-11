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
manager: craigg
ms.openlocfilehash: 479b0d562ffb78bc0003ca320eea0a85ab172430
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62721690"
---
# <a name="connect-to-server-oracle-connection-properties"></a>Verbindung mit Server herstellen (Oracle), Verbindungseigenschaften
  Mithilfe der Registerkarte **Verbindungs Eigenschaften** des Dialog Felds Verbindung **mit Server herstellen** können Sie eine Veröffentlichungs Option von **Gateway** oder **Complete**angeben. Nachdem ein Verleger identifiziert wurde, kann diese Option nicht mehr geändert werden, ohne dass der Verleger gelöscht und neu konfiguriert wird. Weitere Informationen finden Sie unter [Konfigurieren eines Oracle-Verlegers](non-sql/configure-an-oracle-publisher.md).  
  
## <a name="options"></a>Tastatur  
 **Verlegertyp**  
 Wählen Sie **Gateway** oder **Vollständig**aus. Die **Complete** -Option ist so konzipiert, dass Momentaufnahme-und Transaktions Veröffentlichungen mit dem kompletten Satz unterstützter Funktionen für die Veröffentlichung von Oracle bereitgestellt werden. Die Option **Gateway** bietet spezielle Designoptimierungen, um die Leistung in Fällen zu verbessern, in denen die Replikation als Gateway zwischen Systemen verwendet wird. Sie können die Option **Gateway** nicht verwenden, wenn Sie planen, dieselbe Tabelle in mehreren Transaktionsveröffentlichungen zu veröffentlichen. Wenn Sie **Gateway**auswählen, kann eine Tabelle höchstens in einer Transaktionsveröffentlichung und in einer beliebigen Zahl an Momentaufnahmeveröffentlichungen erscheinen.  
  
 **Timeouts**  
 Geben Sie an, [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wie lange der Verteiler versuchen soll, eine Verbindung mit dem Oracle-Verleger herzustellen, bevor ein Timeout Fehler auftritt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Begriffe im Zusammenhang mit dem Veröffentlichen von Oracle-Daten](non-sql/glossary-of-terms-for-oracle-publishing.md)   
 [Leistungsoptimierung für Oracle-Verleger](non-sql/performance-tuning-for-oracle-publishers.md)  
  
  
