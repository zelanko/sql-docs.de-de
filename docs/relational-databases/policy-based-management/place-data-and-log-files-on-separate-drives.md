---
title: Platzieren von Daten- und Protokolldateien auf separaten Laufwerken | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 6cbedc27-4d77-44ad-bed2-c23b628475a7
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: adc29ad63e3c0e089e5be954b62019806c07c0ec
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47648368"
---
# <a name="place-data-and-log-files-on-separate-drives"></a>Platzieren von Daten- und Protokolldateien auf separaten Laufwerken
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Diese Regel überprüft, ob Daten- und Protokolldateien auf separaten logischen Laufwerken platziert werden. Wenn Daten- und Protokolldateien auf demselben Gerät platziert werden, können bei diesem Gerät Konflikte und eine schlechte Leistung die Folge sein. Wenn die Dateien auf separaten Laufwerken platziert werden, kann die E/A-Aktivität sowohl für die Daten- als auch die Protokolldateien gleichzeitig stattfinden.  
  
## <a name="recommendations"></a>Empfehlungen  
 Wenn Sie eine neue Datenbank erstellen, geben Sie separate Laufwerke für die Daten und das Protokoll an. Die Datenbank muss offline geschaltet werden, um Dateien nach Erstellen der Datenbank zu verschieben. Verschieben Sie Dateien mithilfe einer der folgenden Methoden:  
  
> [!NOTE]  
>  Diese Richtlinie kann separate physische Geräte nicht durch Einbindungspunkte erkennen.  
  
-   Stellen Sie die Datenbank über die Sicherung wieder her. Verwenden Sie dazu die RESTORE DATABASE-Anweisung mit der WITH MOVE-Option.  
  
-   Trennen Sie die Datenbank, und fügen Sie sie anschließend wieder an. Geben Sie dabei separate Speicherorte für das Daten- und das Protokollgerät an.  
  
-   Geben Sie einen neuen Speicherort an. Führen Sie dazu die ALTER DATABASE-Anweisung mit der MODIFY FILE-Option aus, und starten Sie die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]neu.  
  
## <a name="for-more-information"></a>Weitere Informationen  
 [Verschieben von Datenbankdateien](../../relational-databases/databases/move-database-files.md)  
  
 [Verschieben von Benutzerdatenbanken](../../relational-databases/databases/move-user-databases.md)  
  
 [Anfügen und Trennen von Datenbanken &#40;SQL Server&#41;](../../relational-databases/databases/database-detach-and-attach-sql-server.md)  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Überwachen und Erzwingen von Best Practices mit der richtlinienbasierten Verwaltung](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
