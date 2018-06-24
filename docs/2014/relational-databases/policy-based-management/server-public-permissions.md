---
title: Serverberechtigungen für „public“ | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 9a276caa-ea38-473d-92bc-26302bfcf660
caps.latest.revision: 11
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a0b125841e2d3c9f03b7ba46519f80af9293a1cd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36059122"
---
# <a name="server-public-permissions"></a>Serverberechtigungen für 'public'
  Diese Regel bestimmt, ob die Serverrolle public Serverberechtigung besitzt. Jede Anmeldung, die auf dem Server erstellt wird, ist ein Element der Serverrolle public. Wenn diese Bedingung erfüllt ist, besitzt jede Anmeldung am Server Serverberechtigung.  
  
## <a name="best-practices-recommendations"></a>Empfehlungen zu Best Practices  
 Gewähren Sie der Serverrolle public keine Serverberechtigung.  
  
> [!IMPORTANT]  
>  Nach Abschluss des Setups die **öffentlichen** Rolle verfügt über `CONNECT` -Berechtigung für alle Endpunkte außer der **dedizierte Administratorverbindung**. Dies ist normal und sollte üblicherweise nicht geändert werden. (Der Zugriff wird gesteuert, mithilfe der `CONNECT SQL` Berechtigung für die beim Erstellen neuer Anmeldungen automatisch erteilt wird.)  
  
### <a name="for-more-information"></a>Weitere Informationen finden Sie unter  
 [Sichern von SQL Server](../security/securing-sql-server.md)  
  
  