---
title: Hinzufügen einer verschlüsselten Datenbank zu einer Verfügbarkeitsgruppe
description: In diesem Artikel werden die Schritte dafür beschrieben, wie Sie eine verschlüsselte (oder vor Kurzem entschlüsselte) Datenbank zu einer AlwaysOn-Verfügbarkeitsgruppe hinzufügen.
ms.custom: seodec18
ms.date: 05/17/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: how-to
helpviewer_keywords:
- Transparent Data Encryption, AlwaysOn Availability Groups
- TDE, AlwaysOn Availability Groups
- Availability Groups [SQL Server], interoperability
ms.assetid: 09eb6ebc-3051-4fff-86a5-93524507b1fc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6ba9bc691bb3af223ea7ee16b64a808b5ef48834
ms.sourcegitcommit: cc23d8646041336d119b74bf239a6ac305ff3d31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "91110986"
---
# <a name="add-an-encrypted-database-to-an-always-on-availability-group"></a>Hinzufügen einer verschlüsselten Datenbank zu einer Always On-Verfügbarkeitsgruppe
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]

  Dieses Thema enthält Informationen zur Verwendung aktuell verschlüsselter oder vor kurzem entschlüsselter Datenbanken mit [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
 
##  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Einschränkungen  
  
-   Wenn eine Datenbank verschlüsselt ist oder sogar einen Datenbankverschlüsselungs-Schlüssel (DEK) enthält, können Sie die Datenbank nicht mithilfe von [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] oder [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] einer Verfügbarkeitsgruppe hinzufügen. Selbst wenn eine verschlüsselte Datenbank entschlüsselt wurde, enthalten ihre Protokollsicherungen möglicherweise verschlüsselte Daten. In diesem Fall ist es unter Umständen nicht möglich, die anfängliche Datensynchronisierung vollständig auf der Datenbank durchzuführen. Grund hierfür ist die Tatsache, dass für den Wiederherstellungsprotokollvorgang eventuell das Zertifikat erforderlich ist, das von den Datenbank-Verschlüsselungsschlüsseln (DEKs) verwendet wurde, und dieses Zertifikat möglicherweise nicht verfügbar ist.  
  
     So machen Sie eine entschlüsselte Datenbank verfügbar für das Hinzufügen zu einer Verfügbarkeitsgruppe mithilfe des Assistenten:  
  
    1.  Erstellen Sie eine Protokollsicherung von der primären Datenbank.  
  
    2.  Erstellen Sie eine vollständige Datenbanksicherung der primären Datenbank.  
  
    3.  Stellen Sie die Datenbanksicherung auf der Serverinstanz wieder her, die das sekundäre Replikat hostet.  
  
    4.  Erstellen Sie eine neue Protokollsicherung aus der primären Datenbank.  
  
    5.  Stellen Sie diese Protokollsicherung in der sekundären Datenbank wieder her.  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Verwandte Aufgaben  
  
-   [Manuelles Vorbereiten einer sekundären Datenbank auf eine Verfügbarkeitsgruppe &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [Verwenden des Assistenten für Verfügbarkeitsgruppen &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Verwenden des Assistenten zum Hinzufügen von Datenbanken zu Verfügbarkeitsgruppen &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/availability-group-add-database-to-group-wizard.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Transparente Datenverschlüsselung &#40;TDE&#41;](../../../relational-databases/security/encryption/transparent-data-encryption.md)  
  
  
