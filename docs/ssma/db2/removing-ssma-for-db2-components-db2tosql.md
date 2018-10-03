---
title: Removing SSMA for DB2 Components (DB2ToSQL) entfernen | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 4ee0d698-6246-48eb-b963-d62be81cab6a
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: b4ffde9828a2136dc01dbb37dd4009f9a2783001
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47844678"
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
  
