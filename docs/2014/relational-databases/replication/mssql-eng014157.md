---
title: MSSQL_ENG014157 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014157 error
ms.assetid: 1a0890cf-d977-43e0-a2ba-9c5ff1a8f856
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 26befe89debb6fd890abeee9ea258e53a028b50c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63191501"
---
# <a name="mssql_eng014157"></a>MSSQL_ENG014157
    
## <a name="message-details"></a>Meldungsdetails  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|14157|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Symbolischer Name||  
|Meldungstext|Das Abonnement des Abonnenten '%1!s!' für die %2!s!-Veröffentlichung ist abgelaufen und wurde gelöscht.|  
  
## <a name="explanation"></a>Erklärung  
 Ein Abonnent muss innerhalb der angegebenen Beibehaltungsdauer für die Veröffentlichung mit dem Verleger synchronisiert werden. Falls ein Abonnent nicht innerhalb dieses Zeitraums synchronisiert wird, läuft das Abonnement ab. Weitere Informationen finden Sie unter [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md).  
  
## <a name="user-action"></a>Benutzeraktion  
 Das Abonnement muss neu erstellt und initialisiert werden, damit der Abonnent wieder Datenänderungen empfangen kann:  
  
-   Weitere Informationen zum Erstellen von Abonnements finden Sie unter [Abonnieren von Veröffentlichungen](subscribe-to-publications.md).  
  
-   Informationen zum Initialisieren von Abonnements finden Sie unter [Initialisieren eines Abonnements](initialize-a-subscription.md).  
  
 Wenn die Abonnementdatenbank Änderungen enthält, die noch nicht mit dem Verleger synchronisiert wurden, können Sie mit [tablediff Utility](../../tools/tablediff-utility.md) (Hilfsprogramm) ermitteln, welche Zeilen in der Veröffentlichungs- bzw. Abonnementdatenbanken unterschiedlich sind.  
  
 Sie können die Beibehaltungsdauer für die Veröffentlichung erhöhen, um zu vermeiden, dass Abonnements ablaufen. Geben Sie keinen zu hohen Wert ein, da dies zur Speicherung von mehr Daten und Metadaten und damit einer Beeinträchtigung der Leistung führen kann. Weitere Informationen finden Sie unter [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Fehler- und Ereignisreferenz &#40;Replikation&#41;](errors-and-events-reference-replication.md)  
  
  
