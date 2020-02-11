---
title: Verwalten von Oracle-Tabellenbereichen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Oracle publishing [SQL Server replication], managing tablespaces
- tablespaces [SQL Server replication]
ms.assetid: b8ea6c3b-01d6-4efc-bbfb-03b264530bbd
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9a6bf22c7649646506b65628f556b52fead23375
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63022296"
---
# <a name="manage-oracle-tablespaces"></a>Verwalten von Oracle-Tabellenbereichen
  Ein Tabellenbereich ist eine Einheit des Daten Bank Speichers, die in etwa einer Datei Gruppe in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]entspricht. Tabellenbereiche ermöglichen das Speichern und Verwalten von Datenbankobjekten innerhalb einzelner Gruppen. Weitere Informationen finden Sie in der Oracle-Dokumentation.  
  
 Wenn Sie eine Tabelle als Teil einer Oracle-Veröffentlichung konfigurieren, können Sie optional einen vorhandenen Oracle-Tabellenbereich angeben, der beim Speichern der Replikations-Protokollinformationen verwendet wird. Wird kein spezifischer Tabellenbereich angegeben, wird für die Replikationsobjekte der Standardtabellenbereich verwendet, der mit dem Schema für den administrativen Replikationsbenutzer verknüpft ist, das beim Konfigurieren des Verlegers konfiguriert wurde.  
  
 **So geben Sie einen Tabellenbereich für eine Artikel Protokollierungs Tabelle an**:  
  
-   Geben Sie im Dialogfeld **Artikeleigenschaften** einen Tabellenbereich an. Weitere Informationen zum Zugreifen auf dieses Dialogfeld finden Sie unter [View and Modify Publication Properties](../publish/view-and-modify-publication-properties.md).  
  
-   Verwenden Sie [sp_changearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changearticle-transact-sql). Soll **sp_changearticle**verwendet werden, geben Sie Folgendes an:  
  
    -   Der Name des Oracle-Verlegers für den **@publisher**Parameter.  
  
    -   Der Name der Oracle-Veröffentlichung für den Parameter **@publication**.  
  
    -   Der Name des Artikels für den Parameter **@article**.  
  
    -   Der Wert ' Tablespace ' für den Parameter **@property**.  
  
    -   Der Name des Tabellen Bereichs für den Parameter **@value**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren eines Oracle-Verlegers](configure-an-oracle-publisher.md)   
 [Auf dem Oracle-Verleger erstellte Objekte](objects-created-on-the-oracle-publisher.md)  
  
  
