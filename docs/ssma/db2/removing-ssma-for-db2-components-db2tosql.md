---
title: Removing SSMA for DB2 Components (DB2ToSQL) entfernen | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 4ee0d698-6246-48eb-b963-d62be81cab6a
caps.latest.revision: 6
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 6f93ca145c96e2cc9b6d86e0ebc8c2c9899afad9
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2018
ms.locfileid: "40396485"
---
# <a name="removing-ssma-for-db2-components-db2tosql"></a>Removing SSMA for DB2 Components (DB2ToSQL) entfernen
Nach Abschluss des Migrieren von Datenbanken aus DB2 in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], empfiehlt es sich um SSMA-Komponenten zu deinstallieren. Sie können die Clientkomponenten jederzeit deinstallieren. Allerdings sollten Sie nicht das Erweiterungspaket aus Deinstallieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] es sei denn, Ihre migrierten Datenbanken nicht mehr Funktionen in der **ssma_DB2** Schema der **Sysdb** Datenbank.  
  
## <a name="uninstalling-the-ssma-for-db2-client"></a>Deinstallieren von SSMA für DB2-Client  
Sie können mit SSMA Deinstallieren **Software**.  
  
**So deinstallieren Sie SSMA**  
  
1.  Öffnen Sie in der Systemsteuerung **Software**.  
  
2.  Wählen Sie  **[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant für DB2**, und klicken Sie dann auf **entfernen**.  
  
3.  Um zu bestätigen, dass Sie SSMA deinstallieren möchten, klicken Sie auf **Ja**.  
  
## <a name="uninstalling-the-extension-pack"></a>Deinstallieren der Erweiterung Packs  
Wenn Sie sicher sind, verwenden Ihre migrierten Datenbanken nicht Objekte in der **sysdb.ssma_DB2** Schema, das Erweiterungspaket kann durch das Löschen aus dem Schema entfernt – es gibt keine Windows-Deinstallation ist  
  
## <a name="see-also"></a>Siehe auch  
[Installieren von SSMA für DB2-Client &#40;DB2ToSQL&#41;](../../ssma/db2/installing-ssma-for-db2-client-db2tosql.md)  
[Installieren von SSMA-Komponenten auf SQLServer &#40;DB2ToSQL&#41;](../../ssma/db2/installing-ssma-components-on-sql-server-db2tosql.md)  
  
