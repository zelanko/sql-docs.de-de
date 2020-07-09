---
title: Serverberechtigungen für „public“ | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 9a276caa-ea38-473d-92bc-26302bfcf660
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: ffdcfcecf88bfaa12a9d1defee2fc40ef3900c0b
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85774214"
---
# <a name="server-public-permissions"></a>Serverberechtigungen für 'public'
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Diese Regel bestimmt, ob die Serverrolle public Serverberechtigung besitzt. Jede Anmeldung, die auf dem Server erstellt wird, ist ein Element der Serverrolle public. Wenn diese Bedingung erfüllt ist, besitzt jede Anmeldung am Server Serverberechtigung.  
  
## <a name="best-practices-recommendations"></a>Empfehlungen zu Best Practices  
 Gewähren Sie der Serverrolle public keine Serverberechtigung.  
  
> [!IMPORTANT]  
>  Nach Abschluss des Setups verfügt die Rolle **PUBLIC** für alle Endpunkte außer der **dedizierten Administratorverbindung** über eine **CONNECT**-Berechtigung. Dies ist normal und sollte üblicherweise nicht geändert werden. (Der Zugriff wird mit der Berechtigung **CONNECT SQL** gesteuert, die beim Erstellen neuer Anmeldungen automatisch erteilt wird.)  
  
### <a name="for-more-information"></a>Weitere Informationen finden Sie unter  
 [Sichern von SQL Server](../../relational-databases/security/securing-sql-server.md)  
  
  
