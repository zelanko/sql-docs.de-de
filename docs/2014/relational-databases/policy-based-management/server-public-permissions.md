---
title: Serverberechtigungen für „public“ | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 9a276caa-ea38-473d-92bc-26302bfcf660
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 6f240973def97dea739c21381f38dc366deb8920
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62691471"
---
# <a name="server-public-permissions"></a>Serverberechtigungen für 'public'
  Diese Regel bestimmt, ob die Serverrolle public Serverberechtigung besitzt. Jede Anmeldung, die auf dem Server erstellt wird, ist ein Element der Serverrolle public. Wenn diese Bedingung erfüllt ist, besitzt jede Anmeldung am Server Serverberechtigung.  
  
## <a name="best-practices-recommendations"></a>Empfehlungen zu Best Practices  
 Gewähren Sie der Serverrolle public keine Serverberechtigung.  
  
> [!IMPORTANT]  
>  Nachdem das Setup abgeschlossen **** ist, verfügt `CONNECT` die public-Rolle über die Berechtigung für alle Endpunkte außer der **dedizierten Administrator Verbindung**. Dies ist normal und sollte üblicherweise nicht geändert werden. (Der Zugriff wird mit der `CONNECT SQL`-Berechtigung gesteuert, die beim Erstellen neuer Anmeldungen automatisch erteilt wird.)  
  
### <a name="for-more-information"></a>Weitere Informationen finden Sie unter  
 [Sichern von SQL Server](../security/securing-sql-server.md)  
  
  
