---
title: Einrichten einer verschlüsselten Spiegeldatenbank | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- cryptography [SQL Server], database mirroring
- encryption [SQL Server], database mirroring
- database master key [SQL Server], database mirroring
- mirror database [SQL Server]
- database mirroring [SQL Server], security
ms.assetid: 7329a575-be29-46e0-abc6-1344db37920c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e96342ca114ae06d2c1d75954ccd32a674f900a4
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68025230"
---
# <a name="set-up-an-encrypted-mirror-database"></a>Einrichten einer verschlüsselten Spiegeldatenbank
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Geben Sie zum Aktivieren der automatischen Entschlüsselung des Datenbank-Hauptschlüssels einer Spiegeldatenbank das Kennwort an, das zum Verschlüsseln des Hauptschlüssels der Spiegelserverinstanz verwendet wurde. [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] und höhere Versionen schließen Mechanismen zum Übertragen des Kennworts ein. Erstellen Sie vor Beginn der Datenbankspiegelung eine Berechtigung für den Datenbank-Hauptschlüssel mithilfe von **sp_control_dbmasterkey_password** . Sie müssen diesen Vorgang für jede Datenbank wiederholen, die Sie spiegeln möchten. Weitere Informationen finden Sie unter [sp_control_dbmasterkey_password &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-control-dbmasterkey-password-transact-sql.md).  
  
> [!CAUTION]  
>  Aktivieren Sie keine Failoverentschlüsselung einer Datenbank, auf die **sa** und andere Serverprinzipale mit hohen Berechtigungen nicht zugreifen dürfen. Sie können eine Datenbank so konfigurieren, dass ihre Schlüsselhierarchie nicht vom Diensthauptschlüssel entschlüsselt werden kann. Diese Option wird als sicherer Schutz für Datenbanken unterstützt, die Informationen enthalten, auf die **Systemadministratoren** oder andere Serverprinzipale mit hohen Berechtigungen nicht zugreifen dürfen sollten. Durch die Aktivierung der Failoverentschlüsselung einer solchen Datenbank wird dieser sichere Schutz entfernt, wodurch **Systemadministratoren** und andere Serverprinzipale mit hohen Berechtigungen die Datenbank entschlüsseln können.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_control_dbmasterkey_password &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-control-dbmasterkey-password-transact-sql.md)   
 [CREATE MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-master-key-transact-sql.md)   
 [ALTER MASTER KEY (Transact-SQL)](../../t-sql/statements/alter-master-key-transact-sql.md)   
 [Verschlüsselungshierarchie](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [Einrichten der Datenbankspiegelung &#40;SQL Server&#41;](../../database-engine/database-mirroring/setting-up-database-mirroring-sql-server.md)  
  
  
