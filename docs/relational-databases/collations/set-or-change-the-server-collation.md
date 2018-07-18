---
title: Festlegen oder Ändern der Serversortierung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- server collations [SQL Server]
- collations [SQL Server], server
ms.assetid: 3242deef-6f5f-4051-a121-36b3b4da851d
caps.latest.revision: 34
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a1aa7c772b5a204f51a863f8c22780261156929f
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2018
ms.locfileid: "35698781"
---
# <a name="set-or-change-the-server-collation"></a>Festlegen oder Ändern der Serversortierung
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Die Serversortierung fungiert als Standardsortierung für alle Systemdatenbanken, die zusammen mit der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]installiert werden, sowie für alle neu erstellten Benutzerdatenbanken. Die Serversortierung wird bei der Installation von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] angegeben. Weitere Informationen finden Sie unter [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md).  
  
## <a name="changing-the-server-collation"></a>Ändern der Serversortierung  
 Das Ändern der Standardsortierung für eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kann ein komplexer Vorgang sein, der die folgenden Schritte umfasst:  
  
-   Sicherstellen, dass Ihnen alle Informationen oder Skripts zur Verfügung stehen, die zum erneuten Erstellen der Benutzerdatenbanken und aller darin enthaltenen Objekte erforderlich sind.  
  
-   Exportieren aller Daten mithilfe eines Tools wie z. B. dem [bcp Utility](../../tools/bcp-utility.md). Weitere Informationen finden Sie unter [Massenimport und -export von Daten &#40;SQL Server&#41;](../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md).  
  
-   Löschen aller Benutzerdatenbanken.  
  
-   Neuerstellen der Masterdatenbank unter Angabe der neuen Sortierung in der SQLCOLLATION-Eigenschaft des **setup** -Befehls. Zum Beispiel:  
  
    ```  
    Setup /QUIET /ACTION=REBUILDDATABASE /INSTANCENAME=InstanceName   
    /SQLSYSADMINACCOUNTS=accounts /[ SAPWD= StrongPassword ]   
    /SQLCOLLATION=CollationName  
    ```  
  
     Weitere Informationen finden Sie unter [Neuerstellen von Systemdatenbanken](../../relational-databases/databases/rebuild-system-databases.md).  
  
-   Erstellen aller Datenbanken und aller darin enthaltenen Objekte.  
  
-   Importieren aller Daten.  
  
> [!NOTE]  
>  Anstatt die Standardsortierung einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zu ändern, können Sie eine Standardsortierung für alle neu zu erstellenden Datenbanken angeben.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md)   
 [Festlegen oder Ändern der Datenbanksortierung](../../relational-databases/collations/set-or-change-the-database-collation.md)   
 [Festlegen oder Ändern der Spaltensortierung](../../relational-databases/collations/set-or-change-the-column-collation.md)   
 [Neuerstellen von Systemdatenbanken](../../relational-databases/databases/rebuild-system-databases.md)  
  
  
