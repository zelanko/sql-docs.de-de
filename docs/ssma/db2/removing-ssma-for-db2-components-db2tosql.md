---
title: Entfernen von SSMA für DB2-Komponenten (DB2ToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 4ee0d698-6246-48eb-b963-d62be81cab6a
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 25c8222009c2ea9358c0bab2ad5ae077588fb3cb
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68060094"
---
# <a name="removing-ssma-for-db2-components-db2tosql"></a>Entfernen von SSMA für DB2-Komponenten (DB2ToSQL)
Wenn Sie die Migration von Datenbanken von DB2 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zu abgeschlossen haben, können Sie SSMA-Komponenten deinstallieren. Sie können die Client Komponenten jederzeit deinstallieren. Sie sollten das Erweiterungspaket jedoch nicht von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] deinstallieren, es sei denn, die migrierten Datenbanken verwenden keine Funktionen mehr im **ssma_DB2** Schema der **sysdb** -Datenbank.  
  
## <a name="uninstalling-the-ssma-for-db2-client"></a>Deinstallieren von SSMA für DB2-Client  
Sie können SSMA **mithilfe der**Option Software deinstallieren.  
  
**So deinstallieren Sie SSMA**  
  
1.  Öffnen Sie in der Systemsteuerung **Programme hinzufügen/entfernen**.  
  
2.  Wählen Sie ** [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant für DB2 aus**, und klicken Sie dann auf **Entfernen**.  
  
3.  Um zu bestätigen, dass Sie SSMA deinstallieren möchten, klicken Sie auf **Ja**.  
  
## <a name="uninstalling-the-extension-pack"></a>Deinstallieren des Erweiterungspakets  
Wenn Sie sicher sind, dass die migrierten Datenbanken keine Objekte im **sysdb. ssma_DB2** -Schema verwenden, können Sie das Erweiterungspaket entfernen, indem Sie es aus dem Schema löschen. es ist keine Windows-Deinstallation vorhanden.  
  
## <a name="see-also"></a>Weitere Informationen  
[Installieren von SSMA für DB2-Client &#40;DB2ToSQL&#41;](../../ssma/db2/installing-ssma-for-db2-client-db2tosql.md)  
[Installieren von SSMA-Komponenten auf SQL Server &#40;DB2ToSQL&#41;](../../ssma/db2/installing-ssma-components-on-sql-server-db2tosql.md)  
  
