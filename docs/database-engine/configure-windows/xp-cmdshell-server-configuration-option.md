---
title: xp_cmdshell (Serverkonfigurationsoption)
description: Erfahren Sie mehr über die Option „xp_cmdshell“. Hier erfahren Sie, wie Sie mit dieser Option steuern, ob die erweiterte gespeicherte Prozedur „xp_cmdshell“ in SQL Server ausgeführt werden kann. Erfahren Sie, wie Sie die Option aktivieren.
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- xp_cmdshell
ms.assetid: c147c9e1-b81d-49c8-b800-3019f4d86a13
author: markingmyname
ms.author: maghan
ms.custom: contperfq4
ms.date: 06/12/2020
ms.openlocfilehash: 004a7b0a50a657632bb2b9970f0558857d416494
ms.sourcegitcommit: ae474d21db4f724523e419622ce79f611e956a22
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/20/2020
ms.locfileid: "92257979"
---
# <a name="xp_cmdshell-server-configuration-option"></a>xp_cmdshell (Serverkonfigurationsoption)

 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

In diesem Artikel wird beschrieben, wie Sie die SQL Server-Konfigurationsoption **xp_cmdshell** aktivieren. Mit dieser Option können Systemadministratoren steuern, ob die [erweiterte gespeicherte Prozedur „xp_cmdshell“](../../relational-databases/system-stored-procedures/xp-cmdshell-transact-sql.md) in einem System ausgeführt werden kann. In neuen Installationen ist die **xp_cmdshell** -Option standardmäßig deaktiviert.

Bevor Sie diese Option aktivieren, berücksichtigen Sie die möglichen Sicherheitsrisiken.

- Es wird allgemein empfohlen, die Option nicht zu aktiveren. Auch für neu entwickelten Code sollte die gespeicherte Prozedur **xp_cmdshell** nicht verwendet werden.
- Für einige ältere Anwendungen muss **xp_cmdshell** jedoch aktiviert werden. Wenn dies nicht geändert werden kann, können Sie die gespeicherte Prozedur wie nachfolgend beschrieben aktivieren.

> [!NOTE]  
> Wenn **xp_cmdshell** verwendet werden muss, wird als bewährte Methode empfohlen, diese nur für die Dauer der Task zu aktivieren, für die sie erforderlich ist.

Sie können **xp_cmdshell** entweder über die [richtlinienbasierte Verwaltung](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md) aktivieren oder indem Sie, wie im folgenden Codebeispiel veranschaulicht, die gespeicherte Systemprozedur **sp_configure** ausführen:  
  
``` sql
-- To allow advanced options to be changed.  
EXECUTE sp_configure 'show advanced options', 1;  
GO  
-- To update the currently configured value for advanced options.  
RECONFIGURE;  
GO  
-- To enable the feature.  
EXECUTE sp_configure 'xp_cmdshell', 1;  
GO  
-- To update the currently configured value for this feature.  
RECONFIGURE;  
GO  
```  
  
## <a name="next-steps"></a>Nächste Schritte

- [Erweiterte gespeicherte Prozedur „xp_cmdshell“](../../relational-databases/system-stored-procedures/xp-cmdshell-transact-sql.md)
- [Serverkonfigurationsoptionen (SQL Server)](server-configuration-options-sql-server.md)
- [Verwalten von Servern mit der richtlinienbasierten Verwaltung](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)  
